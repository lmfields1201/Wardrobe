# 👗 Wardrobe Builder Simulator

A virtual wardrobe builder and fashion show simulator. Create outfits, share them with friends, and watch them come to life on a virtual runway with music and lighting effects.

---

## ✨ Features (Current)

### 🎨 Outfit Builder
- **Mix & Match** — Tops, bottoms, shoes, accessories, outerwear
- **Live Preview** — Mannequin updates instantly
- **Randomize / Clear** — Quick start or reset
- **Submit to Gallery** — Copying an outfit code automatically adds it to the Fashion Show gallery

### 🎭 Fashion Show
- **Runway Stage** — Animated spotlights, music, transitions, fullscreen
- **Gallery-Driven Sequence** — Paste codes → load gallery → click outfits to include/exclude; shuffle or clear sequence
- **Auto-Advance** — Plays through gallery selection with progress + on-stage counter
- **Manual Controls** — Prev / Next / Pause + keyboard shortcuts (Space, ← →, Esc)

### 💾 Save & Share
- **Outfit Codes** — Short base36 codes (5 chars per outfit segment)
- **Named Outfits** — `Name:code` supported
- **Saved Shows** — Local saves; export/import JSON; shareable links
- **Recent Outfits** — Quickly re-add what you just built

### 👥 Multi-Designer Shows
- **Designer Codes** — Compact alphanumeric codes that include outfits + lighting
- **Collect Mode** — Facilitator gathers codes, builds combined show order
- **Attribution** — Stage shows “by Designer Name” during playback

---

## 🚀 Getting Started

### Quick Start
1. Open `index.html` in a modern browser. No build, no server.

### Create & Submit an Outfit
1. Click items in **Closet** to add/remove on the mannequin
2. Optional: **Random** or **Clear**
3. Click **Submit Outfit** → copy the code (this also adds it to the gallery)

### Run a Fashion Show
1. Switch to **Fashion Show**
2. Paste outfit codes (one per line) in **Outfit Codes**, then **Load / Refresh Gallery**
3. Click gallery cards to include/exclude from the show (clear or shuffle as needed)
4. Set seconds per outfit, transition type/duration, music, and spotlight colors
5. **Start Show** → auto-advance; use Prev / Next / Pause or keyboard shortcuts

---

## 📖 User Guide

### Outfit Code Format
Outfits are encoded as 5 numbers separated by dashes:
```
topId-bottomId-shoeId-accessoryId-outerwearId
```
Use `0` for any empty slot. Examples: `1-2-3-0-0`, `5-1-4-2-1`.

### Named Outfits
Add a name by prefixing the code with `Name:`:
```
Date Night:5-2-3-1-0
Casual Friday:1-1-4-0-2
```

### Gallery / Sequence Controls
| Action | How |
|--------|-----|
| Include / exclude | Click a gallery card to toggle it in the show sequence |
| Shuffle order | Click **Shuffle** |
| Clear sequence | Click **Clear Sequence** |
| Refresh gallery | Click **Load / Refresh Gallery** after editing the codes box |

### Keyboard Shortcuts (during show)
| Key | Action |
|-----|--------|
| `Space` | Pause / Resume |
| `←` | Previous outfit |
| `→` | Next outfit |
| `Escape` | Exit fullscreen / stop |

### Show Settings
| Setting | Description |
|---------|-------------|
| **Seconds per outfit** | How long each outfit displays (default: 4s) |
| **Transition seconds** | Duration of transition effect (default: 1s) |
| **Transition effect** | Fade, Slide, or None |
| **Soundtrack** | Background music selection |
| **Spotlight colors** | Three colors (A, B, C) that tint the stage lighting |

### Multi-Designer Shows (Collaborative Mode)

Multiple designers (each on their own device) can hand a single facilitator their codes to build one combined show.

#### Designer Steps
1) Enter your name in **Generate Your Show Code**
2) Load outfits into the gallery (paste codes or submit from Builder)
3) Choose your lighting colors
4) Click **Get My Show Code** and share the code with the facilitator

#### Facilitator Steps
1) Go to **Collect Designer Codes** (Fashion Show tab)
2) Paste each designer code and click **Add** (chips show designer + outfit count)
3) Click **Build Combined Show** (round-robin order)
4) Start the show; stage shows “by Designer Name” attribution

#### Designer Code Format (compact)
- `NAME` — Uppercase alphanumeric, max 10 chars
- `OUTFITDATA` — Base36 outfits, 5 chars per outfit (tops/bottoms/shoes/accessories/outerwear)
- `COLORS` — Optional, 18 hex chars (3 colors * 6 hex each) appended as the third segment

Examples:
- `CASEY-1ab01z-FF3B81AAAFFF22C55E` (with colors)
- `JAMIE-2301a` (no colors, legacy-compatible)

---

## 💡 Tips & Tricks

- **Batch import**: Paste multiple outfit codes at once, one per line
- **Repeat outfits**: Add the same outfit multiple times to the timeline for longer display
- **Share shows**: Use "Copy Share Link" to share your complete show with friends
- **Backup shows**: Export to JSON before clearing your browser data
- **Quick preview**: Drag any gallery outfit to the timeline to preview it on stage

---

## 🛠️ Technical Details

### Stack
- **HTML5** — Semantic markup
- **Tailwind CSS** — Utility-first styling (via CDN)
- **Vanilla JavaScript** — No framework dependencies
- **localStorage** — Client-side persistence

### Browser Support
Works in all modern browsers:
- Chrome 80+
- Firefox 75+
- Safari 13+
- Edge 80+

### Data Storage
All data is stored locally in your browser:
- `wardrobe_recent_outfits` — Last 10 submitted outfits
- `wardrobe_saved_shows` — Saved show configurations (up to 20)

### No Backend Required
This is a fully client-side application. All features work without a server:
- Images hosted on postimg.cc
- Music from Pixabay (royalty-free)
- Share links encode all data in URL parameters

---

## 📁 Project Structure

```
Wardrobe/
├── index.html      # Complete application (HTML + CSS + JS)
├── README.md       # This file
└── LICENSE         # MIT License
```

---

## 🎨 Customization

### Adding New Clothing Items
Edit the `closetData` object in the `<script>` section:

```javascript
const closetData = {
    tops: [
        { id: 1, name: 'Item Name', imageUrl: 'https://...' },
        // Add more items here
    ],
    // ... other categories
};
```

### Adding Music Tracks
Add options to the `#songSelect` dropdown:

```html
<option value="https://your-audio-url.mp3">Track Name</option>
```

### Changing Spotlight Animation
Modify the CSS keyframes for `spotlight-sway` and `stagePulse`.

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---