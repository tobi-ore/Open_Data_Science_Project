# Petrophysical Analysis using Data Analytics
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
STRT.FT                         50.00000 :START DEPTH
STOP.FT                      11200.00000 :STOP DEPTH
STEP.FT                          0.50000 :STEP
NULL.                         -999.00000 :NULL VALUE
COMP.   Data output from TerraStation II         : COMPANY
WELL.   Awuna 1                                  : WELL NAME
UWI.    50-155-20001                             : WELL UWI
API.    50-155-20001                             : WELL API
LOC.    30   3S  25W                             : WELL LOCATION
DATE.   NorthSlope.W44                           : WELL DATE
FLD.    No Project Selected                      : Project NAME
~CURVE INFORMATION
#================================================
M__DEPTH.FT                  :M__DEPTH
SP      .MV                  :SP
GR      .GAPI                :GR
CALI    .IN                  :CALI
BitSize .IN                  :BitSize
MSFL    .OHMM                :MSFL
LL8     .OHMM                :LL8
ILM     .OHMM                :ILM
ILD     .OHMM                :ILD
NPHI    .%                   :NPHI
RHOB    .G/CC                :RHOB
DT      .US/F                :DT
MudWgt  .LBS/GAL             :MudWgt
~PARAMETER INFORMATION
#================================================
~OTHER INFORMATION
#================================================
~A
      50.00000    -999.00000    -999.00000    -999.00000    -999.00000    -999.00000    -999.00000    -999.00000    -999.00000    -999.00000    -999.00000    -999.00000    -999.00000
      50.50000    -999.00000    -999.00000    -999.00000    -999.00000    -999.00000    -999.00000    -999.00000    -999.00000    -999.00000    -999.00000    -999.00000    -999.00000
```
Data of this nature is in abundance due to the high volume of oil and gas exploration. In this project, data from the Department of the Interior U.S. Geological Survey repository of Wildcat Wells in the National Petroleum Reserve in Alaska will be used [https://certmapper.cr.usgs.gov/data/PubArchives/OF00-200/WELLS/WELLIDX.HTM]. However, this project is not exclusive to this data, therefore, the workflow and codes could be applied to data from other databases.
## 3) Implementation
Bash, R and Python
packages: wget, bash, numpy, matplotlib, lasio and pandas

## 4) Expected Products
