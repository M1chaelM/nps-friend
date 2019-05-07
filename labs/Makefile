
.PHONY: all solutions problems clean distclean install 

TARGETS := lab1.pdf lab2.pdf lab3.pdf lab4.pdf lab5.pdf \
	lab6.pdf lab7.pdf lab8.pdf lab9.pdf lab10.pdf \
        lab5_extra.pdf lab6_extra.pdf

SOLS := $(TARGETS:%.pdf=%_solutions.pdf)

all: $(SOLS) $(TARGETS) 

problems: $(TARGETS)

solutions: $(SOLS)

%.pdf: PDFLATEXOPTS := -pdflatex='pdflatex -interaction=nonstopmode -shell-escape'
%.pdf: %.tex
	latexmk -pdf $(PDFLATEXOPTS) -use-make $<

%_solutions.pdf: PDFLATEXOPTS := -pdflatex='pdflatex %O -interaction=nonstopmode -synctex=1 -shell-escape "\PassOptionsToClass{answers}{exam}\input{%S}"'
%_solutions.pdf: %.tex
	latexmk -pdf $(PDFLATEXOPTS) -use-make $< && mv $*.pdf $*_solutions.pdf

install: 
	cp $(TARGETS) $(SOLS) ~/google_drive/NPS/teaching/2019/CS3001/labs/

clean: 
	latexmk -c

distclean: 
	latexmk -C

