# VCS Support 2 flows:
1. Pure Verilog flow
2. Mixed-Languge Flow

### Pure Verilog Flow follows 2 step
1. Compilation / Elaboration
    - Command: `vcs` where we specify all verilog code.
    - Ex. `vcs <option> <files.v>`
2. Simulation
    - Command: `simv`
    - Ex. `simv <options>`

### Mixed-Languge Flow follows 3 step
1. Analyze
    - Analyze Verilog Code
        - Command: `vlogan`
        - Ex: `vlogan <files.v>`
    - Analyze VHDL Code(bottom-up)
        - Command: `vhdlan`
        - Ex: `vhdlan <files.vhd>`
2. Compilation / Elaboration
    - Command: `vcs`
    - Ex: `vcs <options> <design_top>`
3. Simulation
    - Command: `simv`