# `aarch64` version of Paddle Paddle compiled with Python 3.9 

I build this for my rochchip rk3588.

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
make -j$(nproc)
 ```

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
