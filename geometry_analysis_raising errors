"""
geometry_analysis.py
This module contains the geometry_analysis project
"""

import numpy
import os
import sys

def open_xyz(filename):
    """
    Takes one file, stand xyz format, (input) and converts it both to symbols and coordinates output.
    """
    xyz_file = numpy.genfromtxt(fname=filename, dtype='unicode', skip_header = 2)
    symbols = xyz_file[:,0]
    coordinates = xyz_file[:, 1:]
    coordinates = coordinates.astype(numpy.float)
    return symbols, coordinates

def bond_check(bond_distance, min_length=0, max_length=1.5):
    """
    This function checks a single bond length for distance.  Compares this to specified min (spec first, default=0)
    or maxiumum bond (spec second, default = 1.5) values.  Returns true or false.
    """

    if bond_distance < 0:
        raise ValueError (F"This bond length is a negative number ({bond_distance}).  Please check")
        #it would be hard to test this code;  could add a line below above script calling just the bond_check function - show below with ##

    if bond_distance < min_length or bond_distance > max_length:
        return False
    else:
        return True

def calculate_distance(atom1_coord, atom2_coord):
    """
    This function takes the coordinates of two atoms and calculates the distances between them.
    Inputs: atom1_coord, atom2_coord
    return: distance
    """
    x_dist = atom1_coord[0] - atom2_coord[0]
    y_dist = atom1_coord[1] - atom2_coord[1]
    z_dist = atom1_coord[2] - atom2_coord[2]
    distance = numpy.sqrt(x_dist**2 + y_dist**2 + z_dist**2)
    return distance

#file_location=os.path.join('data','water.xyz')
#starts at sys.argv[1] because [0]=geometry_analysis.py
print(F'Running {sys.argv[0]}')

if len(sys.argv) < 2:
    raise NameError("Incorrect input!  Please specify an xyz file to be analyzed.")
#if we forget to specify the file name, we can 'raise an error' to print when there is an issue

##bond_check(-5)  This would work for checking code here.  Then run in window.  


file_location = sys.argv[1]
symbols, coord = open_xyz(file_location)
num_atoms =  len(symbols)
for num1 in range(0,num_atoms):
    for num2 in range(0,num_atoms):
        if num1<num2:
            bond_length_12 = calculate_distance(coord[num1], coord[num2])
            if bond_check(bond_length_12) is True:
                        print(F'{symbols[num1]} to {symbols[num2]}: {bond_length_12:.3f}')
