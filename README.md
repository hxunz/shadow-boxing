# SHADOW ROUND — Shadow Boxing Combo Trainer

A phone-first web app for shadow boxing without a coach in the room. It runs real boxing-style rounds (work / rest) and calls out randomly generated combos — spoken out loud in English and shown on screen at the same time.

It's a single HTML file, so opening it in a browser is all you need to do.

Two versions are included:

| File | UI language | Voice |
|---|---|---|
| `shadow-round.html` | Korean | English (Reed, British) |
| `shadow-round-en.html` | English | English (Reed, British) |

Both work identically — pick whichever UI language you're more comfortable reading. The spoken combo callouts are always in English in both versions.

---

## 1. Getting started

1. Open `shadow-round.html` or `shadow-round-en.html` in a browser (Safari / Chrome both work fine, on desktop or mobile).
2. An internet connection is needed the first time you open it (to load a Google Font). After that it works offline too.
3. On the settings screen, choose your rounds / round length / difficulty / pace, then tap **START**.
4. Or just tap one of the presets (Beginner / Standard / Pro) at the top for a quick setup.

> 💡 Prop your phone up somewhere you can see and hear it, and make sure it's not on silent/mute.

---

## 2. Settings

| Setting | Description |
|---|---|
| Rounds | 1–15 rounds |
| Round length | 1:30 / 2:00 / 3:00 (real boxing rounds are 3 minutes) |
| Rest length | 0:30 / 1:00 / 1:30 (real boxing rest is 1 minute) |
| Difficulty | Beginner / Intermediate / Advanced — changes combo length and complexity (body shots, defensive moves) |
| Combo pace | Slow / Normal / Fast — changes the gap between combos |

### Presets

| Preset | Rounds | Round length | Difficulty | Pace |
|---|---|---|---|---|
| Beginner | 3R | 2:00 | Beginner | Slow |
| Standard | 3R | 3:00 | Intermediate | Normal |
| Pro | 12R | 3:00 | Advanced | Fast |

---

## 3. How combos are written

Combos use the numbering system real boxing trainers actually use.

| Number | Punch (spoken) | Name |
|---|---|---|
| 1 | One | Jab |
| 2 | Two | Cross |
| 3 | Three | Lead Hook |
| 4 | Four | Rear Hook |
| 5 | Five | Lead Uppercut |
| 6 | Six | Rear Uppercut |

- A combo shown as `1-2-3·B` means throw punch `3` **to the body**. It's spoken as "One, Two, Three body."
- Defensive/footwork cues (slip, roll, duck, pivot, step, etc.) sometimes appear before, after, or in the middle of a combo — e.g. "SLIP LEFT / 1-2".
- Occasionally you'll get a standalone cue with no punches at all, like "Guard up" or "Circle left."
- Combos aren't fully random — punch sequences follow rough real-world tendencies (a jab is often followed by a cross or hook, for example), so they feel closer to what a trainer would actually call.

---

## 4. Voice

- The voice is fixed to **English (British — "Reed")**, so you always hear combos in the same consistent voice.
- This app uses the browser's built-in **Web Speech API** — no audio files or server needed — but that means the **"Reed" voice has to actually be installed on your device**.
  - It's commonly available by default on Windows / Microsoft Edge.
  - If it's missing, the app automatically falls back to another English voice and shows a banner telling you which one it picked instead.
  - If a device has **no English voice at all** (common on Android phones without an English TTS language pack), go to **Settings → Accessibility (or Language & Input) → Text-to-speech → download an English voice**.
- On iOS, the **silent/mute switch** can block Web Speech audio — make sure it's off.

---

## 5. How a round plays out

- At the start of a round, a bell rings once and "Round N" is announced.
- 10 seconds before a work round ends, you get a warning beep (three short beeps) plus a vibration — like the "10 seconds" clapper in a real boxing gym.
- When the round ends, the bell rings twice and "Rest" is announced as the rest timer starts.
- After the final round, the bell rings three times and "Workout complete" is announced.
- The screen is kept from sleeping during training (on devices that support it).
- A running history of recent combos is shown at the bottom of the training screen so you can review them afterward.

---

## 6. Customizing it

Open either HTML file in a text editor — the code is organized into commented sections, so these are easy to find and tweak:

- **Punch names / translations**: `PUNCH_WORD`, `PUNCH_NAME_KO` (Korean file) / `PUNCH_NAME_EN` (English file)
- **Defensive move list**: `DEFENSE_MOVES`
- **Standalone footwork/defense cues**: `STANDALONE_DRILLS`
- **Punch transition probabilities** (what tends to follow what): `TRANSITIONS`
- **Combo length / body-shot / defensive-move ratios per difficulty**: inside `generateCombo()` — look for `lenRange`, `bodyChance`, `prefixMoveChance`
- **Time between combos**: `PACE_RANGE`
- **Voice speed/pitch**: `rate` and `pitch` inside the `speak()` function
- **Colors / fonts / layout**: the CSS variables at the top of the file, inside `:root`

---

## 7. Known limitations

- Web Speech API support and the list of installed voices vary by browser and device — the "Reed" voice in particular isn't available everywhere.
- Browser tabs can throttle timers or pause speech when backgrounded, so keep this tab active/foregrounded during a session.
- Works offline after the first load, but that first load needs an internet connection to fetch the web font.

---

Have a good session! 🥊
