# imToolBox

imToolBox is a software package developed to facilitate analysis of large four-dimensional diffraction datasets (4D-DDs) collected by scanning electron nanodiffraction (SEND) or 4D-scanning transmission electron microscopy (4D-STEM) techniques with focus on strain analysis. The main features of imToolBox include: 
1.	Support mainstream data formats (ser/dm3/dm4/etc.) of 4D-DDs even when the data file is much larger than the memory size. 
2.	Easy visualization and preprocessing of 4D-DDs. 
3.	Strain analysis with numerous options and diagnostic tools for the best results. 

Installing imToolBox
1.	Download and install Matlab Runtime Version: R2020a (9.8) from https://www.mathworks.com/products/compiler/mcr.html
2.	Download imToolBox.exe and save to any directory. 

Loading 4D-DDs
There are three major ways to read 4D-DDs into imToolBox: 
1.	Reading the 4D-DDs contained in a single data file entirely into memory. Data format supported: ser, dm3, dm4, mrc, avi, dfp, img. 
2.	Reading only a small chunk of the dataset currently being processed instead of the entire file into memory. This works best when the data file is too large to fit in the memory at once. Data format supported: ser, dm4. 
3.	Reading a series of image files numbered in sequence. Data format supported: tiff, bmp, jpg, png. 

Preprocessing 4D-DDs
A number of functions are included in imToolBox for preprocessing of 4D-DDs, including contrast/gamma adjustment, binning, cropping, masking, and aligning diffraction patterns for imperfect descan. Diffraction pattern alignment works by doing cross-correlation of the transmitted beams from different patterns to calculate relative shift in the diffraction pattern. The shift values can be stored in a separate file without modifying the raw data and can be loaded by the software when the data file is closed and opened again. 

Visualizing 4D-DDs
To easily visualize large 4D-DDs, we provide methods including:
1.	Virtual bright/dark-field (VB/DF) imaging: place a circular detector of any radius at any desired position of the diffraction pattern to integrate all intensities within the detector. VB/DF images can be generated to provide an overview of the sample with diffraction contrast. 
2.	Virtual annular dark-field (VADF) imaging: place a customized annular dark-field detector on the diffraction pattern to integrate all intensities within the detector region. VADF images also provide overview of the sample to compare with ADF images acquired by physical ADF detectors to examine sample drift. 
3.	Stack averaging: average all diffraction patterns in 4D-DDs.
4.	Diffraction pattern grouping: use an unsupervised machine learning method, K-means clustering, to group diffraction patterns based on their similarity (defined by correlation). 

Strain Analysis
Choose from different strain analysis schemes: 
1.	One pair: calculate one-dimensional strain from the distance of a pair of diffraction peaks.
2.	Center 3x3: calculate two-dimensional strain components by fitting a reciprocal lattice to the center beam and 8 diffracted beams around it. 
3.	All: calculate two-dimensional strain components by fitting a reciprocal lattice to all diffraction peaks detectable in the pattern.
4.	Center 6: calculate two-dimensional strain components but with focus on just one direction. 
Choose from different methods to measure diffraction peak positions:
1.	Circular Hough transform: fit a circle to the edge of the diffraction disk to find the center position. Works best with large diffraction disks.
2.	Template matching: find the position of the diffraction peak by doing cross-correlation with a template. Works best when all diffraction peaks have similar intensity distribution: spot patterns or kinematic disk patterns. 
3.	Peak fitting: use Gaussian or Lorentzian peak fitting to find the peak position. Works best with spot patterns from parallel illumination.
4.	Neural network: use trained convolutional neural networks to find the position of diffraction peaks. Requires network training for different experimental conditions.
Full diagnostic capability:
1.	Output peak detection and lattice fitting results with estimated uncertainty. 
2.	Display all intermediate steps of detection to help pinpoint the error-causing issue. 
3.	Process only a selected range of the dataset to save time. 
Versatile calculation and display of strain maps:
1.	Define reference for strain calculation by choosing one pattern or average over a range of patterns in the dataset. 
2.	Define x direction for strain calculation. 
3.	Plot the strain results in 2D maps or 1D profile. 
4.	Adjust display range of strain maps.
