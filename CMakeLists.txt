
INCLUDE_DIRECTORIES( ${CMAKE_CURRENT_SOURCE_DIR}/inc )

if( __LINUX__ )
	ADD_DEFINITIONS( -fPIC )
endif( __LINUX__ )

set( SRC src )
set( TLS tls )
set( GSM_SOURCES 	${SRC}/add.c
		${SRC}/code.c
		${SRC}/debug.c
		${SRC}/decode.c
		${SRC}/long_term.c
		${SRC}/lpc.c
		${SRC}/preprocess.c
		${SRC}/rpe.c
		${SRC}/gsm_destroy.c
		${SRC}/gsm_decode.c
		${SRC}/gsm_encode.c
		${SRC}/gsm_explode.c
		${SRC}/gsm_implode.c
		${SRC}/gsm_create.c
		${SRC}/gsm_print.c
		${SRC}/gsm_option.c
		${SRC}/short_term.c
		${SRC}/table.c )

set( TOAST_SOURCES  ${SRC}/toast.c
		${SRC}/toast_lin.c
		${SRC}/toast_ulaw.c
		${SRC}/toast_alaw.c
		${SRC}/toast_audio.c )


set( TST tst )
set( TEST_SOURCES   ${TST}/cod2lin.c
		${TST}/cod2txt.c
		${TST}/gsm2cod.c
		${TST}/lin2cod.c
		${TST}/lin2txt.c )

#		${ADDTST}/add_test.c

add_library( gsm-1.0-pl13 ${GSM_SOURCES} )

#add_executable( gsm-toast ${TOAST_SOURCES} )
#target_link_libraries( gsm-toast gsm-1.0-pl13 )

if( BUILD_GSM_MISC )

	add_executable( bitter ${TLS}bitter.c ${TLS}bitter.dta )
	add_executable( sweet ${TLS}sweet.c )
	add_executable( sour ${TLS}sour.c ${TLS}sour1.dta ${TLS}sour2.dta )
	add_executable( ginger ${TLS}ginger.c )
	add_executable( taste ${TLS}taste.c )

endif( BUILD_GSM_MISC )
