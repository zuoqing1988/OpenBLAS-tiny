TOPDIR	= ..
include $(TOPDIR)/Makefile.system

SUPPORT_GEMM3M = 0

ifeq ($(ARCH), x86)
SUPPORT_GEMM3M = 1
endif

ifeq ($(ARCH), x86_64)
SUPPORT_GEMM3M = 1
endif

ifeq ($(ARCH), ia64)
SUPPORT_GEMM3M = 1
endif

ifeq ($(ARCH), MIPS)
SUPPORT_GEMM3M = 1
endif

ifndef NO_FBLAS

SBLAS1OBJS    = \
		saxpy.$(SUFFIX) sswap.$(SUFFIX) \
		scopy.$(SUFFIX) sscal.$(SUFFIX) \
		sdot.$(SUFFIX) sdsdot.$(SUFFIX) dsdot.$(SUFFIX) \
		sasum.$(SUFFIX) snrm2.$(SUFFIX) \
		smax.$(SUFFIX) samax.$(SUFFIX) ismax.$(SUFFIX) isamax.$(SUFFIX) \
		smin.$(SUFFIX) samin.$(SUFFIX) ismin.$(SUFFIX) isamin.$(SUFFIX) \
		srot.$(SUFFIX) srotg.$(SUFFIX) srotm.$(SUFFIX) srotmg.$(SUFFIX) \
		saxpby.$(SUFFIX)

SBLAS2OBJS    = \
		sgemv.$(SUFFIX) sger.$(SUFFIX) \
		strsv.$(SUFFIX) strmv.$(SUFFIX) ssymv.$(SUFFIX) \
		ssyr.$(SUFFIX)  ssyr2.$(SUFFIX) sgbmv.$(SUFFIX) \
		ssbmv.$(SUFFIX) sspmv.$(SUFFIX) \
		sspr.$(SUFFIX)  sspr2.$(SUFFIX) \
		stbsv.$(SUFFIX) stbmv.$(SUFFIX) \
		stpsv.$(SUFFIX) stpmv.$(SUFFIX)

SBLAS3OBJS    = \
		sgemm.$(SUFFIX) ssymm.$(SUFFIX) strmm.$(SUFFIX) \
		strsm.$(SUFFIX) ssyrk.$(SUFFIX) ssyr2k.$(SUFFIX) \
		somatcopy.$(SUFFIX) simatcopy.$(SUFFIX)\
		sgeadd.$(SUFFIX)


endif

HPLOBJS = dgemm.$(SUFFIX) dtrsm.$(SUFFIX) \
	  dgemv.$(SUFFIX)  dtrsv.$(SUFFIX) dger.$(SUFFIX) \
	  idamax.$(SUFFIX) daxpy.$(SUFFIX) dcopy.$(SUFFIX) dscal.$(SUFFIX)

CSBLAS1OBJS   = \
	cblas_isamax.$(SUFFIX) cblas_isamin.$(SUFFIX) cblas_sasum.$(SUFFIX) cblas_saxpy.$(SUFFIX) \
	cblas_scopy.$(SUFFIX) cblas_sdot.$(SUFFIX) cblas_sdsdot.$(SUFFIX) cblas_dsdot.$(SUFFIX) \
	cblas_srot.$(SUFFIX) cblas_srotg.$(SUFFIX) cblas_srotm.$(SUFFIX) cblas_srotmg.$(SUFFIX) \
	cblas_sscal.$(SUFFIX) cblas_sswap.$(SUFFIX) cblas_snrm2.$(SUFFIX) cblas_saxpby.$(SUFFIX)

CSBLAS2OBJS   = \
	cblas_sgemv.$(SUFFIX) cblas_sger.$(SUFFIX) cblas_ssymv.$(SUFFIX) cblas_strmv.$(SUFFIX) \
	cblas_strsv.$(SUFFIX) cblas_ssyr.$(SUFFIX) cblas_ssyr2.$(SUFFIX) cblas_sgbmv.$(SUFFIX) \
	cblas_ssbmv.$(SUFFIX) cblas_sspmv.$(SUFFIX) cblas_sspr.$(SUFFIX) cblas_sspr2.$(SUFFIX) \
	cblas_stbmv.$(SUFFIX) cblas_stbsv.$(SUFFIX) cblas_stpmv.$(SUFFIX) cblas_stpsv.$(SUFFIX)

