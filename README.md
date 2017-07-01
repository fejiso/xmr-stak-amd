### XMR-Stak-AMD - Monero mining software

XMR-Stak is a universal Stratum pool miner. This is the Intel GPU-mining version; based on the [AMD one](https://github.com/fireice-uk/xmr-stak-amd).

-- #### HTML reports

-- <img src="https://gist.githubusercontent.com/fireice-uk/2da301131ac01695ff79539a27b81d68/raw/e948641897ba79e5a6ee78e8248cc07779d6eac7/xmr-stak-amd-hashrate.png" width="260"> <img src="https://gist.githubusercontent.com/fireice-uk/2da301131ac01695ff79539a27b81d68/raw/e948641897ba79e5a6ee78e8248cc07779d6eac7/xmr-stak-amd-results.png" width="260"> <img src="https://gist.githubusercontent.com/fireice-uk/2da301131ac01695ff79539a27b81d68/raw/e948641897ba79e5a6ee78e8248cc07779d6eac7/xmr-stak-amd-connection.png" width="260">

-- The hashrate shown above was generated on a non-modded, non-overclocked RX 480.



#### Usage on Linux (Arch-based distros)

PKGBUILD available in AUR.

pacaur/yaourt/ -S xmr-stak-intel

It will install the OpenCL needed dependencies: intel-opencl (for integrated graphics), beignet (for integrated graphics, wider support). You would be able to use one or both platforms depending on your hardware. 

#### Usage on Linux (Debian-based distros)

**Intel Driver**

For recent Intel Graphics chipsets you should use:

https://software.intel.com/en-us/articles/opencl-drivers#philinux

If you have an older chipset, as back as IvyBridge Intel Core/Xeon and BayTrail Atoms (but also modern ones) you need beignet:

    

```
    sudo apt-get install beignet  
    cmake .
    make
```

GCC version 5.1 or higher is required for full C++11 support. CMake release compile scripts, as well as CodeBlocks build environment for debug builds is included.

#### Usage on Windows  (unsupported)

Not supported for the time being, you can build it yourself though:  XMR-Stak should compile on any C++11 compliant compiler like zmr-stak-amd does. Windows compiler is assumed to be MSVC 2015 CE. MSVC build environment is not vendored.

Once built, two things to do:

1) Edit the config.txt file to enter your pool login and password. 
2) Double click the exe file. 

#### Mining performance 

Mining core is a direct port (except for sercurity fixes) of wolf9466's AMD mining code. Performance is likely to be identical. Limiting the amount of running processes improves the performance significantly as the cache miss ratio is reduced. The ideal mining machine should have the miner run as root, with high priority (realtime priority if you have unused cores/threads) and no other than the bare minimum services and daemons running.


You will need to adjust config.txt values, particularly intensity and worksize. Check what works best for other owners of the same chipset, and start little by little adjusting from there.

#### Default dev donation
By default the miner will donate 1% of the hashpower (1 minute in 100 minutes) to my pool. If you want to change that, edit **donate-level.h** before you build the binaries.

If you want to donate directly to support further development, here is my wallet
```
48kstTxZUxKKFSkPH8MhmyazDAzHF2qF4Z5mUtyJ6GM8akzBGmybqdgLy86Uw6VkrC17PZEcWQaUyQSXUpnPQJB9TzAsWd6
```

