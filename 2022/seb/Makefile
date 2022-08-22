IN2CSV           :=in2csv
LEDGER           :=ledger

# Custom scripts
ROOT_DIR         := $(shell git rev-parse --show-toplevel)
TOOLS_DIR        := $(ROOT_DIR)/Tools
LEDGERIZE        :=$(TOOLS_DIR)/seb-csv-ledgerize

# Target ledger file
TARGET           := seb-principal.ledger
ACCOUNT          := Assets:SEB:SEB Principal

# Directories
SRCDIR           := in
BUILDDIR         := gen
TARGETDIR        := bin
SRCEXT           := xlsx
OBJEXT           := csv

# Build logic
SOURCES := $(shell find $(SRCDIR) -type f -name *.$(SRCEXT))
OBJECTS := $(patsubst $(SRCDIR)/%,$(BUILDDIR)/%,$(SOURCES:.$(SRCEXT)=.$(OBJEXT)))

all: directories $(TARGET)

$(BUILDDIR)/%.csv: $(SRCDIR)/%.xlsx directories
	$(IN2CSV) $< | $(LEDGERIZE) > $@

directories:
	@mkdir -p $(BUILDDIR)

clean:
	@$(RM) -rf $(BUILDDIR)

$(TARGET): $(BUILDDIR)/%.csv
	ledger convert $< --input-date-format "%Y-%m-%d" --acount $(ACCOUNT) --invert