# Hailstone Conjecture Simulation
> *.pdsprj* can be open with Proteus8

## Project Overview
This project simulates the mathematical "Hailstone Conjecture," which states:  
For a positive integer `x`:
- If `x` is odd, compute `3x + 1`.
- If `x` is even, compute `x / 2`.  
The process repeats until the number reaches `1`.

Using the hardware and circuits from other Experiment, this program takes input from a keyboard, performs the calculations, and displays intermediate results in both hexadecimal and decimal formats. The implementation is written in assembly language.

---

## Objectives
1. **Input and Display**:
   - Input a decimal number (≤ 100) from the keyboard.
   - Display results on a seven-segment display in hexadecimal by default and optionally in decimal.
2. **Calculation and Timing**:
   - Compute and display intermediate results every second.
   - Support continuous operation for new inputs and calculations.
3. **Data Handling**:
   - Use 16-bit storage for intermediate results to handle large numbers (e.g., maximum intermediate result for `27` is `9232` in decimal).

---

## Design and Development

### 1. General Design
1. Input a number using the keyboard and start the calculation by pressing "=".
2. Display intermediate results every second until the number reaches `1`.
3. Reset and prepare for a new input after completion.
4. Default to hexadecimal display but include an extended feature for decimal conversion.
5. Store data in hexadecimal format for efficiency and use a conversion function for decimal display.

### 2. Hardware Design
- **Key Components**:
  - **Keyboard**: Connected via `P0` for scanning and input.
  - **Seven-Segment Display**: Display digits controlled via `P1` (digit selection) and `P2` (character mapping).
- **Circuit Design**:
  - `P0`: Keyboard scanning and input.
  - `P1 (Low 4 bits)`: Controls which segment to display.
  - `P2`: Outputs character data for the display.

### 3. Software Design
- **Modular Approach**:
  - Separate functional modules for input, storage, calculation, and display.
  - Use interrupt routines for timely updates and processing.
- **Development Steps**:
  - Design individual functional blocks.
  - Integrate them into a main routine for seamless operation.
- **Challenges**:
  - Debugging register conflicts and managing stack operations.
  - Avoiding excessive complexity in interrupt handling.
  - Efficient memory management by declaring global variables to replace frequent stack operations.

### 4. Testing
- Key test cases:
  - Input `5`: A simple, intuitive test for manual verification.
  - Input `27`: Produces the largest intermediate result within the range, verifying robustness.

---

## Challenges and Solutions
1. **Display Issues**:
   - **Bug**: One segment failing to display.
   - **Solution**: Debug small issues systematically and correct them.
2. **Register Management**:
   - **Bug**: Conflicts caused by limited register availability.
   - **Solution**: Use global variables to simplify memory management.
3. **Interrupt Handling**:
   - **Lesson**: Avoid complex recursive calls or nested functions within interrupts to prevent instability.

---

## Summary
This project, completed independently, was both challenging and rewarding. It involved debugging hardware and software issues, improving memory management, and learning to streamline interrupt handling. The experience not only enhanced problem-solving skills but also increased confidence in tackling similar tasks in the future.

### Key Learnings:
- Effective use of registers and global variables.
- Importance of systematic debugging.
- Improved efficiency in handling interrupts and modular coding.

By the end of this project, subsequent problems became more manageable, allowing for more focus on refining and optimizing solutions.
