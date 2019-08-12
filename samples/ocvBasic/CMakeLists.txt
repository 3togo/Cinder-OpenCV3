cmake_minimum_required( VERSION 2.8 FATAL_ERROR )
set( CMAKE_VERBOSE_MAKEFILE ON )
set( PRJ "ocvBasic" )
set( OpenCV_DIR "/usr/share/OpenCV" )
project( ${PRJ} )
#include(FindPkgConfig)
#pkg_check_modules(OpenCV REQUIRED "opencv")

find_package( OpenCV REQUIRED )

message(STATUS "OpenCV library status:")
message(STATUS "    version: ${OpenCV_VERSION}")	#
message(STATUS "    libraries: ${OpenCV_LIBS}")		#
message(STATUS "    include path: ${OpenCV_INCLUDE_DIRS}")	#
message(STATUS "    lib path: ${OpenCV_LIBRARY_DIRS}")
message(STATUS "    libraies path: ${OpenCV_LIBRARIES}")
message(STATUS "    cflags path: ${OpenCV_CFLAGS}")
message(STATUS "    ldflags path: ${OpenCV_LDFLAGS}")



get_filename_component( CINDER_PATH "${CMAKE_CURRENT_SOURCE_DIR}/../../../Cinder" ABSOLUTE )
get_filename_component( APP_PATH "${CMAKE_CURRENT_SOURCE_DIR}" ABSOLUTE )
get_filename_component( OCV_PATH "${CMAKE_CURRENT_SOURCE_DIR}../../.." ABSOLUTE )
include( "${CINDER_PATH}/proj/cmake/modules/cinderMakeApp.cmake" )
#include_directories( ${OpenCV_INCLUDE_DIRS} )
#string(REPLACE ";" " " ${OpenCV_LDFLAGS} ${OpenCV_LDFLAGS} )
#add_link_options( ${OpenCV_LDFLAGS} )
#set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS}" ${OpenCV_LDFLAGS})
#target_link_libraries(${PRJ} ${OpenCV_LIBS})
#set_property(TARGET ${PRJ} APPEND_STRING PROPERTY LINK_FLAGS " ${OpenCV_LDFLAGS} ")
ci_make_app(
    APP_NAME    ${PRJ}
    CINDER_PATH ${CINDER_PATH}
    SOURCES     ${APP_PATH}/src/ocvBasicApp.cpp
    INCLUDES    ${OCV_PATH}/include
    INCLUDES    ${APP_PATH}/include
    INCLUDES 	/usr/include
	LIBRARIES 	${OpenCV_LIBRARIES}
     
    #RESOURCES   ${APP_PATH}/../../data/models/8lbs.obj
)
message(STATUS "    CINDER_LIBS_DEPENDS: ${CINDER_LIBS_DEPENDS}")
message(STATUS "    ARG_LIBRARIES : ${ARG_LIBRARIES} ")
