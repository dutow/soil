cmake_minimum_required(VERSION 2.6)

include_directories(inc)

option(STATIC_RUNTIME "Use static runtime" ON)

IF (STATIC_RUNTIME)
	IF (MSVC)
		SET( CMAKE_CXX_FLAGS "/W3 /WX /EHsc -D_SCL_SECURE_NO_WARNINGS" )
		SET( CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} /MTd" )
		SET( CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} /MT" )
		SET( CMAKE_CXX_FLAGS_RELWITHDEBINFO "${CMAKE_CXX_FLAGS_RELWITHDEBINFO} /MT" )
	ENDIF ()
ELSE ()
	# TODO (default)
ENDIF ()

ADD_LIBRARY( soil STATIC
  src/image_helper.c
  src/stb_image_aug.c
  src/image_DXT.c
  src/SOIL.c
  )
