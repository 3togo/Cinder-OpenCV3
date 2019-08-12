cmake_minimum_required( VERSION 2.8 FATAL_ERROR )
set( CMAKE_VERBOSE_MAKEFILE ON )
set( PRJ "ocvWarp" )
#set( OpenCV_DIR "/usr/share/OpenCV" )
project( ${PRJ} )

find_package( OpenCV REQUIRED )

get_filename_component( CINDER_PATH "${CMAKE_CURRENT_SOURCE_DIR}/../../../Cinder" ABSOLUTE )
get_filename_component( APP_PATH "${CMAKE_CURRENT_SOURCE_DIR}" ABSOLUTE )
get_filename_component( OCV_PATH "${CMAKE_CURRENT_SOURCE_DIR}../../.." ABSOLUTE )
include( "${CINDER_PATH}/proj/cmake/modules/cinderMakeApp.cmake" )

ci_make_app(
    APP_NAME    ${PRJ}
    CINDER_PATH ${CINDER_PATH}
    SOURCES     ${APP_PATH}/src/${PRJ}App.cpp
    INCLUDES    ${OCV_PATH}/include
    INCLUDES    ${APP_PATH}/include
    INCLUDES 	/usr/include
	LIBRARIES 	${OpenCV_LIBRARIES}
    #RESOURCES   ${APP_PATH}/../../data/models/8lbs.obj
)
