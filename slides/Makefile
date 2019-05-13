
.PHONY: all print clean distclean install 

TARGETS := abelson.pdf animate_derivations.pdf automata-mutualind.pdf \
	discrete_math_review.pdf mutualind.pdf pgmsasautomata.pdf \
	post.pdf sampleRTderivation.pdf set_seq_strings.pdf \
	strongind.pdf logicoverview.pdf whyproplogic.pdf pl_syntax_semantics.pdf \
        decisionproc.pdf fol_part_1.pdf fol_part_2.pdf \
        whytemporallogic.pdf ptl_syntax_semantics.pdf \
        tptl.pdf relations_functions.pdf pl_sat_val.pdf resolution.pdf

PRINTVERS := $(TARGETS:%.pdf=printable/%.pdf)

INSTALL_DIR := ~/google_drive/NPS/teaching/2019/CS3001/slides/

all: $(TARGETS) $(PRINTVERS) 

presentations: $(TARGETS)

print: $(PRINTVERS) 

%.pdf: %.ps
	ps2pdf $< $@

%.ps: %.dvi
	dvips $< -o $@

printable/%.dvi: LATEXOPTS := -latex='latex %O -interaction=nonstopmode -synctex=1 "\PassOptionsToClass{mode=print}{powerdot}\input{%S}"'
printable/%.dvi: %.tex 
	@mkdir -p $(@D)
	latexmk -use-make -outdir=printable $(LATEXOPTS) $<

%.dvi: LATEXOPTS :=
%.dvi: %.tex 
	latexmk -use-make $(LATEXOPTS) $<

install: 
	cp $(TARGETS) $(INSTALL_DIR) 
	if [ -d "printable" ]; then mkdir -p $(INSTALL_DIR)/printable && cp $(PRINTVERS) $(INSTALL_DIR)/printable; fi

clean: 
	latexmk -c && rm -f *.bm *.vrb *.gz 
	if [ -d "printable" ]; then latexmk -c -outdir=printable && rm -f printable/*.bm printable/*.vrb printable/*.gz; fi

distclean: 
	latexmk -C && rm -f *.bm *.vrb *.gz
	if [ -d "printable" ]; then latexmk -C -outdir=printable && rm -f printable/*.bm printable/*.vrb printable*.gz/*.gz && rmdir printable; fi
