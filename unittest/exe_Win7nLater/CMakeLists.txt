set(SOURCES
    main_exe.cpp
    symcryptunittest.rc
  )

set_source_files_properties(symcryptunittest.rc PROPERTIES LANGUAGE RC)

add_compile_options(-DTESTDRIVER_NAME=\"SymCryptDriver_win7nlater.sys\")

include_directories(${CMAKE_SOURCE_DIR}/SymCryptDependencies/inc)

add_executable(symcryptunittest_win7nlater ${SOURCES})

find_library(RSA32_LIB rsa32.lib HINTS ${CMAKE_SOURCE_DIR}/SymCryptDependencies/${CMAKE_SYSTEM_PROCESSOR})
find_library(MSBIGNUM_LIB msbignum.lib HINTS ${CMAKE_SOURCE_DIR}/SymCryptDependencies/${CMAKE_SYSTEM_PROCESSOR})

target_link_libraries(symcryptunittest_win7nlater symcryptunittest_lib symcrypt_usermodewin7 bcrypt ntdll ${RSA32_LIB} ${MSBIGNUM_LIB})