IN2CSV:=in2csv

# Custom scripts
ROOT_DIR         := $(shell git rev-parse --show-toplevel)
TOOLS_DIR        := $(ROOT_DIR)/Tools
LEDGERIZE=$(TOOLS_DIR)/seb-csv-ledgerize

TARGET           := seb-principal.ledger

# Directories
SRCDIR           := in
BUILDDIR         := gen
TARGETDIR        := bin
SRCEXT           := xlsx
OBJEXT           := csv

SOURCES := $(shell find $(SRCDIR) -type f -name *.$(SRCEXT))
OBJECTS := $(patsubst $(SRCDIR)/%,$(BUILDDIR)/%,$(SOURCES:.$(SRCEXT)=.$(OBJEXT)))

all: directories $(TARGET)

$(BUILDDIR)/%.csv: $(SRCDIR)/%.xlsx
	$(IN2CSV) $< | $(LEDGERIZE) > $@

directories:
	@mkdir -p $(BUILDDIR)

clean:
	@(RM) -rf $(BUILDDIR)

$(TARGET): $(OBJECTS)