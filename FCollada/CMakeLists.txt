cmake_minimum_required(VERSION 3.0)

project(Fcollada)

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

add_library(Fcollada ${FCollada_SRC} ${FCollada_H} ${FCDocument_SRC} ${FCDocument_H} ${FMath_SRC} ${FMath_H} ${FUtils_SRC} ${FUtils_H})
target_link_libraries(Fcollada ColladaXML)

set(FCOLLADA_INSTALL_PATH ${CMAKE_INSTALL_PREFIX}/Fcollada)

install(TARGETS Fcollada DESTINATION lib)
install(FILES ${FCollada_H} DESTINATION include)
install(DIRECTORY FCDocument DESTINATION include FILES_MATCHING PATTERN "*.h")
install(DIRECTORY FMath DESTINATION include FILES_MATCHING PATTERN "*.h")
install(DIRECTORY FUtils DESTINATION include FILES_MATCHING PATTERN "*.h")
