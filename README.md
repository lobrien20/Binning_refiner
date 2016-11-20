Binning_refiner
---

+ Binning_refiner: Improving genome bins through the combination of different binning programs
+ A manuscript describing how it works and its performance on mock and real metagenomic datasets can be found at doc/manual.
+ Version: 1.0.0
+ Last update: 2016-11-11
+ Contact: Weizhi Song (songwz03@gmail.com), Torsten Thomas(t.thomas@unsw.edu.au)
+ Affiliation: The Centre for Marine Bio-Innovation (CMB), The University of New South Wales, Sydney, Australia

Dependencies:
---

+ [R](https://www.r-project.org)
+ R package: [GoogleVis](https://github.com/mages/googleVis#googlevis)
+ Python module: [rpy2](http://rpy2.bitbucket.org)
+ Python module: [Numpy](http://www.numpy.org)
+ Python module: [Matplotlib](http://matplotlib.org)
+ Python module: [BioPython](https://github.com/biopython/biopython.github.io/)
+ [CheckM](http://ecogenomics.github.io/CheckM/)
+ [Blast+ 2.2.31](http://www.ncbi.nlm.nih.gov/news/06-16-2015-blast-plus-update/)

How to run:
---

1. Binning_refiner takes two binning programs produced bin sets as inputs. You need to define a working directory to
hold all input and output files. Input bin sets from different binning programs need to be placed in different folders
directly under working directory.

1. Accepted bin file extensions include 'fa', 'fas' or 'fasta'. All input bins in the same folder must have the same extension.

1. Binning_refiner scripts are implemented in python3, please use python3 instead of python.

1. For Katana users from UNSW, a specialized manual was prepared and placed at doc/manual.


        # For help:
        python3 Binning_refiner.py -h
        python3 CheckM_qsuber.py -h
        python3 Get_statistics.py -h

        # Example commands:
        # 1. get refined bins
        python3 Binning_refiner.py -1 MetaBAT -2 MyCC

        # 2. get qualities for each of the three bin sets
        python3 CheckM_qsuber.py -e your_email_address

        # 3. get statistics
        python3 Get_statistics.py -1 MetaBAT -2 MyCC -r outputs/Refined

Output files:
---

1. All refined bins larger than defined size cutoff

1. Contamination-free refined bins

1. Cross-link (shared sequences) between input bins

    ![Sankey_plot](doc/images/sankey_plot.jpg)

    Each band will be treated as a refined bin, its width is proportional to the total length of shared contigs between
    two connected bins. We will get 9 refined bins in the above illustration:

        MetaBAT_bin2___MyCC_bin5.fasta   MetaBAT_bin1___MyCC_bin5.fasta   MetaBAT_bin6___MyCC_bin1.fasta
        MetaBAT_bin6___MyCC_bin4.fasta   MetaBAT_bin3___MyCC_bin1.fasta   MetaBAT_bin3___MyCC_bin4.fasta
        MetaBAT_bin4___MyCC_bin2.fasta   MetaBAT_bin5___MyCC_bin3.fasta   MetaBAT_bin5___MyCC_bin6.fasta

1. Statistics of input and refined bins

    ![Statistics](doc/images/statistics.png)
