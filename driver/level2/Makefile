TOPDIR	= ../..
include ../../Makefile.system

SBLASOBJS = \
	sgbmv_n.$(SUFFIX) sgbmv_t.$(SUFFIX) \
	ssbmv_U.$(SUFFIX) ssbmv_L.$(SUFFIX) sspmv_U.$(SUFFIX) sspmv_L.$(SUFFIX) \
	sspr_U.$(SUFFIX) sspr_L.$(SUFFIX) sspr2_U.$(SUFFIX) sspr2_L.$(SUFFIX) \
	ssyr_U.$(SUFFIX) ssyr_L.$(SUFFIX) ssyr2_U.$(SUFFIX) ssyr2_L.$(SUFFIX) \
	stbmv_NUU.$(SUFFIX) stbmv_NUN.$(SUFFIX) stbmv_NLU.$(SUFFIX) stbmv_NLN.$(SUFFIX) \
	stbmv_TUU.$(SUFFIX) stbmv_TUN.$(SUFFIX) stbmv_TLU.$(SUFFIX) stbmv_TLN.$(SUFFIX) \
	stbsv_NUU.$(SUFFIX) stbsv_NUN.$(SUFFIX) stbsv_NLU.$(SUFFIX) stbsv_NLN.$(SUFFIX) \
	stbsv_TUU.$(SUFFIX) stbsv_TUN.$(SUFFIX) stbsv_TLU.$(SUFFIX) stbsv_TLN.$(SUFFIX) \
	stpmv_NUU.$(SUFFIX) stpmv_NUN.$(SUFFIX) stpmv_NLU.$(SUFFIX) stpmv_NLN.$(SUFFIX) \
	stpmv_TUU.$(SUFFIX) stpmv_TUN.$(SUFFIX) stpmv_TLU.$(SUFFIX) stpmv_TLN.$(SUFFIX) \
	stpsv_NUU.$(SUFFIX) stpsv_NUN.$(SUFFIX) stpsv_NLU.$(SUFFIX) stpsv_NLN.$(SUFFIX) \
	stpsv_TUU.$(SUFFIX) stpsv_TUN.$(SUFFIX) stpsv_TLU.$(SUFFIX) stpsv_TLN.$(SUFFIX) \
	strmv_NUU.$(SUFFIX) strmv_NUN.$(SUFFIX) strmv_NLU.$(SUFFIX) strmv_NLN.$(SUFFIX) \
	strmv_TUU.$(SUFFIX) strmv_TUN.$(SUFFIX) strmv_TLU.$(SUFFIX) strmv_TLN.$(SUFFIX) \
	strsv_NUU.$(SUFFIX) strsv_NUN.$(SUFFIX) strsv_NLU.$(SUFFIX) strsv_NLN.$(SUFFIX) \
	strsv_TUU.$(SUFFIX) strsv_TUN.$(SUFFIX) strsv_TLU.$(SUFFIX) strsv_TLN.$(SUFFIX)


ifdef SMP
SBLASOBJS   += \
	sgemv_thread_n.$(SUFFIX)	sgemv_thread_t.$(SUFFIX) \
	sger_thread.$(SUFFIX) \
	ssymv_thread_U.$(SUFFIX)	ssymv_thread_L.$(SUFFIX) \
	ssyr_thread_U.$(SUFFIX)		ssyr_thread_L.$(SUFFIX)  \
	ssyr2_thread_U.$(SUFFIX)	ssyr2_thread_L.$(SUFFIX) \
	sspr_thread_U.$(SUFFIX)		sspr_thread_L.$(SUFFIX)  \
	sspr2_thread_U.$(SUFFIX)	sspr2_thread_L.$(SUFFIX) \
	strmv_thread_NUU.$(SUFFIX)	strmv_thread_NUN.$(SUFFIX) \
	strmv_thread_NLU.$(SUFFIX)	strmv_thread_NLN.$(SUFFIX) \
	strmv_thread_TUU.$(SUFFIX)	strmv_thread_TUN.$(SUFFIX) \
	strmv_thread_TLU.$(SUFFIX)	strmv_thread_TLN.$(SUFFIX) \
	sspmv_thread_U.$(SUFFIX)	sspmv_thread_L.$(SUFFIX) \
	stpmv_thread_NUU.$(SUFFIX)	stpmv_thread_NUN.$(SUFFIX) \
	stpmv_thread_NLU.$(SUFFIX)	stpmv_thread_NLN.$(SUFFIX) \
	stpmv_thread_TUU.$(SUFFIX)	stpmv_thread_TUN.$(SUFFIX) \
	stpmv_thread_TLU.$(SUFFIX)	stpmv_thread_TLN.$(SUFFIX) \
	sgbmv_thread_n.$(SUFFIX)	sgbmv_thread_t.$(SUFFIX) \
	ssbmv_thread_U.$(SUFFIX)	ssbmv_thread_L.$(SUFFIX) \
	stbmv_thread_NUU.$(SUFFIX)	stbmv_thread_NUN.$(SUFFIX) \
	stbmv_thread_NLU.$(SUFFIX)	stbmv_thread_NLN.$(SUFFIX) \
	stbmv_thread_TUU.$(SUFFIX)	stbmv_thread_TUN.$(SUFFIX) \
	stbmv_thread_TLU.$(SUFFIX)	stbmv_thread_TLN.$(SUFFIX) \

