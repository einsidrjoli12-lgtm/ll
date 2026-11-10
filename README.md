# Bubble Bash

A phone-first bubble shooter in a single HTML file. Open `index.html` in any browser to play.

## Menus
- **Start screen**: "Tap to start" (this first tap also switches on sound, which browsers require).
- **Main menu**: Play and Settings, with the high score for every mode.
- **Play** asks for a difficulty. Each mode shows its high score before you pick it.
  - Easy: 3 colors, 8 shots before a new row, full aim line.
  - Normal: 4 colors, 6 shots before a new row, 1.5x points.
  - Hard: 5 colors, 4 shots before a new row, short aim line, 2x points.
- **Settings**: sound effects on/off and volume, music on/off and volume, vibration, test sound.
- **Pause** (button top right, or Esc/P): Resume, Settings, Quit to menu.

## Scoring and combos
- 10 points per popped bubble, 20 per bubble that falls off, +50 for a single match of 6 or more.
- **Combos**: pop on back-to-back shots to raise the multiplier for the next pop:
  ×1 → ×1.5 → ×2 → ×2.5 … up to ×4. A shot that pops nothing resets it.
  The COMBO meter next to the launcher shows the multiplier your next pop will get.
- The difficulty multiplier (Normal 1.5x, Hard 2x) applies on top.
- One high score per mode. When you beat your previous best mid-game the Best counter
  flashes, a "New high score!" banner appears and a fanfare plays.

## Levels
Every level is generated at random: a shape (full reef, funnel, hourglass, pillars, coral holes,
diamond, staircase, wave) combined with a color pattern (clusters, stripes, diagonals, columns,
scatter, rings) and a random set of colors.

## Sound and vibration
- Menu sounds, game sounds and two synthesized music tracks (calm menu, upbeat game that speeds up
  near the red line). No audio files; everything is made with the Web Audio API.
- Vibration:
  - **iPhone/Android app (App Store / Google Play build)**: native haptics through `@capacitor/haptics`
    (light/medium/heavy taps plus success, warning and error patterns).
  - **Android browser**: the Vibration API.
  - **iPhone Safari**: Safari does not let web pages use the vibration motor. On iOS 18+ the game
    uses the system switch haptic as a light tick; full haptics need the app build.

## Phones
The board fills the screen, touch targets are at least 44px, and the page doesn't zoom, scroll or
select text while you play. Drag to aim and lift to shoot; tap the launcher to swap. The game pauses
when you switch apps or lock the phone.

## Building the iPhone app (App Store)
The game is wrapped with [Capacitor](https://capacitorjs.com). You need a Mac with Xcode and an
Apple Developer account to put it on the App Store.

1. Change `appId` in `capacitor.config.json` to your own reverse domain, e.g. `com.yourname.bubblebash`.
2. `npm install`
3. `npx cap add ios` (first time only)
4. `npm run ios` copies the game into `www/`, syncs it and opens Xcode.
5. In Xcode pick your team under Signing, run it on your iPhone, then Product → Archive to upload.

Android works the same way with `npx cap add android` and `npm run android` (needs Android Studio).
