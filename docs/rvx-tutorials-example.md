# NPX Example Platforms

Examples are the best way to learn.
Each example is a platform that shows one NPX feature.

## Prerequisite

- [Tutorial: Hello](rvx-tutorials-hello.md)

## Location

The example platforms are installed with NPX (`make install`) in `#(cloned directory)/rvx_platform_example`.

- Source: <https://github.com/riscvexpress/rvx_platform_example>

Each platform directory has a `README.md` with the same content as the pages below.

## Example List

| Platform | Description |
| --- | --- |
| [test_clock](examples/test_clock.md) | Clocks defined in the platform XML and assigned to clock domains |
| [test_fileio](examples/test_fileio.md) | Fakefile API: open, read, and write files by name |
| [test_flash](examples/test_flash.md) | SPI flash for app binaries and the flash file system (littlefs) |
| [test_gpio](examples/test_gpio.md) | User GPIO read by polling or by interrupt |
| [test_ila](examples/test_ila.md) | Xilinx ILA added to the FPGA implementation |
| [test_image](examples/test_image.md) | ArduCAM camera and RGB/BW OLED displays |
| [test_interrupt](examples/test_interrupt.md) | Every interrupt source: software, timer, and PLIC |
| [test_matrix](examples/test_matrix.md) | Template for checking a matrix accelerator against the software library |
| [test_mmio_gen](examples/test_mmio_gen.md) | User IP registers: `user_mmiox1` or generated from XML |
| [test_profiling](examples/test_profiling.md) | Timing functions and the profiling API |
| [test_sim](examples/test_sim.md) | Simulation options in the platform XML |
| [test_user_ip](examples/test_user_ip.md) | User IPs added to a platform and accessed from software |

## Running an Example

```text
cd #(cloned directory)/rvx_platform_example/#(platform name)
make syn
make sim_rtl
cd sim_rtl
make #(app name).sim
```

For FPGA runs and the apps of each platform, see its page.
