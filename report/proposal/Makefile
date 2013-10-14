TITLE    := proj
DEPS     := refs.bib

LATEX    := pdflatex -file-line-error -interaction nonstopmode
BIBTEX   := bibtex -terse

pdf: $(TITLE).pdf

$(TITLE).pdf: $(TITLE).tex $(DEPS)
	@printf "\e[1;34m%s\e[0;37m\n" "[1] LATEX"
	$(LATEX)  $(TITLE)
	@printf "\e[1;34m%s\e[0;37m\n" "[2] BIBTEX"
	$(BIBTEX) $(TITLE)
	@printf "\e[1;34m%s\e[0;37m\n" "[3] LATEX"
	$(LATEX)  $(TITLE)
	@printf "\e[1;34m%s\e[0;37m\n" "[4] LATEX"
	$(LATEX)  $(TITLE)
	@printf "\e[m"

clean:
	$(RM) *.aux *.log *.blg *.bbl *.out

spotless: clean
	$(RM) $(TITLE).pdf

.PHONY: pdf clean spotless
