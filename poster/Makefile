TEXFILE :=probkb
BIBFILE :=$(wildcard $(TEXFILE).bib)
HANDOUT :=$(TEXFILE).handout
NOTES   :=$(TEXFILE).notes
PLOTDIR :=
PLOTS   :=
FIGURES :=$(PLOTDIR)/$(PLOTS)
INPUTS  :=

all: $(TEXFILE).pdf clean

$(TEXFILE).pdf: $(TEXFILE).tex $(BIBFILE) $(FIGURES) $(INPUTS)
       # Initial run
	pdflatex $(TEXFILE)

       # Run BibTex if missing citations
	@if(grep "Citation" $(TEXFILE).log >/dev/null);\
	then \
	    bibtex $(TEXFILE);\
	    pdflatex $(TEXFILE); \
	fi

       # Recompile if instructed
	@if(grep "Rerun" $(TEXFILE).log >/dev/null);\
	then \
	    pdflatex $(TEXFILE); \
	fi

clean:
	$(RM) *.log *.aux *.blg *.bbl *.nav *.snm *.toc *.out
