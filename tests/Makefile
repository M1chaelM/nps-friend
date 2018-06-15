
.PHONY: all clean install 

TARGETS := quiz1.pdf quiz2.pdf quiz3.pdf quiz4.pdf quiz5.pdf exam1.pdf exam2.pdf exam3.pdf


all: $(TARGETS)

%.pdf: %.tex
	latexmk -pdf -pdflatex="pdflatex -interaction=nonstopmode" -use-make $<

install: 
	cp $(TARGETS) ~/google_drive/NPS/teaching/2018/CS3920/labs/


clean: 
	latexmk -C
