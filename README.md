# Object detection using tensorflow API on Nvidia jetson NX

We will need to build a pipeline where we can 'fine tune' a pretrained model, so its just not detection but a lot more.


### Install the appropriate NGC for your hardware from here

https://ngc.nvidia.com/catalog/containers/

I am running on a Jetson Xavier NX, I got the latest l4t available at the time of this writing 'l4t-tensorflow:r32.5.0-tf1.15-py3'

Check your l4t version, e.g. 

`$ cat /etc/nv_tegra_release`
`# R32 (release), REVISION: 4.4, GCID: 23942405, BOARD: t186ref, EABI: aarch64, DATE: Fri Oct 16 19:37:08 UTC 2020`

`sudo docker run -it --rm --runtime=nvidia nvcr.io/nvidia/l4t-tensorflow:r32.5.0-tf1.15-py3`

`apt update`

`apt-get install protobuf-compiler python-pil python-lxml python-tk`

`apt install git`

`git clone https://github.com/tensorflow/models.git`

`apt-get install vim`

### you need to upgrade pip

`$ cd /models/research/`
`$ cp object_detection/packages/tf2/setup.py .`


Unfortunately this will get us the newer version of pip that has a new dependency resolver which causes the install take a lot of time, several hours infact, this is why we will use the constraints file

`pip3 install --upgrade pip`

`python3 -m pip install -c constraints.txt .`

While installing it says

Collecting kiwisolver>=1.1.0 and keeps trying to download and verify all the versions of this package that satisfies the criteria >=1.1.0

which means the new pip [version here] it is going to try to download and verify all the kiwisolver greater than equal to version 1.1.0

Adding a restriction to this check in the constraint.txt file will ensure that the process finishes faster.


