Icons taken Chromium source:

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
