cmake_minimum_required(VERSION 3.0)

project(FCollada)

set(FCollada_SRC 
   DLLEntry.cpp
   FCollada.cpp
   FColladaPlugin.cpp
   StdAfx.cpp
)

set(FCollada_H
	FCollada.h
	FColladaPlugin.h
	StdAfx.h
)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}
                    ${CMAKE_CURRENT_BINARY_DIR}
)

add_subdirectory(FCDocument)
add_subdirectory(FMath)
add_subdirectory(FUtils)
add_subdirectory(LibXML)


add_library(FCollada ${FCollada_SRC} ${FCollada_H})
target_link_libraries(FCollada ColladaXML)

target_include_directories(FCollada PUBLIC
	$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
	$<INSTALL_INTERFACE:include>
)

set(FCOLLADA_INSTALL_PATH ${CMAKE_INSTALL_PREFIX}/Fcollada)

install(TARGETS FCollada DESTINATION lib)
install(FILES ${FCollada_H} DESTINATION include)
