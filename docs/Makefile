
.PHONY: all clean distclean install 

TARGETS := induction.pdf mutexproof.pdf 

all: $(TARGETS)

%.pdf: %.tex
	latexmk -pdf -pdflatex="pdflatex -interaction=nonstopmode -shell-escape" -use-make $<

install: 
	cp $(TARGETS) ~/google_drive/NPS/teaching/2019/CS3001/labs/


clean: 
	latexmk -c

distclean: 
	latexmk -C
