SUBDIRS = po

bin_PROGRAMS = halevt-mount

halevt_mount_SOURCES = halevt-mount.c
halevt_mount_CPPFLAGS = -DLOCALSTATEDIR="\"$(localstatedir)\"" \
  -DDATADIR="\"$(datadir)\"" \
  $(HAL_CFLAGS) $(DBUS_CFLAGS)
halevt_mount_LDADD = $(HAL_LIBS) $(DBUS_LIBS)

# halevt-umount is a symlink to halevt-mount. We ignore if it fails, because
# the link may already be there

all-local:
	-$(LN_S) halevt-mount halevt-umount

install-exec-local:
	-f=`echo "halevt-mount" | sed 's|^.*/||;$(transform)'`; \
	  t=`echo "halevt-umount" | sed 's|^.*/||;$(transform)'`; \
	  $(LN_S) "$$f" "$(DESTDIR)$(bindir)/$$t"

# data directory for halevt-mount
install-data-local:
	$(MKDIR_P) "$(DESTDIR)$(localstatedir)/lib/$(PACKAGE_NAME)"

uninstall-local:
	t=`echo "halevt-umount" | sed 's|^.*/||;$(transform)'`; \
	  $(RM) "$(DESTDIR)$(bindir)/$$t"
	-rmdir "$(DESTDIR)$(localstatedir)/lib/$(PACKAGE_NAME)"

perms:
	chown $(HALEVT_DEFAULT_USER) "$(DESTDIR)$(localstatedir)/lib/$(PACKAGE_NAME)"
	chgrp $(HALEVT_DEFAULT_GROUP) "$(DESTDIR)$(localstatedir)/lib/$(PACKAGE_NAME)"

CLEANFILES = halevt-umount
