#******************************************************************************
#
# Makefile - Generic makefile for building the template project.
#
# Copyright (c) 2012-2014 Texas Instruments Incorporated.  All rights reserved.
# Software License Agreement
#
# Texas Instruments (TI) is supplying this software for use solely and
# exclusively on TI's microcontroller products. The software is owned by
# TI and/or its suppliers, and is protected under applicable copyright
# laws. You may not combine this software with "viral" open-source
# software in order to form a larger program.
#
# THIS SOFTWARE IS PROVIDED "AS IS" AND WITH ALL FAULTS.
# NO WARRANTIES, WHETHER EXPRESS, IMPLIED OR STATUTORY, INCLUDING, BUT
# NOT LIMITED TO, IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
# A PARTICULAR PURPOSE APPLY TO THIS SOFTWARE. TI SHALL NOT, UNDER ANY
# CIRCUMSTANCES, BE LIABLE FOR SPECIAL, INCIDENTAL, OR CONSEQUENTIAL
# DAMAGES, FOR ANY REASON WHATSOEVER.
#
# This is part of revision 2.1.0.12573 of the EK-TM4C123GXL Firmware Package.
#
# Updated: 2014-04-06 to be used in the CodeBlocks template.
#                     Still generic as to what compiler it can use
#
#******************************************************************************

#
# Defines the part type that this project uses.
#
PART=TM4C123GH6PM

#
# The base directory for TivaWare.
# If you have placed the Tiva libraries somewhere else you need to change this
#
ROOT=/opt/tiva

#
# The project name, you need to change this to your own name
#
PROJECT=template

#
# Include the common make definitions.
#
include ${ROOT}/makedefs

#
# Where to find files that do not live in the source root directory.
#
#
IPATH=${ROOT}

#
# If you need to specify external build dependencies this should be done here
#
VPATH=src

#
# Define any build specific flags here
#
CFLAGS += -g

.PHONY: all
.DEFAULT: all
#
# The default rule, which causes the template to be built.
#
Debug: all
Release: all

all: ${COMPILER}
all: ${COMPILER}/${PROJECT}.axf

#
# Rules to clean out all the build products.
#
cleanDebug:
	@rm -rf ${COMPILER} ${wildcard *~}

cleanRelease:
	@rm -rf ${COMPILER} ${wildcard *~}

#
# The rule to create the target directory.
#
${COMPILER}:
	@mkdir -p ${COMPILER}

#
# Rules for building the blinky example.
#
${COMPILER}/${PROJECT}.axf: ${COMPILER}/main.o
${COMPILER}/${PROJECT}.axf: ${COMPILER}/startup_${COMPILER}.o
${COMPILER}/${PROJECT}.axf: linker.ld
SCATTERgcc_${PROJECT}=linker.ld
ENTRY_${PROJECT}=ResetISR

#
# Include the automatically generated dependency files.
#
ifneq (${MAKECMDGOALS},clean)
-include ${wildcard ${COMPILER}/*.d} __dummy__
endif
