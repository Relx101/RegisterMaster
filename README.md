
# Register-Master
General purpose register viewer/editor with a strong focus to aid hardware designers in their daily work

## the problem 
- In HW design, it is a tedious job to find all registers in all the data sheets you have in your disposal. You sometimes do the hole day the following flow: 
  - Find a register in a datasheet and whant to know what is set to so you take the register add -> load the value in a different program -> go back to the PDF and see what it is set to -> mostly also convert it on the way to compare it better ind the PDF -> you want to change an option in the Register -> convert it back to the format we read it in -> load the new values in the HW.
  - quickly find a register options in a data sheet or a set of data sheets.
- Register descriptions are a sometimes a NDA sensitive business not everyone has accesses to everything big fragmentation where/how the data sheets are handled
- HW designer don't have fancy polished tools which do one task well

### Why not using [Mkdocs](https://www.mkdocs.org/)? 
I really like Mkdocs for its simplicity to generate browsable documentations, but my goal is to connect in the end to arbitrary hardware in the end. So I need the extra user interactivity.

### There is [PeakRDL](https://github.com/SystemRDL/PeakRDL-html) 
This is a very good template how the user could interact with the register descritions.
I also really like the markdown idea to enrich the RDL files with more informations. 

## my vision
A modern crossplatform elecron APP 
- central space where we can view and handle registers descriptions 
- use of the SystemRDL language for register descriptions, see https://github.com/SystemRDL/systemrdl-compiler
  - \+ standardized file format for easy sharing
  - \+ easy versioning with git
  - \- live compiling necessary on each start up possible bottelneck?
  - the files can be on your PC or in NDA protected network shares
  - use the idea of [PeakRDL](https://github.com/SystemRDL/PeakRDL-html) enrich md into files
- Modular design of feature sets right from the start
  - Core functionality is the handling and managing of register descriptions
  - from hard drive / network share
  - (future) from a repo server

- basic core Modules 
  - view and search description files
  - Modules can provide external connections to interactively read and write those registers with internal or external hardware
- future core ideas
  - extent the view and seach to modify the RDL files
    - so the user can enrich on the fly the doc of this register when he finds something which is noteable
    - lowers the barrier to document everything for future use
  - logger interpreter 
    - to interpret bus data (i2c/SPI) and annotate to the log register descriptions
  - device specific GUIs (signal flow charts) which are user creatable and in cooperate register data
  -  RDL file creator which parses PDF files interactifly (pdfplumber?) 
