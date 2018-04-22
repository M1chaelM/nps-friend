
.PHONY: all clean install 

TARGETS := lab1.pdf lab1_solutions.pdf lab2.pdf lab2_solutions.pdf lab3.pdf \
	   lab3_solutions.pdf


all: $(TARGETS)

%.pdf: %.tex
	latexmk -pdf -pdflatex="pdflatex -interaction=nonstopmode" -use-make $<

install: 
	cp $(TARGETS) ~/google_drive/NPS/teaching/2018/CS3920/labs/


clean: 
	latexmk -C
