# rpi4 build steps

1. Fetch the sources
   
   $ repo init -u https://github.com/AtomarMent/rpi4_manifest.git -b master -m manifest.xml 
   $ repo sync

2. Set the build environment

   $ source poky/oe-init-build-env rpi-build

3. Set MACHINE in local.conf to one of the supported boards

   $ vi rpi-build/conf/local.conf 
   Add raspberrypi4-64 to MACHINE variable, i.e. MACHINE ?= "raspberrypi4-64"

4. Add meta-raspberrypi and other layers(from meta-openembedded) to bblayers.conf
   
   $ cat rpi-build/conf/bblayers.conf
    
   BBLAYERS ?= " \
  /scratch/work/sources/poky/meta \
  /scratch/work/sources/poky/meta-poky \
  /scratch/work/sources/poky/meta-yocto-bsp \
  /scratch/work/sources/meta-raspberrypi \
  /scratch/work/sources/meta-openembedded/meta-oe \
  /scratch/work/sources/meta-openembedded/meta-multimedia \
  /scratch/work/sources/meta-openembedded/meta-networking \
  /scratch/work/sources/meta-openembedded/meta-python \
  "

5. Build RPI4 images 

   $ bitbake core-image-base


