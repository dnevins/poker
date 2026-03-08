# Texas Hold'em Poker Trainer

A single-file, zero-dependency poker learning game that teaches Texas Hold'em strategy through interactive play and real-time coaching. No build tools, no frameworks, no server — just open `index.html` in a browser.

![Vanilla JS](https://img.shields.io/badge/vanilla-JS%2FCSS%2FHTML-f7df1e)
![Zero Dependencies](https://img.shields.io/badge/dependencies-0-brightgreen)
![License](https://img.shields.io/badge/license-MIT-blue)

## Features

**Interactive 4-Player Game**
- Play against 3 AI opponents with adaptive aggression
- Full betting rounds: preflop, flop, turn, river
- Side pot calculation for all-in scenarios
- Dynamic blind escalation (10/20 → 15/30 → 25/50 → 40/80 → 75/150 → 100/200)

**Real-Time Coaching Panel**
- Hand strength meter with 5-tier rating (Weak → Premium)
- Position-aware advice (adjusts for heads-up, 3-handed, full table)
- Draw and out calculations (flush draws, straight draws, combo draws)
- Pot odds analysis with clear call/fold recommendations
- Bluff spot detection: c-bet opportunities, semi-bluff raises, position steals
- Opponent read hints based on bet sizing patterns

**16 Educational Scenarios**
Each scenario deals a specific hand to teach a key concept:

| Scenario | Concept |
|----------|---------|
| Pocket Jacks | Overpair play and set avoidance |
| Flush Draw | Drawing odds and semi-bluffing |
| Open-Ended Straight | 8-out draw equity |
| Set Mining | Implied odds with small pairs |
| Monster Draw | Combo draw aggression |
| Big Slick | AK postflop decision-making |
| Weak Kicker | Kicker trouble and pot control |
| Two Pair Danger | Board texture awareness |
| Bluff Catch | Calling with medium-strength hands |
| Pocket Aces vs Set | Overpair vs hidden set dynamics |
| Overcards C-Bet | Continuation betting strategy |
| Gutshot | Inside straight draw discipline |
| Pure Bluff | Bluffing with air |
| Semi-Bluff Raise | Raising with draws for fold equity |
| Three-Bet | Preflop re-raising ranges |
| Check-Raise Trap | Trapping with strong hands |

**Difficulty Modes**
- **Beginner**: Shows scenario banners, coaching recommendations, and full guidance
- **Expert**: Hides scenario hints and recommendations — test your own reads

**Stats & History**
- Tracks hands played, win rate, and bluff success
- Collapsible hand history panel (last 20 hands)
- Current blind level display

**Keyboard Controls**
- `F` — Fold
- `C` — Check/Call
- `R` — Raise
- `A` — All-In
- `N` / `Enter` — Next hand / Deal

## Getting Started

Just open the file:

```bash
# Clone the repo
git clone https://github.com/dnevins/poker.git

# Open in your browser
open poker/index.html
```

Or serve it with any static file server:

```bash
# Python
python3 -m http.server 8000

# Node
npx serve .
```

No install, no build, no config.

## How It Works

Everything lives in a single `index.html` file (~1900 lines):

- **HTML** — Game table layout with CSS-rendered cards (no images)
- **CSS** — Dark theme with felt-green table, responsive down to mobile
- **JavaScript** — Game engine, AI logic, hand evaluation, coaching system

The game state is managed through a single global `G` object that resets each hand. AI opponents use position-aware strategy with configurable aggression that increases as players are eliminated.

## Browser Support

Works in any modern browser (Chrome, Firefox, Safari, Edge). No Internet connection required — it's fully offline.

## Security

The app uses a strict Content Security Policy:
- No external scripts, styles, images, or connections
- `unsafe-inline` is required since everything is in a single file
- Zero network requests — nothing leaves your browser

## Contributing

Contributions welcome! Some ideas:

- **More scenarios** — Add new teaching hands to the `SCENARIOS` array
- **Tournament mode** — Multi-table progression
- **Hand replay** — Step through past hands move by move
- **Sound effects** — Card dealing, chip sounds
- **Multiplayer** — WebRTC peer-to-peer play
- **Mobile polish** — Touch-optimized controls

To add a new scenario, add an entry to the `SCENARIOS` array around line 244:

```javascript
{
  id: 'your_scenario',
  title: 'Scenario Title',
  hero: [c('A','s'), c('K','s')],  // Your hole cards
  villains: [...],                   // Opponent hands
  board: [c('Q','h'), c('J','d'), c('T','s'), c('2','c'), c('7','h')],
  lesson: 'What this scenario teaches...'
}
```

## License

MIT — do whatever you want with it.
