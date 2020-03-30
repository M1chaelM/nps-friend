
.PHONY: all print clean distclean install

REV_PRES  := discrete_math_review.pdf
SAP_PRES  := sap_part_1.pdf sap_part_2.pdf 
LONE_PRES := logicoverview.pdf decisionproc.pdf animate_derivations.pdf sampleRTderivation.pdf

PL_PRES   := pl_part_1.pdf pl_part_2.pdf
FOL_PRES  := fol_part_1.pdf fol_part_2.pdf
PTL_PRES  := ptl.pdf 

REV_PRINT := $(REV_PRES:%.pdf=printable/%.pdf)
SAP_PRINT := $(SAP_PRES:%.pdf=printable/%.pdf)
LONE_PRINT := $(LONE_PRES:%.pdf=printable/%.pdf) 

PL_PRINT  := $(PL_PRES:%.pdf=printable/%.pdf)
FOL_PRINT := $(FOL_PRES:%.pdf=printable/%.pdf)
PTL_PRINT := $(PTL_PRES:%.pdf=printable/%.pdf) 

SAP_TARGETS := $(SAP_PRINT) $(SAP_PRES)
PL_TARGETS := $(PL_PRINT) $(PL_PRES)
FOL_TARGETS := $(FOL_PRINT) $(FOL_PRES)
PTL_TARGETS := $(PTL_PRINT) $(PTL_PRES)

PRES := $(REV_PRES) $(SAP_PRES) $(LONE_PRES) $(PL_PRES) $(FOL_PRES) $(PTL_PRES) 
PRINTVERS := $(REV_PRINT) $(SAP_PRINT) $(LONE_PRINT) $(PL_PRINT) $(FOL_PRINT) $(PTL_PRINT) 

INSTALL_DIR := ~/google_drive/NPS/teaching/2020/CS3001_Q3/slides/

PRINTLATEXOPTS := -latex='latex %O -interaction=nonstopmode -synctex=1 "\PassOptionsToClass{mode=print}{powerdot}\input{%S}"'

all: $(PRES) $(PRINTVERS) 

presentations: $(PRES)

print: $(PRINTVERS) 

$(REV_TARGETS): $(wildcard rev_content/*.tex)

$(SAP_TARGETS): $(wildcard sap_content/*.tex)

$(PL_TARGETS): $(wildcard pl_content/*.tex)

$(FOL_TARGETS): $(wildcard fol_content/*.tex)

$(PTL_TARGETS): $(wildcard ptl_content/*.tex)

%.pdf: %.ps
	ps2pdf $< $@

%.ps: %.dvi
	dvips $< -o $@

printable/%.dvi: %.tex 
	@mkdir -p $(@D)
	latexmk -use-make -outdir=printable $(PRINTLATEXOPTS) $<

%.dvi: %.tex 
	latexmk -interaction=nonstopmode -use-make $<

install: 
	cp $(PRES) $(INSTALL_DIR) 
	if [ -d "printable" ]; then mkdir -p $(INSTALL_DIR)/printable && cp $(PRINTVERS) $(INSTALL_DIR)/printable; fi

clean: 
	latexmk -c && rm -f *.bm *.vrb *.gz 
	if [ -d "printable" ]; then latexmk -c -outdir=printable && rm -f printable/*.bm printable/*.vrb printable/*.gz; fi

distclean: 
	latexmk -C && rm -f *.bm *.vrb *.gz
	if [ -d "printable" ]; then latexmk -C -outdir=printable && rm -f printable/*.bm printable/*.vrb printable*.gz/*.gz && rmdir printable; fi
