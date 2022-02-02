### **What is PyGeoT?** ### 
PyGeoT is a script written in Python language that automates the use of GeoT and iGeoT softwares, performing pre- and post-processing input and ouput files, runs extensive sensitivity analysis, filters results to ease the post-processing of the data, and provides a graph synthesizing the obtained results.
This script is useful because the ability of PyGeoT to test many mineral assemblages and select a set of minerals to compute a reservoir temperature lets the users eliminate the exhaustive effort of manually examining these assemblages. Also, the statistical and visual analysis of the mineral combinations are facilitated by the post-processing capacity of PyGeoT. 
![A](https://user-images.githubusercontent.com/98906501/152246997-d100b213-d766-4f49-b25d-e2a928898f15.png)


### **Requirements** ###
To run PyGeoT is requiered: 
- Python 3.7
- NumPy
- Matplotlib
- Pandas
- GeoT-iGeoT licence
- Text file with the chemical compositions of water samples
- Thermodynamic database

### **How to use** ###
- **PyGeoT_Part1** This part of the script reads the input file that contains the chemical composition of the waters that will be used (the user needs to name this file "InputWaters_database.txt".). At this point, the script also reads the file named "Groups", which is the file that contains the mineral assemblages that the user wants to try. PyGeoT writes an input file whit this information to execute GeoT/iGeoT. After, the script opens the output files and extracts all the information concerning classical geothermometers, statistical parameters, and temperatures computed by GeoT/iGeoT, and writes a file1.txt file. Finally, PyGeoT extracts the optimized concentrations of Al and Mg and creates a file2.txt file.
- **PyGeoT_Part2** The objectives of the PyGeoT_Part2 script are to merge both files of results (file1.txt and file2.txt) and also filter the results, by deleting the values of Al and Mg concentrations that are equal to the lower or upper limit of the specified value ranges. For this step, it is required that the user deletes manually the first line of the file1.txt and file2.txt, which is the titles of the columns.
- **PyGeoT_Part3** This is the last part of the script. The PyGeoT_Part3 results evaluate each output file and remove those for which the temperature estimation has a T-spread higher than ±20°C and an RMED/nmin value higher than 0.01. Then, PyGeoT selects, orders, and extracts 20 results with the lowest T-spread and RMED/nmin values. These are the results of GeoT/iGeoT for the best-clustering different mineral assemblages. PyGeoT then reads the associated 20 estimated temperatures and computes the corresponding median, standard deviation, and temperature spread. The median temperature is reported as the temperature estimated by PyGeoT (TPyGeoT). Finally, PyGeoT provides a graph synthesizing the results obtained with the 20 best-clustering mineral assemblages. 
The 20 temperature results are displayed in the upper part of the graph (y1 axis), with an error bar corresponding to the T-spread value computed by iGeoT. The values of optimized parameters are also included (y2 axis). The minerals involved in every assemblage with their respective identification number are shown in the lower part of the graph. The PyGeoT temperature estimate (median of the 20 temperature values) is shown on the right side of the graph, together with the associated statistical parameters (T-spread and standard deviation), temperature estimates from classical geothermometers as well as the reservoir temperature (e.g., bottom-hole temperature) if available.

### **Citing** ###
PyGeoT was developed as a Ph.D. project from CICESE.
If you use this project's script for your academic work, we encourage you to cite Olguín-Martínez et al., 2022
