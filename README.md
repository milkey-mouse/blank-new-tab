# Blank New Tab

![Screenshot of the eponymous](screenshot.png)

Yet another new tab emblankener. For some reason you need to write an extension to do this, smh. Looks exactly like the default dark-mode new tab sans Google.

# Install

Grab [`blank-new-tab.crx`](https://github.com/milkey-mouse/blank-new-tab/releases/latest/download/blank-new-tab.crx). Failing that, clone or [download](https://github.com/milkey-mouse/blank-new-tab/archive/refs/heads/master.zip) this repo and load the `blank-new-tab` directory (the one containing `manifest.json`) as an [unpacked extension](https://developer.chrome.com/docs/extensions/get-started/tutorial/hello-world#load-unpacked).

# Release

To cut a new release:

- Bump version in `blank-new-tab/manifest.json`
- `git commit`
- `git tag`
- `git push && git push --tags`
- `chromium --pack-extension=blank-new-tab --pack-extension-key=blank-new-tab.pem`
- Upload `blank-new-tab.crx` to latest release on GitHub

We have CI at home.

# License

All [three lines](blank-new-tab/index.html) of mine are CC0-1.0/public domain.

The favicon is taken from the Chromium project:

https://source.chromium.org/chromium/chromium/src/+/main:chrome/app/theme/default_100_percent/common/favicon_ntp.png
https://source.chromium.org/chromium/chromium/src/+/main:chrome/app/theme/default_200_percent/common/favicon_ntp.png

...then inverted for dark mode:

    mogrify -channel rgb -negate +channel favicon_ntp-100.png
    mogrify -channel rgb -negate +channel favicon_ntp-200.png

...then reoptimized:

    pngquant --quality 100 --speed 1 --verbose favicon_ntp-100.png
    pngquant --quality 100 --speed 1 --verbose favicon_ntp-200.png 

    optipng -o7 -zm1-9 favicon_ntp-100-fs8.png
    optipng -o7 -zm1-9 favicon_ntp-200-fs8.png

    rename '-fs8' '' *-fs8.png
