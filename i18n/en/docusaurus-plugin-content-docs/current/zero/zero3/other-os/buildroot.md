---
sidebar_position: 10
description: "Buildroot"
---

# Buildroot

## Preparation

We need one Ubuntu 20.04/22.04 x86_64 PC.\
(ubuntu-22.04.5-live-server-amd64 virtual machine with 120G disk used in example.)

## Install build dependencies

```
sudo apt update
sudo apt install python2 git rsync gcc g++ make device-tree-compiler bc flex bison lz4 libssl-dev libgmp-dev libmpc-dev expect expect-dev file unzip bzip2 fakeroot bsdmainutils
sudo ln -s /bin/python2 /bin/python
```

## Get rockchip original SDK

- Mega: https://mega.nz/file/JugCGDDC#NNL5_qRDRr-NL6TS3F1FSzkoXFwRCwDTNTW3KAiTtpI
- BaiduPan: https://pan.baidu.com/s/12rQmYaRMKwgz8cOBNjc4yQ?pwd=35mj

## Extract SDK

On Ubuntu PC we use the following commands to extract the SDK.

```
tar xvf rk356x_linux5.10_rkr8_sdk.repo.tar
.repo/repo/repo  sync -l
```

## Add board Zero 3E support

Use Radxa reposiory, rockchip.

```
cd device/rockchip
git remote add radxa https://github.com/radxa/device-rockchip.git
git pull radxa rk3566_rk3568-linux-5.10
git checkout rk3566_rk3568-linux-5.10
```

Use Radxa repository, kernel.

```
cd kernel
git remote add radxa https://github.com/radxa/kernel.git
git pull radxa linux-5.10-gen-rkr8-buildroot
git checkout linux-5.10-gen-rkr8-buildroot
```

## Build SDK

Navigate to the top-level directory of the SDK, run command.

```
./build.sh
```

And select defconfig `rockchip_rk3566_radxa_zero_3e_defconfig`.
The target images will be stored on rockdev directory.
