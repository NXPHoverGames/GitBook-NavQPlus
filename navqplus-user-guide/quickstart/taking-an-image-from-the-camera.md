---
description: Take an image using the camera
---

# Camera Usage

NavQPlus models typically ship with one Omnivision camera module which is either from Innowave or Google Coral Camera. 3rd parties may also have other cameras. An additional camera can also be added to the second MIPI port.  Note that other USB or Ethernet cameras can also supply image data to the NavQPlus.\
\
To take an image using an attached MIPI camera module on NavQPlus, use the `gstreamer` command. An example command is as follows:

```
sudo gst-launch-1.0 -v v4l2src device=/dev/video3 num-buffers=1 ! jpegenc ! filesink location=capture1.jpeg
```

