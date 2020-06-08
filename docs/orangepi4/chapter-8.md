# USB Camera use

## 1、UVC British Fick USB webcam

1. Insert the camera directly into Pi4's USB2.0 or 3.0, and then you can query the
node of the USB camera:

```bash
root@OrangePi:~# ls /dev/video10 -la
crw-rw----+ 1 root video 81, 15 Jan 2 13:15 /dev/video10
```

My node is video10, the device node may not be /dev/video10 on your board, you
need to check。

2. After the device node comes out, you can use the USB camera。

Use motion to use the USB camera:

Install motion
```bash
Sudo apt-get install motion
```

Change setting

```bash
$ sudo nano /etc/motion/motion.conf
$ stream_localhost off
```

In the motion.cong configuration file, please note that the device node of the USB
camera is video? How many, and modify accordingly

Create a folder for saving pictures

```bash
$ mkdir ~/motion
```

Modify permissions

```bash
$ chmod 777 motion
```

Continue to modify the configuration

```bash
$ sudo nano /etc/default/motion
$ start_motion_daemon=yes
```

Start the server

```bash
$ sudo /etc/init.d/motion start
```

The last step, enter in the browser

``localhost:8081``

You can view the image output by the camera