XCFFILES=$(wildcard *.xcf)

OUTPUTFILES=$(addprefix output/, $(patsubst %.xcf,%.png, $(XCFFILES)))

SMALLOUTPUTFILES=$(addprefix output/, $(patsubst %.xcf,%_small.png, $(XCFFILES)))

all: output/tileset.png

output:
	mkdir output

output/%.png: %.xcf output
	xcftopnm $< | pnmtopng > $@

output/%_small.png: output/%.png
	convert -sample 32x32 $< $@

output/tileset.png: $(SMALLOUTPUTFILES) 
	convert -append output/*_small.png $@

clean:
	rm -f $(OUTPUTFILES)

.PHONY : clean

# EOF #