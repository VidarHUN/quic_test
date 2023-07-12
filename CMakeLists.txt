cmake_minimum_required(VERSION 3.10)
project(Sample)

set(CMAKE_C_STANDARD 11)

# Enable fetching content
include(FetchContent)

# Fetch the picoquic library, which brings in picotls with it
FetchContent_Declare(
    picoquic
    GIT_REPOSITORY  https://github.com/private-octopus/picoquic.git
    GIT_TAG         master
)

# Set the option to force picoquic to fetch the picotls
set(PICOQUIC_FETCH_PTLS ON)

# Make dependencies available
FetchContent_MakeAvailable(picoquic)

# Add picoquic include and library paths
# set(PICOQUIC_INCLUDE_DIR "../picoquic/picoquic")
# set(PICOQUIC_LIBRARY "../picoquic/libpicoquic-core.a")
# set(PICOQUIC_LOGGING "../picoquic/loglib")

add_executable(sample_client sample_client.c)
# target_include_directories(sample_client PRIVATE ${PICOQUIC_INCLUDE_DIR} ${PICOQUIC_LOGGING})
target_link_libraries(sample_client PRIVATE picoquic-core picoquic-log)

add_executable(sample_server sample_server.c)
# target_include_directories(sample_server PRIVATE ${PICOQUIC_INCLUDE_DIR} ${PICOQUIC_LOGGING})
target_link_libraries(sample_server PRIVATE picoquic-core picoquic-log)

add_executable(sample sample.c)
# target_include_directories(sample PRIVATE ${PICOQUIC_INCLUDE_DIR} ${PICOQUIC_LOGGING})
target_link_libraries(sample PRIVATE picoquic-core picoquic-log)