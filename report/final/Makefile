REPORT=report
LATEX=pdflatex
BIBTEX=bibtex
REF1=refs

TEX  = $(wildcard *.tex)
CLS  = $(wildcard *.cls)
SRCS = $(TEX)
REFS = $(REF1).bib

all: pdf

pdf: $(CLS) $(SRCS) $(REFS)
	$(LATEX) $(REPORT)
	$(BIBTEX) $(REPORT)
	$(LATEX) $(REPORT)
	$(LATEX) $(REPORT)

clean:
	$(RM) *.dvi *.aux *.log *.blg *.bbl *.out
	$(RM) *~

clean-all: clean
	$(RM) $(REPORT).pdf
