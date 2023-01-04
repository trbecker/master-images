.PHONY: all pdf eps clean

all: pdf eps

pdf: c-son-meta-algo.pdf e2node_block_arch.pdf oran-slicing.pdf sctp.pdf

eps: c-son-meta-algo.eps e2node_block_arch.eps oran-slicing.eps sctp.eps

%.pdf: %.tikz tikz_template.latex
	pdflatex -jobname=$(basename $<) "\def\inputfile{$<} \input{tikz_template.latex}"

%.eps: %.pdf
	pdftops -eps $<

clean:
	rm -fr *.aux *.log *.pdf *.eps
