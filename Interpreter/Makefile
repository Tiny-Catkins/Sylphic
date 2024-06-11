CC = clang++
SRC = src
INC = inc
BUILD = build
TARGET = sylphic

OBJ = $(patsubst $(SRC)/%.cpp,$(BUILD)/%.o,$(wildcard $(SRC)/*.cpp))

CXX_Includes = -I$(INC)

CXXFLAGS += $(CXX_Includes) -std=c++20

CXXFLAGS += -MMD -MP -MF"$(@:%.o=%.d)"

$(BUILD)/$(TARGET): $(OBJ)
	$(CC) -o $@ $^

$(BUILD)/%.o: $(SRC)/%.cpp $(INC)/%.hpp
	$(CC) -o $@ -c $(CXXFLAGS) $<


$(BUILD):
	mkdir $@

.PHONY : clean
clean:
	rm -rf $(BUILD)

.PHONY : test
test:
	echo $(patsubst $(SRC)/%.cpp,$(BUILD)/%.o,$(wildcard $(SRC)/*.cpp))

-include $(wildcard $(BUILD)/*.d)
