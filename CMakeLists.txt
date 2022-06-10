#
# ControlFreak
#
cmake_minimum_required (VERSION 3.18)

set(This "ControlFreak")
project (${This} VERSION 0.1.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

option(BUILD_SHARED_LIBS "Build using shared libraries" OFF)


if(MSVC)
    set(config_lib "libconfig++")
else()
    set(config_lib "config++")
endif()

add_subdirectory(extern)

add_subdirectory(src)




########## COntrolFreak

add_executable(${This})

target_sources(${This}
	PRIVATE
		"src/main.cpp"
	)

target_link_libraries(${This}
    PRIVATE
        lib_include
		${config_lib}
		osc_objlib
		config_objlib
		platform_objlib
	)
# TODO: Add tests and install targets if needed.
