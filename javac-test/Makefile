#-----------------------------------------------------------------------
# Tools
#-----------------------------------------------------------------------
JAVAC = javac
JAR = jar

#-----------------------------------------------------------------------
# Directories.
#-----------------------------------------------------------------------
SRC_DIR = src
CLASSES_DIR = classes
BUILD_DIR = build

#-----------------------------------------------------------------------
# Files
#-----------------------------------------------------------------------
SRCS = $(shell find $(SRC_DIR) -name "*.java")
CLASSES = $(patsubst $(SRC_DIR)/%.java, $(CLASSES_DIR)/%.class, $(SRCS))

ENTRY_CLASS = test/TestClass
JAR_FILE = build/test.jar

.PHONY : all clean run


#-----------------------------------------------------------------------
# Rules.
#-----------------------------------------------------------------------
all: $(JAR_FILE)
	@echo "If you want to run, type 'java -jar $(JAR_FILE)'"

$(JAR_FILE): $(CLASSES) $(BUILD_DIR)
	$(JAR) cvfe $(JAR_FILE) $(ENTRY_CLASS) -C $(CLASSES_DIR) $(shell ls -1 classes)
	cat $(BUILD_DIR)/test.jar | $(JAR) -t


$(BUILD_DIR) :
	@if [ ! -d $@ ] ; then \
	    mkdir $@; \
	fi


$(CLASSES_DIR)/%.class: $(SRC_DIR)/%.java  $(CLASSES_DIR)
	$(JAVAC) -d $(CLASSES_DIR) $<

$(CLASSES_DIR) :
	@if [ ! -d $@ ] ; then \
	    mkdir $@; \
	fi

clean:
	rm -rf ./build ./classes

run: $(TARGETS)
	java -jar $(JAR_FILE)