CSBLAS3OBJS   = \
	cblas_sgemm.$(SUFFIX) cblas_ssymm.$(SUFFIX) cblas_strmm.$(SUFFIX) cblas_strsm.$(SUFFIX) \
	cblas_ssyrk.$(SUFFIX) cblas_ssyr2k.$(SUFFIX) cblas_somatcopy.$(SUFFIX)  cblas_simatcopy.$(SUFFIX)\
	cblas_sgeadd.$(SUFFIX)


ifndef NO_CBLAS

override CFLAGS += -I.

SBLAS1OBJS   += $(CSBLAS1OBJS)
SBLAS2OBJS   += $(CSBLAS2OBJS)
SBLAS3OBJS   += $(CSBLAS3OBJS)

endif

SBLASOBJS    = $(SBLAS1OBJS) $(SBLAS2OBJS) $(SBLAS3OBJS)

#SLAPACKOBJS	= \
#	sgetrf.$(SUFFIX) sgetrs.$(SUFFIX) spotrf.$(SUFFIX) sgetf2.$(SUFFIX) \
#	spotf2.$(SUFFIX) slaswp.$(SUFFIX) sgesv.$(SUFFIX) slauu2.$(SUFFIX)  \
#	slauum.$(SUFFIX) strti2.$(SUFFIX) strtri.$(SUFFIX) spotri.$(SUFFIX)

SLAPACKOBJS	= \
	sgetrf.$(SUFFIX) sgetrs.$(SUFFIX) spotrf.$(SUFFIX) sgetf2.$(SUFFIX) \
	spotf2.$(SUFFIX) slaswp.$(SUFFIX) sgesv.$(SUFFIX) slauu2.$(SUFFIX)  \
	slauum.$(SUFFIX) strti2.$(SUFFIX) strtri.$(SUFFIX)



ifneq ($(NO_LAPACK), 1)
SBLASOBJS += $(SLAPACKOBJS)
endif

FUNCOBJS    = $(SBLASOBJS) 

FUNCALLFILES = $(FUNCOBJS:.$(SUFFIX)=)

include $(TOPDIR)/Makefile.tail

all :: libs

ifdef FUNCTION_PROFILE
$(BLASOBJS) $(BLASOBJS_P) : functable.h
$(BLASOBJS) $(BLASOBJS_P) : override CFLAGS += -DPROFILE_FUNC_NAME=interface_$(*F)

functable.h : Makefile
	./create $(FUNCALLFILES) > functable.h

endif

clean ::
	@rm -f functable.h

level1 : $(SBLAS1OBJS) 
	$(AR) $(ARFLAGS) -ru $(TOPDIR)/$(LIBNAME) $^

level2 : $(SBLAS2OBJS) 
	$(AR) $(ARFLAGS) -ru $(TOPDIR)/$(LIBNAME) $^

level3 : $(SBLAS3OBJS) 
	$(AR) $(ARFLAGS) -ru $(TOPDIR)/$(LIBNAME) $^

$(CSBLASOBJS) $(CSBLASOBJS_P) : override CFLAGS += -DCBLAS

srot.$(SUFFIX) srot.$(PSUFFIX) : rot.c
	$(CC) $(CFLAGS) -c $< -o $(@F)


srotm.$(SUFFIX) srotm.$(PSUFFIX): rotm.c
	$(CC) -c $(CFLAGS) $< -o $(@F)

srotg.$(SUFFIX) srotg.$(PSUFFIX): rotg.c
	$(CC) -c $(CFLAGS) $< -o $(@F)


sasum.$(SUFFIX) sasum.$(PSUFFIX) : asum.c
	$(CC) $(CFLAGS) -c $< -o $(@F)

snrm2.$(SUFFIX) snrm2.$(PSUFFIX) : nrm2.c
	$(CC) $(CFLAGS) -c $< -o $(@F)

samax.$(SUFFIX) samax.$(PSUFFIX) : max.c
	$(CC) $(CFLAGS) -c -DUSE_ABS -UUSE_MIN $< -o $(@F)


samin.$(SUFFIX) samin.$(PSUFFIX) : max.c
	$(CC) $(CFLAGS) -c -DUSE_ABS -DUSE_MIN $< -o $(@F)


smax.$(SUFFIX) smax.$(PSUFFIX) : max.c
	$(CC) $(CFLAGS) -c -UUSE_ABS -UUSE_MIN $< -o $(@F)


