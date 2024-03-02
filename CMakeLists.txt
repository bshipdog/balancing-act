cmake_minimum_required(VERSION 3.13)            # Specify the minimum required version of cmake
set(ENV{PICO_SDK_PATH} "~/pico/pico-sdk/")      # Specify the path to Raspberry Pi Pico C/C++ SDK in your system
include(pico_sdk_import.cmake)                  # Include the contents of the pico_sdk_import.cmake file that exists in the same folder
project(myProject C CXX ASM)                    # Specify the name of the project and the type of source files it may contain

set(CMAKE_C_STANDARD 11)                        # Specify what C standard to follow
set(CMAKE_CXX_STANDARD 17)                      # Specify what C++ standard to follow
pico_sdk_init()                                 # Initialize necessary components of the SDK

add_executable(myProject                        # This is where the name of the C/C++ file will go.
*.c
)
pico_add_extra_outputs(myProject)               # Tell cmake to create a UF2 file

pico_enable_stdio_usb(myProject 1)              # Configures USB as the 'Standard Input Output'
pico_enable_stdio_uart(myProject 0)             # Don't configure UART as the 'Standard Input Output'

target_link_libraries(myProject pico_stdlib)    # Link libraries that are used in this project
