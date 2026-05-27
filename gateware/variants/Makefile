
all:
	$(MAKE) -C hl2b2_main
	$(MAKE) -C hl2b3to4_main
	$(MAKE) -C hl2b3to4_cicrx
	$(MAKE) -C hl2b5up_main
	$(MAKE) -C hl2b5up_6rx
	$(MAKE) -C hl2b5up_cicrx
	$(MAKE) -C hl2b5up_15ce
	$(MAKE) -C hl2b5up_ak4951v3

release:
	$(MAKE) -C hl2b2_main
	$(MAKE) -C hl2b3to4_main
	$(MAKE) -C hl2b3to4_cicrx
	$(MAKE) -C hl2b5up_main
	$(MAKE) -C hl2b5up_6rx
	$(MAKE) -C hl2b5up_cicrx
	python3 release.py

git_status:
	@git diff --ignore-matching-lines=LAST_QUARTUS_VERSION --exit-code >/dev/null || (echo You have unstaged changes && exit 1)
	@git diff --ignore-matching-lines=LAST_QUARTUS_VERSION --cached --exit-code >/dev/null || (echo You have staged but uncommitted changes && exit 1)
	@echo git status is clean

release_test: git_status release
	date=`date "+%Y%m%d"`; \
	gitrev=`git rev-parse --short HEAD`; \
	eval `sed -n 's/localparam.*VERSION_/VERSION_/p' ../rtl/hermeslite_core.v |sed 's/ =.* 8.d/=/'`; \
	dirname=../bitfiles/testing/"$${date}_$${VERSION_MAJOR}p$${VERSION_MINOR}_$${gitrev}"; \
	rm -rf $$dirname && mkdir $$dirname && \
	(cd release; tar cf - */*.rbf */*/*.rbf) | tar xf - -C $$dirname

clean:
	$(MAKE) -C hl2b2_main clean
	$(MAKE) -C hl2b3to4_main clean
	$(MAKE) -C hl2b3to4_cicrx clean
	$(MAKE) -C hl2b5up_main clean
	$(MAKE) -C hl2b5up_6rx clean
	$(MAKE) -C hl2b5up_cicrx clean
	$(MAKE) -C hl2b5up_15ce clean
	$(MAKE) -C hl2b5up_ak4951v3 clean

realclean:
	$(MAKE) -C hl2b2_main realclean
	$(MAKE) -C hl2b3to4_main realclean
	$(MAKE) -C hl2b3to4_cicrx realclean
	$(MAKE) -C hl2b5up_main realclean
	$(MAKE) -C hl2b5up_6rx realclean
	$(MAKE) -C hl2b5up_cicrx realclean
	$(MAKE) -C hl2b5up_15ce realclean
	$(MAKE) -C hl2b5up_ak4951v3 realclean


.PHONY: all clean realclean release
