
.PHONY: all print clean distclean install 

TARGETS := abelson.pdf animate_derivations.pdf automata-mutualind.pdf \
	discrete_math_review.pdf mutualind.pdf pgmsasautomata.pdf \
	post.pdf post_animate.pdf sampleRTderivation.pdf set_seq_strings.pdf \
	strongind.pdf logicoverview.pdf whyproplogic.pdf pl_syntax_semantics.pdf \
        decisionproc.pdf folpolicies.pdf fol_syntax_semantics.pdf \
        fol_sat_val.pdf fol_functions_pcnf.pdf fol_comp_dec.pdf \
        whytemporallogic.pdf ptl_syntax_semantics.pdf \
        tptl.pdf relations_functions.pdf pl_sat_val.pdf
       


#posts :=$(latex:%.pdf=%.ps)

print: LATEXOPTS := -latex='latex %O -interaction=nonstopmode -synctex=1 "\PassOptionsToClass{mode=print}{powerdot}\input{%S}"'
print: $(TARGETS)

all: LATEXOPTS :=
all: $(TARGETS)

%.pdf: %.ps
	ps2pdf $<


%.ps: %.dvi
	dvips $<

%.dvi: %.tex 
	latexmk -use-make $(LATEXOPTS) $<

install: 
	cp $(TARGETS) ~/google_drive/NPS/teaching/2019/CS3001/slides/

clean: 
	latexmk -c && rm *.bm && rm *.vrb

distclean: 
	latexmk -C && rm *.bm && rm *.vrb
