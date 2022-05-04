# GStreamer

## Pipeline examples

### Take an image
```
gst-launch-1.0 -v v4l2src num-buffers=1 device=/dev/video3 ! jpegenc ! filesink location=capture.jpeg
```

### Record a video
```
gst-launch-1.0 v4l2src device=/dev/video3 ! imxvideoconvert_g2d ! "video/x-raw, height=640, width=480, framerate=30/1" ! vpuenc_h264 ! avimux ! filesink location='/home/user/video.avi'
```