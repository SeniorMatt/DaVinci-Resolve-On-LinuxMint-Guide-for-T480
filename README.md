# DaVinci Resolve on LinuxMint Guide for T480
> also it supposed to work for any laptop / desktop with an a i5-8350u iGPU
# Installing
Download the issue from the official site - https://apps.cloud.blackmagicdesign.com/davinci-resolve
You will need to register to install.
After you downloaded the `.zip` extract it anywhere you want.
Then open the terminal...

# Setting up
Change directory where `.run` is located. **In my case here:**
```
cd ~/Downloads/DaVinci_Resolve_20.2.3_Linux/
```
Then write this command to run the official installation progress. write `./NameOfTheRunFile.run`, which **in my case is this**:
```
sudo SKIP_PACKAGE_CHECK=1 ./DaVinci_Resolve_20.2.3_Linux.run -i
```
Then click `y` a bunch of times.

# Make DaVinci launch properly
It won't launch right away. You need to ran this commands:
```
cd /opt/resolve/libs
```
```
sudo mkdir oldlibs
```
```
sudo mv libglib* oldlibs
```
```
sudo mv libgio* oldlibs
```
```
sudo mv libgmodule* oldlibs
```
```
sudo mv libgobject* oldlibs
```
Then it is supposed to launch.

# Unsupported GPU type error
If you are using Intel GPU run this command to install the **OpenCL** drivers:
```
sudo apt install intel-opencl-icd
```
! IMPORTANT !
If you are using a CPU that is Older than 12-th gen then you can follow guide bellow to install correct latest available **OpenCL** drivers (also works perfectly for your *glorious* **Thinkpad T480 i5-8350u iGPU**).

# How to install last available OpenCL-legacy1 drivers
Read this:
https://github.com/intel/compute-runtime/blob/master/LEGACY_PLATFORMS.md
And then this: 
https://github.com/intel/compute-runtime/releases/tag/24.35.30872.22

You can either follow the installation, but I was hit with an error `libigdgmm12:i386` was never version than the `libigdgmm12:amd64` that I needed to install. So I needed to write this command:
```
sudo apt remove --purge libigdgmm12:i386
```
To remove it. After that I manually downloaded and installed these files from here https://github.com/intel/compute-runtime/releases/tag/24.35.30872.22:
1. `libigdgmm12_22.5.0_amd64.deb`
2. `intel-level-zero-gpu-legacy1_1.3.30872.22_amd64.deb`
3. `intel-opencl-icd-legacy1_24.35.30872.22_amd64.deb`

And now DaVinci Resolve just works!
