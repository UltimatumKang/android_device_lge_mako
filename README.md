android_device_lge_mako
=======================

Linaro Instructions
--------

-This will show you how to compile Mako with the SaberMod Linaro Toolchains and compile with the SaberMod Mako Kernel
-First take the below manifest and put it in a blank file and rename it to "local_manifest.xml" and put in the .repo folder of you Xylon source folder.
-It will pull in the Linaro Toolchains and SaberMod Kernel source and replace the CM Kernel Source as well as the Google 4.7 Toolchains.
-Next go into tge device/lge/mako folder and open up "BoardConfig.mk" and look for "TARGET_KERNEL_CUSTOM_TOOLCHAIN := arm-eabi-4.6" and delete that line and save.
-Next do a repo sync and build. :D

local_manifest.xml
---------------------------------------

<?xml version="1.0" encoding="UTF-8"?>
<manifest>

 <remote  name="sm"
          fetch="https://github.com/SaberMod/" />

 <!-- Kernel Swap -->
 <remove-project name="lge-kernel-mako" />
 <project path="kernel/lge/mako" name="lge-kernel-mako" remote="sm" revision="sm-jb-mr1-wip" />
 
  
 <!-- Toolchain Swap -->
 <remove-project name="platform/prebuilts/gcc/linux-x86/arm/arm-eabi-4.7" />
 <remove-project name="platform/prebuilts/gcc/linux-x86/arm/arm-linux-androideabi-4.7" />
 <project path="prebuilts/gcc/linux-x86/arm/arm-eabi-4.7" name="android_prebuilts_gcc_linux-x86_arm_sabermod-arm-eabi-4.7" remote="sm" revision="master" />
 <project path="prebuilts/gcc/linux-x86/arm/arm-linux-androideabi-4.7" name="android_prebuilts_gcc_linux-x86_arm_sabermod-arm-linux-androideabi-4.7" remote="sm" revision="master" />
  
</manifest>
