SUBDIRS = references

info_TEXINFOS = halevt.texi
MAKEINFOHTML = $(MAKEINFO) --html --no-split

man_MANS = halevt.1 halevt-mount.1 halevt-umount.1 hvmount.1

HTMLS = halevt.1.html halevt-mount.1.html \
 halevt-umount.1.html halevt.html hvmount.1.html

EXTRA_DIST = halevt.1.in halevt-mount.1.in halevt-umount.1 hvmount.1.in

CLEANFILES = halevt.1 halevt-mount.1 hvmount.1 halevt.1.html \
 halevt-mount.1.html halevt-umount.1.html hvmount.1.html

all-local: html

halevt.1: halevt.1.in ../config.status
	sed -e "s/[@]PACKAGE_VERSION[@]/$(PACKAGE_VERSION)/" \
		-e "s/[@]PACKAGE_NAME[@]/$(PACKAGE_NAME)/g" \
		-e "s#[@]sysconfdir[@]#$(sysconfdir)#" \
		-e "s#[@]HALEVT_PIDDIR[@]#$(HALEVT_PIDDIR)#" \
		-e "s#[@]HALEVT_DEFAULT_GROUP[@]#$(HALEVT_DEFAULT_GROUP)#" \
		-e "s#[@]HALEVT_DEFAULT_USER[@]#$(HALEVT_DEFAULT_USER)#" \
		-e "s#[@]datadir[@]#$(datadir)#" $< > $@

halevt-mount.1: halevt-mount.1.in ../config.status
	sed -e "s/[@]PACKAGE_VERSION[@]/$(PACKAGE_VERSION)/" \
		-e "s/[@]PACKAGE_NAME[@]/$(PACKAGE_NAME)/g" \
		-e "s/[@]HALEVT_DEFAULT_USER[@]/$(HALEVT_DEFAULT_USER)/g" \
		$< > $@

hvmount.1: hvmount.1.in ../config.status
	sed -e "s/[@]PACKAGE_VERSION[@]/$(PACKAGE_VERSION)/" \
		-e "s/[@]PACKAGE_NAME[@]/$(PACKAGE_NAME)/g" \
		$< > $@

if USE_MAKEINFO
else
halevt.html: halevt.texi
	cp $(srcdir)/references/halevt.html halevt.html
endif

halevt-mount.1.html: halevt-mount.1
if USE_MAN2HTML
	$(MAN2HTML) -r $< | sed '1d' | sed 's|"\.\./man./|"|g; s|"\.\.\/index\.html|"halevt.html|g;'  > halevt-mount.1.html
else
	cp $(srcdir)/references/halevt-mount.1.html halevt-mount.1.html
endif

halevt-umount.1.html: halevt-mount.1
if USE_MAN2HTML
	$(MAN2HTML) -r $< | sed '1d' | sed 's|"\.\./man./|"|g; s|"\.\.\/index\.html|"halevt.html|g;'  > halevt-umount.1.html
else
	cp $(srcdir)/references/halevt-umount.1.html halevt-umount.1.html
endif

halevt.1.html: halevt.1
if USE_MAN2HTML
	$(MAN2HTML) -r $< | sed '1d' | sed 's|"\.\./man./|"|g; s|"\.\.\/index\.html|"halevt.html|g;'  > halevt.1.html
else
	cp $(srcdir)/references/halevt.1.html halevt.1.html
endif

hvmount.1.html: hvmount.1
if USE_MAN2HTML
	$(MAN2HTML) -r $< | sed '1d' | sed 's|"\.\./man./|"|g; s|"\.\.\/index\.html|"halevt.html|g;'  > hvmount.1.html
else
	cp $(srcdir)/references/hvmount.1.html hvmount.1.html
endif