isamax.$(SUFFIX) isamax.$(PSUFFIX) : imax.c
	$(CC) $(CFLAGS) -c -DUSE_ABS -UUSE_MIN $< -o $(@F)

isamin.$(SUFFIX) isamin.$(PSUFFIX) : imax.c
	$(CC) $(CFLAGS) -c -DUSE_ABS -DUSE_MIN $< -o $(@F)

ismax.$(SUFFIX) ismax.$(PSUFFIX) : imax.c
	$(CC) $(CFLAGS) -c -UUSE_ABS -UUSE_MIN $< -o $(@F)
	
ismin.$(SUFFIX) ismin.$(PSUFFIX) : imax.c
	$(CC) $(CFLAGS) -c -UUSE_ABS -DUSE_MIN $< -o $(@F)

sdsdot.$(SUFFIX) sdsdot.$(PSUFFIX) : sdsdot.c
	$(CC) $(CFLAGS) -c $< -o $(@F)

dsdot.$(SUFFIX) dsdot.$(PSUFFIX) : dsdot.c
	$(CC) $(CFLAGS) -c $< -o $(@F)

sdot.$(SUFFIX) sdot.$(PSUFFIX) : dot.c
	$(CC) $(CFLAGS) -c $< -o $(@F)

ddot.$(SUFFIX) ddot.$(PSUFFIX) : dot.c
	$(CC) $(CFLAGS) -c $< -o $(@F)


saxpy.$(SUFFIX) saxpy.$(PSUFFIX) : axpy.c
	$(CC) $(CFLAGS) -c $< -o $(@F)


sscal.$(SUFFIX) sscal.$(PSUFFIX) : scal.c
	$(CC) $(CFLAGS) -c $< -o $(@F)

scopy.$(SUFFIX) scopy.$(PSUFFIX) : copy.c
	$(CC) $(CFLAGS) -c $< -o $(@F)

sswap.$(SUFFIX) sswap.$(PSUFFIX) : swap.c
	$(CC) $(CFLAGS) -c $< -o $(@F)

sger.$(SUFFIX) sger.$(PSUFFIX) : ger.c
	$(CC) -c $(CFLAGS) $< -o $(@F)

ifndef USE_NETLIB_GEMV
sgemv.$(SUFFIX) sgemv.$(PSUFFIX): gemv.c
	$(CC) -c $(CFLAGS) -o $(@F) $<

else
sgemv.$(SUFFIX) sgemv.$(PSUFFIX): netlib/sgemv.f
	$(FC) -c $(FFLAGS) -o $(@F) $<

endif

strsv.$(SUFFIX) strsv.$(PSUFFIX) : trsv.c
	$(CC) -c $(CFLAGS) $< -o $(@F)


strmv.$(SUFFIX) strmv.$(PSUFFIX) : trmv.c
	$(CC) -c $(CFLAGS) $< -o $(@F)


ssymv.$(SUFFIX) ssymv.$(PSUFFIX) : symv.c
	$(CC) -c $(CFLAGS) $< -o $(@F)


ssyr.$(SUFFIX) ssyr.$(PSUFFIX) : syr.c
	$(CC) -c $(CFLAGS) $< -o $(@F)


ssyr2.$(SUFFIX) ssyr2.$(PSUFFIX) : syr2.c
	$(CC) -c $(CFLAGS) $< -o $(@F)

sgbmv.$(SUFFIX) sgbmv.$(PSUFFIX): gbmv.c
	$(CC) -c $(CFLAGS) -o $(@F) $<

ssbmv.$(SUFFIX) ssbmv.$(PSUFFIX) : sbmv.c
	$(CC) -c $(CFLAGS) $< -o $(@F)


sspmv.$(SUFFIX) sspmv.$(PSUFFIX) : spmv.c
	$(CC) -c $(CFLAGS) $< -o $(@F)

sspr.$(SUFFIX) sspr.$(PSUFFIX) : spr.c
	$(CC) -c $(CFLAGS) $< -o $(@F)

sspr2.$(SUFFIX) sspr2.$(PSUFFIX) : spr2.c
	$(CC) -c $(CFLAGS) $< -o $(@F)

stbmv.$(SUFFIX) stbmv.$(PSUFFIX) : tbmv.c
	$(CC) -c $(CFLAGS) $< -o $(@F)

