PROJECT      = max_min_algorithms.gpr
CHAPTER_NAME = maxmin

# timeout for chapter
MAX_MIN_DEFAULT_TIMEOUT = "TIMEOUT=5"

# all proof targets
ALL_PROOF_TARGET = max_element_wo_ghost max_element max_seq min_element

# specification dependencies for each function
SPEC_TYPES       		= ../spec/types.ads
SPEC_MAX_ELEMENT_WO_GHOST 	= $(SPEC_TYPES)
SPEC_MAX_ELEMENT	 	= $(SPEC_TYPES) ../spec/upper_bound_p.ads
SPEC_MIN_ELEMENT 		= $(SPEC_TYPES)
SPEC_MAX_SEQ 			= $(SPEC_MAX_ELEMENT) ../spec/has_value_p.ads $(call GENERATE_DEP, max_element)

# proof level for each function
LEVEL_MAX_ELEMENT            = 0
LEVEL_MAX_ELEMENT_WO_GHOST   = 0
LEVEL_MIN_ELEMENT            = 0
LEVEL_MAX_SEQ	             = 0

include ../Makefile-common

.PHONY: $(ALL_PROOF_TARGETS)

# Max_Element_WO_Ghost
max_element_wo_ghost: $(call GENERATE_DEP, max_element_wo_ghost) $(SPEC_MAX_ELEMENT_WO_GHOST)
	make prove FILE=$@_p.adb LEVEL=$(LEVEL_MAX_ELEMENT_WO_GHOST) $(MAX_MIN_DEFAULT_TIMEOUT)

# Max_Element
max_element: $(call GENERATE_DEP, max_element) $(SPEC_MAX_ELEMENT)
	make prove FILE=$@_p.adb LEVEL=$(LEVEL_MAX_ELEMENT) $(MAX_MIN_DEFAUT_TIMEOUT)

# Max_Seq
max_seq: $(call GENERATE_DEP, max_seq) $(SPEC_MAX_SEQ)
	make prove FILE=$@_p.adb LEVEL=$(LEVEL_MAX_SEQ) $(MAX_MIN_DEFAULT_TIMEOUT)

# Min_Element
min_element: $(call GENERATE_DEP, min_element) $(SPEC_MIN_ELEMENT)
	make prove FILE=$@_p.adb LEVEL=$(LEVEL_MIN_ELEMENT) $(MAX_MIN_DEFAULT_TIMEOUT)

# all proofs
all: $(ALL_PROOF_TARGET)
	$(_STATS_CHAPTER)
