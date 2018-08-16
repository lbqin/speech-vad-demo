cmake_minimum_required(VERSION 2.8)
set(CMAKE_VERBOSE_MAKEFILE on)
project(vad-demo)
set(CMAKE_BUILD_TYPE DEBUG)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
#set(CMAKE_C_STANDARD 99)
file(GLOB SRC_FILES src/main.c src/file_cut.c src/period_format.c src/simple_vad.c src/file_cut.h src/period_format.h src/simple_vad.h
        thirdparty/webrtc/common_audio/*/*.c thirdparty/webrtc/rtc_base/*.c*)
include_directories(thirdparty/webrtc) #thirdparty/include/webrtc
add_executable(vad-demo ${SRC_FILES})
target_link_libraries(vad-demo pthread)

file(GLOB SRC_FILES_vad src/vad_main.c src/file_cut.c src/period_format.c src/simple_vad.c src/file_cut.h src/period_format.h src/simple_vad.h
        thirdparty/webrtc/common_audio/*/*.c thirdparty/webrtc/rtc_base/*.c*)
add_executable(vad ${SRC_FILES_vad})
target_link_libraries(vad pthread)