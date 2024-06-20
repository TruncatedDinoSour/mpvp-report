# This repository has been migrated to the self-hosted ari-web Forgejo instance: <https://git.ari.lt/ari/mpvp-report>
# Mpvp-report

> Collect MPV player data

# Installation

-   Using [baz plugin manager](https://ari-web.xyz/gh/baz):

```bash
$ baz install git 'https://ari-web.xyz/gh/mpvp-report'
```

# Requirements

-   Python 3
-   Pip
-   Mpv
-   Basic coreutils

# Usage

## Environment variables

-   `MPVP_FILE` -- The file where the data is collected to (`~/.mpvp`)
-   `MPVP_IPC` -- The MPV IPC socket to be exposed in (`/tmp/mpvipc`)

## Usage

Don't use `mpv` to play your music or whatever other
media you want, use `mpvp` instead, it automatically
sets up the MPV IPC socket

To generate an HTML report use the `mpvp_report index.html` command
or something like that, this specific command will
generate the report to `index.html`, all resources
are static

### `mpvp_report` config

```json
{
    "song-mapping": {},
    "styles": "~/.config/mpvp.css",
    "script": "~/.config/mpvp.js",
    "song-name-delims": ["\u2013", "-", ",", "feat.", ".", "&"],
    "yt-url": "https://ari-web.xyz/yt/watch?v=%s"
}
```

This is an example config, let me explain what it means
now:

-   `song-mapping` -- This is a key-value pair of songs with unknown artists, for example:

```json
"song-mapping": {
    "1985": "bo burnham",
    "apocalypse": "cigarettes after Sex",
    "astronomy": "conan gray",
    "brooklyn baby": "lana del rey",
    "come home to me": "crawlers",
    "daddy issues": "the neighbourhood",
    "feel better": "penelope scott",
    "hornylovesickmess": "girl in red",
    "i wanna be your girlfriend": "girl in red",
    "k.": "cigarettes after Sex",
    "lookalike": "conan gray",
    "lotta true crime": "penelope scott",
    "my man's a hexagon (music video)": "münecat",
    "rät": "penelope scott",
    "sappho": "bushies",
    "serial killer - lana del rey lyrics": "lana del rey",
    "sugar, we're goin down but it's creepier": "kade",
    "sweater weather": "the neighbourhood",
    "talia ⧸⧸ girl in red cover": "girl in red",
    "tv": "bushies",
    "unionize - münecat (music video)": "münecat",
    "watch you sleep.": "girl in red",
    "you used me for my love_girl in red": "girl in red",
    "placebo": "crawlers"
}
```

That is an example from my playlist

-   `styles` -- the path to CSS of your page
-   `script` -- the path to JavaScript of your page
-   `song-name-delims` -- The song delimiters to find the artist and song name: `Artist [seperator] song name`
-   `yt-url` -- A YouTube URL template, `%s` gets substituted with the YouTube video ID
