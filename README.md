
# 2024-bnryan-radiological-material-trafficking
Data repository for "Finding Trafficked Radiological Materials via Coherent Elastic Neutrino-Nucleus Scattering".  The files in this repository can be seperated into two categories: detector material comparison and material trafficking work. All of the methodology behind this code can be found in B. Ryan et al 2025 [1] and [B. Ryan 2024](https://dspace.mit.edu/handle/1721.1/155639) [2].

## Table of Contents

1. Detector Material Comparison

    1a. Cross Section Generator (xs.ipynb)

    1b. Material Comparison (material_comparison.ipynb)

3. Material Trafficking Work

    a. Reaction Rate

    b. Results

## 1. Detector Material Comparison

The detector material comparison folder contains the following:
- Al (Folder)
- Sn (Folder)
- Zn (Folder) 
- material_comparison.ipynb
- xs.ipynb
- mat_comp_big.pdf
- mat_comp_small.pdf

### 1a) Cross Section Generator (xs.ipynb)

While there is a different file for each detecting material considered, they all follow the same format as shown in xs.ipynb.  xs.ipynb is divided into the following sections:
- Imports
- Defining all variables (Requires User)
- Defining the cross section function
- Defining each detecting isotope (Requires User)
- Calculate the cross section (Requires User)
- Generate results files  

#### Imports
To run this file (or any of its duplicates) you must have the following packages installed:
- [numpy](https://numpy.org/)
- [matplotlib](https://matplotlib.org/)
- [csv](https://docs.python.org/3/library/csv.html)
- [math](https://docs.python.org/3/library/math.html)

To check if you have the required packages or to install the ones you do not, you can run the following:
```bash
pip install numpy
pip install csv
pip install matplotlib
pip install math
```

#### Inputs
In the defining all variables section, the user is required to define:
- Q = Maxiumum Energy to Consider (int, in keV)
- mat = Name of the Detecting Material (str)
- Z = Proton Number (int)
- ratio = 
- T_c = Superconducting Critical Temperature (float, Kelvin)
- M = Mass of the HEAVIEST Detecting Isotope (float, eV)

In the defining each detecting isotope section, the user needs to define:
- prob_x = Abundance of Isotope (float)
- N_x = Number of Neutrons in Isotope (int)
- M_x = Mass of Isotope (float, eV)
- xs_x = Empty List to Store Results

This can be done by editting and copying the following cell:
```bash
# Isotope x
prob_x = 
N_x = 
M_x =  # eV
xs_x = []
```

Finally, the user needs to update the cells in the calculate the cross section section to run for each isotope.  

For the inputs, I used the following sources:
- [KAERI Table of Nuclides](https://atom.kaeri.re.kr/nuchart/) [3]
- R. G. Sharma Superconductivity Basics and Applications to Magnets Second Edition [4]

#### Outputs
This notebook generates the CE$\nu$NS cross section as a function of energy. It outputs this information as a plot (saved as a pdf) and as a csv file.

### 1b) Material Comparison (material_comparison.ipynb)

This file was written to generate the plots that can compare the isotopes.  It was written specifically for comparing the three isotopes of interest, but the user could edit it accordingly.

#### Imports
To run this file ou must have the following packages installed:
- matplotlib
- csv

To check if you have the required packages or to install the ones you do not, you can run the following:
```bash
pip install csv
pip install matplotlib
```

#### Inputs
For each of the isotpes you want to compare you need to input the csv file generated from the according xs.ipynb file.

#### Outputs
This file outputs two plots (saved as pdfs): mat_comp_big and mat_comp_small.  mat_comp_big shows the cross section over the entire energy range inputed.  mat_comp_small shows the cross section up to 100 keV.  If your initial given energy range in xs.ipynb is smaller than 100 keV, this will cause an error.

## 2. Material Trafficking Work

### 2a) Reaction Rates

### 2b) Results

## References
1. 
2. B. Ryan, Cevns in natural zinc superconductors and its applications for nuclear non-proliferation, chapter 2.1 (2024), https://dspace.mit.edu/handle/1721.1/155639.
3. Y.-S. Cho, Korea atomic energy research institute table of nuclides, Accessed Jan-May 2024, 2000. url: https://atom.kaeri.re.kr/nuchart/.
4. R. G. Sharma, in Superconductivity Basics and Applications to Magnets (2021) Chap. 2, pp. 15–37, second edition ed



