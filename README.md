# setup-OpenCV-3.2-python
Install script for OpenCV


## In Ubuntu 16.04

Open the Terminal inside the SceneDensity directory, activate the virtual environment you by following command.

```sh
workon OpenCV
```

Use the following command to run the annotation tool. You will see an instruction about how to use this tool.

```sh
python annotate.py
```

## In Windows 10

Open command prompt and use the command below to run the tool.You will see an instruction about how to use this tool.

```sh
python annotate.py
```


# Install OpenCV on Ubuntu

## Install dependencies

Open Terminal and use the following commands

```sh
cd ~ && mkdir OpenCV && cd OpenCV && wget https://raw.githubusercontent.com/ImOmid/SceneDensity/master/installDep.sh
```
Now, you should be inside OpenCv directory. Use the following command to install dependencies.

```sh
bash ./installDep.sh
```

Please wait, it will take time. Afterwards, close the Terminal and open a new Terminal.

## Create your Python Virtual Environment using following commands.

For Python 2.7 use:

```sh
mkvirtualenv OpenCV -p python2
```

For Python 3.5 use:

```sh
mkvirtualenv OpenCV -p python3
```

Use the following command to change your Python environment into the virtual environment you just created.

```sh
workon OpenCV
```

## Install numpy in OpenCV virtual environment using following command.

```sh
pip install numpy
```

## Change the current working directory.

Use the following command to change the directory to build directory.

```sh
cd ~/OpenCV/build
```

## Configure the build

Use the following command to configure the build. Copy and paste it into the Terminal. Current working directory <b>must be build</b>.

```sh
cmake -D CMAKE_BUILD_TYPE=RELEASE \
    -D CMAKE_INSTALL_PREFIX=/usr/local \
    -D INSTALL_PYTHON_EXAMPLES=ON \
    -D INSTALL_C_EXAMPLES=OFF \
    -D OPENCV_EXTRA_MODULES_PATH=~/OpenCV/opencv_contrib-3.2.0/modules \
    -D PYTHON_EXECUTABLE=~/.virtualenvs/OpenCV/bin/python \
    -D BUILD_EXAMPLES=ON ../opencv-3.2.0
```

<b>Be sure to check the output of CMake</b> before going to next step. You sould see an output in which cmake found the Interpreter, Libraries, numpy path for Python. The output is similar to YouTube Video on <a href="https://youtu.be/LneXUj7NBng?t=232" target="_blank">How to build and Install OpenCV 3.2 Python on Ubuntu 16.04.</a><br/>


## If there is no error in the previsous pass, use the following command to compile OpenCV.

```sh
make
```

<b>It can take up to 2 hours based on your Computer specifications. Be patient!</b>

If the compile finished without any error go to next step. Otherwise, use the following command to clean and make again.

```sh
make clean && make
```

## Install OpenCV

Use the below commands to install OpenCV

```sh
sudo make install
sudo ldconfig
```

## Finish OpenCV installation

Use the folllowing commands to build a symbolic link for OpenCV cv2.so.

For Python 2.7:
```sh
cd ~/.virtualenvs/OpenCV/lib/python2.7/site-packages/
ln -s /usr/local/lib/python2.7/site-packages/cv2.so cv2.so
```

For Python 3.5:
```sh
cd /usr/local/lib/python3.5/site-packages/
sudo mv cv2.cpython-35m-x86_64-linux-gnu.so cv2.so # Rename the file
cd ~/.virtualenvs/cv/lib/python3.5/site-packages/
ln -s /usr/local/lib/python3.5/site-packages/cv2.so cv2.so
```

## Test OpenCV install

If all the previous steps are done successfully. You should be able to import OpenCV in your virtual environment. Use the following commands to verify it.

### Open python inside OpenCV virtula environment.
```sh
cd ~
workon OpenCV
python
```

### In the python interpereter import cv2 and check its version.
```sh
import cv2
cv2.__version__
```

The output should be '3.2.0'


