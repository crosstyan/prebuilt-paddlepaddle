# `aarch64` version of Paddle Paddle compiled

I build this for my rochchip rk3588. Check the [release](https://github.com/crosstyan/prebuilt-paddlepaddle/releases/tag/v2.5.0)

See also [飞腾/鲲鹏下从源码编译](https://www.paddlepaddle.org.cn/documentation/docs/zh/install/compile/arm-compile.html)

```bash
git clone https://github.com/PaddlePaddle/Paddle --branch v2.5.0
cd Paddle
git checkout v2.5.0
mkdir build
cd build
# change `PY_VERSION` adn `PYTHON_EXECUTABLE` to your python version
# install `python3.9-dev` to get header files
# use `which python3.9` to get the path of python3.9
cmake .. -DPY_VERSION=3.9 -DWITH_GPU=OFF -DWITH_ARM=ON -DWITH_TESTING=OFF -DCMAKE_BUILD_TYPE=Release -DON_INFER=ON -DWITH_XBYAK=OFF -DPYTHON_EXECUTABLE=/usr/bin/python3.9
# `TARGET=ARMV8` is not really needed since I don't do cross compile
sudo -H make -j$(nproc)
 ```

If you want compile with Python 3.11

 ```bash
# https://github.com/PaddlePaddle/Paddle/blob/develop/python/requirements.txt
# pwd is build directory
sudo -H python3.11 -m pip install -r ../python/requirements.txt
cmake .. -DPY_VERSION=3.11 -DWITH_GPU=OFF -DWITH_ARM=ON -DWITH_TESTING=OFF -DCMAKE_BUILD_TYPE=Release -DON_INFER=ON -DWITH_XBYAK=OFF -DPYTHON_EXECUTABLE=/usr/local/bin/python3.11 -DPYTHON_LIBRARY=/usr/local/lib/libpython3.11.a -DPYTHON_INCLUDE_DIR=/usr/local/include/python3.11
sudo -H make -j$(nproc)
 ```

 See also [FindPythonLibs](https://github.com/Kitware/CMake/blob/master/Modules/FindPythonLibs.cmake).

```txt
OS: Debian GNU/Linux 11 (bullseye) aarch64 
Host: Firefly ITX-3588J HDMI(Linux) 
Kernel: 5.10.66 
Uptime: 41 days, 1 hour, 2 mins 
Packages: 2215 (dpkg) 
Shell: zsh 5.8 
Terminal: /dev/pts/0 
CPU: (8) @ 1.800GHz 
Memory: 1975MiB / 15445MiB
```
