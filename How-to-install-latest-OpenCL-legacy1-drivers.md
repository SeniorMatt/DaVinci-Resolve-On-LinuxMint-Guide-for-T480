Read this:
https://github.com/intel/compute-runtime/blob/master/LEGACY_PLATFORMS.md
And then this: 
https://github.com/intel/compute-runtime/releases/tag/24.35.30872.22


You can either follow the installation, but I was hit with an error `libigdgmm12:i386` was never version than the `libigdgmm12:amd64` that I needed to install. So I needed to write this command
```
sudo apt remove --purge libigdgmm12:i386
```
To remove it. After that I manually downloaded and installed the
1. `libigdgmm12_22.5.0_amd64.deb`
2. `intel-level-zero-gpu-legacy1_1.3.30872.22_amd64.deb`
3. `intel-opencl-icd-legacy1_24.35.30872.22_amd64.deb`

And now DaVinci Resolve just works!
