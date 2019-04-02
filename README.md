# Introduction
MSFragger, an ultrafast database search tool, has been increasingly used for peptide identification. In an attempt to allow users easily manipulate MSFragger, we implement this tool as a processing node in Thermo Scientific Proteome Discoverer (PD) such that it can be operated through the graphical user interface of PD. Since Percolator currently lacks the capability of performing peptide-spectrum match (PSM) validation on open searches, we also implemented Philosopher’s PeptideProphet as a PD processing node. Comparing the search results of SequestHT and Percolator using a public HEK293 data set (PXD001468), using MSFragger and PeptideProphet(Philosopher) makes the processing speed much faster and more proteins/peptide/PSMs being identified.

# Installation

The MSFragger node can be used with Thermo Scientific Proteome Discoverer 2.2.

Please follow the steps belwo for the installation:

Step 1. Download the latest version of PDNode.dll from our github repository.

Step 2. Make sure that Thermo Scientific Proteome Discoverer in your computer is closed.

Step 3. Open the folder where Thermo Scientific Proteome Discoverer is installed.
(To find out where you install Thermo Scientific Proteome Discoverer, please right click on your Thermo Scientific Proteome Discoverer desktop icon and then click on "Properties". The folder path is shown in the field of Target)

Step 4. Copy the "PDNode.dll" to the folder. (Please ensure that the old version of PDNode.dll is deleted.)

Step 5. Open Thermo Scientific Proteome Discoverer, select the licensing page and click on Scan for Missing Features.

Step 6. Restart Thermo Scientific Proteome Discoverer.



# How to use

MSFragger

Step1. File conversion




PeptideProphet(Philosopher)
