# ColabPRC
## **ColabPCR**: A validated Google Colaboratory Notebook for Reproducible and Precise Primer Design
[![DOI](https://zenodo.org/badge/1116805347.svg)](https://doi.org/10.5281/zenodo.18034799)

ColabPCR, a program designed to optimize the selection and evaluation of primers for a defined target genomic region. 
ColabPCR features:
* refinement of primer length and melting temperature parameters using Primer3 software
* quantification of the number of potential off-target binding regions within the target genome via BLASTn analysis
* integration of restriction enzyme recognition sites at the 5’ ends of primers
* generation of a restriction analysis report of the intended amplification region
* GUI utilizing Google Colab's computational resources to ensure high performance and accessibility without requiring local software installation.

<br><br>
ColabPCR can be run locally as a Jupyter notebook ([how to install Jupyter](https://jupyter.org/install)), in Microsoft Code or Google's Antigravity. <br>
To run directly on Google Collaboratory just click the following button.
<br>
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](  https://colab.research.google.com/github/maurijlozano/ColabPRC/blob/main/ColabPCR.ipynb)

## Manual
To run ColabPCR in Google Collaboratoy click the open in Colab buton. A Colab webpage with the notebook will be loaded.
The notebook is organized in blocks that perform different tasks. The blocks must be run in orther by filling the from optinos and clicking the "_play_" buton in the left corner.
* The 1st block: "_Install software and load functions_" will install all the required dependencies and load the required python functions and libraries.
* The 2nd block: '_Download target genome_' will download the target genome specified either by NCBI assembly accession number, load a local file, upload a file to Colab, or download preset _Daucus carota_ genomes. This block also prints the available replicons/chromosomes and their zero based index (cindex) that will be required later.
* The 3rd block: "_Extract the target sequence from the downloaded genome_" will extract the genomic region where the primers will be designed. Different modes are also available. The region mode requires only the start and end coordinates (genomic location) and the replicon index (cindex, required in all running modes). The promoter and terminator modes, use the _locus_tag_ corresponding to the gene for which the user wishes to amplify the promoter or terminator region. A product size must also be provided that defines the maximum size of the promoter or terminator region. The gene mode requires only the locus tag. In the case that the user wants to design primers for an internal gene fragment, the "_start_position_within_gene_" and "_end_position_within_gene_" options can be used. These options specify how many bases from either gene end should be left out of the target region. Finally, the "_Flexibility_" options indicates how far away (nts) from the start/end coordinates can the designed primers bind. This option is for both sides unless fixedNear or fixedFar is selected. Where "_FixedNear_" fixes the primer that binds near the start (promoter mode) or end (terminator mode) of the start/stop codon, and "_FixedFar_" fixes the distant primer.
* The 4th block: "_Use a custom sequence \[cut and paste\]_" allows the user to directly cut and paste the target sequence. The Flexibility option is also available with fixedLeft and fixedRight to anchor either the left or right primer to the target sequence ends.
* The 5th block: "_Evaluate the presence of REs sites in the target sequence_" searches for restriction endonuclease (RE) binding sites in the target region. A custom RE names list can be provided, and also the option to show all the non-cutters is available.
* The 6th block: "_Add 5' Oligonucleotides and restriction enzyme recognition sites to the fwd and rv primers_" adds a custom oligonucleotide and/or the selected RE binding region to the 5' end of the primers. If the primers will be used for cloning with RE, the sites should be added so that they are considered by the Primer3 program.
* The 7th block: "_Run Primer3 program_" runs Primer3 using custom settings for: Primer length (without 5'- oligonucleotides; PRIMER_OPT_SIZE, PRIMER_MIN_SIZE; PRIMER_MAX_SIZE) and Tm (PRIMER_OPT_TM, PRIMER_MAX_TM, PRIMER_MIN_TM, PRIMER_PAIR_MAX_DIFF_TM). A custom Primer3 configuration file can be used instead for otherwise custom settings.
* The 8th block: "_Load the primers and generate the primer table_" prints and saves a table with the designed primer pairs.
* The 9th block: "_Blastn Virtual PCR_", in this block Blastn is run to search for the primer pairs and report perfect and non perfect binding sites. A maximum difference of the primer can be set with the "_max_diff_aln_len_" option.
* The 10th block: "_VirtualPCR with custom primers_", allows the user to search the target genome for custom primer binding sites.



