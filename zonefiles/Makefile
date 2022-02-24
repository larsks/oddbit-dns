ZONES = \
	oddbit.com \
	dyn.oddbit.com \
	larsshack.org \
	vankelsted.org \
	avglks.org

ZONEFILES = $(ZONES:=.zone)
ZONETIMES = $(ZONEFILES:.zone=.zone.t)

%.zone:
	cli53 export $(patsubst %.zone,%,$@) | column -t -s$$'\t' > $@ || { rm -f $@; exit 1; }

%.zone.t: %.zone
	cli53 import --replace --file $< $(patsubst  %.zone,%,$<)
	touch $@

all: $(ZONEFILES)

update: $(ZONETIMES)

clean:
	rm -f $(ZONEFILES)
