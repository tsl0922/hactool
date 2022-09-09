cmake_minimum_required (VERSION 3.8)

project ("hactool")

set(ENABLE_PROGRAMS OFF)
set(ENABLE_TESTING OFF)
add_subdirectory(mbedtls)

set(src
	aes.c
	cJSON.c
	extkeys.c
	hfs0.c
	lz4.c
	nax0.c
	nca0_romfs.c
	nso.c
	pfs0.c
	romfs.c
	save.c
	utils.c
	bktr.c
	ConvertUTF.c
	filepath.c
	kip.c
	main.c
	nca.c
	npdm.c
	packages.c
	pki.c
	rsa.c
	sha.c
	xci.c
)

set(include_dir mbedtls/include)
if(WIN32)
	list(APPEND src getopt/getopt.c)
	list(APPEND include_dir getopt)
endif()

add_executable(hactool ${src})
target_include_directories(hactool PUBLIC ${include_dir})
target_link_libraries(hactool mbedtls)
