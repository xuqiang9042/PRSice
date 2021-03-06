PRSice: Polygenic Risk Score software
============

PRSice (pronounced 'precise') a software package for calculating, applying, evaluating and plotting the results of polygenic risk scores  

**Publised:**[Bioinformatics](http://bioinformatics.oxfordjournals.org/content/early/2014/12/28/bioinformatics.btu848.abstract)  
**Software:** PRSice  
**Version:** 1.2
**Authors:**   
    - Jack Euesden <jack.euesden@kcl.ac.uk>  
    - Cathryn M. Lewis <cathryn.lewis@kcl.ac.uk>  
    - Paul F. O'Reilly <paul.oreilly@kcl.ac.uk>  
**Website:** http://PRSice.info  
*********************
**Summary:** A polygenic risk score (PRS) is a sum of trait-associated alleles across many genetic loci, typically weighted by effect sizes estimated from a genome-wide association study (GWAS). The application of PRS has grown in recent years as their utility for detecting shared genetic aetiology among traits has become appreciated; PRS can also be used to establish the presence of a genetic signal in underpowered studies, infer the genetic architecture of a trait, for screening in clinical trials, and can act as a biomarker for a phenotype. Here we present the first dedicated PRS software, PRSice (‘precise’), for calculating, applying, evaluating and plotting the results of polygenic risk scores. PRSice can calculate PRS at a large number of thresholds (“high resolution”) to provide the best-fit PRS, as well as provide results calculated at broad P-value thresholds, can thin SNPs according to linkage disequilibrium and P-value or use all SNPs, handles genotyped and imputed data, can calculate and incorporate ancestry-informative variables, and can apply PRS across multiple traits in a single run. We exemplify the use of PRSice via application to data on Schizophrenia, Major Depressive Disorder and Smoking, illustrate the importance of identifying the best-fit PRS, and estimate a P-value significance threshold for high-resolution PRS studies.

**Availability:** PRSice is written in R, including wrappers for bash data management scripts and PLINK-1.9 to minimise computational time. PRSice runs as a command-line program with a variety of user-options

## PRSice: [Dockerised](https://www.docker.com/) for your polygenic pleasure!
Here we provide a Docker image of PRSice v1.1 for you to run on your Windows or Mac or Linux box.  

#### Dockered by: 
- Stephen J Newhouse <stepen.j.newhouse@gmail.com>    
- [linkedin](http://uk.linkedin.com/pub/dr-stephen-newhouse/29/89a/11a)    
- [Twitter @s_j_newhouse](https://twitter.com/s_j_newhouse)   

### Releases

|Date| Release |
|----------|-------------------------------------------------------------------|
21/02/2015 | [prsice-1.2.0-210215](https://github.com/KHP-Informatics/PRSice/releases/tag/v1.2.0)
25/01/2015 | [prsice-1.1.0-240115](https://github.com/KHP-Informatics/PRSice/releases/tag/v1.1.0)


*********************

**Read the Docs!**  
The Vignette: [PRSice_VIGNETTE_v1.2.pdf](https://github.com/KHP-Informatics/PRSice/blob/master/docs/PRSice_VIGNETTE_v1.2.pdf)  
 

*********************
## Get me the Docker Version

**Intsall docker**  

Windows: https://docs.docker.com/installation/windows/  
Mac: https://docs.docker.com/installation/mac/  

**Build from scratch**

If on Windows or Mac then start **boot2docker**

```{bash}
## eg on Mac
boot2docker start
```

```{bash}
docker pull compbio/prsice:1.2
```

## Runnig PRSice

**Plink Versions**
The following PLINK executables are provided and installed in the docker images at :-  

- /usr/local/bin/plink1.9_i686  
- /usr/local/bin/plink1.9_x86_64  

Make sure you use the right binary for your system eg 64bit vx 32bit!

**Running PRSice on a 64bit machine (x86_64)**

See user docs or details on running PRSice:  
The Vignette: [PRSice_VIGNETTE_v1.2.pdf](https://github.com/KHP-Informatics/PRSice/blob/master/docs/PRSice_VIGNETTE_v1.2.pdf) 

```{bash}
## make dir for your data
#
mkdir ${HOME}/pgrs
cd ${HOME}/pgrs

## run compbio/prsice:1.2
#
docker \
        run \
        --rm=true \
        -v ${HOME}/pgrs:/home/pipeman \
        --name prsice \
        -i \
        -t compbio/prsice:1.2 \
        R \
        -q \
        --file=/usr/local/bin/PRSice_v1.2.R \
        --args \
        plink /usr/local/bin/plink1.9_x86_64 \
        base /usr/local/bin/TOY_BASE_GWAS.assoc \
        target /usr/local/bin/TOY_TARGET_DATA \
        slower 0 \
        supper 0.5 \
        sinc 0.01 \
        covary F \
        figname /home/pipeman/EXAMPLE_1

```


*********************

## Example Output

The first two figures are based on a PRSice run over PGC Schizophrenia and RADIANT-UK Major Depressive Disorder data, as shown in our paper, while the quantile plot is produced from simulated data.

![fig1](/figs/PGC2_MANUSCRIPT_FIGURES_BARPLOT_2014-09-16-eps-converted-to.png)

![fig2](/figs/PGC2_MANUSCRIPT_FIGURES_POINTPLOT_2014-09-16-eps-converted-to.png)

![fig3](/figs/EXAMPLE_3_QUANTILES_1_QUANTILES_PLOT.png)



http://www.carlboettiger.info/2014/09/22/containerizing-my-development-environment.html  

**********************************


