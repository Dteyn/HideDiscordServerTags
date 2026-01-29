# Hide Discord Server Tags

A simple browser extension to hide Discord’s new server tag badges in the web app.

NOTE: Only works with Discord in web browser - does not work with standalone app.

## Installation

1. Clone or download the repo.
2. Load the extension in your browser as a temporary add-on:
   - **Firefox:** Go to `about:debugging#/runtime/this-firefox` -> Load Temporary Add-on -> select `manifest.json`.
   - **Chrome:** Go to `chrome://extensions/`, enable Developer Mode, click "Load unpacked," and select the folder.
   - **Microsoft Edge:** Go to `edge://extensions/`, enable Developer Mode, click "Load unpacked," and select the folder.
3. Open or refresh Discord. Server tags will be hidden.

NOTE: With Firefox, you will need to repeat the above step each restart since it's not a signed add-on.

## How It Works

Injects CSS to hide elements with class containing `clanTagChiplet` (Discord’s server tag badges).

## Source Code

`manifest.json`:
```json
{
  "manifest_version": 3,
  "name": "Hide Discord Server Tags",
  "version": "1.0",
  "description": "Hides the new server tag labels in Discord’s web app.",
  "content_scripts": [
    {
      "matches": ["*://discord.com/*"],
      "css": ["hide-tags.css"],
      "run_at": "document_start"
    }
  ]
}
```


`hide-tags.css`:
```css
/* Hide Discord server tag (clan/guild tag) badges in all contexts */
[class*="clanTagChiplet"] {
  display: none !important;
}
```

## Notes

- Only affects your browser’s view (not the standalone app).
- Only affects server tags shown in chat. Tags are still shown in user listings.
- Discord updates may break the selector; update the CSS if tags reappear.

You are visitor: ![Page views](https://dteyn-rad-page.netlify.app/.netlify/functions/pageviews?repo=HideDiscordServerTags)
