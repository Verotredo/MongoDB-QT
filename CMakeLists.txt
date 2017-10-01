cmake_minimum_required(VERSION 2.8.12)
if (APPLE)
   cmake_policy (SET CMP0042 OLD)
endif ()

set (CMAKE_CXX_STANDARD 11)
project(test)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOMOC ON)

find_package(Qt5Core)

find_package(libmongocxx)
find_package(libbsoncxx)

message("LIBMONGOCXX_INCLUDE_DIRS = ${LIBMONGOCXX_INCLUDE_DIRS}")
message("LIBMONGOCXX_LIBRARIES = ${LIBMONGOCXX_LIBRARIES}")

message("LIBBSONCXX_INCLUDE_DIRS = ${LIBBSONCXX_INCLUDE_DIRS}")
message("LIBBSONCXX_LIBRARIES = ${LIBBSONCXX_LIBRARIES}")


add_executable (${PROJECT_NAME} "main.cpp")
message ("--   mongoc found version \"${LIBMONGOCXX_VERSION}\"")
message ("--   mongoc include path \"${LIBMONGOCXX_INCLUDE_DIRS}\"")
message ("--   mongoc libraries \"${LIBMONGOCXX_LIBRARIES}\"")
target_link_libraries(${PROJECT_NAME} Qt5::Core ${MONGOC_LIBRARIES} ${LIBBSONCXX_LIBRARIES} ${LIBMONGOCXX_LIBRARIES})
target_include_directories (${PROJECT_NAME} PRIVATE ${LIBMONGOCXX_INCLUDE_DIRS})
target_include_directories (${PROJECT_NAME} PRIVATE ${LIBBSONCXX_INCLUDE_DIRS})

#target_link_libraries (text2 PRIVATE ${LIBBSONCXX_LIBRARIES} ${LIBMONGOCXX_LIBRARIES})
#target_compile_definitions (test PRIVATE "${MONGOC_DEFINITIONS}")
