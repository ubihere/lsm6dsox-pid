find_package(Zephyr REQUIRED HINTS $ENV{ZEPHYR_BASE})

add_library(lsm6dsox-pid STATIC
    src/lsm6dsox_reg.c
)

target_include_directories(lsm6dsox-pid
    PUBLIC
        ${CMAKE_CURRENT_SOURCE_DIR}/inc
)

# Link against Zephyr
target_link_libraries(lsm6dsox-pid
    PRIVATE
        zephyr_interface
)

add_dependencies(lsm6dsox-pid zephyr_generated_headers)