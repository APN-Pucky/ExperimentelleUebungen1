
TEX = $(wildcard *.tex)
PDF = $(patsubst %.tex, %.pdf, $(TEX))
BIB = $(patsubst %.tex, %, $(TEX))

default: bib pdf
commit: 
	-git checkout -- $(PDF)
	-git add .
	-git commit 
push: commit
	git push
pull: commit
	git pull
bib:
	biber $(BIB)
pdf:
	pdflatex -synctex=1 -interaction=nonstopmode -halt-on-error $(TEX)
zip: 
	zip Daten.zip -R Daten/

job:
	while inotifywait -e close_write $(TEX) || true; do make pdf ; done
