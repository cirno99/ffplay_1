cmake_minimum_required(VERSION 3.20)
project(ffplay_clion)

set(CMAKE_CXX_STANDARD 14)

## 添加头文件
include_directories(/usr/include)
include_directories(/usr/include/SDL2)

## 添加目标链接
link_libraries(/usr/lib/libSDL2-2.0.so.0)
link_libraries(/usr/lib/libm.so.6)

find_package(PkgConfig REQUIRED)
pkg_check_modules(LIBAV REQUIRED IMPORTED_TARGET
        libavdevice
        libavfilter
        libavformat
        libavcodec
        libswresample
        libswscale
        libavutil
        )
link_libraries(PkgConfig::LIBAV)

# 执行编译命令
add_executable(${PROJECT_NAME} ffplay.c fftools/cmdutils.c fftools/opt_common.c)
