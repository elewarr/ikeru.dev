---
title: "OpenBSD Kernel Drivers"
description: "Kernel drivers for Allwinner ARM SoCs accepted into the official OpenBSD source tree — Security ID, PWM controller, and backlight."
weight: 4
---

## OpenBSD Kernel Drivers

A set of kernel drivers for Allwinner ARM system-on-chip platforms, accepted into the official [OpenBSD](https://www.openbsd.org/) source tree. These drivers target the ARM-based SoCs commonly found in single-board computers like Pine64 and Orange Pi, enabling hardware support for PWM, display backlight control, and chip identification.

All drivers use the Flattened Device Tree (FDT) framework for hardware description and follow OpenBSD's kernel coding conventions.

{{< spacer >}}

## The Drivers

{{< cards count=3 >}}
{{< card >}}
### sxisid
**Security ID / eFuse Reader**

Reads factory-programmed unique chip identification data from Allwinner SoC non-volatile memory. Supports multiple SoC variants (A10, A20, A83T, H3, A64, H5, H6) and feeds chip entropy into the kernel's random number pool.

[View source](https://github.com/openbsd/src/blob/master/sys/dev/fdt/sxisid.c)
{{< /card >}}
{{< card >}}
### sxipwm
**PWM Controller**

Driver for the Allwinner sun5i-a13 Pulse Width Modulation controller. Manages PWM channels with configurable prescalers, period, and duty cycle — the low-level hardware interface that other subsystems (like backlight control) build on.

[View source](https://github.com/openbsd/src/blob/master/sys/dev/fdt/sxipwm.c)
{{< /card >}}
{{< card >}}
### pwmbl
**PWM Backlight**

Controls LCD and display backlight brightness via PWM signals. Supports brightness level tables from the device tree, smooth interpolation between levels, suspend/resume handling, and integration with OpenBSD's wscons display subsystem.

[View source](https://github.com/openbsd/src/blob/master/sys/dev/fdt/pwmbl.c)
{{< /card >}}
{{< /cards >}}

{{< spacer >}}

## Technical Details

- **Platform:** Allwinner ARM SoCs (sun4i through sun50i families)
- **Framework:** FDT (Flattened Device Tree) for hardware discovery and configuration
- **Language:** C, following OpenBSD kernel style
- **License:** ISC (standard OpenBSD license)

The drivers work together as a stack: **sxisid** handles chip identification and entropy seeding, **sxipwm** provides the PWM hardware interface, and **pwmbl** uses it to control display brightness — all essential pieces for running OpenBSD on Allwinner-based ARM boards.
