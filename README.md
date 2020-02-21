Thank you for your interest in our tool. The SWEEP attack targets MUX-based logic locking techniques. SWEEP does not require the unlocked design (oracle-less), but it needs some training data for benchmarks that are obfuscated using the same locking algorithm. 

Additional information can be found on our published paper:
https://drive.google.com/open?id=1EDcxIWBD9FAfY0525oVNkPzlpaWR-_s9

Benchmark Format:
SWEEP uses .bench circuits only. Key inputs for locked designs must be named exactly "keyinput" followed by an integer (for example: keyinput01, keyinput99, ...etc). no other letters, symbols or spaces allowed.

Training Data:
Locked designs with known key values are required for SWEEP to establish a correlation (weights) between design features and correct key values. The correct key values must be commented in the bench file. Please see the example benchmarks for correct formatting. 

Targetted Locking techniques:
We have used benchmarks that were originally generated by Pramod Subramanyan, please check his bitbucket for more information about the benchmarks and the locking methods:
https://bitbucket.org/spramod/host15-logic-encryption/src/default/

Additionally, we have created randomlly inserted MUX-based locked benchmarks, these include c6288.

Tool dependancy:
Please download and install ABC compiler in the provided folder in order to run the tool. The compiler can be found here: 
https://github.com/berkeley-abc/abc

The ABC binary must be compiled in "abc_compiler" folder (./abc_compiler/abc must exist).

Running the SWEEP attack:
in order to run the attack, please place the training benchmarks in the "training" folder, and make sure that the correct key is included. The benchmarks that will be attacked must be placed in the "attacked_files" folder. SWEEP supports attacking multiple benchmarks. Please check the included examples carefully and follow their syntax to avoid errors.
WARNING: do not rename the provided folders.

Running the following command will start the SWEEP attack:
$ ./src/sweep [margin]

Margin is an optional argument that controls the allowed margin between features. The value should be between 0 and 1, but the going beyond 0.1 will reduce the attack accurecy (please refer to the paper for more information. The following two examples show how to start the SWEEP attack, EXAMPLE 1 uses the default margin value (0.00), while EXAMPLE 2 uses a specific value.

EXAMPLE 1: $ ./src/sweep

EXAMPLE 2: $ ./src/sweep 0.02

If a "permission denied" error occurs, run:
$ chmod u+x ./src/sweep

Please contact me if you have any questions/feedback: alaql89@ufl.edu

If you use the tool, please refere to the original publication: 

Sweep to the Secret: A Constant Propagation Attack on Logic Locking
A. Alaql, D. Forte, and S. Bhunia
IEEE Asian Hardware Oriented Security and Trust Symposium
