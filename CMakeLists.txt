cmake_minimum_required(VERSION 3.13)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set(PICO_BOARD pico_w CACHE STRING "Board type")
include(pico_sdk_import.cmake)
project(mqtt_client C CXX ASM)
pico_sdk_init()

add_executable(mqtt_client mqtt_client.c)

pico_set_program_name(mqtt_client "mqtt_client")
pico_set_program_version(mqtt_client "0.1")

pico_enable_stdio_uart(mqtt_client 1)
pico_enable_stdio_usb(mqtt_client 1)

target_link_libraries(mqtt_client
    pico_stdlib
    hardware_adc
    hardware_pwm
    pico_cyw43_arch_lwip_threadsafe_background
    pico_lwip_mqtt
    pico_mbedtls
    pico_lwip_mbedtls
    )

target_include_directories(mqtt_client PRIVATE
        ${CMAKE_CURRENT_LIST_DIR}/lib
)

pico_add_extra_outputs(mqtt_client)