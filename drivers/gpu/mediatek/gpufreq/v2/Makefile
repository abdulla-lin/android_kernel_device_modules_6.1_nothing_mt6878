#
# Copyright (C) 2019 MediaTek Inc.
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License version 2 as
# published by the Free Software Foundation.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
# See http://www.gnu.org/licenses/gpl-2.0.html for more details.
#
ccflags-y += -I$(DEVICE_MODULES_PATH)/include/
ccflags-y += -I$(DEVICE_MODULES_PATH)/drivers/gpu/mediatek/gpufreq/v2/include/
ccflags-y += -I$(DEVICE_MODULES_PATH)/drivers/gpu/mediatek/ged/include/
ccflags-y += -I$(DEVICE_MODULES_PATH)/drivers/gpu/mediatek/gpueb/include/
ccflags-y += -I$(DEVICE_MODULES_PATH)/drivers/gpu/mediatek/mt-plat/
ccflags-y += -I$(DEVICE_MODULES_PATH)/drivers/misc/mediatek/include/
ccflags-y += -I$(DEVICE_MODULES_PATH)/drivers/misc/mediatek/base/power/include/
ccflags-y += -I$(DEVICE_MODULES_PATH)/drivers/clk/mediatek/
ccflags-y += -I$(DEVICE_MODULES_PATH)/drivers/misc/mediatek/power_throttling/
ccflags-y += -I$(DEVICE_MODULES_PATH)/drivers/misc/mediatek/pbm/
ccflags-y += -I$(DEVICE_MODULES_PATH)/drivers/misc/mediatek/aee/aed/

ccflags-y += \
\t-Wno-unused-variable \
\t-Wno-unused-function

ifeq ($(findstring aging,$(PROJECT_DTB_NAMES)),aging)
\tccflags-y += -DGPUFREQ_AGING_LOAD
endif

# Common wrapper
mtk_gpufreq_wrapper-y := \
\tgpufreq_v2.o \
\tgpufreq_history.o \
\tgpufreq_debug.o \
\tgpu_misc.o

# Platform bundles (stock)
mtk_gpufreq_mt6878-y := \
\tgpuppm.o \
\tgpufreq_mt6878.o \

mtk_gpufreq_mt6886-y := \
\tgpufreq_history_mt6886.o \
\tgpuppm.o \
\tgpufreq_mt6886.o \

mtk_gpufreq_mt6897-y := \
\tgpufreq_history_mt6897.o \
\tgpuppm.o \
\tgpufreq_mt6897.o \

mtk_gpufreq_mt6985-y := \
\tgpufreq_history_mt6985.o \
\tgpuppm.o \
\tgpufreq_mt6985.o

mtk_gpufreq_mt6989_fpga-y := \
\tgpufreq_history_mt6989_fpga.o \
\tgpuppm.o \
\tgpufreq_mt6989_fpga.o

mtk_gpufreq_mt6989-y := \
\tgpufreq_history_mt6989.o \
\tgpuppm.o \
\tgpufreq_mt6989.o \
\tgpu_smmu_mt6989.o

# Optimized MT6878 bundle (new)
# Place gpufreq_mt6878_optimized.c in this directory.
mtk_gpufreq_mt6878_opt-y := \
\tgpuppm.o \
\tgpufreq_mt6878_optimized.o

# Object selections
obj-$(CONFIG_MTK_GPU_SUPPORT) += mtk_gpufreq_wrapper.o

# Stock MT6878 (kept)
ifneq ($(wildcard $(srctree)/$(src)/gpufreq_mt6878.c),)
obj-$(CONFIG_MTK_GPU_MT6878_SUPPORT) += mtk_gpufreq_mt6878.o
endif

# Optimized MT6878 (new)
ifneq ($(wildcard $(srctree)/$(src)/gpufreq_mt6878_optimized.c),)
obj-$(CONFIG_MTK_GPU_MT6878_OPT_SUPPORT) += mtk_gpufreq_mt6878_opt.o
endif

# Other platforms (unchanged)
ifneq ($(wildcard $(srctree)/$(src)/gpufreq_mt6886.c),)
ifneq ($(wildcard $(srctree)/$(src)/gpufreq_history_mt6886.c),)
obj-$(CONFIG_MTK_GPU_MT6886_SUPPORT) += mtk_gpufreq_mt6886.o
endif
endif

ifneq ($(wildcard $(srctree)/$(src)/gpufreq_mt6897.c),)
ifneq ($(wildcard $(srctree)/$(src)/gpufreq_history_mt6897.c),)
obj-$(CONFIG_MTK_GPU_MT6897_SUPPORT) += mtk_gpufreq_mt6897.o
endif
endif

ifneq ($(wildcard $(srctree)/$(src)/gpufreq_mt6985.c),)
ifneq ($(wildcard $(srctree)/$(src)/gpufreq_history_mt6985.c),)
obj-$(CONFIG_MTK_GPU_MT6985_SUPPORT) += mtk_gpufreq_mt6985.o
endif
endif

ifneq ($(wildcard $(srctree)/$(src)/gpufreq_mt6989_fpga.c),)
ifneq ($(wildcard $(srctree)/$(src)/gpufreq_history_mt6989_fpga.c),)
obj-$(CONFIG_MTK_GPU_MT6989_SUPPORT) += mtk_gpufreq_mt6989_fpga.o
endif
endif

ifneq ($(wildcard $(srctree)/$(src)/gpufreq_mt6989.c),)
ifneq ($(wildcard $(srctree)/$(src)/gpufreq_history_mt6989.c),)
ifneq ($(wildcard $(srctree)/$(src)/gpu_smmu_mt6989.c),)
obj-$(CONFIG_MTK_GPU_MT6989_SUPPORT) += mtk_gpufreq_mt6989.o
endif
endif
endif
