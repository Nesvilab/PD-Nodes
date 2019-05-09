## Introduction
[MSFragger](http://msfragger.nesvilab.org/) is an ultrafast database search tool for peptide identifications in mass spectrometry-based proteomics. While we provide a stand-alone Graphical User interface [FragPipe](https://fragpipe.nesvilab.org) for running MSFragger, here we describe the implementation of MSFragger as a processing node in the Thermo Scientific Proteome Discoverer (PD) environment. We also provide PeptideProphet (via [Philosopher](https://nesvilab.github.io/philosopher/)) as part of the PD processing node, enabling downstream processing of MSFragger search results in PD using either Percolator or PeptideProphet. 

The following workflows have been tested and should be fully supported with our MSFragger and PeptideProphet(Philosopher) PD nodes:
- Conventional closed search, label-free or labeling based (e.g. TMT)
- Open search 

Compared to SEQUEST-HT/Percolator (using a publicly available HEK293 data set PXD001468; conventional closed search), MSFragger/PeptideProphet(Philosopher) reduced the total processing speed by at least a factor of four. For open searches, the improvement in the processing speed was much more significant. Using MSFragger instead of SEQUEST-HT (with PeptideProphet or Percolator) also resulted in a significant increase in the number of identified proteins/peptide/PSMs.


## Installation of PD nodes

The MSFragger node can be used with Thermo Scientific Proteome Discoverer versions 2.2 and 2.3 (not suitable for v2.1 or older versions).

Please follow the steps below for the installation:

**Step 1.** Download the latest version of MSFragger-PD.dll from our github repository:
https://github.com/nesvilab/PD-Nodes/releases/

**Step 2.** Make sure that Thermo Scientific Proteome Discoverer on your computer is closed.

**Step 3.** Open the folder where Thermo Scientific Proteome Discoverer is installed.
To find the folder location of Thermo Scientific Proteome Discoverer, please right click on your Thermo Scientific Proteome Discoverer desktop icon and then click on "Properties". The folder path is shown in the field called Target (as shown in the Figure).

<img src="https://github.com/Nesvilab/PD-Nodes/blob/master/fig1.png" height="40%" width="40%" title="Proteome Discoverer Properties">

**Step 4.** Copy "MSFragger-PD.dll" to that folder. Please make sure to delete any old versions of MSFragger-PD.dll.

**Step 5.** Open Thermo Scientific Proteome Discoverer, select the licensing page and click on "Scan for Missing Features".

<img src="https://github.com/Nesvilab/PD-Nodes/blob/master/fig2.png" height="90%" width="90%" title="Find license">

**Step 6.** Restart Thermo Scientific Proteome Discoverer and you should see MSFragger and PeptideProphet in your processing nodes (as shown in the Figure).

<img src="https://github.com/Nesvilab/PD-Nodes/blob/master/fig3.png" height="40%" width="40%" title="MSFragger and PeptideProphet">

**Step 7.** Download the latest versions of MSFragger and Philosopher tools from the corresponding GitHub repositories. They are NOT included with the MSFragger-PD.dll wrapper program.

> MSFragger: https://github.com/Nesvilab/MSFragger
Please follow instructions for obtaining the JAR binary file of MSFragger. 

> Philosopher: https://github.com/Nesvilab/philosopher
You will most likely need the following file: philosopher_windows_amd64.exe

NOTE: the original license agreements for MSFragger and Philosopher also apply when used within the PD environment. 


## Requirements

- Input files should be in either **mzML or mzXML** formats. MSFragger currently does not support files in .RAW format.

IMPORTANT: Please **DO NOT** use "zlib compression" during file conversion because Proteome Discoverer currently does not support the compression function. An example of parameter setting in file conversion using ProteoWizard/MSconvert is shown in the Figure.

<img src="https://github.com/Nesvilab/PD-Nodes/blob/master/fig4.png" height="60%" width="60%" title="File Conversion">

- For searches with multiple PTMs (e.g. phosphorylation) or non-specific digestion searches, MSFragger requires a significant amount of RAM available. For such searches, we recommend at least 32Gb of memory, ideally 64Gb or more. For normal tryptic searches, or open searches, even 16Gb should be sufficient. If you would like to perform searches that require significant amount of RAM, we recommend that you use [FragPipe](https://fragpipe.nesvilab.org) instead. FragPipe provides an option for splitting the protein sequence database, thus circumventing the memory limitations.


## How to use

**Step 1.** Select the binary files of MSFragger and Philosopher in their parameter window.

**Step 2.** Import your protein fasta file via "Maintain FASTA Files" in PD. Specify the database in both MSFragger and (if used) PeptideProphet nodes.

| MSFragger  | Philosopher |
| ------------- | ------------- |
| <img src="https://github.com/Nesvilab/PD-Nodes/blob/master/fig5.png"> | <img src="https://github.com/Nesvilab/PD-Nodes/blob/master/fig6.png">|

**Step 3.** When using PeptideProphet, please ensure "Validation Mode=Control peptide level error rate (Calculate missing q-values for PSMs)" in PeptideValidator (Consensus Step) such that the q-values are calculated during the validation.

<img src="https://github.com/Nesvilab/PD-Nodes/blob/master/fig7.png" height="90%" width="90%">


## Processing/Consensus Workflows
We also provides three processing workflows and two consensus workflows for your references.
- Processing_MSFragger_Percolator.pdProcessingWF: Use MSFragger and Percolator for conventional closed search.
- Processing_MSFragger_PeptideProphet.pdProcessingWF: Use MSFragger and PeptideProphet for conventional closed search.
- Processing_MSFragger_PeptideProphet_OpenSearch.pdProcessingWF: Use MSFragger and PeptideProphet for open search.
- Consensus_Percolator.pdConsensusWF: The consensus workflow for MSFragger and Percolator.
- Consensus_PeptideProphet.pdConsensusWF: The consensus workflor for PeptideProphet.

They can be downloaded from: https://github.com/Nesvilab/PD-Nodes/tree/master/workflows


## Test Data
We recommend the following publicly available HEK293 data set ([PXD001468](http://proteomecentral.proteomexchange.org/cgi/GetDataset?ID=PXD001468)) for testing, since this is what we typically use for testing as well.

## Documentation
For documentation on MSFragger itself (hardware requirements, search parameters, etc.), see MSFragger [Documentation Wiki page](https://github.com/Nesvilab/MSFragger/wiki). For Philosopher(PeptideProphet).

## Questions and Technical Support
Please post all questions/bug reports regarding MSFragger itself on the [MSFragger GitHub page](https://github.com/Nesvilab/MSFragger), or if more appropriate on [Philsopher page](https://github.com/Nesvilab/philosopher).

## How to Cite
If you use MSFragger in Proteome Discoverer, we ask that you cite the manuscript describing the PD node (currently in preparation), and well as the manuscripts describing the key individual components:

Kong AT, Leprevost FV, Avtonomov DM, Mellacheruvu D, Nesvizhskii AI. MSFragger: ultrafast and comprehensive peptide identification in mass spectrometry-based proteomics. Nature Methods 14:513–520 (2017). [Manuscript](https://www.nature.com/articles/nmeth.4256). 

Leprevost F. et al., Philosopher: a complete toolkit for shotgun proteomics data analysis. Manuscript in preparation.


For other tools developed by Nesvizhskii lab, go to our website [www.nesvilab.org](http://www.nesvilab.org)

