<h1>INCISIVE<h1/>
<p>Cadence has two major verification simulation tools. One is IUS and the other is IES.</p>
<p>IUS is the previous simulation tool of Cadence, which has a weaker function. Representative tools, ncverilog.</p>
<p>The official introduction is as follows:</p>

<blockquote>IUS（incisive unified simulator） Cadence IUS allows to perform behavioral simulation on Verilog and VHDL code.</blockquote>

IES is the current simulation tool of Cadence, which has powerful functions. Represents tools, Irun
Official introduction:

<blockquote>IES（incisive Enterprise Simulator） cadence IES is considered to be one of the most considered tool to automates testbench generation, design verification and analysis from the system level to the gate level.</blockquote>

However, Cadence has now developed a new simulation tool called Xcelium. Represents tools, xrun.

<h3>Simulation mode</h3>
Cadence's simulation tool is divided into Single -step simulation mode,and Multi -step simulation mode。
Single -step simulation mode refers to simulation as long as a command. Multiple -step simulation mode refers to the combination of multiple commands to achieve simulation.

<h4>Multi -step simulation mode</h4>
Use NCVLOG (NCSC, NCVHDL), NCLAB, NCSIM commands to achieve simulation.
ncvlog, compile source code
NCLAB (NCSC, NCVHDL), perform ELABORATE on the results of compilation, establish a snapshot file
NCSIM, simulate the Snapshot file


The figure below gives the simulation Flow. For different source files, use different tools to compile.

<ul>
    <li>SystemC: Compile with NCSC tools</li>
    <li>VHDL: Compile with NCVHDL tools</li>
    <li>Verilog: Compile with NCVLOG tools</li>
</ul>

<h4>Single -step simulation mode</h4>
<p>Single -step simulation mode, including NCVerilog and Irun.
In the early IUS, using NCVerilog to perform a single -step simulation mode, NCVerilog, the inside will automatically call NCVLOG, NCLAB, NCSIM tools for simulation.</p>
<p>Starting from IUS8.1, the NCVerilog command is replaced with an Irun command. With ncverILOG, the Irun command will be directly called. The IRUN tool will automatically call NCVLOG, NCLAB, NCSIM tools for simulation.</p>
<p>The following is explained in the official document:</p>

<blockquote>because irun supports all features of ncverilog, including its command-line options, Cadence is replacing ncverilog with irun. Beginning with the IUS 8.1 release, using the ncverilog command will invoke irun.</blockquote>

<h2>IRUN tool</h2>
<p>Irun supports various source program file input, Verilog, SystemVerilog, VHDL, VERILOG AMS, VHDL AMS, SPECMAN E, and other language programs, such as C, C ++, and compile them with appropriate compilers. When the input files are compiled, IRUN automatically starts Ncelab, go to Elabora, generates Snapshot, and finally starts the NCSIM simulator to simulate Snapshot.</p>

<ul>
    <li>.v file, use NCVLOG</li>
    <li>.sv file, use NCVLOG</li>
    <li>.vhd file, use NCVHDL</li>
    <li>.e file, use Sn_compile.SH script</li>
</ul>
<table>
    <thead>
        <tr>
            <th>Option</th>
            <th>illustrate</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>-64bit</td>
            <td>Use 64bit Irun mode</td>
        </tr>
        <tr>
            <td>-f</td>
            <td>Specify File List</td>
        </tr>
        <tr>
            <td>-vlog_ext</td>
            <td>Modify the default suffix of the Verilog file, such as -vlog_ext.vvv, .vv, and modified the default suffix of Verilog as .vvv and .vv</td>
        </tr>
        <tr>
            <td>-c</td>
            <td>Only generate Snapshot, not simulation</td>
        </tr>
        <tr>
            <td>-access</td>
            <td>Set access permission</td>
        </tr>
        <tr>
            <td>-nclibdirpath</td>
            <td>Specify the inca_libs directory</td>
        </tr>
        <tr>
            <td>-R</td>
            <td>Only simulation, you need to be generated in advance</td>
        </tr>
        <tr>
            <td>-sv</td>
            <td>Support SystemVerilog language</td>
        </tr>
        <tr>
            <td>-uvm</td>
            <td>Open UVM and automatically compile the UVM library</td>
        </tr>
        <tr>
            <td>-uvmhome</td>
            <td>Specify the position of the UVM library, CDNS-1.2 UVM-1.2 version in the default IES</td>
        </tr>
        <tr>
            <td>-uvmnoautocompile</td>
            <td>Not automatically compile UVM library</td>
        </tr>
        <tr>
            <td>-clean</td>
            <td>Before the run execution, delete the Inca_libs folder</td>
        </tr>
        <tr>
            <td>-l</td>
            <td>Specify the output log file</td>
        </tr>
        <tr>
            <td>-seed</td>
            <td>Specify the number of random seeds</td>
        </tr>
        <tr>
            <td>-top</td>
            <td>Specify the top layer module</td>
        </tr>
        <tr>
            <td>-hdlvar</td>
            <td>Specify the hdl.var file</td>
        </tr>
        <tr>
            <td>-cdslib</td>
            <td>Specify CDS.lib file</td>
        </tr>
        <tr>
            <td>-loadpli1</td>
            <td>Specify the library file of the read -readable reading</td>
        </tr>
        <tr>
            <td>-prep</td>
            <td>Open the Prep Mode, do not simulate, and generate more step simulation script files. 4 files are generated: parameter files of ncvlog_ver.args: ncvlog tools, parameter files of NCLAB.ARGS NCLAB tools, parameter files of NCSIM.ARGS: NCSIM tools, Run_NC: Similar script files, call NCVLOG, NCSIM.</td>
        </tr>
        <tr>
            <td>-checkargs</td>
            <td>Check the input parameter of Irun, whether there is any mistake</td>
        </tr>
        <tr>
            <td>-helpargs</td>
            <td>Print the role of each input parameter</td>
        </tr>
        <tr>
            <td>-helpall</td>
            <td>Print help information</td>
        </tr>
        <tr>
            <td>+xxx=yyy</td>
            <td>The simulation parameter XXX is transferred to the verification environment, the value is yyy</td>
        </tr>
    </tbody>
</table>

[Reference](https://programmersought.com/article/228711283583/)