.PHONY : clean, default, publish

TEX_FILES   = ms
TMP_SUFFS   = pdf aux bbl blg log dvi ps eps out ent
SUFF        = pdf
RM_TMP      = $(foreach d, ${TEX_FILES}, rm -rf $(foreach suff, ${TMP_SUFFS}, ${d}.${suff}))
FIGURES     = $(patsubst %.ipynb,%.pdf,$(wildcard ../notebooks/figures/*.ipynb))

default: ms.pdf

ms.pdf: ms.tex bib.bib $(FIGURES)
	tectonic ms.tex --print --keep-logs

clean:
	$(RM_TMP)
	rm -rf $(FIGURES)
	rm -rf $(FIGTIMES)

../notebooks/figures/%.pdf: ../notebooks/figures/%.ipynb
	cd $(<D) && jupyter nbconvert --to notebook --execute $(<F) --output $(<F)