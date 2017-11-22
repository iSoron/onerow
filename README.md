[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.1064311.svg)](https://doi.org/10.5281/zenodo.1064311)

Intersection Cuts for Single Row Relaxations
============================================

This package contains the source code for the wedge cut generator
described in the paper **Intersection Cuts for Single Row Relaxations**,
by Ricardo Fukasawa, Laurent Poirrier and Álinson S. Xavier.


Required Tools and Libraries
----------------------------

To produce the tables in the paper, the following tools and libraries were
used. Different versions may produce slightly different outputs.

- GNU Make, version 3.81
- CMake, version 3.5.1
- GCC, the GNU Compiler Collection, version 4.8.4
- GMP, the GNU Multiple Precision Arithmetic Library, version 6.1.0
- Ruby, version 1.9.3
- IBM® ILOG® CPLEX®, version 12.6.2


Build instructions
------------------

1. Make sure that CPLEX is correctly installed in your system and that
the paths in `cmake/FindCPLEX.cmake` point to the correct install location.
2. Navigate to the folder `build` and run `cmake ..` followed by `make`
3. After the compilation is finished, two binaries will be generated inside
 the `build` folder: a library `libonerow.a`, which can be used
 independently to generate wedge cuts, and an executable
 `onerow-benchmark.run`, which can be used to run the experiments presented
 in the paper.

Running the experiments
-----------------------

1. Navigate to the folder `onerow/benchmark`.
2. To run the computational experiments for all instances, run:

        ./make

3. To run the computational experiments for a particular instance, give the
   filename as argument. For example:

        ./make instances/30n20b8.pre.done

4. To run the computational experiments for multiple instances in parallel,
   the option -j can be used. For example, to run four instances simultaneously,
   run:

        ./make -j4

5. Two files will be generated per instance, inside the folder `out`. One file
   contains the log, which was printed to the terminal during the execution,
   while the other file (ending in .yaml), contains the experiment results.


Generating the tables
---------------------

1. Navigate to the folder `onerow/benchmark`.
2. Run the computational experiments, as describe above.
2. After the experiments are finished, run `./generate_tables`.
3. Extended versions of Table 1 and 2 will be printed, in CSV format. A
   copy will also be saved in `onerow/benchmark/tables`.

Heuristics
----------

Many parameters for the cut generator can be specified by modifying the
file `params.hpp`, located in `onerow/library/include/onerow/`.
For example, the three heuristics described in the paper can be achieved
by setting:

    MAX_CUT_DEPTH = 5
    MAX_R1_RAYS   = 100
    MAX_GOOD_ROWS = 100

After changing these parameters, it will be necessary to recompile the
project.
