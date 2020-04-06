
.PHONY: all solutions problems clean distclean install 

TARGETS := lab1.pdf lab2.pdf lab3.pdf lab4.pdf lab5.pdf \
	lab6.pdf lab7.pdf lab8.pdf lab9.pdf lab10.pdf \
        lab5_extra.pdf lab6_extra.pdf

SOLS   := $(TARGETS:%.pdf=solutions/%.pdf)

INSTALL_DIR := ~/google_drive/NPS/teaching/2020/CS3001_Q3/labs/

all: $(SOLS) $(TARGETS) 

problems: $(TARGETS)

solutions: $(SOLS)

%.pdf: PDFLATEXOPTS := -pdflatex='pdflatex -interaction=nonstopmode -shell-escape'
%.pdf: %.tex
	@mkdir -p $(@D)
	latexmk -pdf $(PDFLATEXOPTS) -use-make $<

solutions/%.pdf: PDFLATEXOPTS := -pdflatex='pdflatex %O -interaction=nonstopmode -synctex=1 -shell-escape "\PassOptionsToClass{answers}{exam}\input{%S}"'
solutions/%.pdf: %.tex
	@mkdir -p $(@D)
	latexmk -pdf $(PDFLATEXOPTS) -outdir=solutions -use-make $< 

install: 
	cp $(TARGETS) $(INSTALL_DIR)
	if [ -d "solutions" ]; then mkdir -p $(INSTALL_DIR)/solutions && cp $(SOLS) $(INSTALL_DIR)/solutions; fi

clean: 
	latexmk -c
	if [ -d "solutions" ]; then latexmk -c -outdir=solutions; fi

distclean: 
	latexmk -C
	if [ -d "solutions" ]; then latexmk -C -outdir=solutions && rmdir solutions; fi