endif

all ::

sgbmv_n.$(SUFFIX)  sgbmv_n.$(PSUFFIX)  : gbmv_k.c
	$(CC) -c -UCOMPLEX -UDOUBLE -UTRANS $(CFLAGS) -o $(@F) $<

sgbmv_t.$(SUFFIX)  sgbmv_t.$(PSUFFIX)  : gbmv_k.c
	$(CC) -c -UCOMPLEX -UDOUBLE -DTRANS $(CFLAGS) -o $(@F) $<

sgbmv_thread_n.$(SUFFIX)  sgbmv_thread_n.$(PSUFFIX)  : gbmv_thread.c
	$(CC) -c -UCOMPLEX -UDOUBLE -UTRANSA $(CFLAGS) -o $(@F) $<

sgbmv_thread_t.$(SUFFIX)  sgbmv_thread_t.$(PSUFFIX)  : gbmv_thread.c
	$(CC) -c -UCOMPLEX -UDOUBLE -DTRANSA $(CFLAGS) -o $(@F) $<

sgemv_thread_n.$(SUFFIX) sgemv_thread_n.$(PSUFFIX) : gemv_thread.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE  -UTRANSA -UCONJ -UXCONJ $< -o $(@F)

sgemv_thread_t.$(SUFFIX) sgemv_thread_t.$(PSUFFIX) : gemv_thread.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE  -DTRANSA -UCONJ -UXCONJ $< -o $(@F)


sger_thread.$(SUFFIX) sger_thread.$(PSUFFIX) : ger_thread.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE  -UCONJ -UXCONJ $< -o $(@F)


ssymv_thread_U.$(SUFFIX)  ssymv_thread_U.$(PSUFFIX)  : symv_thread.c ../../param.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -ULOWER $< -o $(@F)

ssymv_thread_L.$(SUFFIX)  ssymv_thread_L.$(PSUFFIX)  : symv_thread.c ../../param.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DLOWER $< -o $(@F)

ssyr_thread_U.$(SUFFIX)  ssyr_thread_U.$(PSUFFIX)  : syr_thread.c ../../param.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -ULOWER $< -o $(@F)

ssyr_thread_L.$(SUFFIX)  ssyr_thread_L.$(PSUFFIX)  : syr_thread.c ../../param.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DLOWER $< -o $(@F)

ssyr2_thread_U.$(SUFFIX)  ssyr2_thread_U.$(PSUFFIX)  : syr2_thread.c ../../param.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -ULOWER $< -o $(@F)

ssyr2_thread_L.$(SUFFIX)  ssyr2_thread_L.$(PSUFFIX)  : syr2_thread.c ../../param.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DLOWER $< -o $(@F)


ssbmv_U.$(SUFFIX)  ssbmv_U.$(PSUFFIX)  : sbmv_k.c ../../param.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -ULOWER $< -o $(@F)

ssbmv_L.$(SUFFIX)  ssbmv_L.$(PSUFFIX)  : sbmv_k.c ../../param.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DLOWER $< -o $(@F)


ssbmv_thread_U.$(SUFFIX)  ssbmv_thread_U.$(PSUFFIX)  : sbmv_thread.c ../../param.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -ULOWER $< -o $(@F)

ssbmv_thread_L.$(SUFFIX)  ssbmv_thread_L.$(PSUFFIX)  : sbmv_thread.c ../../param.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DLOWER $< -o $(@F)

