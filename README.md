# Bubble Reef

A small bubble shooter in a single HTML file. Open `index.html` in any browser.

## Menus
- **Main menu**: Play and Settings.
- **Play** asks for a difficulty:
  - Easy: 3 colors, 8 shots before a new row, full aim line.
  - Normal: 4 colors, 6 shots before a new row, 1.5x points.
  - Hard: 5 colors, 4 shots before a new row, short aim line, 2x points.
- **Settings**: sound effects on/off, music on/off, volume. Saved in your browser.
- **Pause** (button top right, or Esc/P): Resume, Settings, Quit to menu.

## Levels
Every level is generated at random: a shape (full reef, funnel, hourglass, pillars,
coral holes, diamond, staircase, wave) combined with a color pattern (clusters, stripes,
diagonals, columns, scatter, rings) and a random set of colors. Later levels add colors,
rows and fewer shots between new rows.

## How to play
- Aim with the mouse or a finger, release to shoot. Bubbles bounce off the side walls.
- Match 3 or more of one color to pop them. Bubbles left hanging fall off for bonus points.
- If bubbles cross the red line, the game ends.
- Keys: ← → aim, Space shoot, X swap with the next bubble, Esc pause.

Sound effects and music are synthesized in the browser with the Web Audio API, so there are no audio files.
