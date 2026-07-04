# Custom New Tab

A minimal, elegant replacement for Chrome's New Tab page. Features a frosted-glass widget system (clock, search bar, shortcuts) on a grid layout, plus a custom wallpaper you set yourself.

## Features

- **Custom wallpaper** — upload any image from your computer as your background. It's saved locally and persists across sessions.
- **Widgets**
  - **Clock** — live time and date, updates every second.
  - **Search Bar** — searches Google, opens results in a new tab.
  - **Custom Link** — a 2×1 shortcut with a name you choose.
  - **Small Shortcut** — a 1×1 shortcut with a favicon, great for quick links.
- **Edit mode** — drag widgets around a snapping grid, right-click to delete, double-click a link to rename it.
- **Persistent layout** — widget positions, links, and wallpaper are all saved in `localStorage`, so your setup is exactly the same every time you open a new tab.

## Installation

1. Download or clone this repository.
2. Open `chrome://extensions` in Chrome.
3. Enable **Developer mode** (toggle in the top-right corner).
4. Click **Load unpacked** and select the folder containing `manifest.json` and `wallpaper.html`.
5. Open a new tab — you should see your custom new tab page.

## Usage

### Setting a wallpaper
Click the 🖼 button in the bottom-right corner and choose any image file from your computer. It's applied instantly and saved for next time.

### Adding widgets
1. Click **✎** (bottom-right) to enter edit mode.
2. Click **+ Add** (bottom-left) to open the widget panel.
3. Choose a widget type:
   - **Clock**
   - **Search Bar** — 4×1
   - **Custom Link** — 2×1 (you'll be prompted for a name and URL, e.g. `Google, google.com`)
   - **Small Shortcut** — 1×1 (same prompt, shown with a favicon)
4. Drag widgets to rearrange them — they snap to a grid automatically.
5. Click **✓** to exit edit mode and save your layout.

### Editing or removing widgets
- While in edit mode, **double-click** a link widget to rename it.
- While in edit mode, **right-click** any widget to delete it.
- **Clear All** in the widget panel resets everything (layout and links) back to default.

## File structure

```
.
├── manifest.json     # Chrome extension manifest (Manifest V3)
└── wallpaper.html     # New tab page markup, styles, and logic
```

## Technical notes

- All data (layout, links, wallpaper) is stored in the browser's `localStorage` — nothing is sent anywhere or stored in the cloud.
- Wallpaper images are stored as base64 data URLs. `localStorage` has a per-origin size limit (typically 5–10MB depending on the browser), so very large or high-resolution images may fail to save permanently, though they'll still display for the current session. If you regularly use large images, consider switching wallpaper storage to `IndexedDB` for a much higher quota.
- Favicons for small shortcuts are fetched from Google's public favicon service (`s2/favicons`).
- Fonts are loaded from Google Fonts (`Playfair Display`).

## Permissions

This extension requests no special permissions beyond overriding the new tab page (`chrome_url_overrides`). It does not access browsing history, tabs, or any other browser data.

## License

Free to use, modify, and distribute for personal use.