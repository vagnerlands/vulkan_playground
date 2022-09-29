add_executable(Vulkan_Playground
        example.cpp
)

find_package(Vulkan REQUIRED FATAL_ERROR)

# Note the Conan-specific library namees, beginning with CONAN_PKG.
# Conan sets up these names when its cmake generator is used.
# This ties your project to using Conan.
target_link_libraries(
        Vulkan_Playground
        CONAN_PKG::glm CONAN_PKG::tinyobjloader CONAN_PKG::glfw)
target_link_libraries (Vulkan_Playground ${Vulkan_LIBRARIES})		
		
target_include_directories(Vulkan_Playground PRIVATE "../dependencies/includes/")
target_include_directories (Vulkan_Playground PUBLIC ${Vulkan_INCLUDE_DIRS})
		
target_compile_definitions(Vulkan_Playground PRIVATE NOMINMAX)		
		

target_compile_features(Vulkan_Playground PUBLIC cxx_std_20)
#set(CMAKE_CXX_STANDARD 20)
set_target_properties(Vulkan_Playground PROPERTIES CXX_EXTENSIONS OFF)


#set(CMAKE_BINARY_DIR ${CMAKE_BINARY_DIR}/../../Assets)
#set( CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/../../Assets )
#set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/Assets) 
#set_directory_properties(EXECUTABLE_OUTPUT_PATH ${CMAKE_CURRENT_SOURCE_DIR}/Assets) 
