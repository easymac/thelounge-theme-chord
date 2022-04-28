# Chord
Darkly elegant theme for The Lounge.

![Preview](https://github.com/easymac/thelounge-theme-chord/blob/master/chord-screenshot.png)

Chord is designed to offer a pleasant visual revamp with specific improvements in mobile usability, support for devices with rounded screens, and an emphasis on type and legibility.

## Installation
If you installed The Lounge with a package manager:
```
thelounge install thelounge-theme-chord
```

If you installed The Lounge from source:
```
node index.js install thelounge-theme-chord
```

## Cookbook
Below are snippets designed to be pasted in the `Custom Stylesheet` setting to offer basic tweaks, personalization, and configuration.

#### Style for bots
```CSS
/* Monospace font for better ASCII */
#chat .msg[data-from=BOT_NICKNAME] .content {
  font-family: monospace !important;
  color: #888;
}

/* Reduce line height to 1.0 for better ASCII */
#chat .msg[data-from=BOT_NICKNAME] .time, #chat .msg[data-from=BOT_NICKNAME] .from, #chat .msg[data-from=BOT_NICKNAME] .content {
  padding-top: 0;
  padding-bottom: 0;
}
#chat .msg[data-from=BOT_NICKNAME] .content span {
  display: inline-block;
}
#chat .msg[data-from=BOT_NICKNAME] {
  margin-bottom: 0;
}

/* Restore spacing for non-bot messages adjacent to bot messages when using
 * the previous block.
 */
#chat .msg[data-from=BOT_NICKNAME].previous-source + .msg:not(.previous-source) {
  padding-top: 3px;
}

/* Hide timestamps for consecutive bot messages */
#chat .msg[data-from=BOT_NICKNAME].previous-source .time {
  visibility: hidden;
}
```
#### Set your own nickname color
```CSS
#chat .msg.self .user {
	color: #236BFF;
}
```
#### Adjust message width
```CSS
:root {
	--chat-wrap-width: 1200px /* default */
}
```
#### Disable update indicator
```CSS
:root {
  --update-available: 0;
}
```

## Contributing
Bug reports, feature requests, suggestions, and feedback should be posted in the [issue tracker](https://github.com/easymac/thelounge-theme-chord/issues).

PRs are welcome and very much appreciated. To get started:

```
git clone git@github.com:easymac/thelounge-theme-chord.git
cd /thelounge-theme-chord
npm run scss
```

Since The Lounge doesn't at the time of writing support installing themes from
local npm packages, for development purposes the theme needs to be installed
with `thelounge install thelounge-theme-chord` and modifications to `theme.css`
need to be copied to `/etc/thelounge/packages/node_modules/thelounge-theme-chord/theme.css`.

Right now, I'm just manually copying it over after every change, which sucks.
I should set up a watcher to do it for me but I haven't.

### Todo:
Feel free to take a crack at any of these that interest you:
- **Optimize for your devices**: I only tested Chord on my own devices. If you identify any fixes or areas that can be improved for your device, please open an issue with a screenshot! (Or make a PR if you're feeling generous.) This particularly includes adjustments that can be made to media queries to better scale the UI to your screens.
- **Update the icons**: fontawesome is great and free but some of the icons seem a little too thick for Chord.
- **Add some more nickname colors**: Chord currently has 14 defined and as many as 32 could be supported.
- **Create GitHub Actions**: Triggers to automatically build the CSS file, bump the version number, and release on GitHub would be really awesome.
- **Design a light mode**: I would love for the theme to respect a user's `prefers-color-scheme` setting eventually, but a light mode needs to be created first. This could be achieved by implementing better CSS variable integration into the stylesheet, overriding the dark colors, and making necessary adjustments for legibility.
- **Add a GitHub Page**: It'd be cute, and I would like this package to show up when you search for "thelounge dark theme"