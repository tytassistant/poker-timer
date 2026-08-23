# Poker Tournament Timer

A fully self-contained, offline poker tournament timekeeping app — one HTML file, no dependencies, no build step. Just open `index.html` in any modern browser.

## Features

- **Blind structure editor** — add a list of small blind levels; each new session defaults to 2× the previous SB, adjustable with configurable +/− steps
- **Big blind always 2× small blind**, displayed prominently in SB/BB form
- **Session timer** — large countdown with progress bar, default 20 minutes (configurable)
- **Voice announcements** (Web Speech API) at 5 and 1 minute remaining, plus a call at each session start
- **Audio cues** — triple beep at session end, then a 3-second "Next Session" interlude before auto-advancing
- **Auto-raising** — when the predefined list is exhausted, blinds keep doubling automatically until you stop
- **Controls** — Skip to Next session, or Stop & return to setup

## Usage

1. Open `index.html`
2. Enter your starting small blind (use +/− or type), set the step size and minutes per session
3. Click **Add Session to List** for each level (or just hit **Start Tournament** to run from the current value)
4. **Start Tournament** — the timer takes over; the app advances through (and past) your list automatically

Voice output uses your OS's built-in speech synthesis; sound cues work even without a TTS voice installed.

## Tech

Vanilla HTML/CSS/JS. `AudioContext` for beeps, `SpeechSynthesis` for voice. Nothing else.
