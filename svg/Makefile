.PHONY: all eps png

all: eps png

FILES=algo_example lte-to-5g lte-to-5g-with-scale mlb
FILES_PNG := $(foreach img,$(FILES),$(img).png)
FILES_EPS := $(foreach img,$(FILES),$(img).eps)

eps: $(FILES_EPS)
png: $(FILES_PNG)


%.png: %.svg
	inkscape -D $< -o $@

%.eps: %.svg
	inkscape -D $< -o $@
