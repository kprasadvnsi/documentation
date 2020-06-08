# Integrated caffe

1. Install dependencies

```bash
sudo apt-get install libprotobuf-dev libleveldb-dev libsnappy-dev
libopencv-dev libhdf5-serial-dev protobuf-compiler
sudo apt-get install --no-install-recommends libboost-all-dev
sudo apt-get install libopenblas-dev liblapack-dev libatlas-base-dev
sudo apt-get install libgflags-dev libgoogle-glog-dev liblmdb-dev
```

2. Download Caffe and modify configuration parameters

```bash
git clone https://github.com/BVLC/caffe
cd caffe
cp Makefile.config.example Makefile.config
```

Modify the parameters of Makefile.config
Change #CPU_ONLY := 1 into CPU_ONLY := 1
Change #OPENCV_VERSION := 3 into OPENCV_VERSION := 3

3. Install caffe

```bash
mkdir build
cd build
cmake ..
make all -j1
make pycaffe -j1
make test -j1
make runtest -j1
```

4. Run a simple example

Run the caffe example -- mnist instance:

Mnist is a handwritten digital library.Originally used for handwritten numeral recognition on checks, and it is now the DL's starting exercise library .The special model for mnist identification is Lenet, which is the earliest CNN model. 

The training samples of mnist data are 60,000 units, and the test samples are 10,000 units. Each sample is a black and white picture of size 28*28, and the handwritten number is 0-9, so it is divided into 10 categories.

1 Download the mnist data first

```bash
root@OrangePi:~/caffe# sh data/mnist/get_mnist.sh
```

2 There are four files under the directory after running successfully.

```bash
root@OrangePi:~/caffe/data/mnist# ls
t10k-labels-idx1-ubyte //Corresponding annotation of training set
train-labels-idx1-ubyte //Corresponding annotation of testing set
t10k-images-idx3-ubyte //Training set samples
train-images-idx3-ubyte //Testing set sample
```

3 These data cannot be used directly in caffe, and need to be converted into LMDB data:

```bash
root@OrangePi:~/caffe# sh examples/mnist/create_mnist.sh
```

4 If you want to run leveldb data, run the program under examples/ Siamese/folder.The examples/mnist/ folder will generate two folders in the examples/mnist/ directory, namely mnist_train_lmdb and mnist_test_lmdb after the LMDB data conversion is successful. The date.mdb and lock.mdb stored in the folder are the running data we need.

5 Next modify the configuration file lenet_solver.prototxt Root @ OrangePi: ~ / caffe/examples/mnist# vi lenet_solver prototxt As needed, set the maximum number of iterations at max_iter, and the last line, solver_mode, to CPU

6 Finally, run this example:

```bash
root@OrangePi:~/caffe# time sh examples/mnist/train_lenet.sh
```

```bash
I0110 06:28:06.117972 25078 caffe.cpp:197] Use CPU.
I0110 06:28:06.118988 25078 solver.cpp:45] Initializing solver from parameters:
test_iter: 100
test_interval: 500
base_lr: 0.01
display: 100
max_iter: 10000
lr_policy: "inv"
gamma: 0.0001
power: 0.75
momentum: 0.9
weight_decay: 0.0005
snapshot: 5000
snapshot_prefix: "examples/mnist/lenet"
solver_mode: CPU
net: "examples/mnist/lenet_train_test.prototxt"
......
......
......
I0110 07:25:37.016746 25078 sgd_solver.cpp:284] Snapshotting solver state to binary proto file
examples/mnist/lenet_iter_10000.solverstate
I0110 07:25:37.146054 25078 solver.cpp:327] Iteration 10000, loss = 0.00200602
I0110 07:25:37.146195 25078 solver.cpp:347] Iteration 10000, Testing net (#0)
I0110 07:25:54.299634 25080 data_layer.cpp:73] Restarting data prefetching from start.
I0110 07:25:55.010598 25078 solver.cpp:414]
Test net output #0: accuracy = 0.9913
I0110 07:25:55.010757 25078 solver.cpp:414]
Test net output #1: loss = 0.0273203 (* 1 =
0.0273203 loss)
I0110 07:25:55.010777 25078 solver.cpp:332] Optimization Done.
I0110 07:25:55.010793 25078 caffe.cpp:250] Optimization Done.
real 57m48.984s
user 58m6.479s
sys 0m1.977s
```

7 Operation conclusion

According to the above results, the running time of the CPU is about 58 minutes, with an accuracy of about 99%.