cmake_minimum_required(VERSION 3.4.1)

# OpenCV stuff
include_directories( libs/3rdparty/OpenCV3.4.1Java/sdk/native/jni/include )
add_library( lib_opencv SHARED IMPORTED )
set_target_properties(lib_opencv PROPERTIES IMPORTED_LOCATION ${CMAKE_CURRENT_SOURCE_DIR}/src/main/jniLibs/${ANDROID_ABI}/libopencv_java3.so)

find_library( log-lib log )

add_library( native-lib  SHARED  src/main/cpp/native-lib.cpp )
target_link_libraries( native-lib  lib_opencv   ${log-lib} )