stbsv.$(SUFFIX) stbsv.$(PSUFFIX) : tbsv.c
	$(CC) -c $(CFLAGS) $< -o $(@F)


stpsv.$(SUFFIX) stpsv.$(PSUFFIX) : tpsv.c
	$(CC) -c $(CFLAGS) $< -o $(@F)

stpmv.$(SUFFIX) stpmv.$(PSUFFIX) : tpmv.c
	$(CC) -c $(CFLAGS) $< -o $(@F)


sgemm.$(SUFFIX) sgemm.$(PSUFFIX) : gemm.c ../param.h
	$(CC) -c $(CFLAGS) $< -o $(@F)


ssymm.$(SUFFIX) ssymm.$(PSUFFIX) : symm.c
	$(CC) -c $(CFLAGS) $< -o $(@F)


strmm.$(SUFFIX) strmm.$(PSUFFIX) : trsm.c
	$(CC) -c $(CFLAGS) -DTRMM $< -o $(@F)

strsm.$(SUFFIX) strsm.$(PSUFFIX) : trsm.c
	$(CC) -c $(CFLAGS) $< -o $(@F)

ssyrk.$(SUFFIX) ssyrk.$(PSUFFIX) : syrk.c
	$(CC) -c $(CFLAGS) $< -o $(@F)


ssyr2k.$(SUFFIX) ssyr2k.$(PSUFFIX) : syr2k.c
	$(CC) -c $(CFLAGS) $< -o $(@F)


cblas_isamax.$(SUFFIX) cblas_isamax.$(PSUFFIX) : imax.c
	$(CC) $(CFLAGS) -DCBLAS -c -DUSE_ABS -UUSE_MIN $< -o $(@F)


cblas_isamin.$(SUFFIX) cblas_isamin.$(PSUFFIX) : imax.c
	$(CC) $(CFLAGS) -DCBLAS -c -DUSE_ABS -DUSE_MIN $< -o $(@F)

cblas_ismax.$(SUFFIX) cblas_ismax.$(PSUFFIX) : imax.c
	$(CC) $(CFLAGS) -DCBLAS -c -UUSE_ABS -UUSE_MIN $< -o $(@F)

cblas_ismin.$(SUFFIX) cblas_ismin.$(PSUFFIX) : imax.c
	$(CC) $(CFLAGS) -DCBLAS -c -UUSE_ABS -DUSE_MIN $< -o $(@F)


cblas_sasum.$(SUFFIX) cblas_sasum.$(PSUFFIX) : asum.c
	$(CC) $(CFLAGS) -DCBLAS -c $< -o $(@F)


cblas_scasum.$(SUFFIX) cblas_scasum.$(PSUFFIX) : asum.c
	$(CC) $(CFLAGS) -DCBLAS -c $< -o $(@F)

cblas_sdsdot.$(SUFFIX) cblas_sdsdot.$(PSUFFIX) : sdsdot.c
	$(CC) $(CFLAGS) -DCBLAS -c $< -o $(@F)


cblas_sdot.$(SUFFIX) cblas_sdot.$(PSUFFIX) : dot.c
	$(CC) $(CFLAGS) -DCBLAS -c $< -o $(@F)


cblas_snrm2.$(SUFFIX) cblas_snrm2.$(PSUFFIX) : nrm2.c
	$(CC) $(CFLAGS) -DCBLAS -c $< -o $(@F)


cblas_scnrm2.$(SUFFIX) cblas_scnrm2.$(PSUFFIX) : nrm2.c
	$(CC) $(CFLAGS) -DCBLAS -c $< -o $(@F)


cblas_saxpy.$(SUFFIX) cblas_saxpy.$(PSUFFIX) : axpy.c
	$(CC) $(CFLAGS) -DCBLAS -c $< -o $(@F)


cblas_scopy.$(SUFFIX) cblas_scopy.$(PSUFFIX) : copy.c
	$(CC) $(CFLAGS) -DCBLAS -c $< -o $(@F)


cblas_sswap.$(SUFFIX) cblas_sswap.$(PSUFFIX) : swap.c
	$(CC) $(CFLAGS) -DCBLAS -c $< -o $(@F)


cblas_srot.$(SUFFIX) cblas_srot.$(PSUFFIX) : rot.c
	$(CC) $(CFLAGS) -DCBLAS -c $< -o $(@F)


