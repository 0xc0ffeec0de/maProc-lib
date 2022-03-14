cmake_minimum_required(VERSION 3.5)

project(maProc VERSION 0.1)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

set(OPTIMIZATIONS ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(DEBUGGER OFF)
set(NO_FLAG OFF)

if(OPTIMIZATIONS)
    set(CMAKE_CXX_FLAGS "-mavx -fno-stack-protector -march=native -O2 -Os -fdelete-null-pointer-checks -fdelete-dead-exceptions")
        if(DEBUGGER)
            set(CMAKE_CXX_FLAGS "-g -gdwarf -gdwarf-version")
        endif()
    if(NO_FLAG)
        set(CMAKE_CXX_FLAGS " ")
    endif()
endif()

add_library(maProclib SHARED

        maProclib/ps.hpp
        maProclib/ps.cpp

        maProclib/filedescriptor.hpp
        maProclib/filedescriptor.cpp
        
        maProclib/pmap.hpp
        maProclib/pmap.cpp

        maProclib/proclib.hpp
        maProclib/proclib.cpp

        maProclib/proclib.cpp
        maProclib/proclib.hpp
)
