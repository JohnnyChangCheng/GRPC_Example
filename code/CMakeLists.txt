cmake_minimum_required (VERSION 2.6)
project (server)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ./bin)
set(CMAKE_CXX_FLAGS "-pedantic-errors -DTIMER")
set(CMAKE_C_FLAGS "-g")
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_BUILD_TYPE Debug)
include_directories(${CMAKE_SOURCE_DIR}/../include)
include_directories(${CMAKE_SOURCE_DIR}/inc)
link_directories(${CMAKE_SOURCE_DIR}/../lib)
set(SERVER_SOUR  ${CMAKE_SOURCE_DIR}/src/greeter_server.cc  
		${CMAKE_SOURCE_DIR}/src/helloworld.grpc.pb.cc  	
		${CMAKE_SOURCE_DIR}/src/helloworld.pb.cc)
set(CLIENT_SOUR  ${CMAKE_SOURCE_DIR}/src/greeter_client.cc  
		${CMAKE_SOURCE_DIR}/src/helloworld.grpc.pb.cc  	
		${CMAKE_SOURCE_DIR}/src/helloworld.pb.cc)
add_executable(server ${SERVER_SOUR})
add_executable(client ${CLIENT_SOUR})
set(grpc_lib  pthread protobuf ++ grpc)
target_link_libraries(server ${grpc_lib} pthread)
target_link_libraries(client ${grpc_lib} pthread)