cmake_minimum_required(VERSION 3.10)

set(CMAKE_C_COMPILER /usr/bin/arm-none-eabi-gcc)
set(CMAKE_CXX_COMPILER /usr/bin/arm-none-eabi-g++)

include(cmake/toolchain.cmake)

project(n32g031_template)

enable_language(C)
enable_language(CXX)
enable_language(ASM)

# Custom linker script
set(TARGET_LD_SCRIPT ${CMAKE_SOURCE_DIR}/ld/n32g031_flash.ld)
# Custom startup
# set(TARGET_STARTUP_ASM ${CMAKE_SOURCE_DIR}/startup/startup_n32g031_gcc.s)

# Add N32G031 SDK
add_subdirectory(sdk)

# Add project sources
add_executable(${PROJECT_NAME} src/main.c src/n32g031_it.c)
target_include_directories(${PROJECT_NAME} PUBLIC src)

target_link_libraries(${PROJECT_NAME} N32G031_SDK)

# Generate outputs. Comment out if not needed
generate_binary_file(${PROJECT_NAME})
generate_hex_file(${PROJECT_NAME})
generate_lst_file(${PROJECT_NAME})
generate_map_file(${PROJECT_NAME})
