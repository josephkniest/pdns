SUBDIRS=modules codedocs @programdescend@
DIST_SUBDIRS=modules codedocs pdns pdns/ext/rapidjson
EXTRA_DIST=README INSTALL NOTICE debian-pdns/* pdns.spec  \
codedocs/doxygen.conf contrib/powerdns.solaris.init.d \
contrib/systemd-pdns.service contrib/systemd-pdns-recursor.service \
bootstrap build-scripts/semistaticg++ pdns/docs/dnstcpbench.1 \
build-scripts/redhat/pdns-server-test.spec \
pdns/ext/rapidjson/Makefile \
pdns/named.conf.parsertest regression-tests/zones/unit.test

ACLOCAL_AMFLAGS = -I m4

man8_MANS=pdns/docs/pdns_control.8 pdns/docs/pdnssec.8 pdns/docs/pdns_server.8 \
  pdns/docs/zone2ldap.8 pdns/docs/zone2sql.8

if TOOLS
  man8_MANS += pdns/docs/dnsreplay.8 pdns/docs/dnsscope.8 pdns/docs/dnswasher.8
  man1_MANS = pdns/docs/dnstcpbench.1
endif

pdns/docs/dnstcpbench.1:
	cd pdns/docs && $(MAKE) dnstcpbench.1

install-exec-local: 
	-@chmod +x pdns/pdns
	@echo "***********************************************************"
	@echo
	@echo An init.d startup script has been made for you in pdns/pdns.
	@echo You may want to copy these to /etc/init.d or equivalent
	@echo
	@echo "***********************************************************"


# remove .la files. We don't need them, because we use dlopen, not libltdl.
# If we ever switch to libltdl (to support dynamic loading on OSX, perhaps)
# remove this hook.
install-exec-hook:
	find $(DESTDIR)$(pkglibdir) -type f -name \*.la -delete