cblas_srotg.$(SUFFIX) cblas_srotg.$(PSUFFIX): rotg.c
	$(CC) $(CFLAGS) -DCBLAS -c $< -o $(@F)

cblas_srotm.$(SUFFIX) cblas_srotm.$(PSUFFIX): rotm.c
	$(CC) $(CFLAGS) -DCBLAS -c $< -o $(@F)

cblas_srotmg.$(SUFFIX) cblas_srotmg.$(PSUFFIX): rotmg.c
	$(CC) $(CFLAGS) -DCBLAS -c $< -o $(@F)


cblas_sscal.$(SUFFIX) cblas_sscal.$(PSUFFIX) : scal.c
	$(CC) $(CFLAGS) -DCBLAS -c $< -o $(@F)


cblas_sgemv.$(SUFFIX) cblas_sgemv.$(PSUFFIX): gemv.c
	$(CC) -DCBLAS -c $(CFLAGS) -o $(@F) $<

cblas_sger.$(SUFFIX) cblas_sger.$(PSUFFIX) : ger.c
	$(CC) -DCBLAS -c $(CFLAGS) $< -o $(@F)

cblas_strsv.$(SUFFIX) cblas_strsv.$(PSUFFIX) : trsv.c
	$(CC) -DCBLAS -c $(CFLAGS) $< -o $(@F)

cblas_strmv.$(SUFFIX) cblas_strmv.$(PSUFFIX) : trmv.c
	$(CC) -DCBLAS -c $(CFLAGS) $< -o $(@F)

cblas_ssyr.$(SUFFIX) cblas_ssyr.$(PSUFFIX) : syr.c
	$(CC) -DCBLAS -c $(CFLAGS) $< -o $(@F)

cblas_ssyr2.$(SUFFIX) cblas_ssyr2.$(PSUFFIX) : syr2.c
	$(CC) -DCBLAS -c $(CFLAGS) $< -o $(@F)

cblas_sgbmv.$(SUFFIX) cblas_sgbmv.$(PSUFFIX): gbmv.c
	$(CC) -DCBLAS -c $(CFLAGS) -o $(@F) $<

cblas_ssbmv.$(SUFFIX) cblas_ssbmv.$(PSUFFIX) : sbmv.c
	$(CC) -DCBLAS -c $(CFLAGS) $< -o $(@F)

cblas_sspmv.$(SUFFIX) cblas_sspmv.$(PSUFFIX) : spmv.c
	$(CC) -DCBLAS -c $(CFLAGS) $< -o $(@F)

cblas_sspr.$(SUFFIX) cblas_sspr.$(PSUFFIX) : spr.c
	$(CC) -DCBLAS -c $(CFLAGS) $< -o $(@F)


cblas_sspr2.$(SUFFIX) cblas_sspr2.$(PSUFFIX) : spr2.c
	$(CC) -DCBLAS -c $(CFLAGS) $< -o $(@F)


cblas_stbmv.$(SUFFIX) cblas_stbmv.$(PSUFFIX) : tbmv.c
	$(CC) -DCBLAS -c $(CFLAGS) $< -o $(@F)

cblas_stbsv.$(SUFFIX) cblas_stbsv.$(PSUFFIX) : tbsv.c
	$(CC) -DCBLAS -c $(CFLAGS) $< -o $(@F)

cblas_stpmv.$(SUFFIX) cblas_stpmv.$(PSUFFIX) : tpmv.c
	$(CC) -DCBLAS -c $(CFLAGS) $< -o $(@F)

cblas_stpsv.$(SUFFIX) cblas_stpsv.$(PSUFFIX) : tpsv.c
	$(CC) -DCBLAS -c $(CFLAGS) $< -o $(@F)

cblas_ssymv.$(SUFFIX) cblas_ssymv.$(PSUFFIX) : symv.c
	$(CC) -DCBLAS -c $(CFLAGS) $< -o $(@F)


cblas_sgemm.$(SUFFIX) cblas_sgemm.$(PSUFFIX) : gemm.c ../param.h
	$(CC) -DCBLAS -c $(CFLAGS) $< -o $(@F)

cblas_ssymm.$(SUFFIX) cblas_ssymm.$(PSUFFIX) : symm.c
	$(CC) -DCBLAS -c $(CFLAGS) $< -o $(@F)


cblas_ssyrk.$(SUFFIX) cblas_ssyrk.$(PSUFFIX) : syrk.c
	$(CC) -DCBLAS -c $(CFLAGS) $< -o $(@F)


