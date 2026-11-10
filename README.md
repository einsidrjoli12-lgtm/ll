# Bubble Bash

A phone-first bubble shooter in a single HTML file. Open `index.html` in any browser to play.

## Modes
Each mode is its own place under the sea, with its own music:

| Mode | World | Colors | Shots before a new row | Aim line | Points |
|---|---|---|---|---|---|
| Easy | Sunny Lagoon | 3 | 8 | full | 1x |
| Normal | Coral Reef | 4 | 6 | full | 1.5x |
| Hard | Twilight Trench | 5 | 4 | short | 2x |
| God | Abyssal Fury | 6 | 3, plus a new row every 10 s (faster each level) | none | 3x |

Every level goes a little deeper (darker water, fewer light rays) and swaps its scenery
(kelp, coral, rocks, volcanic vents).

## Battle
Race an AI rival on boards side by side. Pick the target score (any number, or 1,000 / 3,000 /
5,000 / 10,000) and the rival (Rookie, Pro, Champion). First to the target wins; if your reef floods
you lose. A combo of 3+ or dropping 4+ bubbles pushes a row onto the other board. Wins and losses
are saved.

## Menus
Tap to start → main menu (Play, Battle, Settings) → pick a mode, each showing its high score.
Settings: sound effects, music, both volumes, vibration, test sound. Pause with the button or Esc.

## Scoring and combos
- 10 points per popped bubble, 20 per bubble that falls off, +50 for a single match of 6 or more.
- **Combos** start on the 3rd popping shot in a row: ×1.5, then ×2, ×2.5 … up to ×4. A shot that
  pops nothing resets it. The COMBO meter by the launcher fills two dots, then shows the multiplier.
- The mode multiplier applies on top. One high score per mode.

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
