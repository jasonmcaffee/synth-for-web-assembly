cmake_minimum_required(VERSION 3.9)
project(synth_for_web_assembly)
set(CMAKE_CXX_STANDARD 11)

set(PORTAUDIO_DIR ${CMAKE_CURRENT_SOURCE_DIR}/vendor/portaudio)
set(PORTAUDIO_INCLUDE_DIR ${PORTAUDIO_DIR}/include)

add_executable(synth_for_web_assembly main.cpp)
include_directories(${PORTAUDIO_INCLUDE_DIR})
target_link_libraries(synth_for_web_assembly ${PORTAUDIO_DIR}/libportaudio_static.a)

find_library(AUDIO_UNIT AudioUnit)
find_library(CORE_SERVICES CoreServices)
find_library(CORE_FOUNDATION CoreFoundation)
find_library(AUDIO_TOOLBOX AudioToolbox)
find_library(CORE_AUDIO CoreAudio)
target_link_libraries(synth_for_web_assembly ${AUDIO_UNIT})
target_link_libraries(synth_for_web_assembly ${CORE_SERVICES})
target_link_libraries(synth_for_web_assembly ${CORE_FOUNDATION})
target_link_libraries(synth_for_web_assembly ${AUDIO_TOOLBOX})
target_link_libraries(synth_for_web_assembly ${CORE_AUDIO})