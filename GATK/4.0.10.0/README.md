# Singularity recipe for the version 4.0.10.0 of GATK


The Singularity recipe file to build GATK v4.0.10.0 Singularity image.
Also contained in the repository are the script install_R_packages.R used to include R packages in the image and the licence delivered by The Broad Institute.


The recipe allows to build the singularity image with conda gatk active environment - tested with the command:

```
singularity exec gatk-4.0.10.0.simg conda info
```

Output:

```
 active environment : gatk
    active env location : /opt/miniconda/envs/gatk
            shell level : 1
       user config file : /home/hugo/.condarc
 populated config files : 
          conda version : 4.5.11
    conda-build version : not installed
         python version : 3.7.0.final.0
       base environment : /opt/miniconda  (read only)
           channel URLs : https://repo.anaconda.com/pkgs/main/linux-64
                          https://repo.anaconda.com/pkgs/main/noarch
                          https://repo.anaconda.com/pkgs/free/linux-64
                          https://repo.anaconda.com/pkgs/free/noarch
                          https://repo.anaconda.com/pkgs/r/linux-64
                          https://repo.anaconda.com/pkgs/r/noarch
                          https://repo.anaconda.com/pkgs/pro/linux-64
                          https://repo.anaconda.com/pkgs/pro/noarch
          package cache : /opt/miniconda/pkgs
                          /home/hugo/.conda/pkgs
       envs directories : /home/hugo/.conda/envs
                          /opt/miniconda/envs
               platform : linux-64
             user-agent : conda/4.5.11 requests/2.19.1 CPython/3.7.0 Linux/4.15.0-36-generic ubuntu/16.04 glibc/2.23
                UID:GID : 1000:1000
             netrc file : None
           offline mode : False
```


The singularity image has been tested with the test command provided in the GATK4 documentation, and did not generate the error predicted for an incorrect configuration of the conda environment

https://software.broadinstitute.org/gatk/documentation/article?id=12836

Test command used:
 
```
singularity exec \
	gatk-4.0.10.0.simg \
	gatk CNNScoreVariants \
	-R ucsc.hg19.fasta \
	-V NA12878.vcf.gz \
	-O NA12878_CNNScoreVariants_filtered.vcf
```