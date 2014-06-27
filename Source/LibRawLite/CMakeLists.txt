cmake_minimum_required(VERSION 2.6.1)

INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR})

ADD_DEFINITIONS(-D_CRT_SECURE_NO_WARNINGS -DLIBRAW_NODLL -DLIBRAW_LIBRARY_BUILD -DNO_LCMS)

set( LIBRAWLITE_SOURCES 
    internal/dcraw_common.cpp 
    internal/dcraw_fileio.cpp 
    internal/demosaic_packs.cpp
    internal/defines.h 
    internal/libraw_internal_funcs.h 
    internal/var_defines.h 
    libraw/libraw.h 
    libraw/libraw_alloc.h 
    libraw/libraw_const.h 
    libraw/libraw_datastream.h 
    libraw/libraw_internal.h 
    libraw/libraw_types.h 
    libraw/libraw_version.h 
    src/libraw_c_api.cpp 
    src/libraw_cxx.cpp 
    src/libraw_datastream.cpp
)

#ADD_DEFINITIONS(-DPNG_BUILD_DLL)

add_library ( LibRawLite_s STATIC ${LIBRAWLITE_SOURCES} )

  IF(FREEIMAGE_BUILD_STATIC)
    INSTALL(TARGETS 
    LibRawLite_s
    RUNTIME DESTINATION "${CMAKE_INSTALL_PREFIX}/bin" 
    ARCHIVE DESTINATION "${CMAKE_INSTALL_PREFIX}/lib" 
    LIBRARY DESTINATION "${CMAKE_INSTALL_PREFIX}/lib"
    )
  ENDIF()  
