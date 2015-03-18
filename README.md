# android-h264-stream-demo

## What it does
This is an example project to show how to streaming from android camera to 
VLC or gstreamer.

This demo project use MediaCodec API to encode H.264 data
and simply wrap with UDP packet then send these packets to VLC or gstreamer.

## How does it work 
The working flow as below
camera preview data(YV12) -> YUV420sp -> MediaCodec -> H.264 data -> UDP 

## Media Server

By using VLC and gstreamer, we can ensure that the H.264 video streaming is working fine.
You can use the following command to start a media server.

### VLC
```
vlc -vvv udp://@:<port>
```

### gstreamer
```
gst-launch udpsrc port=<port> ! video/x-h264,width=<w>,height=<h>,framerate=<framerate>/1 ! ffdec_h264 ! autovideosink
```
 
## Requirement
- Minimal API requirement: 16

## License
```
Copyright (C) 2015 Ping-Chun Tseng <lucas.pctseng@gmail.com> 
Licensed under Apache 2.0
```

## Notes
- In some network environment, UDP packet may be cut by MTU limitation


## Future works
- Support H.264 over RTP (RFC3984)
- Support NV21 and YUV420p image format

