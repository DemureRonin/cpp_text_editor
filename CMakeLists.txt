cmake_minimum_required(VERSION 3.15)
project(SentenceSplitter LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Add SDL2 subdirectory
add_subdirectory(libs/SDL)

# Add executable
add_executable(SentenceSplitter main.cpp)

# Link SDL2
target_link_libraries(SentenceSplitter SDL3::SDL3)

# Include SDL2 headers
target_include_directories(SentenceSplitter PRIVATE libs/SDL/include)

# Platform-specific settings
if (WIN32)
	# Required for SDL main() on Windows
	target_link_libraries(SentenceSplitter PRIVATE SDL2main)
	target_compile_definitions(SentenceSplitter PRIVATE SDL_MAIN_HANDLED)
endif()
