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

set(CollaXML_BASE_H
	include/win32config.h
	include/wsockcompat.h
)

set(ColladaXML_LIB_H
	include/libxml/c14n.h
	include/libxml/catalog.h
	include/libxml/chvalid.h
	include/libxml/debugXML.h
	include/libxml/dict.h
	include/libxml/DOCBparser.h
	include/libxml/encoding.h
	include/libxml/entities.h
	include/libxml/globals.h
	include/libxml/hash.h
	include/libxml/HTMLparser.h
	include/libxml/HTMLtree.h
	include/libxml/list.h
	include/libxml/nanoftp.h
	include/libxml/nanohttp.h
	include/libxml/parser.h
	include/libxml/parserInternals.h
	include/libxml/pattern.h
	include/libxml/relaxng.h
	include/libxml/SAX.h
	include/libxml/SAX2.h
	include/libxml/schemasInternals.h
	include/libxml/threads.h
	include/libxml/tree.h
	include/libxml/uri.h
	include/libxml/valid.h
	include/libxml/xinclude.h
	include/libxml/xlink.h
	include/libxml/xmlautomata.h
	include/libxml/xmlerror.h
	include/libxml/xmlexports.h
	include/libxml/xmlIO.h
	include/libxml/xmlmemory.h
	include/libxml/xmlmodule.h
	include/libxml/xmlreader.h
	include/libxml/xmlregexp.h
	include/libxml/xmlsave.h
	include/libxml/xmlschemas.h
	include/libxml/xmlschemastypes.h
	include/libxml/xmlstring.h
	include/libxml/xmlunicode.h
	include/libxml/xmlversion.h
	include/libxml/xmlwriter.h
	include/libxml/xpath.h
	include/libxml/xpathInternals.h
	include/libxml/xpointer.h
)
set(ColladaXML_H ${ColladaXML_BASE_H} ${ColladaXML_LIB_H})

include_directories(${CMAKE_CURRENT_SOURCE_DIR}
                    ${CMAKE_CURRENT_SOURCE_DIR}/include
                    ${CMAKE_CURRENT_BINARY_DIR})

add_library(ColladaXML ${ColladaXML_SRC} ${ColladaXML_H})

target_include_directories(ColladaXML PUBLIC
	$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
	$<INSTALL_INTERFACE:include>
)

install(TARGETS ColladaXML DESTINATION lib)
install(FILES ${ColladaXML_BASE_H} DESTINATION include/LibXML)
install(FILES ${ColladaXML_LIB_H} DESTINATION include/LibXML/libxml)
