# Stash

[![Build Status](https://travis-ci.org/stashapp/stash.svg?branch=master)](https://travis-ci.org/stashapp/stash)

**Stash is a Go app which organizes and serves your porn.**

See a demo [here](https://vimeo.com/275537038) (password is stashapp).

TODO: This does not match the features of the Rails project quite yet and is still a little buggy.  Fall back to the Rails project if you run into issues as an existing user.

# Install

Stash supports macOS, Windows, and Linux.  Download the [latest release here](https://github.com/stashapp/stash/releases).

Simply run the executable and navigate to either https://localhost:9999 or http://localhost:9998 to get started.

*Note for Windows users:* Running the app might present a security prompt since the binary isn't signed yet.  Just click more info and then the run anyway button.

#### FFMPEG

If stash is unable to find or download FFMPEG then download it yourself from the link for your platform:

* [macOS](https://ffmpeg.zeranoe.com/builds/macos64/static/ffmpeg-4.0-macos64-static.zip)
* [Windows](https://ffmpeg.zeranoe.com/builds/win64/static/ffmpeg-4.0-win64-static.zip)
* [Linux](https://johnvansickle.com/ffmpeg/releases/ffmpeg-release-amd64-static.tar.xz)

The `ffmpeg(.exe)` and `ffprobe(.exe)` files should be placed in `~/.stash` on macOS / Linux or `C:\Users\YourUsername\.stash` on Windows.

# FAQ

> Does stash support multiple folders?

Not yet, but this will come in the future.

# Development

## Environment

### macOS

TODO

### Windows

1. Download and install [Go for Windows](https://golang.org/dl/)
2. Download and install [MingW](https://sourceforge.net/projects/mingw-w64/)
3. Search for "advanced system settings" and open the system properties dialog.
	1. Click the `Environment Variables` button
	2. Add `GO111MODULE=on`
	3. Under system variables find the `Path`.  Edit and add `C:\Program Files\mingw-w64\*\mingw64\bin` (replace * with the correct path).

## Commands

* `make build` - Builds the binary
* `make gqlgen` - Regenerate Go GraphQL files

## Building a release

1. cd into the UI directory and run `ng build --prod`
2. cd back to the root directory and run `make build` to build the executable

#### Notes for the dev

https://blog.filippo.io/easy-windows-and-linux-cross-compilers-for-macos/

`docker run --rm --mount type=bind,source="$(pwd)",target=/stash -w /stash -i -t bepsays/ci-goreleaser:1.11-2 /bin/bash`