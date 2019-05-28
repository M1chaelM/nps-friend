
.PHONY: all print clean distclean install

FOL_TARGETS := fol_part_1.pdf fol_part_2.pdf
PTL_TARGETS := ptl.pdf 

TARGETS := discrete_math_review.pdf relations_functions.pdf set_seq_strings.pdf \
	post.pdf animate_derivations.pdf strongind.pdf mutualind.pdf \
	pgmsasautomata.pdf automata-mutualind.pdf sampleRTderivation.pdf  \
	logicoverview.pdf whyproplogic.pdf pl_syntax_semantics.pdf pl_sat_val.pdf \
	decisionproc.pdf resolution.pdf $(FOL_TARGETS) $(PTL_TARGETS) 

PRINTVERS := $(TARGETS:%.pdf=printable/%.pdf)

INSTALL_DIR := ~/google_drive/NPS/teaching/2019/CS3001/slides/

PRINTLATEXOPTS := -latex='latex %O -interaction=nonstopmode -synctex=1 "\PassOptionsToClass{mode=print}{powerdot}\input{%S}"'

all: $(TARGETS) $(PRINTVERS) 

presentations: $(TARGETS)

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
	cp $(TARGETS) $(INSTALL_DIR) 
	if [ -d "printable" ]; then mkdir -p $(INSTALL_DIR)/printable && cp $(PRINTVERS) $(INSTALL_DIR)/printable; fi

clean: 
	latexmk -c && rm -f *.bm *.vrb *.gz 
	if [ -d "printable" ]; then latexmk -c -outdir=printable && rm -f printable/*.bm printable/*.vrb printable/*.gz; fi

distclean: 
	latexmk -C && rm -f *.bm *.vrb *.gz
	if [ -d "printable" ]; then latexmk -C -outdir=printable && rm -f printable/*.bm printable/*.vrb printable*.gz/*.gz && rmdir printable; fi
