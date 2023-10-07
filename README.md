# principal-axes-calculator
Python script for calculating the principal rotational axes of a molecule and its isotopologues.

## Description

Provided an input file containing the Cartesian coordinates of a molecule, along with a list of its isotopologues,
this tool will determine the principal axes coordinate system for each isotopologue and return the corresponding
Cartesian coordinates. It will also transform the dipole moment as well, which is useful when processing results
of theoretical calculations, or to obtain the dipole moments for the isotopologues.

## Requirements

```
python==3.7
mendeleev==0.6.1
numpy==1.19.5
pandas==1.2.1
```

## Input

An example input file is provided in [example/hn3.txt](example/hn3.txt).

## Outputs

The tool will generate a `_pac.out` file and a `_pac.csv` file:

* `_pac.out`
  * reproduces the input file,
  * records the results of the mathematical steps to identify and transform to the principal axes systems,
  * and summarizes the final results in a couple of different formats.
* `_pac.csv`
  * tabulates the results with values in raw precision

Example outputs are provided in [example/](example/).

## Math

For each isotopologue, the Cartesian coordinates of the molecule is combined with the exact masses of the atoms
to calculate the moment of inertia tensor. 
The transform that diagonalizes the moment of inertia tensor is calculated.
Since the moment of inertia tensor is in the same axes system as the Cartesian coordinates, this transform 
is used to convert the original coordinates into the corresponding coordinates in the principal axes system.
The transform is also be used to convert the original dipole vector into the corresponding vector in the principal axes system.

## About

This tool grew out of necessity for various rotational spectroscopy projects during the PhD research of [Andrew N. Owen](https://orcid.org/0000-0001-5903-1651) and related collaborations.
Feedback is welcome, but there is currently no commitment to develop this further.
