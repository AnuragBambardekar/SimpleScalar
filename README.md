# SimpleScalar
SimpleScalar Lab Assignments <br>

## Installation Procedure:
**I used VMWare Virtual Machine, I start off with cygwin (all this can be done using cygwin as well, but I preferred to do it on a linux system** <br>
**Linux Ubuntu version:** 22.04.1 <br>
**Other relevant specifications:** gcc version 11.3.0 (Ubuntu 11.3.0-1ubuntu1~22.04) <br>

I am working on a Windows system, and the installation guide uses Linux commands to install SimpleScalar. So as a workaround, I installed Cygwin [Under Cygwin, source code designed for Unix-like operating systems may be compiled with minimal modification and executed.]. Alternatively, I also installed VMWare Workstation which enables us to install Ubuntu-Linux on it. [Ultimately, I end up working on this.]
Using Cygwin, we can install SimpleScalar as follows:
1. Go to This document is a guide for installing SimpleScalar on a Linux system (umass.edu) [http://www.ecs.umass.edu/ece/koren/architecture/Simplescalar/installingSimpleScalar.htm]
2. Download simplesim-3v0d.tgz
3. Make a folder where you want to Install SimpleScalar. So I made a folder called “Project” and copied the downloaded .tgz file in here.

![Step 3](/Images/image001.png?raw=true "Step 3")

4.Open Cygwin Terminal and change directory to the “Project” folder

![Step 4](/Images/image003.png?raw=true "Step 4")

5. Un-tar the downloaded file using command  tar xzvf simplesim-3v0d.tgz

![Step 5](/Images/image005.png?raw=true "Step 5")

All these files will be extracted to a folder called simplesim-3.0 <br>

6.Change the directory to simplesim-3.0

![Step 6](/Images/image007.png?raw=true "Step 6")

7. Run the command: make config-pisa

![Step 7](/Images/image009.png?raw=true "Step 7")

8. Run the command: make

![Step 8](/Images/image011.png?raw=true "Step 8")

As we can see, It has created the Makefile [The makefile contains targets and commands for execution] <br>
We should see “my work is done here…” on the last line on the Cygwin Terminal after executing the “make” command.

![Step 8-ii](/Images/image013.png?raw=true "Step 8-ii")

9. Now we can test if simplesim was installed or not by executing  ./sim-cache tests-pisa/bin/test-math

![Step 9](/Images/image015.png?raw=true "Step 9")
![Step 9-ii](/Images/image017.png?raw=true "Step 9-ii")

The installation guide says that your output should include the following line, verifying that everything works: “-1e-17 == -1e-17 Worked!”. We can see in the above image; we got the result as desired. <br>

SimpleScalar is an open-source computer architecture simulator. It can be configured as a PortableISA (PISA) simulator, which we configured earlier; and we can also configure it as an ALPHA simulator. <br>
To configure SimpleScalar as Alpha Simulator, we need to execute the following three commands while we are in the simplesim-3.0 directory. <br>

make clean <br>
![Step 10](/Images/image019.png?raw=true "Step 10")

make config-alpha <br>
![Step 11](/Images/image021.png?raw=true "Step 11")

make [This is where we run into an error] <br>
![Step 12](/Images/image023.png?raw=true "Step 12")

ERROR: [as seen on the last line after executing “make”] <br>
![Step 13](/Images/image025.png?raw=true "Step 13")

The installation guide does warn us that we might get an error, but I was unable to resolve this issue, until a **fix to resolve Alpha config issue** was later provided. <br>
Simple Scalar and Alpha Configuration Modification to make Simple Scalar work for the Alpha Configuration <br>
1. Edit target-alpha/alpha.h 
2. Go to the line that has "extern enum md_opcode md_mask2op[]". 
![Step 14](/Images/image001a.gif?raw=true "Step 14")

3. Move that underneath the definition of "enum md_opcode {...}"  <br>
![Step 15](/Images/image002a.gif?raw=true "Step 15")

4. Re-try the make command. There might still be lots of warnings, but no actual errors, so the compilation should be successful. <br>
This Solution Worked in my Ubuntu installed on VM!! <br>
I tried executing one of the alpha benchmarks and it worked! <br>
![Step 16](/Images/image003a.gif?raw=true "Step 16")
![Step 17](/Images/image004a.gif?raw=true "Step 17")

Unfortunately Cygwin doesn’t allow us to execute sudo commands. <br>
![Step 18](/Images/image027.png?raw=true "Step 18")

So, I proceeded to use the VMWare Workstation and installed Ubuntu on it. <br>
Then, downloaded and installed simplescalar on it, like the process detailed above. <br>
![Step 19](/Images/image029.png?raw=true "Step 19")
![Step 20](/Images/image031.png?raw=true "Step 20")
![Step 21](/Images/image033.png?raw=true "Step 21")
![Step 22](/Images/image035.png?raw=true "Step 22") <br>

Similarly, we can configure the simulator for PISA - configuration as well. <br>
Just run the following commands in the simplesim-3.0 directory: <br>
1. make clean
2. make config-pisa
3. make <br>
The lab experiments I performed were implemented on the PISA configured simulator. <br>

Lab Experiments were then performed as instructed on the umass website [http://www.ecs.umass.edu/ece/koren/architecture/Simplescalar/]. <br>

Outputs and Configuration files can be found in the LAB directory. <br>

**Sources:** <br>
- http://www.ecs.umass.edu/ece/koren/architecture/Simplescalar/
- SPEC95 Benchmarks for little-endian machines: http://techtitude.blogspot.com/2011/12/how-to-execute-spec95-benchmarks-in.html
