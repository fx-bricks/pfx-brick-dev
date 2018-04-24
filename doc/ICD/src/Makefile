
VERSION = 3.36
TEMPLATE = mypandoclatex.template
SOURCE = PFxBrickICD-v3.md
RELEASE_FILE = PFxBrickICD-Rev$(VERSION).pdf
RELEASE_DIR = ..

all: 
	pandoc --template $(TEMPLATE) -N -o $(RELEASE_DIR)/$(RELEASE_FILE) $(SOURCE)

clean:
	rm -f $(RELEASE_DIR)/$(RELEASE_FILE)
	rm -f *.log
	