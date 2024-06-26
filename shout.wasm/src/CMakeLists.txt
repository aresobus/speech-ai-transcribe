# from whisper.cpp/examples/whisper.wasm/CMakeLists.txt
set(TARGET loud.wasm)


add_executable(${TARGET}
    loud.wasm.cpp
    )

# include(DefaultTargetOptions)
include(${CMAKE_CURRENT_SOURCE_DIR}/../whisper.cpp/cmake/DefaultTargetOptions.cmake)

target_link_libraries(${TARGET} PRIVATE
    whisper
    )

target_compile_features(${TARGET} PRIVATE cxx_std_17)

unset(EXTRA_FLAGS)

if (WHISPER_WASM_SINGLE_FILE)
    set(EXTRA_FLAGS "-s SINGLE_FILE=1")
    message(STATUS "Embedding transcribe.wasm inside transcribe.wasm.js")
endif()

set_target_properties(${TARGET} PROPERTIES LINK_FLAGS " \
    --bind \
    -s USE_PTHREADS=1 \
    -s PTHREAD_POOL_SIZE_STRICT=0 \
    -s INITIAL_MEMORY=2000MB \
    -s TOTAL_MEMORY=2000MB \
    -s FORCE_FILESYSTEM=1 \
    -s EXPORTED_RUNTIME_METHODS=\"['out', 'err', 'ccall', 'cwrap']\" \
    -s EXPORTED_FUNCTIONS=\"['_malloc', '_free']\" \
    -s EXPORT_ES6=1 \
    -s MODULARIZE=1 \
    -s EXPORT_NAME=\"createModule\" \
    ${EXTRA_FLAGS} \
    ")
