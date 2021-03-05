# object_detection
object detection fine tuning on Nvidia Jetson

## install the appropriate NGC for your hardware from here
https://ngc.nvidia.com/catalog/containers/
I am running on a Jetson Xavier NX, I got the latest l4t available at teh time of this writing 'l4t-tensorflow:r32.5.0-tf1.15-py3'

sudo docker run -it --rm --runtime=nvidia nvcr.io/nvidia/l4t-tensorflow:r32.5.0-tf1.15-py3
apt update
apt-get install protobuf-compiler python-pil python-lxml 
apt-get install python-tk
apt install git
git clone https://github.com/tensorflow/models.git
apt-get install vim
pip3 install --upgrade pip
python3 -m pip install -c constraints.txt .
