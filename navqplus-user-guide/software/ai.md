# AI/ML

{% hint style="info" %}
If using an downloaded image, check first that these packages are not already installed.
{% endhint %}

## Inference examples

The i.MX 8M Plus SOC in the NavQPlus contains a Neural Processing Unit (NPU) that can accelerate inference on the edge. There are some inference examples built into the NavQPlus image that will do image classification with the COCO dataset.

There is a TensorFlow Lite example in the `/usr/bin/tensorflow-lite-2.6.0/examples/` folder. This example runs a mobilenet\_v1 quantized image classification model. To run it, try the command below:

```
USE_GPU_INFERENCE=0 ./label_image --external_delegate_path=/lib/libvx_delegate.so -m mobilenet_v1_1.0_224_quant.tflite -i grace_hopper.bmp -l labels.txt
```

`USE_GPU_INFERENCE=0` specifies that we want to run inference on the NPU. Removing this environment variable will run inference on the GPU.

To run inference on the GPU/NPU, you will need to use the libVX delegate, at the path `/lib/libvx_delegate.so`.

There is also a python script named label\_image.py that contains example code for inference with TFLite.
