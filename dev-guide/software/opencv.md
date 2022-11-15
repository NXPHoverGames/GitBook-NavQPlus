# OpenCV

{% hint style="info" %}
If using an downloaded image, check first that these packages are not already installed.
{% endhint %}

## Accessing the cameras using OpenCV in Python

### Getting started

To install OpenCV for Python to the image, run the following command:

```
sudo apt install python3-opencv
```

### Getting images from the camera using Gstreamer pipelines

To access the Google Coral Camera(s) on NavQ+ in OpenCV, you may use the following VideoCapture instantiation:

```
cap = cv2.VideoCapture('v4l2src device=/dev/video3 ! video/x-raw,framerate=30/1,width=640,height=480 ! appsink', cv2.CAP_GSTREAMER)
```

You may change the source resolution by editing the width and height values in the GStreamer pipeline. See below for a list of supported resolutions and framerates.

```
video/x-raw, format=YUY2, width=2592, height=1944, framerate=8/1
video/x-raw, format=YUY2, width=1920, height=1080, framerate={ (fraction)15/1, (fraction)30/1 }
video/x-raw, format=YUY2, width=1280, height=720, framerate={ (fraction)15/1, (fraction)30/1 }
video/x-raw, format=YUY2, width=1024, height=768, framerate={ (fraction)15/1, (fraction)30/1 }
video/x-raw, format=YUY2, width=720, height=576, framerate={ (fraction)15/1, (fraction)30/1 }
video/x-raw, format=YUY2, width=720, height=480, framerate={ (fraction)15/1, (fraction)30/1 }
video/x-raw, format=YUY2, width=640, height=480, framerate={ (fraction)15/1, (fraction)30/1 }
video/x-raw, format=YUY2, width=320, height=240, framerate={ (fraction)15/1, (fraction)30/1 }
video/x-raw, format=YUY2, width=176, height=144, framerate={ (fraction)15/1, (fraction)30/1 }
```
