# Building Linux for NavQ+

NavQ+ runs on top of NXP's meta-nxp-desktop Yocto meta layer. This meta layer sits on top of the base Yocto BSP from NXP's Linux Factory. Internally, we build meta-nxp-desktop with a custom layer on top to support the NavQ+. Soon, NavQ+ will officially be included in NXP's Yocto BSP, which means an extra layer will not be required.

## Setting up a build machine

To build the Ubuntu 20.04 image for NavQ+, you will need a capable workstation. Your workstation will be required to run Ubuntu 20.04 natively, and will need lots of storage space, cores, and memory. Below are some recommended specs.

* Storage: 100+ GB of free space on a relatively fast SSD
* CPU: (x86.. no ARM!) 8 cores / 16 threads
* RAM: 32 GB
* OS: Ubuntu 20.04
* Relatively fast internet (>100Mb/s)

These specs are the recommended specs for running a build in a reasonable amount of time. It is technically possible to build on a machine with lesser specs, they will just take a long time. With higher thread counts, you will need more RAM to compensate. Internet speed is also quite important for the first build, as the build process will download thousands of packages to compile. After the first build, most of the packages are cached.

### Running the setup script
You will need to install some packages to build. The script for setting up your build machine is at:

`https://github.com/NXPHoverGames/yocto_build_scripts/blob/main/setup_build_machine.sh`

## Building

Once you have successfully run the setup script, you will need to take the script from the link below and place it in a folder. This folder can be called whatever you want and placed whereever you want. We suggest making a folder at `~/yocto`.

`https://github.com/NXPHoverGames/yocto_build_scripts/blob/main/navqp_build_lf5-10-72_ubuntu20-04.sh`

Run this script and it will start building the image. This will take approximately 2 hours (+- ~30 minutes depending on your specs) to finish. The resulting image will be located at `~/yocto/build/build/tmp/deploy/imx8mpnavq/*.wic.bz2`. The filename will be a .wic.bz2 with the date of the build. You will need to decompress this file using `bzip2` to flash it to your SD card. You can flash it using `dd`.