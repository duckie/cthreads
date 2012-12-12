configure_file(config.h.cmake config.h)

include_directories(
    ${PROJECT_SOURCE_DIR}/src 
    ${PROJECT_BINARY_DIR}/src
	)

set(LIBRARIES)

### MANUAL_INCLUDE_DIRS is useful to force ides to find some includes (useless for compilation) ###
### To be used by editing the cache manually
include_directories(${MANUAL_INCLUDE_DIRS})

# pthread
find_package (Threads)
if(Threads_FOUND)
    set(LIBRARIES ${LIBRARIES} ${CMAKE_THREAD_LIBS_INIT})
endif(Threads_FOUND)


### Browsing source files ###
file(GLOB SRCS_FILES *.c)

### Exe ###
add_executable(${PROJECT_NAME} ${SRCS_FILES}) 

### Linking ###
target_link_libraries(${PROJECT_NAME} ${LIBRARIES})
