#
#    Copyright (c) 2020 Project CHIP Authors
#    All rights reserved.
#
#    Licensed under the Apache License, Version 2.0 (the "License");
#    you may not use this file except in compliance with the License.
#    You may obtain a copy of the License at
#
#        http://www.apache.org/licenses/LICENSE-2.0
#
#    Unless required by applicable law or agreed to in writing, software
#    distributed under the License is distributed on an "AS IS" BASIS,
#    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
#    See the License for the specific language governing permissions and
#    limitations under the License.

#
# This is a project Makefile. It is assumed the directory this Makefile resides in is a
# project subdirectory.
#

include $(MAKE_INCLUDE_GEN)

.PHONY: all clean

#*****************************************************************************#
#                               VARIABLES	                              #
#*****************************************************************************#
OUTPUT_DIR = $(CHIPDIR)/examples/thermostat/ameba/build/chip
CODEGEN_DIR = $(OUTPUT_DIR)/codegen

DIR = $(SRCDIR)
DIR += $(CHIPDIR)/src/app
DIR += $(CHIPDIR)/src/app/server
DIR += $(CHIPDIR)/src/lib/dnssd/minimal_mdns/responders
DIR += $(CHIPDIR)/examples/thermostat/thermostat-common
DIR += $(CHIPDIR)/examples/thermostat/ameba/main
DIR += $(CHIPDIR)/examples/platform/ameba/ota
DIR += $(CHIPDIR)/examples/platform/ameba/route_hook
DIR += $(CHIPDIR)/examples/providers
DIR += $(CHIPDIR)/zzz_generated/thermostat/zap-generated
DIR += $(CHIPDIR)/zzz_generated/app-common/app-common/zap-generated
DIR += $(CHIPDIR)/zzz_generated/app-common/app-common/zap-generated/attributes
DIR += $(BASEDIR)/component/common/application/matter/api
DIR += $(BASEDIR)/component/common/application/matter/core
DIR += $(BASEDIR)/component/common/application/matter/driver
DIR += $(BASEDIR)/component/common/application/matter/example/thermostat
DIR += $(BASEDIR)/tools/matter/codegen_helpers/gen/app
DIR += $(CODEGEN_DIR)/app
DIR += $(CODEGEN_DIR)/zap-generated

vpath %.cpp $(DIR) $(shell find $(DIR) -type d)
vpath %.c $(DIR) $(shell find $(DIR) -type d)
#*****************************************************************************#
#                               CFLAGS                                        #
#*****************************************************************************#

GLOBAL_CFLAGS += -DCHIP_PROJECT=1
GLOBAL_CFLAGS += -DCHIP_ADDRESS_RESOLVE_IMPL_INCLUDE_HEADER=\"lib/address_resolve/AddressResolve_DefaultImpl.h\"

#*****************************************************************************#
#                               Include FILE LIST                             #
#*****************************************************************************#
IFLAGS += -I$(BASEDIR)/component/common/application/matter/api
IFLAGS += -I$(BASEDIR)/component/common/application/matter/common/bluetooth/bt_matter_adapter
IFLAGS += -I$(BASEDIR)/component/common/application/matter/common/mbedtls
IFLAGS += -I$(BASEDIR)/component/common/application/matter/common/port
IFLAGS += -I$(BASEDIR)/component/common/application/matter/core
IFLAGS += -I$(BASEDIR)/component/common/application/matter/driver
IFLAGS += -I$(BASEDIR)/component/common/application/matter/example/thermostat

#IFLAGS = -I$(DIR)./
IFLAGS += -I$(CHIPDIR)/zzz_generated
IFLAGS += -I$(CHIPDIR)/zzz_generated/app-common
IFLAGS += -I$(CHIPDIR)/zzz_generated/thermostat
IFLAGS += -I$(CHIPDIR)/zzz_generated/thermostat/zap-generated
IFLAGS += -I$(CHIPDIR)/examples/thermostat/thermostat-common
IFLAGS += -I$(CHIPDIR)/examples/thermostat/ameba/main/include
IFLAGS += -I$(CHIPDIR)/examples/thermostat/ameba/build/chip/gen/include
IFLAGS += -I$(CHIPDIR)/examples/platform/ameba
IFLAGS += -I$(CHIPDIR)/examples/providers
IFLAGS += -I$(CHIPDIR)/src/include/
IFLAGS += -I$(CHIPDIR)/src/lib/
IFLAGS += -I$(CHIPDIR)/src/
IFLAGS += -I$(CHIPDIR)/third_party/nlassert/repo/include/
IFLAGS += -I$(CHIPDIR)/src/app/
IFLAGS += -I$(CHIPDIR)/src/app/util/
IFLAGS += -I$(CHIPDIR)/src/app/server/
IFLAGS += -I$(CHIPDIR)/src/controller/data_model
IFLAGS += -I$(CHIPDIR)/third_party/nlio/repo/include/
IFLAGS += -I$(CHIPDIR)/third_party/nlunit-test/repo/src
IFLAGS += -I$(CODEGEN_DIR)

#*****************************************************************************#
#                               Source FILE LIST                              #
#*****************************************************************************#

