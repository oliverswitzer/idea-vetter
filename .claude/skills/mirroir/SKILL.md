---
name: mirroir
description: How to drive an iPhone via the mirroir MCP server (iPhone Mirroring automation). Covers the tools that actually work, the tools that silently fail, back-navigation, scrolling, and recovery. Invoke whenever you are about to call any mcp__mirroir__* tool or whenever an agent needs to install, onboard, or explore an iOS app on a real iPhone.
---

# Using the mirroir MCP

mirroir automates a real iPhone through macOS **iPhone Mirroring**. Most things that look like they should work like a Mac do not work, because iOS only receives the gestures iPhone Mirroring chooses to forward.

## What iOS actually receives

Through iPhone Mirroring, iOS apps receive **only** these events:

| Tool | What it does |
|---|---|
| `mcp__mirroir__tap` | Single touch at (x, y). Primary input. |
| `mcp__mirroir__double_tap` | Double-tap at (x, y). Zoom, text selection. |
| `mcp__mirroir__long_press` | Touch-and-hold. Context menus, edit mode. |
| `mcp__mirroir__swipe` | Scroll / flick between points. |
| `mcp__mirroir__drag` | Touch-and-drag. Rearranging, sliders. |
| `mcp__mirroir__type_text` | Character input — **only when a text field is already focused on the iPhone**. Tap the field first. |
| `mcp__mirroir__shake` | Device shake. |

Everything else (observation, navigation shortcuts) is Mac-side:

| Tool | What it does |
|---|---|
| `mcp__mirroir__describe_screen` | OCR the screen, return elements + exact tap coordinates + screenshot. Use this before every decision — do not guess coordinates from a screenshot. |
| `mcp__mirroir__screenshot` | Raw screenshot (no OCR). Returned inline; does not save to disk. |
| `mcp__mirroir__launch_app` | Open an installed app by name. |
| `mcp__mirroir__open_url` | Open a URL in Safari. |
| `mcp__mirroir__press_home` | Return to Home. |
| `mcp__mirroir__press_app_switcher` | Open the app switcher. |
| `mcp__mirroir__spotlight` | Open Spotlight search. **Currently broken** for typing — the field opens but `type_text` does not land characters. Use the App Library search instead (see "Finding an installed app" below). |
| `mcp__mirroir__get_orientation` | Portrait vs. landscape. |
| `mcp__mirroir__status` / `check_health` / `list_targets` | Setup diagnostics. |
| `mcp__mirroir__start_recording` / `stop_recording` | Screen recording to `.mov`. |

## Keyboard commands DO NOT work inside iOS apps

**All** keyboard commands (`Cmd+[`, `Cmd+L`, `Cmd+T`, `Cmd+R`, …) are **not forwarded** to iOS apps through iPhone Mirroring. `mcp__mirroir__press_key` with modifiers only works for Mac-level actions (e.g. shake via Ctrl+Cmd+Z). iOS apps never see keyboard shortcuts.

This is the single most common source of silent failures. If something "didn't do anything," check whether you tried to send a keystroke.

## Back navigation

The **only** reliable way to go back inside an iOS app is to tap the on-screen `<` chevron in the top ~15% of the screen.

1. `mcp__mirroir__describe_screen` to find the `<` (or the screen title with an adjacent `<`).
2. `mcp__mirroir__tap` at its coordinates.

`mcp__mirroir__press_key(key: "[", modifiers: ["command"])` does **not** work — ignore any advice or old docs that say otherwise.

## Scrolling / swiping

Use `duration_ms: 800` or higher when swiping to **scroll**. Fast swipes (300–500 ms) frequently fail to register as scroll gestures — especially in list views.

Reserve fast swipes only for flick gestures where you want momentum scrolling to carry past the swipe distance.

## Finding things on screen

Always use `describe_screen` to locate tap targets. It returns OCR text with exact coordinates in the same point system `tap` expects (0,0 = top-left of the mirroring window).

- For long pages: call with `scroll: true` to collect elements across the full scrollable area (page-absolute Y coordinates).
- If you specifically want to run vision yourself and skip mirroir's OCR, pass `skip_ocr: true` — you'll get a grid-overlaid screenshot only.

Do not estimate coordinates from a raw `screenshot`. Use `describe_screen`.

## Typing

`type_text` only works when a text field is already focused on the iPhone. The sequence is always:

1. `describe_screen` → find the field.
2. `tap` the field to focus it.
3. `type_text` with the content.

If nothing appears to be typed, the field wasn't focused — tap it again and retry.

## Finding an installed app (do NOT use Spotlight)

Spotlight (swipe-down search) is currently broken for typing — `type_text` silently drops characters even after the field looks focused. Use the **App Library** search instead:

1. `press_home` → you're on the primary Home page.
2. `swipe` **left** **multiple times** (typically 3–5 swipes — the App Library sits past every home screen page) using a **fast flick** (`duration_ms: 250–350`). Home-screen page navigation is a flick gesture, not a list scroll, so the 800ms rule does NOT apply here — a slow swipe just lets the page snap back. After each swipe, `describe_screen` to check whether you've reached the App Library (it shows category tiles like "Suggestions", "Recently Added", and a prominent search bar at the top). Keep flicking left until you see that layout.
3. `describe_screen` → locate the search bar at the top.
4. `double_tap` the search bar to focus it. A single tap often does not focus it here.
5. `type_text` with the app name — characters will now land.
6. `describe_screen` → tap the matching app icon in the filtered results.

## Saving screenshots to disk

`mcp__mirroir__screenshot` returns an image inline; it does **not** write to disk. To archive a named PNG for a report, capture the mirroring window with `screencapture`:

```bash
# Once: get the iPhone Mirroring window id
WID=$(osascript -e 'tell application "System Events" to tell process "iPhone Mirroring" to id of window 1')

# Per archival screenshot
screencapture -x -o -l "$WID" "path/to/NN-name.png"
```

Never use plain `screencapture` without `-l "$WID"` — it captures the whole desktop and may leak unrelated Mac content.

## Startup checks

Before the first real action, run:

1. `mcp__mirroir__check_health` — diagnoses window state, capture permissions, accessibility.
2. `mcp__mirroir__status` — confirms the mirroring connection is live (not paused / "no window").
3. `mcp__mirroir__list_targets` — confirms an active target.

If any of these fail, stop and report the specific blocker to the user (e.g. "Accessibility permission missing — grant it in System Settings → Privacy & Security → Accessibility"). Do not try to proceed.

## Human-in-the-loop moments

These **require** the user to physically interact with the phone. Pause, tell the user what's needed, and wait for confirmation.

- **Face ID / Touch ID / device passcode** — App Store installs, in-app Apple Pay, sensitive settings.
- **SMS / email 2FA codes** — ask the user to read out the code, then `type_text` it.
- **CAPTCHA** — ask the user to solve it on the phone directly.
- **Payment sheets** — never enter real card info; cancel out.

## MCP restart after updates

If the mirroir server itself is updated (new version of the Swift binary), the running MCP still uses the old binary. Ask the user to run `/mcp` in the coordinator to restart the server. Without a restart, source changes have no effect on tool behavior.

## Recovery

- `describe_screen` returns no elements → mirroring probably disconnected; run `status` and ask the user to re-focus the iPhone Mirroring window.
- A `tap` at OCR'd coordinates does nothing → the element was likely obscured by a keyboard or modal that wasn't in the OCR pass. Re-run `describe_screen` and check for a covering layer.
- Scrolling does nothing → increase `duration_ms` to 800+ and lengthen the swipe distance.
- Typing produces nothing → the field wasn't focused; tap it and retry.
