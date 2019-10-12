# Application of Data Science to Petrophysical Analysis
## 1) Objectives
The aim of this project is to carry out basic petrophysical analysis on well logs.
## 2) Data Sources
The format of the data utilized for this project is the Log ASCII Standard (LAS) is a standard file-format common in the oil-and-gas and water well industries to store well log information. This file type is formatted as shown below where the `~CURVE INFORMATION` is the column header.

```
~VERSION INFORMATION
VERS.      2.0   :CWLS LOG ASCII STANDARD--VERSION 2.0
WRAP.      NO    :ONE LINE PER DEPTH STEP
~WELL INFORMATION
#MNEM.UNIT              DATA          DESCRIPTION
#================================================
STRT.FT                        101.00000 :START DEPTH
STOP.FT                       3666.00000 :STOP DEPTH
STEP.FT                          0.50000 :STEP
NULL.                         -999.00000 :NULL VALUE
COMP.   Data output from TerraStation II         : COMPANY
WELL.   Walakpa 1                                : WELL NAME
UWI.    50-023-20013                             : WELL UWI
API.    50-023-20013                             : WELL API
LOC.    9 20N 19W                                : WELL LOCATION
DATE.   NorthSlope.W08                           : WELL DATE
FLD.    No Project Selected                      : Project NAME
~CURVE INFORMATION
#================================================
M__DEPTH.FT                  :M__DEPTH
SP      .MV                  :SP
GR      .GAPI                :GR
CALI    .IN                  :CALI
BitSize .IN                  :BitSize
LL8     .OHMM                :LL8
ILM     .OHMM                :ILM
ILD     .OHMM                :ILD
RHOB    .G/CC                :RHOB
NPHI    .%                   :NPHI
DT      .US/F                :DT
MudWgt  .LBS/GAL             :MudWgt
~PARAMETER INFORMATION
#================================================
~OTHER INFORMATION
#================================================
~A
     101.00000    -999.00000    -999.00000    -999.00000      12.25000    -999.00000    -999.00000    -999.00000    -999.00000      -0.07240    -999.00000       9.00000
     101.50000    -999.00000    -999.00000    -999.00000      12.25000    -999.00000    -999.00000    -999.00000    -999.00000      -0.07360    -999.00000       9.00000
     102.00000    -999.00000    -999.00000    -999.00000      12.25000    -999.00000    -999.00000    -999.00000    -999.00000      -0.07480    -999.00000       9.00000
```
Data of this nature is in abundance due to the high volume of oil and gas exploration. In this project, data from the Department of the Interior U.S. Geological Survey repository of Wildcat Wells in the National Petroleum Reserve in Alaska will be used [https://certmapper.cr.usgs.gov/data/PubArchives/OF00-200/WELLS/WELLIDX.HTM]. However, this project is not exclusive to this data, therefore, the workflow and codes could be applied to data from other database.

This well logs are subsurface informations and therefore have associated stratigraphic data, stored as text files. An example of this text file for the LAS file above is:
```

Dept. of the Interior
U.S. Geological Survey
Energy Resources Team

Selected Data from Fourteen Wildcat Wells in 
the National Petroleum Reserve in Alaska

USGS Open File Report 00-200 


Wildcat Well Walakpa 1 - Depths to Selected Stratigraphic Horizons

WELL NAME         ROCK UNIT                                   DEPTH, FEET
WALAKPA 1         Surficial Deposits and/or Gubik Formation      19
WALAKPA 1         Torok Formation                                50
WALAKPA 1         Pebble Shale Unit                            1700
WALAKPA 1         Kingak Shale                                 2090
WALAKPA 1         Sag River Sandstone                          3220
WALAKPA 1         Shublik Formation                            3260
WALAKPA 1         Basement Complex                             3630

Data Source
Table 15.3. - Total depth and depths to selected stratigraphic horizons
for Government-drilled wells on the North Slope of Alaska., 
in:

Gryc, George, Ed., 1988, Geology and exploration of the National Petroleum
     Reserve in Alaska, 1974 to 1982, U.S. Geological Survey Professional 
     Paper 1399, Pgs. 322 - 324.
```
The stratigraphic information is used in the interpretation of the well log data.
## 3) Implementation
The analysis of the well logs will be carried out using Python.

packages: wget, bash, numpy, matplotlib, lasio and pandas

wget package will be used to efficiently download the .LAS and .txt file for this project.
LAS is a file format cannot be used in the python programming language. `lasio` is a package built to solve this problem of analysis of LAS files (documentation can be found here: https://buildmedia.readthedocs.org/media/pdf/lasio/latest/lasio.pdf). The lasio package will be utilized to read the LAS file and convert it into a DataFrame using pandas. The pandas package makes for the easy wrangling and utilization of spreadsheet data (i.e data with rows and columns). matplotlib will be utilize to display the logs.

## 4) Expected Products
### Manipulating the stratigraphic information
The textfile contains information not needed for the petrophysical analysis. a script will be written to automtically wrangle each of the textfile to new textfile with only information required for the analysis. The new textfile will look like this:
```
WELL NAME         ROCK UNIT                                   DEPTH, FEET
WALAKPA 1         Surficial Deposits and/or Gubik Formation      19
WALAKPA 1         Torok Formation                                50
WALAKPA 1         Pebble Shale Unit                            1700
WALAKPA 1         Kingak Shale                                 2090
WALAKPA 1         Sag River Sandstone                          3220
WALAKPA 1         Shublik Formation                            3260
WALAKPA 1         Basement Complex                             3630
```
### Visualization of the data in pandas
As earlier mentioned, the LAS file is in a unique format that python and most programming languages can't read appropriately. However, the lasio package is used to convert the LAS file into a DataFrame that python understands. After series data manipulation, the data which will be used for the analysis will look like below. Compare this with the LAS format above and notice the difference.

![Panda_dataframe display](./Proposal_Images/Panda_dataframe_display.JPG)
### Displaying the logs
To visualize the curves using the triple-combo display format (which is the widely used industry format), matplotlib package will be used.
This triple combo display will be made up of three tracks with some related logs plotted on the same track. The first track will have the Gamma Ray log (GR), Self-Potential log (SP) and Caliper log (CALI), the second track will consist of the various types of Resistivity logs (IL8, ILM, ILD), and the third track will have the Density log (RHOB), Sonic log (DT) and Neutron log (NPHI).On this log, the stratigraphic interval will be plotted at the corresponding depth and labelled accordingly.

![Triple Combo Display](./Proposal_Images/WA1_triple_combo_plot.png)
