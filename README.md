# Firefox 157 Nova — Flat Dark userChrome.css

A custom `userChrome.css` for Firefox 157's Nova UI.

The goal is to keep Nova enabled while making the interface flatter, more compact, and closer to a traditional desktop Firefox UI.

I built and tested this using Firefox's Browser Toolbox, with ChatGPT helping generate and refine the CSS.

## Changes

- Removes Nova's purple/orange toolbar gradients
- Replaces most purple UI accents with Firefox-style blue
- Uses flat dark backgrounds throughout the browser chrome
- Makes menus and panels more compact
- Reduces excessive menu/panel corner rounding
- Adjusts vertical-tab and sidebar colors
- Changes selected and hovered tab appearance
- Slightly reduces the vertical-tab close button size
- Restyles the bookmark editor
- Reduces excess padding in the bookmark editor
- Changes bookmark editor buttons, outlines, expanders, and checkbox accents to blue
- Changes the bookmarked-page star to blue
- Changes the completed-download indicator from purple to blue
- Uses a slightly lighter popup/menu background so dark favicons are easier to see
- Includes separate inactive-window colors

## Customizing Colors

The main colors are centralized in the `:root` section near the top of `userChrome.css`.

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

Changing these variables lets you customize most of the color scheme without modifying the individual rules below them.

## Installation

1. Open Firefox and go to `about:config`.
2. Set:

   ```
   toolkit.legacyUserProfileCustomizations.stylesheets
   ```

   to `true`.

3. Open `about:support`.
4. Find **Profile Directory** and click **Open Directory**.
5. Create a folder named `chrome` inside your Firefox profile if it doesn't already exist.
6. Copy `userChrome.css` into the `chrome` folder.
7. Restart Firefox.

The resulting path should look similar to:

```text
<Firefox profile>/chrome/userChrome.css
```

## Compatibility

Tested with:

- Firefox 157
- Nova UI enabled
- Dark theme
- Vertical tabs

Some selectors and internal Firefox variables may change in future Firefox releases.

## Notes

This does not disable Nova or restore the old Firefox interface. It restyles the current Nova interface using `userChrome.css`.

Because `userChrome.css` modifies Firefox's internal UI, future Firefox updates may require adjustments.
