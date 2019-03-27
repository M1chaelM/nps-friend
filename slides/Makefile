
.PHONY: all clean distclean install 

TARGETS := abelson.pdf animate_derivations.pdf automata-mutualind.pdf \
	discrete_math_review.pdf mutualind.pdf pgmsasautomata.pdf \
	post.pdf post_animate.pdf sampleRTderivation.pdf set_seq_strings.pdf \
	strongind.pdf logicoverview.pdf whyproplogic.pdf pl_syntax_semantics.pdf \
        decisionproc.pdf folpolicies.pdf fol_syntax_semantics.pdf \
        fol_sat_val.pdf fol_functions_pcnf.pdf fol_comp_dec.pdf \
        whytemporallogic.pdf ptl_syntax_semantics.pdf \
        tptl.pdf 
       


#posts :=$(latex:%.pdf=%.ps)


all: $(TARGETS)

%.pdf: %.ps
	ps2pdf $<


%.ps: %.dvi
	dvips $<

%.dvi: %.tex 
	latexmk -use-make $<

install: 
	cp $(TARGETS) ~/google_drive/NPS/teaching/2018/CS3920/new_slides/

clean: 
	latexmk -c && rm *.bm && rm *.vrb

distclean: 
	latexmk -C && rm *.bm && rm *.vrb
