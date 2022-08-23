IN2CSV           :=in2csv
LEDGER           :=ledger

# Custom scripts
ROOT_DIR         := $(shell git rev-parse --show-toplevel)
TOOLS_DIR        := $(ROOT_DIR)/Tools
LEDGERIZE        :=$(TOOLS_DIR)/seb-csv-ledgerize

# Target ledger file # TODO: Egenerate Automatically
ACCOUNT_PREFIX   := Assets:SEB:SEB
ACCOUNT          := Assets:SEB:SEB Principal

# Directories
SRCDIR           := in
BUILDDIR         := gen
TARGETDIR        := bin
XLSEXT           := xlsx
CSVEXT           := csv
LEDEXT           := ledger

# Files
XLSXS := $(shell find $(SRCDIR) -type f -name *.$(XLSEXT))
CSVS    := $(patsubst $(SRCDIR)/%,$(BUILDDIR)/%,$(XLSXS:.$(XLSEXT)=.$(CSVEXT)))
LEDGERS := $(patsubst $(SRCDIR)/%,%,$(XLSXS:.$(XLSEXT)=.$(LEDEXT)))

# Targets
all: directories $(LEDGERS)

$(BUILDDIR)/%.csv: $(SRCDIR)/%.$(XLSEXT) directories
	$(IN2CSV) $< | $(LEDGERIZE) > $@

directories:
	@mkdir -p $(BUILDDIR)

clean:
	@$(RM) -rf $(BUILDDIR)

%.$(LEDEXT): $(BUILDDIR)/%.$(CSVEXT)
	ledger convert $< --input-date-format "%Y-%m-%d" --account $(ACCOUNT) --rich-data --invert --auto-match -f $@