CPPSRC += $(CHIPDIR)/src/app/server/AclStorage.cpp
CPPSRC += $(CHIPDIR)/src/app/server/DefaultAclStorage.cpp
CPPSRC += $(CHIPDIR)/src/app/server/Server.cpp
CPPSRC += $(CHIPDIR)/src/app/server/Dnssd.cpp
CPPSRC += $(CHIPDIR)/src/app/server/EchoHandler.cpp
CPPSRC += $(CHIPDIR)/src/app/server/OnboardingCodesUtil.cpp
CPPSRC += $(CHIPDIR)/src/app/server/CommissioningWindowManager.cpp

CPPSRC += $(CHIPDIR)/src/app/util/attribute-storage.cpp
CPPSRC += $(CHIPDIR)/src/app/util/attribute-table.cpp
CPPSRC += $(CHIPDIR)/src/app/util/attribute-size-util.cpp
CPPSRC += $(CHIPDIR)/src/app/util/binding-table.cpp
CPPSRC += $(CHIPDIR)/src/app/util/IcdMonitoringTable.cpp
CPPSRC += $(CHIPDIR)/src/app/util/DataModelHandler.cpp
CPPSRC += $(CHIPDIR)/src/app/util/ember-compatibility-functions.cpp
CPPSRC += $(CHIPDIR)/src/app/util/generic-callback-stubs.cpp
CPPSRC += $(CHIPDIR)/src/app/util/message.cpp
CPPSRC += $(CHIPDIR)/src/app/util/util.cpp
CPPSRC += $(CHIPDIR)/src/app/util/error-mapping.cpp
CPPSRC += $(CHIPDIR)/src/app/util/privilege-storage.cpp

CPPSRC += $(shell cat $(CODEGEN_DIR)/cluster-file.txt)

CPPSRC += $(CODEGEN_DIR)/app/callback-stub.cpp
CPPSRC += $(CODEGEN_DIR)/zap-generated/IMClusterCommandHandler.cpp

CPPSRC += $(CHIPDIR)/src/app/reporting/Engine.cpp

CPPSRC += $(CHIPDIR)/src/lib/dnssd/minimal_mdns/responders/IP.cpp

CPPSRC += $(CHIPDIR)/zzz_generated/app-common/app-common/zap-generated/attributes/Accessors.cpp

CPPSRC += $(CHIPDIR)/examples/providers/DeviceInfoProviderImpl.cpp

CSRC += $(CHIPDIR)/examples/platform/ameba/route_hook/ameba_route_hook.c
CSRC += $(CHIPDIR)/examples/platform/ameba/route_hook/ameba_route_table.c

# Custom thermostat-app src files with porting layer
CPPSRC += $(BASEDIR)/component/common/application/matter/api/matter_api.cpp
CPPSRC += $(BASEDIR)/component/common/application/matter/core/matter_core.cpp
CPPSRC += $(BASEDIR)/component/common/application/matter/core/matter_interaction.cpp
CPPSRC += $(BASEDIR)/component/common/application/matter/core/matter_ota_initializer.cpp
CPPSRC += $(BASEDIR)/component/common/application/matter/driver/thermostat.cpp
CPPSRC += $(BASEDIR)/component/common/application/matter/driver/thermostat_ui.cpp
CPPSRC += $(BASEDIR)/component/common/application/matter/example/thermostat/example_matter_thermostat.cpp
CPPSRC += $(BASEDIR)/component/common/application/matter/example/thermostat/matter_drivers.cpp

#*****************************************************************************#
#                               Object FILE LIST                              #
#*****************************************************************************#
CPPOBJS = $(notdir $(CPPSRC:.cpp=.o))
COBJS = $(notdir $(CSRC:.c=.o))
OBJS = $(CPPOBJS)
OBJS += $(COBJS)
STATIC_LIB = lib_main.a

#*****************************************************************************#
#                               Include Dependency                            #
#*****************************************************************************#
-include $(OBJS:.o=.d)


#*****************************************************************************#
#                        RULES TO GENERATE TARGETS                            #
#*****************************************************************************#

# Define the Rules to build the core targets
all: CORE_TARGETS

#*****************************************************************************#
#              GENERATE OBJECT FILE
#*****************************************************************************#
#CORE_TARGETS:	$(CPPOBJS) $(COBJS)
CORE_TARGETS:	$(OBJS) $(STATIC_LIB)
$(STATIC_LIB):$(OBJS)
	$(AR) rvs $@ $^
	$(MOVE) -f $@ $(ROOTDIR)/lib/application

#*****************************************************************************#
#              CLEAN GENERATED FILES                                          #
#*****************************************************************************#
clean:
	rm -f $(ROOTDIR)/make/chip_main/thermostat_port/*.o
	rm -f $(ROOTDIR)/make/chip_main/thermostat_port/*.i
	rm -f $(ROOTDIR)/make/chip_main/thermostat_port/*.s
	rm -f $(ROOTDIR)/make/chip_main/thermostat_port/*.d
	rm -f $(ROOTDIR)/make/chip_main/thermostat_port/*.ii
	rm -f $(ROOTDIR)/make/chip_main/thermostat_port/*.su

-include $(DEPS)
