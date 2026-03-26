# n32g031-cmake-template
A simple n32g031 cmake project template.

## Required toolchain
- Assumes `arm-none-eabi-gcc` installed in `/usr/bin`. Otherwise, change `CMAKE_C_COMPILER` and `CMAKE_CXX_COMPILER` in [CMakeLists.txt](CMakeLists.txt)
- Uses [picolibc](https://keithp.com/picolibc/) as the standard library
- Uses [pyOCD](https://pyocd.io/) for debugging. Install the required pack with `pyocd pack install N32G031`

## Custom ld or startup.s
Set `TARGET_LD_SCRIPT` and `TARGET_STARTUP_ASM` as your own before `add_subdirectory(sdk)`  
See: [CMakeLists.txt](CMakeLists.txt)

## License
See [LICENSE](LICENSE)