sspmv_U.$(SUFFIX)  sspmv_U.$(PSUFFIX)  : spmv_k.c ../../param.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -ULOWER $< -o $(@F)

sspmv_L.$(SUFFIX)  sspmv_L.$(PSUFFIX)  : spmv_k.c ../../param.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DLOWER $< -o $(@F)


sspmv_thread_U.$(SUFFIX)  sspmv_thread_U.$(PSUFFIX)  : spmv_thread.c ../../param.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -ULOWER $< -o $(@F)

sspmv_thread_L.$(SUFFIX)  sspmv_thread_L.$(PSUFFIX)  : spmv_thread.c ../../param.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DLOWER $< -o $(@F)

sspr_U.$(SUFFIX)  sspr_U.$(PSUFFIX)  : spr_k.c ../../param.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -ULOWER $< -o $(@F)

sspr_L.$(SUFFIX)  sspr_L.$(PSUFFIX)  : spr_k.c ../../param.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DLOWER $< -o $(@F)


sspr_thread_U.$(SUFFIX)  sspr_thread_U.$(PSUFFIX)  : spr_thread.c ../../param.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -ULOWER $< -o $(@F)

sspr_thread_L.$(SUFFIX)  sspr_thread_L.$(PSUFFIX)  : spr_thread.c ../../param.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DLOWER $< -o $(@F)

sspr2_U.$(SUFFIX)  sspr2_U.$(PSUFFIX)  : spr2_k.c ../../param.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -ULOWER $< -o $(@F)

sspr2_L.$(SUFFIX)  sspr2_L.$(PSUFFIX)  : spr2_k.c ../../param.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DLOWER $< -o $(@F)


sspr2_thread_U.$(SUFFIX)  sspr2_thread_U.$(PSUFFIX)  : spr2_thread.c ../../param.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -ULOWER $< -o $(@F)

sspr2_thread_L.$(SUFFIX)  sspr2_thread_L.$(PSUFFIX)  : spr2_thread.c ../../param.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DLOWER $< -o $(@F)

ssyr_U.$(SUFFIX)  ssyr_U.$(PSUFFIX)  : syr_k.c ../../param.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -ULOWER $< -o $(@F)

ssyr_L.$(SUFFIX)  ssyr_L.$(PSUFFIX)  : syr_k.c ../../param.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DLOWER $< -o $(@F)


ssyr2_U.$(SUFFIX)  ssyr2_U.$(PSUFFIX)  : syr2_k.c ../../param.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -ULOWER $< -o $(@F)

ssyr2_L.$(SUFFIX)  ssyr2_L.$(PSUFFIX)  : syr2_k.c ../../param.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DLOWER $< -o $(@F)


stbmv_NUU.$(SUFFIX)  stbmv_NUU.$(PSUFFIX)  : tbmv_U.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -UTRANSA -DUNIT $< -o $(@F)

stbmv_NUN.$(SUFFIX)  stbmv_NUN.$(PSUFFIX)  : tbmv_U.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -UTRANSA -UUNIT $< -o $(@F)

stbmv_TLU.$(SUFFIX)  stbmv_TLU.$(PSUFFIX)  : tbmv_U.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DTRANSA -DUNIT $< -o $(@F)

stbmv_TLN.$(SUFFIX)  stbmv_TLN.$(PSUFFIX)  : tbmv_U.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DTRANSA -UUNIT $< -o $(@F)

stbmv_NLU.$(SUFFIX)  stbmv_NLU.$(PSUFFIX)  : tbmv_L.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -UTRANSA -DUNIT $< -o $(@F)

stbmv_NLN.$(SUFFIX)  stbmv_NLN.$(PSUFFIX)  : tbmv_L.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -UTRANSA -UUNIT $< -o $(@F)

stbmv_TUU.$(SUFFIX)  stbmv_TUU.$(PSUFFIX)  : tbmv_L.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DTRANSA -DUNIT $< -o $(@F)

stbmv_TUN.$(SUFFIX)  stbmv_TUN.$(PSUFFIX)  : tbmv_L.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DTRANSA -UUNIT $< -o $(@F)

stbmv_thread_NUU.$(SUFFIX)  stbmv_thread_NUU.$(PSUFFIX)  : tbmv_thread.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -ULOWER -UTRANSA -DUNIT $< -o $(@F)

