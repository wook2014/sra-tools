# ===========================================================================
#
#                            PUBLIC DOMAIN NOTICE
#               National Center for Biotechnology Information
#
#  This software/database is a "United States Government Work" under the
#  terms of the United States Copyright Act.  It was written as part of
#  the author's official duties as a United States Government employee and
#  thus cannot be copyrighted.  This software/database is freely available
#  to the public for use. The National Library of Medicine and the U.S.
#  Government have not placed any restriction on its use or reproduction.
#
#  Although all reasonable efforts have been taken to ensure the accuracy
#  and reliability of the software and data, the NLM and the U.S.
#  Government do not and cannot warrant the performance or results that
#  may be obtained by using this software or data. The NLM and the U.S.
#  Government disclaim all warranties, express or implied, including
#  warranties of performance, merchantability or fitness for any particular
#  purpose.
#
#  Please cite the author in any work or product based on this material.
#
# ===========================================================================


default: std

TOP ?= $(abspath ../..)

MODULE = tools/ngs-pileup

INT_TOOLS = \
	ngs-pileup \

EXT_TOOLS = \

ALL_TOOLS = \
	$(INT_TOOLS) \
	$(EXT_TOOLS)

include $(TOP)/build/Makefile.env

#-------------------------------------------------------------------------------
# outer targets
#
all std: makedirs
	@ $(MAKE_CMD) $(TARGDIR)/$@-cmn

$(ALL_TOOLS): makedirs
	@ $(MAKE_CMD) $(BINDIR)/$@

.PHONY: all std $(ALL_TOOLS)

#-------------------------------------------------------------------------------
# clean
#
clean: stdclean

.PHONY: clean

#-------------------------------------------------------------------------------
# ngs-pileup
#
NGS_PILEUP_SRC = \
	ngs-pileup    \
	main \

INCDIRS += -I $(TOP)/ngs/ngs-c++

NGS_PILEUP_OBJ = \
	$(addsuffix .$(OBJX),$(NGS_PILEUP_SRC))

NGS_PILEUP_LIBS = \
	-sncbi-ngs-c++    \
	-sngs-c++         \
	-sngs         \
	-sncbi-vdb-static \
	-skapp \
	-stk-version \

$(BINDIR)/ngs-pileup: $(NGS_PILEUP_OBJ)
	$(LP) --exe --vers $(SRCDIR)/../../shared/toolkit.vers -o $@ $^ $(NGS_PILEUP_LIBS)

