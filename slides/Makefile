
.PHONY: all clean install 

TARGETS := abelson.pdf animate_derivations.pdf automata-mutualind.pdf \
	discrete_math_review.pdf mutualind.pdf pgmsasautomata.pdf \
	post.pdf post_animate.pdf sampleRTderivation.pdf strings_sets.pdf \
	strongind.pdf logicoverview.pdf whyproplogic.pdf pl_syntax_semantics.pdf \
       


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
	latexmk -C
