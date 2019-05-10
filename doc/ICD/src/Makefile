
VERSION = 3.37
TEMPLATE = mypandoclatex.template
SOURCE = PFxBrickICD-v3.md
RELEASE_FILE = PFxBrickICD-Rev$(VERSION).pdf
RELEASE_DIR = ..

all:
	pandoc $(SOURCE) --listings --latex-engine=xelatex --template $(TEMPLATE) -N -o $(RELEASE_DIR)/$(RELEASE_FILE) 

clean:
	rm -f $(RELEASE_DIR)/$(RELEASE_FILE)
	rm -f *.log
