# Copyright IBM Corp. All Rights Reserved.
#
# SPDX-License-Identifier: Apache-2.0

TOP = ..
include $(TOP)/build.mk

LD_LIBRARY_PATH := LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:./enclave/lib
SRC := tlcc.go
OUTPUT := tlcc.so

$(OUTPUT): $(SRC)
	$(GO) get github.com/spf13/viper
	$(LD_LIBRARY_PATH) $(GO) build -o $@ -buildmode=plugin $<

build: $(OUTPUT)

test: build
	$(ENV_VARS) $(GO) $@ -test.v

clean:
	$(GO) clean
	rm -rf ledgersData