stbmv_thread_NUN.$(SUFFIX)  stbmv_thread_NUN.$(PSUFFIX)  : tbmv_thread.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -ULOWER -UTRANSA -UUNIT $< -o $(@F)

stbmv_thread_TLU.$(SUFFIX)  stbmv_thread_TLU.$(PSUFFIX)  : tbmv_thread.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DLOWER -DTRANSA -DUNIT $< -o $(@F)

stbmv_thread_TLN.$(SUFFIX)  stbmv_thread_TLN.$(PSUFFIX)  : tbmv_thread.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DLOWER -DTRANSA -UUNIT $< -o $(@F)

stbmv_thread_NLU.$(SUFFIX)  stbmv_thread_NLU.$(PSUFFIX)  : tbmv_thread.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DLOWER -UTRANSA -DUNIT $< -o $(@F)

stbmv_thread_NLN.$(SUFFIX)  stbmv_thread_NLN.$(PSUFFIX)  : tbmv_thread.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DLOWER -UTRANSA -UUNIT $< -o $(@F)

stbmv_thread_TUU.$(SUFFIX)  stbmv_thread_TUU.$(PSUFFIX)  : tbmv_thread.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -ULOWER -DTRANSA -DUNIT $< -o $(@F)

stbmv_thread_TUN.$(SUFFIX)  stbmv_thread_TUN.$(PSUFFIX)  : tbmv_thread.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -ULOWER -DTRANSA -UUNIT $< -o $(@F)

stbsv_NUU.$(SUFFIX)  stbsv_NUU.$(PSUFFIX)  : tbsv_U.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -UTRANSA -DUNIT $< -o $(@F)

stbsv_NUN.$(SUFFIX)  stbsv_NUN.$(PSUFFIX)  : tbsv_U.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -UTRANSA -UUNIT $< -o $(@F)

stbsv_TLU.$(SUFFIX)  stbsv_TLU.$(PSUFFIX)  : tbsv_U.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DTRANSA -DUNIT $< -o $(@F)

stbsv_TLN.$(SUFFIX)  stbsv_TLN.$(PSUFFIX)  : tbsv_U.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DTRANSA -UUNIT $< -o $(@F)

stbsv_NLU.$(SUFFIX)  stbsv_NLU.$(PSUFFIX)  : tbsv_L.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -UTRANSA -DUNIT $< -o $(@F)

stbsv_NLN.$(SUFFIX)  stbsv_NLN.$(PSUFFIX)  : tbsv_L.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -UTRANSA -UUNIT $< -o $(@F)

stbsv_TUU.$(SUFFIX)  stbsv_TUU.$(PSUFFIX)  : tbsv_L.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DTRANSA -DUNIT $< -o $(@F)

stbsv_TUN.$(SUFFIX)  stbsv_TUN.$(PSUFFIX)  : tbsv_L.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DTRANSA -UUNIT $< -o $(@F)


stpmv_NUU.$(SUFFIX)  stpmv_NUU.$(PSUFFIX)  : tpmv_U.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -UTRANSA -DUNIT $< -o $(@F)

stpmv_NUN.$(SUFFIX)  stpmv_NUN.$(PSUFFIX)  : tpmv_U.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -UTRANSA -UUNIT $< -o $(@F)

stpmv_TLU.$(SUFFIX)  stpmv_TLU.$(PSUFFIX)  : tpmv_U.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DTRANSA -DUNIT $< -o $(@F)

stpmv_TLN.$(SUFFIX)  stpmv_TLN.$(PSUFFIX)  : tpmv_U.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DTRANSA -UUNIT $< -o $(@F)

stpmv_NLU.$(SUFFIX)  stpmv_NLU.$(PSUFFIX)  : tpmv_L.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -UTRANSA -DUNIT $< -o $(@F)

stpmv_NLN.$(SUFFIX)  stpmv_NLN.$(PSUFFIX)  : tpmv_L.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -UTRANSA -UUNIT $< -o $(@F)

stpmv_TUU.$(SUFFIX)  stpmv_TUU.$(PSUFFIX)  : tpmv_L.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DTRANSA -DUNIT $< -o $(@F)

stpmv_TUN.$(SUFFIX)  stpmv_TUN.$(PSUFFIX)  : tpmv_L.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DTRANSA -UUNIT $< -o $(@F)

