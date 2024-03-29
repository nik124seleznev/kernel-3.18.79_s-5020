#
# Copyright (C) 2015 MediaTek Inc.
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License version 2 as
# published by the Free Software Foundation.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU General Public License for more details.
#

# New architecture
ifeq ($(CONFIG_MTK_SND_SOC_NEW_ARCH),y)

# MTK Platform Support
MTK_PLATFORM := $(subst ",,$(CONFIG_MTK_PLATFORM))

# MTK Codec Chip Support
MTK_CODEC := $(subst ",,$(CONFIG_MT_SND_SOC_CODEC))

# flags for not ready feature, uncomment after ready
subdir-ccflags-y += -D_GIT318_READY
subdir-ccflags-y += -D_GIT318_PMIC_READY
subdir-ccflags-y += -DAUDIO_USING_WRAP_DRIVER
subdir-ccflags-y += -D_MT_IDLE_HEADER

# include path
subdir-ccflags-y += -Werror -I$(srctree)/drivers/misc/mediatek/include
subdir-ccflags-y += -Werror -I$(srctree)/drivers/misc/mediatek/include/mt-plat/$(MTK_PLATFORM)/include
subdir-ccflags-y += -Werror -I$(srctree)/drivers/misc/mediatek/include/mt-plat
subdir-ccflags-y += -Werror -I$(srctree)/drivers/misc/mediatek/base/power/include
subdir-ccflags-y += -Werror -I$(srctree)/drivers/misc/mediatek/base/power/$(MTK_PLATFORM)
subdir-ccflags-y += -Werror -I$(srctree)/drivers/misc/mediatek/scp/$(MTK_PLATFORM)/

# Common include path
subdir-ccflags-y += -Werror -I$(src)/common

# PMIC include path
subdir-ccflags-y += -Werror -I$(src)/codec/$(MTK_CODEC)

# AP include path
subdir-ccflags-y += -Werror -I$(src)/$(MTK_PLATFORM)

# Update pmic built flow to avoid codec init later than codec probe
obj-y += common/
obj-y += codec/$(MTK_CODEC)/
obj-y += $(MTK_PLATFORM)/

# Old architecture
else

obj-y += common/
obj-$(CONFIG_MT_SND_SOC_6570) += mt6570/
obj-$(CONFIG_MT_SND_SOC_6580) += mt6580/
ifneq ($(CONFIG_MT_SND_SOC_2701),)
obj-$(CONFIG_MT_SND_SOC_2701) += mt2701/
endif

# End CONFIG_MTK_SND_SOC_NEW_ARCH
endif

ifeq ($(CONFIG_MTK_BTCVSD_ALSA),y)
obj-y += common/
endif
