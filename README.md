# Temperate-phage-active-prophage-detection
Detecting temperate phage (active prophage) in assembled bacterial genome sequences

## What is it used for?
Temperate phages (functional prophages induced from bacteria) help control pathogenicity, modulate community structure, and maintain gut homeostasis1. Complete phage genome sequences are indispensable for understanding phage biology. Traditional plaque techniques are not applicable to temperate phages due to lysogenicity of these phages, which curb identification and characterization of temperate phages. Existing in silico tools for prophage prediction usually fail to detect accurate and complete temperate phage genomes.

Here we present a novel method approach to detect acquired complete temperate phage genome sequences using bacterial NGS data. Unlike other tools adopt machine learning or statistical classifier to predict possible prophage regions, our approach uses raw NGS data (reads) to identify sequences that match the circularized temperate phage genome. Rather than computationally prediction like other tools, our approach captures the real replication process of temperate phages in their lytic cycles. Basically, Our approach incorporates three biological principles based upon phage life cycles: 1) In the replication process of the lytic cycle, the genome circularizes. 2) During the cycle of lysogenization, a temperate phage integrates into the host chromosome and shares a core sequence of attachment sites (attP/attB) with its host genome sequence. 3) Functional prophages usually undergo spontaneous induction at a relatively low frequency, resulting in a small amount of temperate phages in the bacterial culture, which will generate circularized phage genome’s reads in the bacterial NGS data. 

Generally, the in silico temperate phage detection method consists of three steps: NGS data processing, prophage region detection, and temperate phage extraction. In principle, our approach can detect all the temperate phages when they are spontaneously induced to a particular concentration from their host strains.
## How to use it?
#### Enviroment Dependencies:
- python >= 3
- perl >= 5.32.1
- blast == 2.9.0
- glimmer >= 3.02
- prokka == 1.13

#### Installation Steps:
- Step 1: Download and build bacterial database (please ignore this step if you already have a bacterial database):
`wget –c ftp://ddbj.nig.ac.jp/public/ddbj_database/ddbj/fasta/ddbjbct*`
`zcat ddbjbct*.gz > ddbjbct.fasta`
`rm –rf ddbjbct*.gz`
`makeblastdb -in ddbjbct.fasta -dbtype nucl -out ddbjbct.fasta`
- Step 2: Install temphd
-- option 1: from conda:
`conda install temphd`
-- option 2: from github:
`git clone https://github.com/NancyZxll/temperate-phage-active-prophage-detection/`
`tar –xvf temphd.tar.gz`
`cd temphd`
`sh build.sh`
- Step 3: Test if the installation is successful:
`temphd.pl –h`

#### Temperate Phage Detection:
- Run the following command to detect the temperate phage(s) in the bacterial data:
`temphd.pl -r1 <R1.fastq> -r2 <R2.fastq> -f <assembled_fasta_file> -id <ID_name> -sp <species_name> -db <bacteria_db>`
- The detected temperate phage is named in the format of ID_species_the direction when detecting (0 for forward/1 for reverse)_phage length_No. of phage_p.fa

#### Temperate Phage Detection Using Test Data:
- Step 1: Download the test data
Unfolding Assets at the bottom of https://github.com/NancyZxll/temperate-phage-active-prophage-detection/releases/tag/V1.0;
Downloading the temperate_phage_detection_testfiles.zip for the test data.
- Step 2: Detect the temperate phage(s) in the test bacterial data
`temphd.pl -r1 your_absolute_path/temperate_phage_detection_testfiles/1365_1P.trim.fastq -r2 your_absolute_path/temperate_phage_detection_testfiles/1365_2P.trim.fastq -f your_absolute_path/temperate_phage_detection_testfiles/1365.454Scaffolds.fna -id 1365.ID -sp 1365.Species -db your_absolute_path/ddbjbct.fasta`
- Notes: The test files were the next-generation sequencing (NGS) data and assembled sequence of one lab-preserved bacterial strain No.1365. By running the above command, you can get a temperate phage (active prophage within the bacterial genome) sequence named 1365.ID_1365.species_0_44851_1_p.fa under the folder called your destination path/temperate_phage_detection/allphages.



Downloading source codes and testing files at:

https://github.com/NancyZxll/temperate-phage-active-prophage-detection/releases/tag/V1.0

Specifically, 
unfolding `Assets` at the bottom of the above page, downloading the `temperate_phage_detection.zip` for the source codes and the `temperate_phage_detection_testfiles.zip` for the testing files.

After downloading the two .zip files, please note:

1.	All scripts needed are in:
temperate_phage_detection.zip
2.	Testing files are in:
temperate_phage_detection.testfiles.zip
3.	Unzip the above two .zip files to your destination path.
4.	Change the configurations in the main.pl, including database paths and program paths.
5.	Run the follwoing command under the folder which all the scripts in (the default folder is temperate_phage_detection):

   `perl main.pl absolute_path/Sample.R1.fastq absolute_path/Sample.R2.fastq absolute_path/Sample.AssembledSeqs.fasta Sample_ID Sample_species`
        
e.g.: `perl main.pl absolute_path/temperate_phage_detection_testfiles/1365_1P.trim.fastq absolute_path/temperate_phage_detection_testfiles/1365_2P.trim.fastq absolute_path/temperate_phage_detection_testfiles/1365.454Scaffolds.fna 1365.ID 1365.Species`
