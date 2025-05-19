
# 2024-bnryan-radiological-material-trafficking
Data repository for "Finding Trafficked Radiological Materials via Coherent Elastic Neutrino-Nucleus Scattering".  The files in this repository can be seperated into three categories: neutrino spectra, detector material comparison, and material trafficking work. All of the methodology behind this code can be found in B. Ryan et al 2025 [1] and [B. Ryan 2024](https://dspace.mit.edu/handle/1721.1/155639) [2].

## Table of Contents

1. Neutrino Spectra

2. Detector Material Comparison

    2a. Cross Section Generator (xs.ipynb)

    2b. Material Comparison (material_comparison.ipynb)

3. Material Trafficking Work

    3a. Reaction Rate

    3b. Results

## 1. Neutrino Spectra

The neutrino spectra folder contains the csv files for the neutrino spectra of the four radioisotopes of interest for this study: Cs-137, Cd-109, Co-57, Ir-192. These files were generated using [SINS](https://github.com/shortlab/2024-bnryan-single-isotope-neutrino-spectrum-generator/blob/main/README.md) [3].

## 2. Detector Material Comparison

The detector material comparison folder contains the following:
- Al (Folder)
    - al_exp_xs.ipynb
    - al_xs.ipynb
    - al_exp_xs.csv
    - al_exp_xs.pdf
    - al_xs.csv
    - al_xs.pdf
- Sn (Folder)
    - sn_xs.ipynb
    - sn_xs.csv
    - sn_xs.pdf
- Zn (Folder) 
    - zn_xs.ipynb
    - zn_xs.csv
    - zn_xs.pdf
- material_comparison.ipynb
- xs.ipynb
- mat_comp_big.pdf
- mat_comp_small.pdf

If you just want the cross section data without having to run the code, please use the according csv files.

### 2a) Cross Section Generator (xs.ipynb)

While there is a different file for each detecting material considered, they all follow the same format as shown in xs.ipynb.  xs.ipynb is divided into the following sections:
- Imports
- Defining all variables (Requires User)
- Defining the cross section function
- Defining each detecting isotope (Requires User)
- Calculate the cross section (Requires User)
- Generate results files  

#### Imports
To run this file (or any of its duplicates) you must have the following packages installed:
- [numpy](https://numpy.org/) [4]
- [matplotlib](https://matplotlib.org/) [5]
- [csv](https://docs.python.org/3/library/csv.html) [6]
- [math](https://docs.python.org/3/library/math.html) [7]

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
- ratio = Superconducting Energy Gap Ratio (float)
- T_c = Superconducting Critical Temperature (float, K)
- M = Mass of the HEAVIEST** Detecting Isotope (float, eV)

** The heaviest isotope is used here to calculate the minimum detectable neutrino energy.  Technically, this varies per isotope, but to ease the calculations I took the conservative approximation of the highest minimum detectable energy.

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

Finally, the user needs to update the cells in the calculate the cross section section to run for each isotope.  See the zn or sn file for an example.

For the inputs, I recommend using the following sources:
- [KAERI Table of Nuclides](https://atom.kaeri.re.kr/nuchart/) [8]
- R. G. Sharma Superconductivity Basics and Applications to Magnets Second Edition [9]

#### Outputs
This notebook generates the CE$\nu$NS cross section as a function of energy. It outputs this information as a plot (saved as a pdf) and as a csv file.

### 2b) Material Comparison (material_comparison.ipynb)

This file was written to generate the plots that can compare the isotopes.  It was written specifically for comparing the three isotopes of interest, but the user could edit it accordingly.

#### Imports
To run this file ou must have the following packages installed:
- [matplotlib](https://matplotlib.org/) [5]
- [csv](https://docs.python.org/3/library/csv.html) [6]

To check if you have the required packages or to install the ones you do not, you can run the following:
```bash
pip install csv
pip install matplotlib
```

#### Inputs
For each of the isotpes you want to compare you need to input the csv file generated from the according xs.ipynb file.

#### Outputs
This file outputs two plots (saved as pdfs): mat_comp_big and mat_comp_small.  mat_comp_big shows the cross section over the entire energy range inputed.  mat_comp_small shows the cross section up to 100 keV.  If your initial given energy range in xs.ipynb is smaller than 100 keV, this will cause an error.

## 3. Material Trafficking Work

The material trafficking folder contains the following:
- Cd-109 Work (Folder)
    - Cd-109 Reaction Rates.ipynb
    - Cd-109_Results.ipynb
    - Cd-109_results.pdf
- Co-57 Work (Folder)
    - Co-57 Reaction Rates.ipynb
    - Co-57_Results.ipynb
    - Co-57_results.pdf
- Cs-137 Exp Work (Folder)
    - Cs-137_Al.ipynb
    - Cs-137_Results.ipynb
    - Cs-137_exp_results.pdf
- Cs-137 Work (Folder)
    - Cs-137_Al.ipynb
    - Cs-137_Results.ipynb
    - Cs-137_Sn.ipynb
    - Cs-137_Zn.ipynb
    - Cs-137_results.pdf
- Ir-192 Work (Folder)
    - Ir-192_Al.ipynb
    - Ir-192_Results.ipynb
    - Ir-192_Sn.ipynb
    - Ir-192_Zn.ipynb
    - Ir-192_results.pdf
- results.ipynb

### 3a) Reaction Rates

The detector reaction rates were predicted using unique files within each of the isotopes folders.  For the solely electron capture isotopes, the file is named Reaction Rate.ipynb.  For the isotopes that decayed via beta decay, there is one file per detector material, so that the best material could be choosen.

### 3b) Results (results.ipynb)

This file can be written to generate the minimum detector exposure required to be 95% confident that there is not a source present (as defined in B. Ryan et al 20205 [1]).  While there is a different file for each smuggled material considered, they all follow (roughly) the same format as shown in results.ipynb. results.ipynb is divided into the following sections:

- Imports
- Defining All Variables (Requires User)
- Read Given Files
- Calculate Average Cross Section
- Final Calculations
- Calculator (Requires User)

#### Imports
To run this file (or any of its duplicates) you must have the following packages installed:
- [matplotlib](https://matplotlib.org/) [5]
- [csv](https://docs.python.org/3/library/csv.html) [6]
- [math](https://docs.python.org/3/library/math.html) [7]
- [scipy.interpolate](https://docs.scipy.org/doc/scipy/reference/interpolate.html) [10]

To check if you have the required packages or to install the ones you do not, you can run the following:
```bash
pip install math
pip install csv
pip install matplotlib
pip install scipy
```

#### Inputs
In the defining all variables section, the user is required to define:

- File Names 
    - spec_file = Name and Location of the Spectrum CSV File (str)
    - xs_file = Name and Location of the Detector Cross Section CSV File (str)
- User Defined Variables 
    - source = Neutrino Source Name (str)
    - A = Detector Material Number of Nucleons (float)
    - M_s = Range of Source Activities (list, bq)
- Special Cases
    - case1 = Activity 1 of Interest (float, bq)
    - case2 = Activity 2 of Interest (float, bq)

#### Outputs
This file outputs the minimum detector exposure for a detector 1 m, 5 m, and 10 m away from the source (saved as a plot in a pdf).  The final section is a calculator that provides the detector mass for the defined cases of interest and can be modified as desired by the user.

## References
1. TBD
2. B. Ryan, Cevns in natural zinc superconductors and its applications for nuclear non-proliferation (2024), https://dspace.mit.edu/handle/1721.1/155639.
3. B. N. Ryan, Single isotope neutrino spectrum generator (2025), https://github.com/shortlab/2024-bnryan-single-isotope-neutrino-spectrum-generator/blob/main/README.md 
4. C.R. Harris et al (2020). Array programming with NumPy. *Nature*, 585(7825), 357-362. https://doi.org/10.1038/s41586-020-2649-2
5. J. D. Hunter (2007). Matplotlib: A 2D graphics environment. *Computing in Science & Engineering*, 9(3), 90-95. https://doi.org/10.1109/MCSE.2007.55
6. Python Software Foundation. (2021). Python documentation. *CSV File Reading and Writing*. https://docs.python.org/3/library/csv.html
7. Python Software Foundation. (2021). Python documentation. *Math module*. https://docs.python.org/3/library/math.html
8. Y.-S. Cho, Korea atomic energy research institute table of nuclides, Accessed Jan-May 2024, 2000. url: https://atom.kaeri.re.kr/nuchart/.
9. R. G. Sharma, in Superconductivity Basics and Applications to Magnets (2021) Chap. 2, pp. 15–37, second edition ed
10. Virtanen, P., Gommers, R., Oliphant, T. E., et al. (2020). SciPy 1.0: Fundamental algorithms for scientific computing in Python. *Nature Methods*, 17(3), 261-272. https://doi.org/10.1038/s41592-019-0686-2



