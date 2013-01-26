TEXFILE :=graphlab
HANDOUT :=$(TEXFILE).handout
NOTES   :=$(TEXFILE).notes
PLOTDIR :=
PLOTS   :=
FIGURES :=$(PLOTDIR)/$(PLOTS)
INPUTS  :=

all: $(TEXFILE).pdf clean

$(TEXFILE).pdf: $(TEXFILE).tex $(FIGURES) $(INPUTS)
	@echo "\ishandoutfalse \isnotesfalse">HandoutTest.tex
       # Initial run
	pdflatex $(TEXFILE)

       # Run BibTex if missing citations
	@if(grep "Citation" $(TEXFILE).log > /dev/null);\
	then \
	    bibtex $(TEXFILE);\
	    pdflatex $(TEXFILE); \
	fi

       # Recompile if instructed
	@if(grep "Rerun" $(TEXFILE).log > /dev/null);\
	then \
	    pdflatex $(TEXFILE); \
	fi

$(HANDOUT).pdf: $(TEXFILE).tex $(FIGURES) $(INPUTS)
	@echo "\ishandouttrue \isnotesfalse">HnadoutTest.tex
       # Initial run
	pdflatex -jobname $(HANDOUT) $(TEXFILE)

       # Run BibTex if missing citations
	@if(grep "Citation" $(HANDOUT).log > /dev/null);\
	then \
	    bibtex -jobname $(HANDOUT) $(TEXFILE);\
	    pdflatex -jobname $(HANDOUT) $(TEXFILE); \
	fi

       # Recompile if instructed
	@if(grep "Rerun" $(HANDOUT).log > /dev/null);\
	then \
	    pdflatex -jobname $(HANDOUT) $(TEXFILE); \
	fi

$(NOTES).pdf: $(TEXFILE).tex $(FIGURES) $(INPUTS)
	@echo "\ishandoutfalse \isnotestrue">HandoutTest.tex
       # Initial run
	pdflatex -jobname $(NOTES) $(TEXFILE)

       # Run BibTeX if missing citations
	@if(grep "Citation" $(NOTES).log > /dev/null);\
	then \
	    bibtex -jobname $(NOTES) $(TEXFILE);\
	    pdflatex -jobname $(NOTES) $(TEXFILE); \
	fi

       # Recompile if instructed
	@if(grep "Rerun" $(NOTES).log > /dev/null);\
	then \
	    pdflatex -jobname $(NOTES) $(TEXFILE); \
	fi

clean:
	$(RM) *.log *.aux *.blg *.bbl *.nav *.snm *.toc *.out