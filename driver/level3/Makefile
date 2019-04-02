TOPDIR	= ../..
include ../../Makefile.system

USE_GEMM3M = 0

ifeq ($(ARCH), x86)
USE_GEMM3M = 1
endif

ifeq ($(ARCH), x86_64)
USE_GEMM3M = 1
endif

ifeq ($(ARCH), ia64)
USE_GEMM3M = 1
endif

ifeq ($(ARCH), MIPS)
USE_GEMM3M = 1
endif

SBLASOBJS	+= \
	sgemm_nn.$(SUFFIX) sgemm_nt.$(SUFFIX) sgemm_tn.$(SUFFIX) sgemm_tt.$(SUFFIX) 


ifdef SMP
COMMONOBJS  += gemm_thread_m.$(SUFFIX) gemm_thread_n.$(SUFFIX) gemm_thread_mn.$(SUFFIX) gemm_thread_variable.$(SUFFIX)
COMMONOBJS  += syrk_thread.$(SUFFIX)

ifndef USE_SIMPLE_THREADED_LEVEL3

SBLASOBJS    += sgemm_thread_nn.$(SUFFIX) sgemm_thread_nt.$(SUFFIX) sgemm_thread_tn.$(SUFFIX) sgemm_thread_tt.$(SUFFIX)

endif
endif


all ::

sgemm_nn.$(SUFFIX) : gemm.c level3.c ../../param.h
	$(CC) $(CFLAGS) $(BLOCKS) -c -UDOUBLE -UCOMPLEX -DNN $< -o $(@F)

sgemm_nt.$(SUFFIX) : gemm.c level3.c ../../param.h
	$(CC) $(CFLAGS) $(BLOCKS) -c -UDOUBLE -UCOMPLEX -DNT $< -o $(@F)

sgemm_tn.$(SUFFIX) : gemm.c level3.c ../../param.h
	$(CC) $(CFLAGS) $(BLOCKS) -c -UDOUBLE -UCOMPLEX -DTN $< -o $(@F)

sgemm_tt.$(SUFFIX) : gemm.c level3.c ../../param.h
	$(CC) $(CFLAGS) $(BLOCKS) -c -UDOUBLE -UCOMPLEX -DTT $< -o $(@F)


gemm_thread_m.$(SUFFIX) : gemm_thread_m.c ../../common.h
	$(CC) -c $(CFLAGS) $< -o $(@F)

gemm_thread_n.$(SUFFIX) : gemm_thread_n.c ../../common.h
	$(CC) -c $(CFLAGS) $< -o $(@F)

gemm_thread_mn.$(SUFFIX) : gemm_thread_mn.c ../../common.h
	$(CC) -c $(CFLAGS) $< -o $(@F)

gemm_thread_variable.$(SUFFIX) : gemm_thread_variable.c ../../common.h
	$(CC) -c $(CFLAGS) $< -o $(@F)

beta_thread.$(SUFFIX) : beta_thread.c ../../common.h
	$(CC) -c $(CFLAGS) $< -o $(@F)


sgemm_thread_nn.$(SUFFIX) : gemm.c level3_thread.c ../../param.h
	$(CC) $(CFLAGS) $(BLOCKS) -c -DTHREADED_LEVEL3 -UDOUBLE -UCOMPLEX -DNN $< -o $(@F)

sgemm_thread_nt.$(SUFFIX) : gemm.c level3_thread.c ../../param.h
	$(CC) $(CFLAGS) $(BLOCKS) -c -DTHREADED_LEVEL3 -UDOUBLE -UCOMPLEX -DNT $< -o $(@F)

sgemm_thread_tn.$(SUFFIX) : gemm.c level3_thread.c ../../param.h
	$(CC) $(CFLAGS) $(BLOCKS) -c -DTHREADED_LEVEL3 -UDOUBLE -UCOMPLEX -DTN $< -o $(@F)

sgemm_thread_tt.$(SUFFIX) : gemm.c level3_thread.c ../../param.h
	$(CC) $(CFLAGS) $(BLOCKS) -c -DTHREADED_LEVEL3 -UDOUBLE -UCOMPLEX -DTT $< -o $(@F)



sgemm_nn.$(PSUFFIX) : gemm.c level3.c ../../param.h
	$(CC) $(PFLAGS) $(BLOCKS) -c -UDOUBLE -UCOMPLEX -DNN $< -o $(@F)

sgemm_nt.$(PSUFFIX) : gemm.c level3.c ../../param.h
	$(CC) $(PFLAGS) $(BLOCKS) -c -UDOUBLE -UCOMPLEX -DNT $< -o $(@F)

sgemm_tn.$(PSUFFIX) : gemm.c level3.c ../../param.h
	$(CC) $(PFLAGS) $(BLOCKS) -c -UDOUBLE -UCOMPLEX -DTN $< -o $(@F)

sgemm_tt.$(PSUFFIX) : gemm.c level3.c ../../param.h
	$(CC) $(PFLAGS) $(BLOCKS) -c -UDOUBLE -UCOMPLEX -DTT $< -o $(@F)


sgemm_thread_nn.$(PSUFFIX) : gemm.c level3_thread.c ../../param.h
	$(CC) $(PFLAGS) $(BLOCKS) -c -DTHREADED_LEVEL3 -UDOUBLE -UCOMPLEX -DNN $< -o $(@F)

sgemm_thread_nt.$(PSUFFIX) : gemm.c level3_thread.c ../../param.h
	$(CC) $(PFLAGS) $(BLOCKS) -c -DTHREADED_LEVEL3 -UDOUBLE -UCOMPLEX -DNT $< -o $(@F)

sgemm_thread_tn.$(PSUFFIX) : gemm.c level3_thread.c ../../param.h
	$(CC) $(PFLAGS) $(BLOCKS) -c -DTHREADED_LEVEL3 -UDOUBLE -UCOMPLEX -DTN $< -o $(@F)

sgemm_thread_tt.$(PSUFFIX) : gemm.c level3_thread.c ../../param.h
	$(CC) $(PFLAGS) $(BLOCKS) -c -DTHREADED_LEVEL3 -UDOUBLE -UCOMPLEX -DTT $< -o $(@F)



include ../../Makefile.tail
