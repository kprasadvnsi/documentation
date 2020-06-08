# Install opencv

## 1. apt-get way installation

Execute the following command

```bash
apt-get install libopencv-dev
apt-get install python-opencv
```

Test program test.py
```bash
import cv2 as cv
img = cv.imread("/usr/share/lxde/wallpapers/orangepi.jpg")
cv.namedWindow("Image")
cv.imshow("Image", img)
cv.waitKey(0)
cv.destroyAllWindows()
```

Run the test program

```bash
python test.py
```