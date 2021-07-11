# Sample Makefile to create a shared library from *.c files in current directory


# To create shared library, 
# Pull code --> $git clone https://github.com/Abhinav248/Makefile.git
# Change dir --> $cd Makefile/create_shared_library
# Run command --> $make
# It will create a sample shared library - libmylib.so


# Compiler macro
CC = gcc


# Compilation flags macro
CFLAGS = -fPIC
# Relocatable binary is created in two forms :-
# Position dependent : In this relocated code is bound to offset
# Position independent : In this relocated code is not bound to offset because of which sharing of libraries among multiple applications becomes easy.
# Preferably, we compile them to get position independent relocatables because of some advantages]
# The code within a dynamic executable is typically position-dependent, and is tied to a fixed address in memory. Shared objects, on the other hand,
# can be loaded at different addresses in different processes. Position-independent code is not tied to a specific address. This independence allows the code
# to execute efficiently at a different address in each process that uses the code. Position-independent code is recommended for the creation of shared objects.
# The -fPIC choice always works, but may produce larger code than -fpic. Using -fpic option usually generates smaller and faster code,
# but will have platform-dependent limitations, such as the number of globally visible symbols or the size of the code.


# Source files macro in current directory with .c extension
SOURCES = $(shell echo *.c)


# Source files corresponding object files macro
OBJECTS = $(SOURCES:.c=.o)


# Target library macro
TARGET = libmylib.so


# Clean up macro
RM = rm -rf


# .PHONY --> https://stackoverflow.com/questions/2145590/what-is-the-purpose-of-phony-in-a-makefile
.PHONY : all


# all --> https://stackoverflow.com/questions/2514903/what-does-all-stand-for-in-a-makefile
all: $(TARGET)


# Below, $@ = $(TARGET) and $^ = $(OBJECTS)
$(TARGET): $(OBJECTS)
	$(CC) -shared -o $@ $^


.PHONY : clean


# Removes object files in OBJECTS macro using command --> $make clean
clean:
	${RM} $(OBJECTS)


# Note: Static libraries are loaded when the program is compiled and Dynamically-linked libraries are loaded at run
# time. Dynamic libraries save the RAM space as against the Static library because linking to static libraries
# includes the actual code for the library functions with the executable. DLL code is kept at one location and
# is shared among all the processes/application that uses the DLL.


# Dynamic Linking doesn’t require the code to be copied, it is done by just placing name/address of the library in the binary file.
# The actual linking happens when the program is run, when both the binary file and the library are in memory.
# Examples of Dynamic libraries (libraries which are linked at run-time) are, .so in Linux and .dll in Windows.
# These are linked dynamically simply including the address of the library (whereas static linking is a waste of space).
# Dynamic linking links the libraries at the run-time. Thus, all the functions are in a special place in memory space,
# and every program can access them, without having multiple copies of them.
