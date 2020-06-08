# Integrated TensorFlow

TensorFlow:1.14.0
Python environment:python2.7

## 1. Installation of python environment and dependencies

Choose pre-installed python2.7 instead of installing python3.x

Installation dependencies:

```bash
sudo apt-get install python-pip python-dev libatlas-base-dev
```

## 2. Install TensorFlow

There are several ways to install TensorFlow, but here you may choose the a
convenient way to command and installa directly .

Steps:
Download the PIP installation package for TensorFlow from the
followingtensorflow-1.14.0-cp27-none-linux_aarch64.whl

https://github.com/lhelontra/tensorflow-on-arm/releases/tag/v1.14.0

Using PIP installation:

Use PIP to install tensorflow 1.14.0 - cp27 - none - linux_aarch64. WHL Note that some dependencies may not be downloaded due to network reasons during the installation process. Please download and install the dependencies according to the version shown in the log before installing TensorFlow. vi test.py

```bash
import tensorflow as tf
hello = tf.constant('Hello, TensorFlow!')
#sess = tf.Session()
sess = tf.compat.v1.Session()
print(sess.run(hello))
```

Run the test program

```bash
root@OrangePi:~# python test.py
Hello, TensorFlow!
```

Note: This time only using python2.7 environment to install TensorFlow, python3.5 and python3.6 are all available, please test by yourself.