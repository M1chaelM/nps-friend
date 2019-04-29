
.PHONY: all clean distclean install 

TARGETS := quiz1.pdf quiz2.pdf quiz3.pdf quiz4.pdf quiz5.pdf exam1.pdf exam2.pdf \
	exam3.pdf ec_quiz1.pdf 


all: $(TARGETS)

%.pdf: %.tex
	latexmk -pdf -pdflatex="pdflatex -interaction=nonstopmode" -use-make $<

install: 
	cp $(TARGETS) ~/google_drive/NPS/teaching/2019/CS3001/tests/


clean: 
	latexmk -c

distclean: 
	latexmk -C
