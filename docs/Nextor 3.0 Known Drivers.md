# Nextor 3.0 Known Drivers

As of Nextor 3.0 the device drivers for specific hardware no longer live in the Nextor repository: each driver has its own dedicated repository, which consumes [the Nextor SDK](../sdk/README.md) and produces a ready-to-use Nextor kernel ROM (and in some cases a RAM-loadable driver file too) by combining the Nextor kernel base file with the driver code. See the README file of each repository for the build instructions and for the downloadable ROM files.

These are the known device drivers available for Nextor 3:

| Driver | Hardware | Repository |
| --- | --- | --- |
| Sunrise IDE | Sunrise IDE cartridges and compatible storage controllers | [SunriseIDE-Nextor-driver](https://github.com/Konamiman/SunriseIDE-Nextor-driver) |
| MegaFlashROM SCC+ SD | [MegaFlashROM SCC+ SD](https://www.msxcartridgeshop.com/) cartridges | [MegaFlashROM-SD-Nextor-driver](https://github.com/Konamiman/MegaFlashROM-SD-Nextor-driver) |
| FlashJacks | FlashJacks IDE interface | [Flashjacks-Nextor-driver](https://github.com/Konamiman/Flashjacks-Nextor-driver) |
| MSX Turbo-R FDD | The floppy disk controller built into the MSX Turbo-R computers (Panasonic FS-A1GT and FS-A1ST); can be built as a ROM kernel or as a RAM-loadable driver | [TurboR-FDD-Nextor-driver](https://github.com/Konamiman/TurboR-FDD-Nextor-driver) |

Additionally, the Nextor repository itself contains [the standalone ROM driver](../source/drivers/standalone-rom-driver.asm) (a dummy driver that doesn't handle any real hardware, used to build the standalone Nextor ROMs) and [an example RAM-loadable driver](../source/drivers/ram-driver-example.asm); both are useful as reference code when developing a new driver.

Notes:

* The Nextor 2 versions of these drivers (except the Turbo-R FDD driver, which is new in Nextor 3) remain available in [the v2.1 branch](https://github.com/Konamiman/Nextor/tree/v2.1/source/kernel/drivers) of the Nextor repository. Remember that Nextor 2 drivers don't work with Nextor 3 and vice versa; see [the Nextor 3.0 Driver Migration Guide](Nextor%203.0%20Driver%20Migration%20Guide.md) for how to adapt a Nextor 2 driver to Nextor 3.

* The OCM (One Chip MSX) driver that was part of Nextor 2 has been discontinued, since its source code is not available.

If you have developed a driver for Nextor 3 and want it listed here, please open an issue or a pull request in [the Nextor repository](https://github.com/Konamiman/Nextor).
