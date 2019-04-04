# Introduction
MSFragger, an ultrafast database search tool, has been increasingly used for peptide identification. In an attempt to allow the easy manipulation of MSFragger, we implement this tool as a processing node in Thermo Scientific Proteome Discoverer (PD) such that it can be operated through the graphical user interface of PD. Since Percolator currently lacks the capability of performing peptide-spectrum match (PSM) validation on open searche results, we also implemented Philosopher’s PeptideProphet as a PD processing node. Comparing the search results with SequestHT and Percolator using a public HEK293 data set (PXD001468), using MSFragger and PeptideProphet(Philosopher) makes the processing speed at least four times faster and identifies more proteins/peptide/PSMs.

Based on our evaluation, you are able to perform the following experiments with our PD nodes:
- Closed search on labeling/label-free data
- Open search on label-free data



# Installation

The MSFragger node can be used with Thermo Scientific Proteome Discoverer 2.2. Please follow the steps below for the installation:

**Step 1.** Download the latest version of PDNode.dll from our github repository:https://github.com/Nesvilab/PD-Nodes/releases/

**Step 2.** Make sure that Thermo Scientific Proteome Discoverer in your computer is closed.

**Step 3.** Open the folder where Thermo Scientific Proteome Discoverer is installed.

>To find out the folder location of Thermo Scientific Proteome Discoverer, please right click on your Thermo Scientific Proteome Discoverer desktop icon and then click on "Properties". The folder path is shown in the field of Target (as the figure shown in below).

<img src="https://github.com/Nesvilab/PD-Nodes/blob/master/fig1.png" height="40%" width="40%" title="Proteome Discoverer Properties">

**Step 4.** Copy the "PDNode.dll" to the folder. (Please make sure that the old version of PDNode.dll is deleted.)

**Step 5.** Open Thermo Scientific Proteome Discoverer, select the licensing page and click on "Scan for Missing Features".

<img src="https://github.com/Nesvilab/PD-Nodes/blob/master/fig2.png" height="90%" width="90%" title="Find license">

**Step 6.** Restart Thermo Scientific Proteome Discoverer and you shall see MSFragger and PeptideProphet in your processing nodes (as shown below).

<img src="https://github.com/Nesvilab/PD-Nodes/blob/master/fig3.png" height="40%" width="40%" title="MSFragger and PeptideProphet">




# Requirements

- Input files should be in either **mzXML or mzML file formats** because MSFragger currently does not support files in .raw format.
- Please **DO NOT** use "zlib compression" during file conversion because Proteome Discoverer currently does not support the compression function. An example of parameter setting in file conversion using ProteoWizard is shown in the figure below.

<img src="https://github.com/Nesvilab/PD-Nodes/blob/master/fig4.png" height="60%" width="60%" title="File Conversion">




# How to use

**Step 1.** Download the latest version of MSFragger and Philosopher from our github.

> MSFragger: https://github.com/Nesvilab/MSFragger

> Philosopher: https://github.com/Nesvilab/philosopher

**Step 2.** Select the binary files of MSFragger and Philosopher in their parameter window.

> Please remember to import your protein fasta file via "Maintain FASTA Files" in PD.

| MSFragger  | Philosopher |
| ------------- | ------------- |
| <img src="https://github.com/Nesvilab/PD-Nodes/blob/master/fig5.png"> | <img src="https://github.com/Nesvilab/PD-Nodes/blob/master/fig6.png">|

**Step 3.** When using PeptideProphet, please ensure "Validation Mode=Control peptide level error rate (Calculate missing q-values for PSMs)" in PeptideValidator (Consensus Step) such that the q-values are calculated during the validation.

<img src="https://github.com/Nesvilab/PD-Nodes/blob/master/fig7.png" height="90%" width="90%">

# Processing/Consensus Workflows
We also provides several processing and consensus workflows for your references.

They can be downloaded from: https://github.com/Nesvilab/PD-Nodes/tree/master/workflows


# Test Data
You are welcome download the public HEK293 data set ([PXD001468](http://proteomecentral.proteomexchange.org/cgi/GetDataset?ID=PXD001468)) for testing.
