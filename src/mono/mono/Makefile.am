MAKEFLAGS := $(MAKEFLAGS) --no-builtin-rules

if SUPPORT_SGEN
sgen_dirs = sgen
endif

if BTLS
btls_dirs = btls
endif

if MONO_NATIVE
native_dirs = native
endif

if ENABLE_NETCORE
btls_dirs =
managed_unit_test_dirs =
native_unit_test_dirs =
else
managed_unit_test_dirs = tests
native_unit_test_dirs = unit-tests
endif

if ENABLE_PERFTRACING
eventpipe_dirs = eventpipe
endif

if ENABLE_NETCORE
SUBDIRS = eglib arch utils sgen zlib $(eventpipe_dirs) metadata mini profiler $(native_unit_test_dirs)
else

if CROSS_COMPILING
SUBDIRS = $(btls_dirs) eglib arch utils cil zlib $(sgen_dirs) metadata mini dis profiler $(native_dirs)
else
if INSTALL_MONOTOUCH
SUBDIRS = $(btls_dirs) eglib arch utils zlib $(sgen_dirs) metadata mini profiler $(native_dirs)
else
SUBDIRS = $(btls_dirs) eglib arch utils cil zlib $(sgen_dirs) metadata mini dis $(managed_unit_test_dirs) $(native_unit_test_dirs) benchmark profiler $(native_dirs)
endif
endif
endif

DIST_SUBDIRS = btls native eglib arch utils cil zlib $(sgen_dirs) metadata mini dis $(managed_unit_test_dirs) $(native_unit_test_dirs) benchmark profiler
