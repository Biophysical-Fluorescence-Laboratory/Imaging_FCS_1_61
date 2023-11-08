Imaging FCS 1.613 (3rd patch of Imaging FCS 1.61) is an ImageJ plugin featuring post-processing tools to calculate and view spatio-temporal correlation functions from 16 bit grey tiff stack files as well as data acquisition software for real-time image analysis. It was written as a FIJI plugin (ImageJ 1.53f; Java 1.8.0_281) and required Imagescience for statistics (simulator) and Apache Poi for file reading and writing.

The details about the sofware are also provided here. 
https://www.dbs.nus.edu.sg/lab/BFL/imfcs_image_j_plugin.html

ImagingFCS 1.613 provides a comprehensive software tool to calculate and evaluate spatiotemporal correlation functions. It includes the calculation of all auto- or cross-correlation functions for arbitrary pixel binning and regions of interest within an image, provides fit functions for total internal reflection fluorescence (TIRF) and single plane illumination microscopy (SPIM) based FCS measurements, can calculate the FCS diffusion laws and contains an essential simulator to create simulated data for different diffusive modes.

ImagingFCS runs under ImageJ, FIJI and Micromanager, and it runs on PC as well as on Mac OS. We will always use FIJI in the following text, but it should be understood that the same is true for ImageJ and Micromanager.

## What's new?
This version includes direct access to the camera for real-time image analysis. We refer to it as Direct Camera Readout. Direct Camera Readout supports Andor iXon DU860, iXon Ultra 897, iXon Ultra 888, Sona 4.2B-11, Hamamatsu ORCA-Flash4.0 V2 and V3, Hamamatsu ORCA-QUEST. Photometrics Evolve 512, Prime 95, and Kinetix. 

## Why Direct camera readout?
TIRF microscopy is a standard imaging modality for membrane imaging in cell biology. On the other hand, FCS provides a dynamic information from a single point in time but requires millisecond time resolution to capture the dynamics. With Direct Camera Readout, you can combine TIRF or any illumination scheme that offers good optical sectioning, such as a light sheet microscope with FCS to scan for dynamics of your imaging sample in real-time quickly. Secondly, monitoring correlation functions in real-time speeds up microscope alignment procedures.

## Installation guide
Currently, we provide two ways to install the plugin.
### Option 1: By using the Update sites of ImageJ/Fiji
Click on Help -> Update. Later click on Manage update sites. Check the boxes next to ImagingFCS and ImageScience. Click on Close. Now click on the Apply Changes button. The plugin will be downloaded. As instructed, please restart ImageJ. The plugin can now be used.

### Option 2: By downloading the files:
The following files are needed:
1. Imaging_FCS_1_613.jar (https://doi.org/10.5281/zenodo.6685875): Put this file in the plugin folder of FIJI (“Fiji.app\plugins”).
2. Imagescience : Either install imagescience.jar in the jar folder within FIJI or link the update side to imagescience. This supports the probability distributions used in the simulator.
3. Apache POI : You need to install Apache poi-3.17 (version used in writing). The Apache Poi provides the necessary code for the writing and reading of .xlsx spreadsheet files, which are used to store, read experimental data, and store metadata in case of data acquisition. You can copy the whole poi-3.17 folder into the jars folder of Fiji (\Fiji.app\jars). It has also been found that sometimes there are errors in reading the jar files inside the poi folder. In case there are errors while trying to run the plugin, and if the error is associated with poi files, one suggestion is to place all the jar files inside the poi folder directly under the jars folder. In total, there must be 13 jar files as per poi 3.17. Six of them are found just inside the folder. Five of them are in the lib folder, and two are in the ooxml-lib folder.

If you wish to compile the program from scratch:

You will then need Imaging_FCS_1_613.java. This is the Java code from which the .jar file was produced. Before building your project, e.g. with a NetBeans IDE, you must generate .dll related to GPU processing and camera access. Generation of dynamic link library is not required if you do not wish to leverage GPU for faster computation or using our home-built data acquisition software.
For manual compilation of the GPU and Direct Camera Readout please refer to section 1.3.3 in the Imaging FCS_1_613 Manual (ImFCS documentation 1_613.pdf)
1. PC: If you want to compile the program on a PC in ImageJ, you need to install a JDK (e.g. I used Jave SE - jdk1.8.0_281). For details see http://forum.imagej.net/t/no-javac-jar-found/2340 and http://stackoverflow.com/questions/18455732/play-framework-cant-find-javac.
2. Mac: To compile the program yourself, you need to install a Java IDE, i.e. an Integrative Development Environment. Netbeans, for instance, is free and worked fine for us. But there are other free IDEs, e.g. Eclipse, JSource, IntelliJ IDEA etc. Note that manual compilation of GPU related linked library requires Mac OS with supported NVIDIA graphic cards, whereas camera access .dll requires Windows PC. We recommend manual compilation through Windows for full functionality.

## Known issues
User notice slows down in image creation upon selecting ROI panel and in ICCS mode after updating ImageJ to version 1.53q. Temporary solution: put ij-1.53f.jar in the jars folder of FIJI ("Fiji.app\jars").

It has been found that sometimes, Direct Camera Readout fails to save metadata information. Check whether versions of commons-collections4-4.1.jar, ooxml-schemas-1.3.jar, xmlbeans-5.1.3.jar are present in the jars folder of FIJI ("Fiji.app\jars").

Switch off SCIFIO for file opening in ImageJ2 as Imaging_FCS_1_613 does not work with SCIFIO yet. To switch SCIFIO off, go to Edit\Options\ImageJ2 in the Fiji control bar. A dialog will appear to untick the option “Use SCIFIO when opening files”.

## Test data
Bilayer.tif: This is an example tiff stack to test the program. In general, a tiff stack should contain at least 20,000 frames which were recorded with a time resolution of 1 ms or less. This is sufficient to resolve the dynamics in lipid bilayers. However, we recommend taking at least 50,000 frames for better statistics. For faster processes, shorter frame times and more frames are required (see Sankaran et al. Analytical Chemistry 2013).

## ImFCS documentation 1_613.pdf
This manual contains the basic instructions on using the program, the definition of all items in the control and fit panels, the file formats of the saved data, and the theoretical functions used for fitting.

# References
This plugin:
1. Aik DYK, Wohland T. Imaging_FCS_1.612. 2022. https://doi.org/10.5281/zenodo.6685875.

Direct camera readout:
1. Aik DYK, Wohland T. "Microscope alignment using real-time Imaging FCS." Biophys J. 2022. https://doi.org/10.1016/j.bpj.2022.06.009.

## Disclaimer
The software and data on this site are provided for personal or academic use only and may not be used in any commercial venture or distributions. All files have been virus scanned, however, for your own protection; you should scan these files again. You assume the entire risk related to your use of this software and data. By using the software and data on this site your expressly assume all risks of data loss or damage alleged to have been caused by the software and data. The Biophysical Fluorescence Laboratory at NUS is providing this data "as is," and disclaims any and all warranties, whether express or implied, including (without limitation) any implied warranties of merchantability or fitness for a particular purpose. In no event will the Biophysical Fluorescence Laboratory at NUS and/or NUS be liable to you or to any third party for any direct, indirect, incidental, consequential, special or exemplary damages or lost profit resulting from any use or misuse of this software and data.
