## TensorFlowLite Micro for RISC-V with Optimized NN Kernels

#### Prerequisites:
 - Ubuntu 22.04 LTS (tested)
 - Active Internet Connection
 - GNU Make
 - GCC Toolchain (as needed)
 - Spike ISA Simulator
#### Usage:

__Directory Structure:__

 - Use ```riscv_makefile.inc``` to modify GCC Toolchain Directory and RISC-V specific parameters as required. This repo supports both V and PSIMD compatible kernels but they are mutually exclusive. Use suitable Toolchain respectively (Switch the Toolchain path).
  - Modify ```TARGET_ARCH=rv32gcp/rv32imp``` to enable PSIMD or ```TARGET_ARCH=rv32imv/rv32im_zve32x``` to enable V extension in ```riscv_makefile.inc```.For manual control with ```TARGET_ARCH=xxxx```, override V and P in ```riscv_makefile.inc```.
   - Run the below command to get required sources (TFLM, muriscv_nn, erap).
   
```bash
make getsrc 
```

  - After modifications as needed, just run this command to build the tflite library with the given configuration.

```bash
make buildlib
```
  -  Use ```source_makefile.inc```to modify the test files in [examples](./examples) to run inference on the tflite model with binary NumPy as input and compile it with the below command.
  
```bash
make compile
```
 - Test the compiled ELF using SPIKE ISA Simulator using the below command (Modify the Spike directory in ```riscv_makefile.inc```).
 
 ```bash
 make run
 ```
  - Get the statistics of the generated ELF using Riscv Application Profiler using the below command. Keep in mind to modify .yaml with correct ISA string ( in ```source_makefile.inc```)
  
  ```bash
  make erap
  ``` 
  <br>
  
  __Shorthand Command:__
   - In short, you can do the above with just this command.
  ```bash
  make compile && make run && make erap
  ```
