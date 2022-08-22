IN2CSV:=in2csv

# Custom scripts
TOOLS_DIR=$(git rev-parsse --show-toplevel)/Tools
LEDGERIZE=$(TOOLS_DIR)/seb-csv-ledgerize

TARGET           := seb-principal.ledger

# Directories
SRCDIR           := in
BUILDDIR         := gen
TARGETDIR        := bin
SRCEXT           := xlsx
OBJEXT           := csv

SOURCES := $(shell find $(SRCDIR) -type f -name *.$(SRCEXT))
OBJECTS := $(pathsubst $(SRCDIR)/%,$(BUILDDIR)/%,$(SOURCES:.$(SRCEXT)=.$(OBJEXT)))

all: directories $(TARGET)

$(BUILDDIR)/%.csv: %.xlsx
	$(IN2CSV) $< | $(LEDGERIZE) > $@

directories:
	@mkdir -p $(BUILDDIR)

clean:
	@(RM) -rf $(BUILDDIR)

$(TARGET): $(OBJECTS)