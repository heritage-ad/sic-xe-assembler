# SIC/XE Two-Pass Assembler

## Overview
This project is a **two-pass assembler for the SIC/XE instruction set architecture**, implemented in Python. It reads SIC/XE assembly source programs and produces:

- An object file with H/T/M/E records  
- A formatted assembly listing file  
- Fully resolved symbol and literal tables  

The assembler supports **all SIC/XE instruction formats, multiple addressing modes, program blocks, literals, and control sections**.

---

## Key Features
- Two-pass assembly pipeline (Pass 1 + Pass 2)
- Full SIC/XE instruction set support
- Supports all 4 instruction formats:
  - Format 1 (1 byte)
  - Format 2 (2 bytes)
  - Format 3 (3 bytes)
  - Format 4 (4 bytes)
- Supports all addressing modes:
  - Immediate (`#`)
  - Indirect (`@`)
  - Indexed (`,X`)
  - Extended (`+`)
- Implements:
  - PC-relative and Base-relative addressing
  - Proper setting of `n, i, x, b, p, e` flags
- Generates:
  - Header (H), Text (T), Modification (M), End (E) records
  - Assembly listing file with object code
- Supports:
  - Literals
  - Program blocks (`USE`)
  - Control sections
- Includes multiple test programs for validation

---

## Architecture

### Pass 1
- Parses assembly source into label, opcode, operand
- Builds:
  - Symbol Table
  - Literal Table
  - Block Table
- Computes memory addresses using a location counter (LOCCTR)
- Handles directives:
  - `START`, `END`, `WORD`, `BYTE`, `RESW`, `RESB`, `USE`
- Outputs an intermediate file and program metadata

### Pass 2
- Reads the intermediate file and symbol tables
- Generates:
  - Object code for each instruction
  - H/T/M/E records
  - Final object file
  - Formatted listing file
- Handles:
  - Instruction encoding
  - Addressing mode flags
  - Displacement calculations
  - Relocation entries

---

## My Contribution
My primary responsibility in this project was **Pass 2 and system integration**, including:

- Instruction encoding for all SIC/XE formats
- Addressing mode handling (immediate, indirect, indexed, extended)
- PC-relative and base-relative displacement calculations
- Bit-level flag encoding (`n, i, x, b, p, e`)
- Object file generation (H/T/M/E records)
- Assembly listing generation
- Integration of Pass 1 and Pass 2 into a complete pipeline

---

## Project Structure
assembler/
pass1.py
pass2.py
parser.py
tables.py
objectwriter.py
listing.py

examples/
test_programs/
tests/

main.py
output_listing.txt


---

## How to Run

```bash 
python main.py test_programs/functions.txt
```

## Outputs:

Object file (.obj)

Listing file (output_listing.txt)

## Technologies

Python

Systems programming concepts

Instruction encoding & bit manipulation

Assembler / compiler architecture

## What I Learned

How real assemblers structure multi-stage pipelines

Bit-level instruction encoding and flag manipulation

Symbol resolution and relocation

How to integrate multi-stage systems reliably

How to test low-level software thoroughly

##Disclaimer 
This project is an educational implementation of a SIC/XE assembler for learning purposes.

## Project Structure

