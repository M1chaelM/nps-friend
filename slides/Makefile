
.PHONY: all print clean distclean install

REV_PRES  := discrete_math_review.pdf relations_functions.pdf set_seq_strings.pdf
IND_PRES  := post.pdf animate_derivations.pdf strongind.pdf mutualind.pdf \
             pgmsasautomata.pdf automata-mutualind.pdf sampleRTderivation.pdf
MSC_PRES  := logicoverview.pdf decisionproc.pdf
PL_PRES   := whyproplogic.pdf pl_syntax_semantics.pdf pl_sat_val.pdf resolution.pdf
FOL_PRES  := fol_part_1.pdf fol_part_2.pdf
PTL_PRES  := ptl.pdf 

REV_PRINT := $(REV_PRES:%.pdf=printable/%.pdf)
IND_PRINT := $(IND_PRES:%.pdf=printable/%.pdf)
MSC_PRINT := $(MSC_PRES:%.pdf=printable/%.pdf) 
PL_PRINT  := $(PL_PRES:%.pdf=printable/%.pdf)
FOL_PRINT := $(FOL_PRES:%.pdf=printable/%.pdf)
PTL_PRINT := $(PTL_PRES:%.pdf=printable/%.pdf) 


FOL_TARGETS := $(FOL_PRINT) $(FOL_PRES)
PTL_TARGETS := $(PTL_PRINT) $(PTL_PRES)

PRES := $(REV_PRES) $(IND_PRES) $(MSC_PRES) $(PL_PRES) $(FOL_PRES) $(PTL_PRES) 
PRINTVERS := $(REV_PRINT) $(IND_PRINT) $(MSC_PRINT) $(PL_PRINT) $(FOL_PRINT) $(PTL_PRINT) 

INSTALL_DIR := ~/google_drive/NPS/teaching/2019/CS3001/slides/

PRINTLATEXOPTS := -latex='latex %O -interaction=nonstopmode -synctex=1 "\PassOptionsToClass{mode=print}{powerdot}\input{%S}"'

all: $(PRES) $(PRINTVERS) 

presentations: $(PRES)

print: $(PRINTVERS) 

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
