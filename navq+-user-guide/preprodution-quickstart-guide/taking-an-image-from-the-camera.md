# Taking an image from the camera

To take an image from the camera on NavQ+, use the `gstreamer` command. An example command is as follows:

```
sudo gst-launch-1.0 -v v4l2src device=/dev/video3 num-buffers=1 ! jpegenc ! filesink location=capture1.jpeg
```

