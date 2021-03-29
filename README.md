# Temperate-phage-active-prophage-detection
detect temperate phage (active prophage) in assembled bacterial genome sequences
## License
available for academic research and non-commercial use. all rights reserved.
## What can I use it to do?
Temperate phages (functional prophages induced from bacteria) help control pathogenicity, modulate community structure, and maintain gut homeostasis1. Complete phage genome sequences are indispensable for understanding phage biology. Traditional plaque techniques are not applicable to temperate phages due to lysogenicity of these phages, which curb identification and characterization of temperate phages. Existing in silico tools for prophage prediction usually fail to detect accurate and complete temperate phage genomes.

Here we present a novel method approach to detectacquire complete  temperate phage genome sequences usingin bacterial NGS data. Unlike other tools adopt machine learning or statistical classifier to predict possible prophage regions, our approach uses raw NGS data (reads) to identify sequences that match the circularized temperate phage genome. Rather than computationally prediction like other tools, our approach captures the real replication process of temperate phages in their lytic cycles. Basically, Oour approach incorporates three biological principles based upon phage life cycles: 1) In the replication process of the lytic cycle, the genome circularizes. 2) During the cycle of lysogenization, a temperate phage integrates into the host chromosome and shares a core sequence of attachment sites (attP/attB) with its host genome sequence. 3) Functional prophages usually undergo spontaneous induction at a relatively low frequency, resulting in a small amount of temperate phages in the bacterial culture, which will generate circularized phage genome’s reads in the bacterial NGS data. 

Generally, the in silico temperate phage detection method consists of three steps: NGS data processing, prophage region detection, and temperate phage extraction. In principle, our approach can detect all the temperate phages when they are spontaneously induced to a particular concentration from their host strains.
## How to use it?
The dependencies include:
*database:phage protein database, bacterial nucleotide database
*tools:blast, glimmer,
blastn, glimmer, 
1.	All scripts needed are under the folder:
new_program_20190515
2.	Test files are under the folder:
new_program.testfiles
3.	In find_prophage.pl, change line 22 to your destination folder:
our $program_path = “your destination folder";
4.	In prophage_grep.pl, change “/data/zhaisx” to your destination folders which include makeblastdb and blastn.
5.	Usage:
perl find_prophage.pl ../new_program.testfiles/trimmomatic_1P.fastq  ../new_program.testfiles/trimmomatic_2P.fastq ../new_program.testfiles/test_Assem_Contigs.fa ID species


