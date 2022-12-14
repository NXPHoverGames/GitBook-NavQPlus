# Take an image using the camera

NavQPlus models typically ship with one Google Coral Camera. An additional camera can also be added to the second MIPI port.  Note that other USB or Ethernet cameras can also supply image data to the NavQPlus.\
\
To take an image using an attached MIPI camera module on NavQPlus, use the `gstreamer` command. An example command is as follows:

```
sudo gst-launch-1.0 -v v4l2src device=/dev/video3 num-buffers=1 ! jpegenc ! filesink location=capture1.jpeg
```

