# Makefile for smoothgestures.

VERSION=0.15.9
JAVA=java 
COMPILER=-jar bin/compiler.jar
COMPILER_FLAGS=--warning_level QUIET

JS_FILES=background.js bsync.scrypt.b64.ls.js define.js helpers.js options.js popup.js translate.js background_pn.js contentscript.js gestures.js jquery.min.js pluginstorage.js status.js
MANIFEST_FILE=manifest.json

SRC_DIR=src
OUTPUT_DIR=package
JS_INPUT_DIR=jso
JS_OUTPUT_DIR=js

all: clean compile_js create_package

compile_js: $(JS_FILES)

%.js:
	$(JAVA) $(COMPILER) $(COMPILER_FLAGS) --js $(JS_INPUT_DIR)/$@ --js_output_file $(OUTPUT_DIR)/$(JS_OUTPUT_DIR)/$@

clean:
	@echo
	@echo -------------------------
	@echo Cleaning up the old files
	@echo -------------------------
	@echo
	rm -f $(OUTPUT_DIR)/$(JS_OUTPUT_DIR)/*
	rm -f $(OUTPUT_DIR)/$(MANIFEST_FILE)
	rm -f $(VERSION).zip
	rm -f smoothgestures-$(VERSION).crx

create_package:
	@echo --------------------
	@echo Creating new package
	@echo --------------------
	sed "s/SMOOTHGESTURE_VERSION/$(VERSION)/" > $(OUTPUT_DIR)/$(MANIFEST_FILE) < $(SRC_DIR)/$(MANIFEST_FILE)
	cd package; zip -r ../$(VERSION).zip *; cd -
	mv $(VERSION).zip smoothgestures-$(VERSION).crx

