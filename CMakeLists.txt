cmake_minimum_required(VERSION 3.10)
project(Sample)

set(CMAKE_C_STANDARD 11)

# Add picoquic include and library paths
set(PICOQUIC_INCLUDE_DIR "/Users/eavricr/Documents/WebTransport/picoquic/picoquic")
set(PICOQUIC_LIBRARY "/Users/eavricr/Documents/WebTransport/picoquic/libpicoquic-core.a")
set(PICOQUIC_LOGGING "/Users/eavricr/Documents/WebTransport/picoquic/loglib")

add_executable(sample_client sample_client.c)
target_include_directories(sample_client PRIVATE ${PICOQUIC_INCLUDE_DIR} ${PICOQUIC_LOGGING})
target_link_libraries(sample_client PRIVATE ${PICOQUIC_LIBRARY})

add_executable(sample_server sample_server.c)
target_include_directories(sample_server PRIVATE ${PICOQUIC_INCLUDE_DIR} ${PICOQUIC_LOGGING})
target_link_libraries(sample_server PRIVATE ${PICOQUIC_LIBRARY})

add_executable(sample sample.c)
target_include_directories(sample PRIVATE ${PICOQUIC_INCLUDE_DIR} ${PICOQUIC_LOGGING})
target_link_libraries(sample PRIVATE ${PICOQUIC_LIBRARY})