#
# Marvell Armada DRM-based driver
#
# Written by Russell King, 2012, derived in part from the
# Intel xorg X server driver.
#

# Turn off -Wnested-externs - these are a good thing because it allows
# information hiding and helps prevent misuse of private externs.
# Turn off -Wcast-qual - this makes stuff like string assignment
# too noisy.
# Turn off -Wredundant-decls - Xorg headers seem to contain a lot
# of this, so why it's in xorg-macros.m4... maybe more of a wish?
# Turn off -Wshadow - Xorg headers seem to declare a lot of globals
# which can conflict - index, range, etc.
AM_CFLAGS = $(filter-out -Wnested-externs -Wcast-qual -Wredundant-decls \
	-Werror=write-strings -Wshadow,$(CWARNFLAGS)) \
	$(XORG_CFLAGS) $(LIBGAL_CFLAGS) $(DRMARMADA_CFLAGS) $(UDEV_CFLAGS)
armada_drv_la_LTLIBRARIES = armada_drv.la
armada_drv_la_LDFLAGS = -module -avoid-version
armada_drv_la_LIBADD = $(LIBGAL_LIBS) $(DRMARMADA_LIBS) $(UDEV_LIBS)
armada_drv_ladir = @moduledir@/drivers
armada_drv_la_SOURCES = armada_module.c \
			armada_drm.c \
			armada_drm_xv.c \
			common_drm.c \
			vivante.c \
			vivante_accel.c \
			vivante_unaccel.c \
			vivante_unaccel_render.c \
			vivante_utils.c
if HAVE_DRI2
armada_drv_la_SOURCES += vivante_dri2.c
armada_drv_la_LIBADD += $(DRI_LIBS)
endif
