IMAGES := E2_INSERT E2_CONTROL E2_REPORT E2_POLICY E2Node \
	official_uc_3.19.3.3_self_optimization \
	official_uc_3.19.3.3_self_optimization_deployment_1 \
	official_uc_3.19.3.3_self_optimization_deployment_2 \
	official_uc_3.19.3.3_self_optimization_deployment_3 \
	mlb_overview mlb_process anr_sequence

IMAGES_PNG := $(foreach img,$(IMAGES),$(img).png)
IMAGES_TIKZ := $(foreach img,$(IMAGES),$(img).latex)
IMAGES_EPS := $(foreach img,$(IMAGES),$(img).eps)

.PHONY: all png eps latex clean

all: $(IMAGES_PNG) $(IMAGES_TIKZ) $(IMAGES_EPS)

png: $(IMAGES_PNG)

latex: $(IMAGES_LATEX)

eps: $(IMAGES_EPS)

%.png: %.plantuml
	plantuml -tpng $<

%.latex: %.plantuml
	plantuml -tlatex $<

%.eps: %.plantuml
	plantuml -teps $<

clean:
	/bin/rm $(IMAGES_PNG) $(IMAGES_TIKZ) $(IMAGES_EPS) *.cmapx
