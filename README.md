# DIGITAL-FILTER-DESIGN-VLSI-TASK-4

COMPANY: CODTECH IT SOLUTIONS

NAME: K SUDHARSHAN

INTERN ID: CT06DF1472

DOMAIN: VLSI

DURATION: 6 WEEKS

MENTOR: NEELA SANTOSH

**In Task 4, a digital FIR (Finite Impulse Response) filter was designed and simulated using Verilog HDL. The purpose of this task was to build a functional digital filter that performs a weighted summation of current and past input samples using fixed coefficients. FIR filters are commonly used in digital signal processing for smoothing, noise reduction, and signal enhancement. The implementation focused on demonstrating the core functionality of an FIR filter through simulation and waveform verification.

The filter was constructed using a four-tap design, meaning it utilizes four coefficients and four delayed versions of the input signal. The filter module defines four coefficient registers, labeled b0, b1, b2, and b3, which were initialized during reset to specific signed fixed-point values. Alongside these coefficients, a delay line composed of four registers was used to store the most recent input samples. This structure ensures that at every clock cycle, the filter has access to the current input and three prior samples required for the computation.

The behavior of the filter is governed by three sequential blocks. The first block handles coefficient initialization during reset. The second block manages the shifting of input samples through the delay line on every positive clock edge. The third block performs the core filter computation by multiplying each delayed input with its respective coefficient and summing the results to form the final output. The computed result is stored in a 32-bit signed register and assigned to the module's output.

To verify the design, a separate testbench module was created. This testbench generated a regular clock signal and controlled the reset sequence. After the reset was deasserted, input values were applied at fixed time intervals to simulate a signal entering the filter. Specifically, values such as 1000, 2000, 3000, 4000, and 5000 were provided sequentially to observe how the filter responds as the delay line fills and the output accumulates. This allowed for a step-by-step examination of the filter's behavior.

Simulation and waveform analysis were carried out using the EDA Playground platform. The output waveforms were observed through EPWave, which provided a visual representation of signal changes over time. The waveforms showed the shifting of input values into the delay line and the resulting output changes based on the current and past samples. The reset, clock, input, and output signals were all captured correctly, and the filter demonstrated the expected behavior as defined by the FIR filter equation.

The results from the simulation confirmed that the filter operated correctly and the output reflected the effect of each input sample weighted by the corresponding coefficients. The waveform indicated that the values built up over time, illustrating how the filter integrates multiple samples to form the output. This validated that the FIR filter design was functioning as intended.

This task offered practical experience in designing and simulating digital filters using hardware description languages. It also enhanced understanding of concepts such as delay lines, coefficient multiplication, and pipeline synchronization. The code and waveform output met all the requirements stated in the task. The design and simulation were completed using EDA Playground, and signal transitions were analyzed using the integrated EPWave waveform viewer.

**SIMULATION OUTPUT

![Image](https://github.com/user-attachments/assets/b46149d0-2a19-4167-aa86-b4ee4b401457)
