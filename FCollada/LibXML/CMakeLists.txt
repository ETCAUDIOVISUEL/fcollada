set(ColladaXML_SRC
	acconfig.h
	c14n.c
	catalog.c
	chvalid.c
	config.h
	config-ps3.h
	debugXML.c
	dict.c
	DOCBparser.c
	elfgcchack.h
	encoding.c
	entities.c
	error.c
	globals.c
	hash.c
	HTMLparser.c
	HTMLtree.c
	legacy.c
	libxml.h
	list.c
	nanoftp.c
	nanohttp.c
	parser.c
	parserInternals.c
	pattern.c
	relaxng.c
	SAX.c
	SAX2.c
	threads.c
	tree.c
	uri.c
	valid.c
	xinclude.c
	xlink.c
	xmlcatalog.c
	xmlIO.c
	xmlmemory.c
	xmlmodule.c
	xmlreader.c
	xmlregexp.c
	xmlsave.c
	xmlstring.c
	xmlunicode.c
	xmlwriter.c
)

add_subdirectory(include)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}
                    ${CMAKE_CURRENT_BINARY_DIR}
)

add_library(ColladaXML ${ColladaXML_SRC} ${ColladaXML_H})

target_include_directories(ColladaXML PUBLIC
	$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
	$<INSTALL_INTERFACE:include>
)

install(TARGETS ColladaXML DESTINATION lib)