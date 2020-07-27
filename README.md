vimeo-dl
========

[![Go](https://github.com/akiomik/vimeo-dl/workflows/Go/badge.svg?branch=master)](https://github.com/akiomik/vimeo-dl/actions?query=workflow%3AGo)

A tool to download private videos on vimeo.

## Usage

```
Usage:
  vimeo-dl [flags]

Flags:
      --audio-id string     audio id
  -h, --help                help for vimeo-dl
  -i, --input string        url for master.json (required)
      --user-agent string   user-agent for request
      --video-id string     video id
```

## Example

```sh
# Download the video as ${clip_id}-video.mp4 (1080p)
vimeo-dl -i "https://skyfire.vimeocdn.com/xxx/yyy/live-archive/video/240p,360p,540p,720p,1080p/master.json?base64_init=1&query_string_ranges=1"
```

```sh
# Download the video as ${clip_id}-video.mp4 (720p) with the specified user-agent
vimeo-dl -i "https://skyfire.vimeocdn.com/xxx/yyy/live-archive/video/240p,360p,540p,720p,1080p/master.json?base64_init=1&query_string_ranges=1" \
         --video-id "720p" \
         --user-agent "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/84.0.4147.89 Safari/537.36"
```

```sh
# Download the video the ${clip_id}-video.mp4 and the audio as ${clip_id}-audio.mp4
vimeo-dl -i "https://8vod-adaptive.akamaized.net/xxx/yyy/sep/video/9f88d1ff,b83d0f9d,da44206b,f34fd50d,f9ebc26f/master.json?base64_init=1" \
         --video-id "b83d0f9d" \
         --audio-id "b83d0f9d"

# Combine both files
ffmpeg -i ${clip_id}-video.mp -i ${clip_id}-audio.mp4 -c copy ${clip_id}.mp4
```

## Install

```
go get -u github.com/akiomik/vimeo-dl
```

## Build

```sh
go build -v .
```

## Test

```sh
go test -v ./...
```
