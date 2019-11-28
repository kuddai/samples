# Audio Video Synchronization Metric Prototype Demo
Shows a basic example of how to estimate delay between audio and video tracks
in WebRTC.

You will need a special Chrome build to run this example.

Chromium changes:
[https://chromium-review.googlesource.com/c/chromium/src/+/1881164](https://chromium-review.googlesource.com/c/chromium/src/+/1881164)

WebRTC changes:
[https://webrtc-review.googlesource.com/c/src/+/158520](https://webrtc-review.googlesource.com/c/src/+/158520)

To fetch correct dependencies version use "Download" button.
Build release version of Chrome as debug version is too slow for audio/video
encoding. Use that `args.gn` config for e.g.:
```
# Set build arguments here. See `gn buildargs`
is_debug=false
enable_nacl = false
is_chrome_branded=false
is_component_build = true
```

Run Chrome with OriginTrial `RtcJitterBufferDelayHint` enabled to
activate `RTCRtpReceiver.jitterBufferDelayHint` property (renamed to
`playoutDelayHint` and enabled by default starting from M79).
```bash
/out/Release/chrome --enable-blink-features=RtcJitterBufferDelayHint
```

Run example with any HTTP server. For e.g. assuming python 2.7:
```
python -m SimpleHTTPServer 8123
```

Go to `localhost:8123` and press `Start` and `Call` buttons. You should be able
to see no delay between audio and video. Then press `Delay Audio By 2 Seconds`,
2 seconds delay between audio and video should gradually appear.



