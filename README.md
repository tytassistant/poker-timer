# Poker Tournament Timer

A fully self-contained, offline poker tournament timekeeping app — one HTML file, no dependencies, no build step. Just open `index.html` in any modern browser.

## Features

- **Blind structure editor** — add a list of small blind levels; each new session defaults to 2× the previous SB, adjustable with +/− steps of 10 (or type any value)
- **Buy-in amount** — set the starting buy-in per player (default 500)
- **Player rosters** — add named players (numbered), mark the starting dealer (always one), then **Randomize Order** or **Randomize Dealer**
- **Big blind always 2× small blind**, displayed prominently in SB/BB form
- **Session timer** — large countdown with progress bar, default 20 minutes (configurable)
- **Pause / Resume** — freeze and unfreeze the clock mid-session
- **Live player table** — on the session page, every player with their running **buy-in total** and an **elimination log** (session number, time from tournament start, who knocked them out, and `+REBUY` when applied)
- **Elimination & rebuy modal** — record who eliminated whom; **Save** knocks the player out (struck through, removed from future play), **Save with Buy-in** lets them stay in and adds another buy-in to their running total
- **Voice announcements** (Web Speech API) at 5 and 1 minute remaining, plus a call at each session start
- **Audio cues** — triple beep at session end, then a 3-second "Next Session" interlude before auto-advancing
- **Auto-raising** — when the predefined list is exhausted, blinds keep doubling automatically until you stop
- **Controls** — Skip to Next session, or Stop & return to setup

## Tournament play (eliminations & rebuys)

The session page tracks the field and each player's running buy-in:

- **Buy-in column** starts at the base buy-in and **only grows** — one step per **Save with Buy-in** on that player.
- **Save** = final knockout: the player is struck through, marked **OUT**, and drops out of both elimination dropdowns. No buy-in change.
- **Save with Buy-in** = rebuy: the player **stays in the game**, and their total increases by the base buy-in (e.g. 500 → 1000 → 1500).
- Each recorded event stores the **session number**, the **cumulative active time from the start of the tournament** (pauses excluded), and **who** eliminated them.
- **Pause** freezes the clock and the active-time counter; resuming continues from the same spot.

## Usage

1. Open `index.html`
2. Enter your starting small blind (use +/− or type), the **buy-in amount**, and the minutes per session
3. Click **Add Session to List** for each level (or just hit **Start Tournament** to run from the current value)
4. **Add your players**, tick the **starting dealer**, and use **Randomize Order** / **Randomize Dealer** if the seating should be random
5. **Start Tournament** — the timer takes over; the app advances through (and past) your list automatically
6. During play: **Pause/Resume** the clock, **Eliminate Player** to log a knock-out or a **rebuy**, **Skip to Next** to jump levels, or **Stop & Setup** to return to configuration

Voice output uses your OS's built-in speech synthesis; sound cues work even without a TTS voice installed.

## Tech

Vanilla HTML/CSS/JS. `AudioContext` for beeps, `SpeechSynthesis` for voice. Nothing else.
