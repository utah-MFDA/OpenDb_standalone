include("swig_lib")

swig_lib(NAME          opendbpy
         NAMESPACE     odb
         LANGUAGE      python
         I_FILE        ../common/odb.i
         SWIG_INCLUDES ${PROJECT_SOURCE_DIR}/include
                       ${PROJECT_SOURCE_DIR}/src/swig/python
         SCRIPTS       ${CMAKE_CURRENT_BINARY_DIR}/opendbpy.py
)

target_include_directories(opendbpy
    PUBLIC
        ${PROJECT_SOURCE_DIR}/include/odb
)

target_link_libraries(opendbpy
    PUBLIC
        odb
        ${TCL_LIBRARY}
        cdl
        odb_swig_common
)


install(
    TARGETS opendbpy
    DESTINATION "."
)


#install(
#    FILES ${CMAKE_CURRENT_BINARY_DIR}/opendbpy.py
#    DESTINATION ${CMAKE_INSTALL_LIBDIR}
#)
