# STVcalc, an application for fetal STV calculation
The application reads binary fetal cardiotocography (CTG) files and calculates fetal heart rate short term variation (STV), the number of accellerations and of decellerations. Currently this program works with binary files stored on a server using MOSOS CTG monitoring and archiving software (BMA health care solutions, Houten, the Netherlands) or with .prn files with a fetal heart rate (FHR) sample, uterine pressure and signal quality at 4 Hz (4 / second) per line. The binary files contains data in 24 bytes sampled for each second from the CTG machine. The first 4 byte pairs contain FHR and signal quality from channel 1, the next 4 bytepairs for channel 2 (twin registration). Byte pair 10 contains 2 values of uterine pressure (sampled at 2 Hz). The last byte is an end of line code. Other byte pairs are reserved for other fetal or maternal information and use depends on addition of extra modules on the CTG machine (like blood pressure, maternal CTG or fetal oxygen saturation). The application's design follows published documentation of the FetalCare system (Huntleigh Healthcare Ltd, Cardiff, UK) for STV calculation. Spyder (Python 3.6) ws used for development. A description of the application and comparison with the FetalCare system is has been published (Wolf, H. et al; J. Perinat. Med. 2019; 47(4): 439–447). A second publication explores STV cut-off levels in a population of women with early fetal growth restriction <32 weeks.(Wolf, H. et al. ; Ultrasound in Obstetrics and Gynecology 2019; doi: 10.1002/uog.21887).
There are two versions, one is a python source code file (A, in repository STVcalc) and the other version is a compiled executable (B, in repository STVexe). Both versions are packed in a 7zip file.
A: The python source file needs installation of Python 3.6 or higher. The modules used are os, sys, pyqtgraph, and numpy, which will be available after normal installation of Python. The easiest way to install Python is to download WinPython (https://sourceforge.net/projects/winpython/Download). If you use MS Office 32 bit it is better to download the 32 bit version because communication is only possible with the same bit version. Otherwise, if you have a 64 bit machine, you can use the 64 bit version. WinPython contains a useful editor with debugging facility (Spider) and all necessary modules to run the program. All necessary files are packed in STVsingle.7z. Click on the green button [Clone or Download], select the tab [Download]. The complete folder with all files will then be downloaded to a zip file "STVexe-master.zip". Unpack this zip file to an empty folder. Place this in an empty folder and unpack STVsingle.7z there. The zip file contains a file STVcalculationSingle.py, which is the python source code, a file STVcalculationSingle.bat, which can be used to start the program, and a folder DatCTGfiles, which contains a set of CTG files.
B: For the executable change to repository STVexe and follow instructions there.
Both versions function identically. After start of the program a file search window will open to select a CTG file in the folder DatCTGfiles. After selection of a CTG file the CTG is opened and calculations are shown in the upper part of the screen. Buttons on top of the screen are available to deselect part of the CTG, to restore complete selection after deselection, to classify decelerations if present and to select a new CTG file. When he program is closed or a new CTG file is selected the data are stored in a text file named STVexport.txt, which is an ASCI file with semi-colon separations and will appear in the working folder. The file contains the baseline FHR, STV., LTV , High LTV minutes %,, Low LTV minutes %, the STV/LTV Z-score, a warning if sinusoid pattern is likely or baseline fitting can be in error, the duration of the CTG (minutes), valid minutes, lost minutes percentage, accellerations, decelleration number, decelerations with more than 20 lost beats, and the description of decelerations which should be entered in the selection box.
A more extensive application is available on request, which opens CTG data from the MOSOS server and stores results in a MsAccess database. For other storage systems the interface for reading binary data has to be adapted. We can assist for this. To do this we need a description of the storage format or you have to send a number of CTG files to determine the storage format.
