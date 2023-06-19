.PHONY: all eps png clean

TIKZ_FILES := nearrt-ric architecture 5g_nr_sa_registration_flow_overview \
	      system_view 3gpp_interfaces

FILES := anr registration \
	 $(TIKZ_FILES)

EPS := $(foreach f,$(FILES),$f.eps)
PNG := $(foreach f,$(FILES),$f.png)

extra_cleanup := $(foreach aux,$(TIKZ_FILES),$(aux).aux) \
		 $(foreach log,$(TIKZ_FILES),$(log).log) \
		 $(foreach pdf,$(TIKZ_FILES),$(pdf).pdf)

all: eps png

eps: $(EPS)

png: $(PNG)

anr.eps: anr.plantuml
	plantuml -teps anr.plantuml

anr.png: anr.plantuml
	plantuml -tpng anr.plantuml

registration.eps: registration.plantuml
	plantuml -teps registration.plantuml

registration.png: registration.plantuml
	plantuml -tpng registration.plantuml

nearrt-ric.pdf: nearrt-ric.tikz tikz_template.latex tikz_style.tex
	pdflatex -jobname=$(basename $<) "\def\inputfile{$<} \input{tikz_template.latex}"

nearrt-ric.eps: nearrt-ric.pdf
	pdftops -eps $<

nearrt-ric.png: nearrt-ric.eps
	convert $< $@

architecture.pdf: architecture.tikz tikz_template.latex tikz_style.tex architecture.defs nearrt-ric.defs
	pdflatex -jobname=$(basename $<) "\def\inputfile{$<} \input{tikz_template.latex}"

architecture.eps: architecture.pdf
	pdftops -eps $<

architecture.png: architecture.eps
	convert $< $@

5g_nr_sa_registration_flow_overview.pdf: 5g_nr_sa_registration_flow_overview.tikz tikz_template.latex tikz_style.tex
	pdflatex -jobname=$(basename $<) "\def\inputfile{$<} \input{tikz_template.latex}"

5g_nr_sa_registration_flow_overview.eps: 5g_nr_sa_registration_flow_overview.pdf
	pdftops -eps $<

5g_nr_sa_registration_flow_overview.png: 5g_nr_sa_registration_flow_overview.eps
	convert $< $@

system_view.pdf: system_view.tikz tikz_template.latex tikz_style.tex
	pdflatex -jobname=$(basename $<) "\def\inputfile{$<} \input{tikz_template.latex}"

system_view.eps: system_view.pdf
	pdftops -eps $<

system_view.png: system_view.eps
	convert $< $@

3gpp_interfaces.pdf: 3gpp_interfaces.tikz tikz_template.latex tikz_style.tex
	pdflatex -jobname=$(basename $<) "\def\inputfile{$<} \input{tikz_template.latex}"

3gpp_interfaces.eps: 3gpp_interfaces.pdf
	pdftops -eps $<

3gpp_interfaces.png: 3gpp_interfaces.eps
	convert $< $@

clean:
	/bin/rm $(EPS) $(PNG) $(extra_cleanup)