stpmv_thread_NUU.$(SUFFIX)  stpmv_thread_NUU.$(PSUFFIX)  : tpmv_thread.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -ULOWER -UTRANSA -DUNIT $< -o $(@F)

stpmv_thread_NUN.$(SUFFIX)  stpmv_thread_NUN.$(PSUFFIX)  : tpmv_thread.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -ULOWER -UTRANSA -UUNIT $< -o $(@F)

stpmv_thread_TLU.$(SUFFIX)  stpmv_thread_TLU.$(PSUFFIX)  : tpmv_thread.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DLOWER -DTRANSA -DUNIT $< -o $(@F)

stpmv_thread_TLN.$(SUFFIX)  stpmv_thread_TLN.$(PSUFFIX)  : tpmv_thread.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DLOWER -DTRANSA -UUNIT $< -o $(@F)

stpmv_thread_NLU.$(SUFFIX)  stpmv_thread_NLU.$(PSUFFIX)  : tpmv_thread.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DLOWER -UTRANSA -DUNIT $< -o $(@F)

stpmv_thread_NLN.$(SUFFIX)  stpmv_thread_NLN.$(PSUFFIX)  : tpmv_thread.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DLOWER -UTRANSA -UUNIT $< -o $(@F)

stpmv_thread_TUU.$(SUFFIX)  stpmv_thread_TUU.$(PSUFFIX)  : tpmv_thread.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -ULOWER -DTRANSA -DUNIT $< -o $(@F)

stpmv_thread_TUN.$(SUFFIX)  stpmv_thread_TUN.$(PSUFFIX)  : tpmv_thread.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -ULOWER -DTRANSA -UUNIT $< -o $(@F)

stpsv_NUU.$(SUFFIX)  stpsv_NUU.$(PSUFFIX)  : tpsv_U.c ../../param.h
	$(CC) -c $(CFLAGS) -UDOUBLE -UTRANSA -DUNIT $< -o $(@F)

stpsv_NUN.$(SUFFIX)  stpsv_NUN.$(PSUFFIX)  : tpsv_U.c ../../param.h
	$(CC) -c $(CFLAGS) -UDOUBLE -UTRANSA -UUNIT $< -o $(@F)

stpsv_TLU.$(SUFFIX)  stpsv_TLU.$(PSUFFIX)  : tpsv_U.c ../../param.h
	$(CC) -c $(CFLAGS) -UDOUBLE -DTRANSA -DUNIT $< -o $(@F)

stpsv_TLN.$(SUFFIX)  stpsv_TLN.$(PSUFFIX)  : tpsv_U.c ../../param.h
	$(CC) -c $(CFLAGS) -UDOUBLE -DTRANSA -UUNIT $< -o $(@F)

stpsv_NLU.$(SUFFIX)  stpsv_NLU.$(PSUFFIX)  : tpsv_L.c ../../param.h
	$(CC) -c $(CFLAGS) -UDOUBLE -UTRANSA -DUNIT $< -o $(@F)

stpsv_NLN.$(SUFFIX)  stpsv_NLN.$(PSUFFIX)  : tpsv_L.c ../../param.h
	$(CC) -c $(CFLAGS) -UDOUBLE -UTRANSA -UUNIT $< -o $(@F)

stpsv_TUU.$(SUFFIX)  stpsv_TUU.$(PSUFFIX)  : tpsv_L.c ../../param.h
	$(CC) -c $(CFLAGS) -UDOUBLE -DTRANSA -DUNIT $< -o $(@F)

stpsv_TUN.$(SUFFIX)  stpsv_TUN.$(PSUFFIX)  : tpsv_L.c ../../param.h
	$(CC) -c $(CFLAGS) -UDOUBLE -DTRANSA -UUNIT $< -o $(@F)


strmv_NUU.$(SUFFIX)  strmv_NUU.$(PSUFFIX)  : trmv_U.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -UTRANSA -DUNIT $< -o $(@F)

strmv_NUN.$(SUFFIX)  strmv_NUN.$(PSUFFIX)  : trmv_U.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -UTRANSA -UUNIT $< -o $(@F)

strmv_TLU.$(SUFFIX)  strmv_TLU.$(PSUFFIX)  : trmv_U.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DTRANSA -DUNIT $< -o $(@F)

strmv_TLN.$(SUFFIX)  strmv_TLN.$(PSUFFIX)  : trmv_U.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DTRANSA -UUNIT $< -o $(@F)

