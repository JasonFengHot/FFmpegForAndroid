# For more information about using CMake with Android Studio, read the
# documentation: https://d.android.com/studio/projects/add-native-code.html

# Sets the minimum version of CMake required to build the native library.

cmake_minimum_required(VERSION 3.4.1)

# Creates and names a library, sets it as either STATIC
# or SHARED, and provides the relative paths to its source code.
# You can define multiple libraries, and CMake builds them for you.
# Gradle automatically packages shared libraries with your APK.

include_directories(src/main/cpp/include/ )


add_library( # Sets the name of the library.
             native-lib

             # Sets the library as a shared library.
             SHARED

             # Provides a relative path to your source file(s).
             src/main/cpp/native-lib.c )

# Searches for a specified prebuilt library and stores the path as a
# variable. Because CMake includes system libraries in the search path by
# default, you only need to specify the name of the public NDK library
# you want to add. CMake verifies that the library exists before
# completing its build.

find_library( # Sets the name of the path variable.
              log-lib

              # Specifies the name of the NDK library that
              # you want CMake to locate.
              log )

# Specifies libraries CMake should link to your target library. You
# can link multiple libraries, such as libraries you define in this
# build script, prebuilt third-party libraries, or system libraries.

target_link_libraries( # Specifies the target library.
                       native-lib

                       /Users/huibin/AndroidProject/FFmpegSample/app/src/main/jniLibs/armeabi-v7a/libijkffmpeg.so
                       # FFmpeg
                       #/Users/huibin/AndroidProject/FFmpegSample/app/src/main/jniLibs/armeabi-v7a/libismartvavcodec2.6.4.so
                       #/Users/huibin/AndroidProject/FFmpegSample/app/src/main/jniLibs/armeabi-v7a/libismartvavfilter2.6.4.so
                       #/Users/huibin/AndroidProject/FFmpegSample/app/src/main/jniLibs/armeabi-v7a/libismartvavformat2.6.4.so
                       #/Users/huibin/AndroidProject/FFmpegSample/app/src/main/jniLibs/armeabi-v7a/libismartvavutil2.6.4.so
                       #/Users/huibin/AndroidProject/FFmpegSample/app/src/main/jniLibs/armeabi-v7a/libismartvswresample2.6.4.so
                       #/Users/huibin/AndroidProject/FFmpegSample/app/src/main/jniLibs/armeabi-v7a/libismartvswscale2.6.4.so
                       # Links the target library to the log library
                       # included in the NDK.
                       ${log-lib} )