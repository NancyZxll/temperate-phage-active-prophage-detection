# Temperate-phage-active-prophage-detection
detect temperate phage (active prophage) in assembled bacterial genome sequences
## License
Available for academic research and non-commercial use. All rights reserved.
## What is it used for?
Temperate phages (functional prophages induced from bacteria) help control pathogenicity, modulate community structure, and maintain gut homeostasis1. Complete phage genome sequences are indispensable for understanding phage biology. Traditional plaque techniques are not applicable to temperate phages due to lysogenicity of these phages, which curb identification and characterization of temperate phages. Existing in silico tools for prophage prediction usually fail to detect accurate and complete temperate phage genomes.

Here we present a novel method approach to detectacquire complete  temperate phage genome sequences usingin bacterial NGS data. Unlike other tools adopt machine learning or statistical classifier to predict possible prophage regions, our approach uses raw NGS data (reads) to identify sequences that match the circularized temperate phage genome. Rather than computationally prediction like other tools, our approach captures the real replication process of temperate phages in their lytic cycles. Basically, Oour approach incorporates three biological principles based upon phage life cycles: 1) In the replication process of the lytic cycle, the genome circularizes. 2) During the cycle of lysogenization, a temperate phage integrates into the host chromosome and shares a core sequence of attachment sites (attP/attB) with its host genome sequence. 3) Functional prophages usually undergo spontaneous induction at a relatively low frequency, resulting in a small amount of temperate phages in the bacterial culture, which will generate circularized phage genome’s reads in the bacterial NGS data. 

Generally, the in silico temperate phage detection method consists of three steps: NGS data processing, prophage region detection, and temperate phage extraction. In principle, our approach can detect all the temperate phages when they are spontaneously induced to a particular concentration from their host strains.
## How to use it?
#### Dependencies
Before use, need to download (and install) the dependencies below on your computer:

* database: phage protein database, bacterial nucleotide database
* tools: blast, glimmer, python2
#### Running instructions
1.	All scripts needed are in:
temperate_phage_detection.zip
2.	Test files are in:
temperate_phage_detection.testfiles.zip
3.	Unzip the above two .zip files to your destionation path.
4.	Change the configurations in the main.pl, including input file paths, database paths, and program paths.
5.	Run perl main.pl under the folder which all the scripts in (the default folder is temperate_phage_detection).



