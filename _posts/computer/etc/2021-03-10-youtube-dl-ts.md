---
title: "Download TS Files from Video Stream"
# excerpt: ""

categories:
  - Computer
tags:
  - Youtube
  - youtube-dl
  - .ts

# toc: true 
# toc_label: "Table of Contents"
# toc_icon: "cog"
# toc_sticky: true

last_modified_at: 2021-03-10 23:37:00 +0900
---

```Text
# List variants (resolutions/bitrates)
$ youtube-dl -F https://bitdash-a.akamaihd.net/content/MI201109210084_1/m3u8s/f08e80da-bf1d-4e3d-8899-f0f6155f6efa.m3u8
[generic] f08e80da-bf1d-4e3d-8899-f0f6155f6efa: Requesting header
[generic] f08e80da-bf1d-4e3d-8899-f0f6155f6efa: Downloading m3u8 information
[info] Available formats for f08e80da-bf1d-4e3d-8899-f0f6155f6efa:
format code           extension  resolution note
audio-English_stereo  mp4        audio only [en] 
628                   mp4        320x180     628k , avc1.42c00d, video only
928                   mp4        480x270     928k , avc1.42c00d, video only
1728                  mp4        640x360    1728k , avc1.42c00d, video only
2528                  mp4        960x540    2528k , avc1.42c00d, video only
4928                  mp4        1280x720   4928k , avc1.42c00d, video only
9728                  mp4        1920x1080  9728k , avc1.42c00d, video only (best)

# Choose a variant to download, and use its format code below
$ youtube-dl --format 628 https://bitdash-a.akamaihd.net/content/MI201109210084_1/m3u8s/f08e80da-bf1d-4e3d-8899-f0f6155f6efa.m3u8
...
frame= 5257 fps=193 q=-1.0 Lsize=    6746kB time=00:03:30.16 bitrate= 263.0kbits/s speed=7.73x    
video:6679kB audio:0kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: 0.998669%
[ffmpeg] Downloaded 6907810 bytes
[download] 100% of 6.59MiB in 00:29

$ open f08e80da-bf1d-4e3d-8899-f0f6155f6efa-f08e80da-bf1d-4e3d-8899-f0f6155f6efa.mp4
```