cblas_ssyr2k.$(SUFFIX) cblas_ssyr2k.$(PSUFFIX) : syr2k.c
	$(CC) -DCBLAS -c $(CFLAGS) $< -o $(@F)

cblas_strmm.$(SUFFIX) cblas_strmm.$(PSUFFIX) : trsm.c
	$(CC) -DCBLAS -c $(CFLAGS) -DTRMM $< -o $(@F)


cblas_strsm.$(SUFFIX) cblas_strsm.$(PSUFFIX) : trsm.c
	$(CC) -DCBLAS -c $(CFLAGS) $< -o $(@F)

sgetf2.$(SUFFIX) sgetf2.$(PSUFFIX) : lapack/getf2.c
	$(CC) -c $(CFLAGS) $< -o $(@F)


sgetrf.$(SUFFIX) sgetrf.$(PSUFFIX) : lapack/getrf.c
	$(CC) -c $(CFLAGS) $< -o $(@F)


slauu2.$(SUFFIX) slauu2.$(PSUFFIX) : lapack/lauu2.c
	$(CC) -c $(CFLAGS) $< -o $(@F)

slauum.$(SUFFIX) slauum.$(PSUFFIX) : lapack/lauum.c
	$(CC) -c $(CFLAGS) $< -o $(@F)

spotf2.$(SUFFIX) spotf2.$(PSUFFIX) : lapack/potf2.c
	$(CC) -c $(CFLAGS) $< -o $(@F)

spotrf.$(SUFFIX) spotrf.$(PSUFFIX) : lapack/potrf.c
	$(CC) -c $(CFLAGS) $< -o $(@F)


strti2.$(SUFFIX) strti2.$(PSUFFIX) : lapack/trti2.c
	$(CC) -c $(CFLAGS) $< -o $(@F)


strtri.$(SUFFIX) strtri.$(PSUFFIX) : lapack/trtri.c
	$(CC) -c $(CFLAGS) $< -o $(@F)

slaswp.$(SUFFIX) slaswp.$(PSUFFIX) : lapack/laswp.c
	$(CC) -c $(CFLAGS) $< -o $(@F)


sgetrs.$(SUFFIX) sgetrs.$(PSUFFIX) : lapack/getrs.c
	$(CC) -c $(CFLAGS) $< -o $(@F)

sgesv.$(SUFFIX) sgesv.$(PSUFFIX) : lapack/gesv.c
	$(CC) -c $(CFLAGS) $< -o $(@F)


spotri.$(SUFFIX) spotri.$(PSUFFIX) : lapack/potri.c
	$(CC) -c $(CFLAGS) $< -o $(@F)

slarf.$(SUFFIX) slarf.$(PSUFFIX) : larf.c
	$(CC) -c $(CFLAGS) $< -o $(@F)


############# BLAS EXTENSIONS #####################################


saxpby.$(SUFFIX) saxpby.$(PSUFFIX) : axpby.c
	$(CC) $(CFLAGS) -c $< -o $(@F)

cblas_saxpby.$(SUFFIX) cblas_saxpby.$(PSUFFIX) : axpby.c
	$(CC) $(CFLAGS) -DCBLAS -c $< -o $(@F)


somatcopy.$(SUFFIX) somatcopy.$(PSUFFIX) : omatcopy.c
	$(CC) -c $(CFLAGS) $< -o $(@F)

cblas_somatcopy.$(SUFFIX) cblas_somatcopy.$(PSUFFIX) : omatcopy.c
	$(CC) -c $(CFLAGS) -DCBLAS $< -o $(@F)

simatcopy.$(SUFFIX) simatcopy.$(PSUFFIX) : imatcopy.c
	$(CC) -c $(CFLAGS) $< -o $(@F)

cblas_simatcopy.$(SUFFIX) cblas_simatcopy.$(PSUFFIX) : imatcopy.c
	$(CC) -c $(CFLAGS) -DCBLAS $< -o $(@F)


sgeadd.$(SUFFIX) sgeadd.$(PSUFFIX) : geadd.c
	$(CC) -c $(CFLAGS) $< -o $(@F)

cblas_sgeadd.$(SUFFIX) cblas_sgeadd.$(PSUFFIX) : geadd.c
	$(CC) -c $(CFLAGS) -DCBLAS $< -o $(@F)
