# Firefox 157 Nova — Flat Dark Theme

A custom `userChrome.css` and `userContent.css` theme for Firefox 157's Nova UI.

The goal is to keep Nova enabled while making the interface flatter, more compact, and closer to a traditional desktop Firefox UI, without losing Nova's newer features.

Built and tested using Firefox's Browser Toolbox, with ChatGPT assisting in generating, debugging, and refining the CSS.

## Changes

### General Appearance

- Removes Nova's purple/orange toolbar and sidebar gradients
- Replaces most purple UI accents with Firefox-style blue
- Uses consistent flat dark backgrounds throughout the browser chrome
- Uses a slightly lighter popup/menu background so dark favicons are easier to see
- Reduces excessive menu and panel corner rounding
- Makes menus and panels more compact
- Includes separate inactive-window colors

### URL Bar

- Removes unwanted background gradients
- Uses a consistent dark URL field background
- Changes URL suggestion links and type indicators to blue
- Reduces the rounding of the autocomplete dropdown to 8px
- Adds a subtle border around the autocomplete dropdown to match other panels

### Vertical Tabs and Sidebar

- Flattens Nova's redesigned sidebar
- Uses consistent sidebar and vertical-tab backgrounds
- Gives the selected vertical tab a subtle background and outline
- Adjusts tab hover highlighting
- Slightly reduces the vertical-tab close button size
- Uses neutral gray close-button outlines

### Bookmarks

- Restyles the bookmark editor with a more compact layout
- Reduces unnecessary horizontal padding
- Changes bookmark editor buttons, outlines, expanders, and checkbox accents to blue
- Restyles the expanded folder and tag selection areas
- Changes the bookmarked-page star to blue

### Downloads

- Changes the completed-download indicator from purple to blue

### Extension Popup Compatibility

- Applies custom panel geometry to Firefox menus and panels while excluding Dark Reader's popup
- Prevents the custom panel rounding and padding from introducing an unwanted outer frame around Dark Reader
- Includes `userContent.css` for an extension-specific popup border adjustment

The Dark Reader exception is handled automatically by `userChrome.css`. The extension-specific `userContent.css` rule is intended for the particular translation extension used during development and may not apply to other installations.

## Customizing Colors

Most theme colors are centralized in the `:root` section near the top of `userChrome.css`.

For example:

```css
:root {
    --my-window-bg: #1c1b22;
    --my-toolbar-bg: #2b2a33;
    --my-sidebar-bg: #2b2a33;

    --my-tab-selected: #52515e;
    --my-tab-hover: rgba(255, 255, 255, 0.08);

    --my-border: #42414d;
    --my-text: #fbfbfe;

    --my-button-hover: rgba(0, 97, 224, 0.25);
    --my-button-active: rgba(0, 97, 224, 0.40);
    --my-button-selected: #0061e0;
}
```

Changing these variables lets you customize most of the color scheme without modifying individual CSS rules.

Some values, particularly selected-tab colors and corner radii, are still defined directly in their respective rules.

## Installation

1. Open Firefox and navigate to `about:config`.
2. Set the following preference to `true`:

   ```
   toolkit.legacyUserProfileCustomizations.stylesheets
   ```

3. Navigate to `about:support`.
4. Find **Profile Directory** and click **Open Directory**.
5. Create a folder named `chrome` inside your Firefox profile if one doesn't already exist.
6. Copy `userChrome.css` into the `chrome` folder.
7. Optionally copy `userContent.css` if you want its extension-specific styling.
8. Restart Firefox.

Your directory should look like:

```text
<Firefox profile>/
└── chrome/
    ├── userChrome.css
    └── userContent.css
```

**Note:** `userChrome.css` modifies Firefox's interface. `userContent.css` modifies the content of specific documents, including extension popup pages. The main theme does not require `userContent.css`.

## Compatibility

Developed and tested with:

- Firefox 157
- Nova UI enabled
- Dark theme
- Vertical tabs
- Dark Reader extension

The theme is designed around Firefox 157's interface. It has not been comprehensively tested with other Firefox versions, themes, or extension combinations.

Some selectors, internal variables, and popup structures may change in future Firefox releases.

## Notes

This theme does not disable Nova or restore the old Firefox interface. It restyles the current Nova interface using Firefox's custom stylesheet support.

The CSS uses Firefox-specific selectors and internal UI variables, so future updates may require adjustments.

Extension popups can use different Firefox containers and their own internal styles. The Dark Reader exception is included to avoid a popup layout issue encountered during development.
