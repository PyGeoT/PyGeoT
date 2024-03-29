### **What is PyGeoT?** ### 
PyGeoT is a script written in Python language that automates the execution of GeoT-iGeoT softwares by pre- and post-processing input and ouput files, runs extensive sensitivity analysis, filters results to ease the post-processing of the data, and provides a graph that synthesizes the obtained results.
This script is useful because the ability of PyGeoT to test many mineral assemblages and select a set of minerals to compute a reservoir temperature lets the users eliminate the exhaustive effort of manually examining these assemblages. Also, the statistical and visual analysis of the mineral combinations is facilitated by the post-processing capacity of PyGeoT. 


### **Requirements** ###
For running PyGeoT, you will require: 
- Python 3.7
- NumPy
- Matplotlib
- Pandas
- GeoT-iGeoT software license (https://eesa.lbl.gov/technology/geot/)
- Text file with the chemical compositions of water samples
- Thermodynamic database

### **How to use** ###
- **PyGeoT_Part1** This part of the script reads the input file named "InputWaters_database.txt". This file contains the chemical composition of the waters under investigation. An example of this file is provided. The script also reads the file named "groups", which contains the mineral assemblages that will be considered for the multicomponent analysis. The list of mineral assemblages is generated with the Combinations_generator script, which is also provided in case the user desires to change the mineral list. To execute the Combinations_generator script, a 'minerals.txt' file is required with the list of minerals that will be used in the assemblages (an example is provided). PyGeoT writes an input file with all this information to execute GeoT/iGeoT. Afterwards, the script opens the output files and extracts all the information concerning classical geothermometers, statistical parameters, and temperatures computed by GeoT/iGeoT, and writes the file1.txt file. Finally, PyGeoT extracts the optimized concentrations of Al and Mg and creates a file2.txt file. To execute PyGeoT_Part1 the code will ask for five files named 'geoT_part1', 'geoT_part2', 'geoT_part3', 'geoT_part4', and 'geoT_part5'. Exactly examples of these files are provided, the user only needs to save them as .txt files. It is also required to have the iGeoT executable, igeot input file (an example is provided), input_files (an example is provided, this file must be saved without extension, to do this in Windows the name of the file must be saved between quotation marks "input_files"), and a thermodynamic database in the same folder.
> **_InputWaters_database.txt_**<br>
The concentrations must be specified in mol/L.<br>
First column: number of water (1, 2, 3...)<br>
Second column: measured temperature<br>
Third column: aH+ (H+ activity: aH+ = 10^-pH)<br>
Fourth column: [Na]<br>
Fifth column: [K]<br>
Sixth column: [Mg]<br>
Seventh column: [Ca]<br>
Eight column: [Cl]<br>
Ninth column: [SO4]<br>
Tenth column: [HCO3]<br>
Eleventh column: [SiO2]<br>
Twelfth column: [Al]<br>


- **PyGeoT_Part2** This second script first merges file1.txt and file2.txt into a single text file named 'newfile.txt'. It further filters the results by deleting the values of Al and Mg concentrations that are equal to the lower or upper limit of the specified value ranges. 


- **PyGeoT_Part3** To execute this last script, the following files are required: 'newfile.txt', 'groups.txt', and 'minerals.txt'. PyGeoT_Part3 evaluates each output file associated with a water composition, and removes the results for which the temperature estimation has a T-spread higher than ±20°C and a RMED/nmin value higher than 0.01. Then, PyGeoT selects, orders, and extracts 20 results with the lowest T-spread and RMED/nmin values. These are the results of GeoT/iGeoT for the best-clustering different mineral assemblages. PyGeoT then reads the associated 20 estimated temperatures and computes the corresponding median, standard deviation, and temperature spread. The median temperature is reported as the temperature estimated by PyGeoT. Finally, PyGeoT provides a graph synthesizing the results obtained with the 20 best-clustering mineral assemblages. The 20 temperature results are displayed in the upper part of the graph (y1 axis), with an error bar corresponding to the T-spread value computed by iGeoT. The values of optimized parameters are also included (y2 axis). The minerals involved in every assemblage with their respective identification number are shown in the lower part of the graph. The PyGeoT temperature estimate (median of the 20 temperature values) is shown on the right side of the graph, together with the associated statistical parameters (T-spread and standard deviation), temperature estimates from classical geothermometers as well as the reservoir temperature (e.g., bottom-hole temperature) if available. The user must manually modify the analyzed Mg concentration (in mg/L) in line 129 of the script (PyGeoT_Part3) to graph the line that compares the analyzed and optimized Mg values in the plot and to compute the K-Mg geothermometer. To change the Al analyzed concentration, line 180 must be modified. Several water samples can be processed at once. However, to graph the results, it is necessary to modify in the code the title of the plot, Mg and Al analyzed concentrations for every water sample under investigation. The 3 PyGeoT scripts can be run in the same folder. 

### **Example of PyGeoT graph for one sample** ### 
![A](https://user-images.githubusercontent.com/98906501/152246997-d100b213-d766-4f49-b25d-e2a928898f15.png)

### **Citing** ###
PyGeoT was developed during the Ph.D. of M. G. Olguín-Martínez (Ph.D. supervisor: Loïc Peiffer).<br>
The project was funded by CONACYT project PN-2016-1998 headed by L. Peiffer ("Exploración de sistemas geotérmicos mediante estudios geoquímicos y de modelación numérica").<br>

If you use this project's script for your academic work, we encourage you to cite Olguín-Martínez et al., 2022: Olguín-Martínez, M. G., Peiffer, L., Dobson, P., Spycher, N., Inguaggiato, C., Wanner, C., Hoyos, A., Wurl, J., Makovsky, K., & Ruiz-Aguilar, D. (2022). PyGeoT: A tool to automate mineral selection for multicomponent geothermometry. Geothermics, 104, 102467.<br>

Please feel free to contact us for any questions. We will be happy to help.<br>

- Email: olguinpyngu@gmail.com, peiffer@cicese.mx, angello.hoyos@cimat.mx


