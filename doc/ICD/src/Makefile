
VERSION = 3.39
# TEMPLATE = thetemplate.tex
TEMPLATE = mypandoclatex.template
SOURCE = PFxBrickICD-v3.md
RELEASE_FILE = PFxBrickICD-Rev$(VERSION).pdf
RELEASE_DIR = ..

all:
	pandoc $(SOURCE) --listings --pdf-engine=xelatex --template $(TEMPLATE) -N -o $(RELEASE_DIR)/$(RELEASE_FILE) 

open:
	pandoc $(SOURCE) --listings --pdf-engine=xelatex --template $(TEMPLATE) -N -o $(RELEASE_DIR)/$(RELEASE_FILE) 
	open $(RELEASE_DIR)/$(RELEASE_FILE) 

clean:
	rm -f $(RELEASE_DIR)/$(RELEASE_FILE)
	rm -f *.log
