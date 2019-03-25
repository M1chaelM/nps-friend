
.PHONY: all clean install 

TARGETS := lab1.pdf lab2.pdf lab3.pdf lab4.pdf lab5.pdf \
	lab6.pdf lab7.pdf lab8.pdf lab9.pdf lab10.pdf \
        lab5_extra.pdf lab6_extra.pdf


all: $(TARGETS)

%.pdf: %.tex
	latexmk -pdf -pdflatex="pdflatex -interaction=nonstopmode -shell-escape" -use-make $<

install: 
	cp $(TARGETS) ~/google_drive/NPS/teaching/2018/CS3920/labs/


clean: 
	latexmk -C
