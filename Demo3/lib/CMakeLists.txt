cmake_minimum_required(VERSION 3.6)

project(testlib VERSION 1.2.3)

add_subdirectory(hello)
add_subdirectory(math)

# add_dependencies(hello LINK_HEADERS)
# add_dependencies(math LINK_HEADERS)

set(STATIC_LIB_NAME ${PROJECT_NAME}-static)
set(SHARED_LIB_NAME ${PROJECT_NAME}-shared)

add_library(
	${STATIC_LIB_NAME} STATIC
	$<TARGET_OBJECTS:hello>
	$<TARGET_OBJECTS:math>
)

add_library(
	${SHARED_LIB_NAME} SHARED
	$<TARGET_OBJECTS:hello>
	$<TARGET_OBJECTS:math>
)

set_target_properties(${STATIC_LIB_NAME} PROPERTIES OUTPUT_NAME ${PROJECT_NAME})
set_target_properties(${SHARED_LIB_NAME} PROPERTIES OUTPUT_NAME ${PROJECT_NAME} VERSION ${PROJECT_VERSION} SOVERSION ${PROJECT_VERSION_MAJOR})

#install(
#    TARGETS ${STATIC_LIB_NAME}
#    ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
#    COMPONENT devel
#)

#install(
#    TARGETS ${SHARED_LIB_NAME}
#    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
#    COMPONENT devel
#)

