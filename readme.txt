files for a NEURON implementation of the Hopfield and Brody (HB) model 
from the papers:
JJ Hopfield and CD Brody, PNAS 97, 13919 (2000)
JJ Hopfield and CD Brody, PNAS 98, 1282 (2001)
complete information about the original model can be found at:

http://str.princeton.edu/mus/Organism/

This is a custom implementation, intended to serve as a basic starting point 
for those who would like to build a more realistic network
using NEURON and the ideas underlying the HB model.

200 "inputs from area A" were implemented, 
composed by 40 input channels 
each of them triggering a set of 5 slowly decaying currents (40x20 in HB).
These currents were modeled as single exponential synaptic events 
with slow decays of 200,300,400,500, and 600ms, respectively,
rather than as linearly decreasing generic currents as in HB.
Each synaptic current was delivered to one Alpha and one Beta "area W" neurons.

The 200 Alpha + 200 Beta area W neurons 
were modeled as a single compartment neurons with Na+ and K+ currents 
from a CA1 model (see the CA1 model on the Senselab website) 
rather than with Leaky Integrate and Fire cells (HB). 

To "train" the network to recognize 
the event times pattern from the "exemplar.txt" file (that can be 
found at the HB website),
30 Alpha and Beta cells (listed in the connections.txt file)
whose firing rates were approximately converging
after about 400ms were selected for all-to-all connections. 

Since the network recognizes only one pattern, only one Gamma cell was used.

Membrane time constants were the same as in HB.

To run the simulations

Under unix systems:
to compile the mod files use the command 
nrnivmodl 
and run the simulation hoc file with the command 
nrngui hopfield-brody_sd.hoc

Under Windows:
to compile the mod files use the "mknrndll DOS box" and 
follow on-screen instructions.
A double click on the simulation file
hopfield-brody_sd.hoc 
will open the simulation window.

Three simulations could be run to show the output of the Gamma cell, a raster 
plot,
and firing rates of the selected Alpha cells when an input pattern was presented
under three different conditions:

"before training": event times pattern from "exemplar.txt" 
		   and no connections among the area W cells;
"after training" : event times pattern from "exemplar.txt" 
		   and all-to-all connections between the selected cells;
		   Note firing synchronization on the raster (red marks)
		   and firing rate plots (bold lines).
"random activation": random event times pattern
		   and all-to-all connections between the selected cells;

On a 1.3GHz pentium IV under Windows2000 each simulation (1sec of model time)
needs about 2.5min of CPU time.

Questions on how to use this model should be directed to
michele.migliore@pa.ibf.cnr.it