strmv_NLU.$(SUFFIX)  strmv_NLU.$(PSUFFIX)  : trmv_L.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -UTRANSA -DUNIT $< -o $(@F)

strmv_NLN.$(SUFFIX)  strmv_NLN.$(PSUFFIX)  : trmv_L.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -UTRANSA -UUNIT $< -o $(@F)

strmv_TUU.$(SUFFIX)  strmv_TUU.$(PSUFFIX)  : trmv_L.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DTRANSA -DUNIT $< -o $(@F)

strmv_TUN.$(SUFFIX)  strmv_TUN.$(PSUFFIX)  : trmv_L.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DTRANSA -UUNIT $< -o $(@F)


strmv_thread_NUU.$(SUFFIX)  strmv_thread_NUU.$(PSUFFIX)  : trmv_thread.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -ULOWER -UTRANSA -DUNIT $< -o $(@F)

strmv_thread_NUN.$(SUFFIX) strmv_thread_NUN.$(PSUFFIX) : trmv_thread.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -ULOWER -UTRANSA -UUNIT $< -o $(@F)

strmv_thread_TLU.$(SUFFIX) strmv_thread_TLU.$(PSUFFIX) : trmv_thread.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DLOWER -DTRANSA -DUNIT $< -o $(@F)

strmv_thread_TLN.$(SUFFIX) strmv_thread_TLN.$(PSUFFIX) : trmv_thread.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DLOWER -DTRANSA -UUNIT $< -o $(@F)

strmv_thread_NLU.$(SUFFIX) strmv_thread_NLU.$(PSUFFIX) : trmv_thread.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DLOWER -UTRANSA -DUNIT $< -o $(@F)

strmv_thread_NLN.$(SUFFIX) strmv_thread_NLN.$(PSUFFIX) : trmv_thread.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -DLOWER -UTRANSA -UUNIT $< -o $(@F)

strmv_thread_TUU.$(SUFFIX) strmv_thread_TUU.$(PSUFFIX) : trmv_thread.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -ULOWER -DTRANSA -DUNIT $< -o $(@F)

strmv_thread_TUN.$(SUFFIX) strmv_thread_TUN.$(PSUFFIX) : trmv_thread.c ../../common.h
	$(CC) -c $(CFLAGS) -UCOMPLEX -UDOUBLE -ULOWER -DTRANSA -UUNIT $< -o $(@F)

strsv_NUU.$(SUFFIX)  strsv_NUU.$(PSUFFIX)  : trsv_U.c ../../param.h
	$(CC) -c $(CFLAGS) -UDOUBLE -UTRANSA -DUNIT $< -o $(@F)

strsv_NUN.$(SUFFIX)  strsv_NUN.$(PSUFFIX)  : trsv_U.c ../../param.h
	$(CC) -c $(CFLAGS) -UDOUBLE -UTRANSA -UUNIT $< -o $(@F)

strsv_TLU.$(SUFFIX)  strsv_TLU.$(PSUFFIX)  : trsv_U.c ../../param.h
	$(CC) -c $(CFLAGS) -UDOUBLE -DTRANSA -DUNIT $< -o $(@F)

strsv_TLN.$(SUFFIX)  strsv_TLN.$(PSUFFIX)  : trsv_U.c ../../param.h
	$(CC) -c $(CFLAGS) -UDOUBLE -DTRANSA -UUNIT $< -o $(@F)

strsv_NLU.$(SUFFIX)  strsv_NLU.$(PSUFFIX)  : trsv_L.c ../../param.h
	$(CC) -c $(CFLAGS) -UDOUBLE -UTRANSA -DUNIT $< -o $(@F)

strsv_NLN.$(SUFFIX)  strsv_NLN.$(PSUFFIX)  : trsv_L.c ../../param.h
	$(CC) -c $(CFLAGS) -UDOUBLE -UTRANSA -UUNIT $< -o $(@F)

strsv_TUU.$(SUFFIX)  strsv_TUU.$(PSUFFIX)  : trsv_L.c ../../param.h
	$(CC) -c $(CFLAGS) -UDOUBLE -DTRANSA -DUNIT $< -o $(@F)

strsv_TUN.$(SUFFIX)  strsv_TUN.$(PSUFFIX)  : trsv_L.c ../../param.h
	$(CC) -c $(CFLAGS) -UDOUBLE -DTRANSA -UUNIT $< -o $(@F)

include ../../Makefile.tail
