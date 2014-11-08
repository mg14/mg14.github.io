---
title: Shearwater
layout: post
---

Our shearwater manuscript is in press at *Bioinformatics* and out as [advanced online publication](http://dx.doi.org/10.1093/bioinformatics/btt750). It's a novel algorithm for calling subclonal mutations in deep sequencing data from cancer patients. 

![Shearwater](http://upload.wikimedia.org/wikipedia/commons/3/3b/Puffinus_gravisPCCA20070623-3738B.jpg)

### Why
I wrote it because I was frustrated with the way how the current suite of variant callers operate: Massive overcalling due to overly simple statistical models and an awful lot of postprocessing to remove all the crap. And in this last step we often loose some important bits. 

In a way those algorithms felt anachronistic: They operate on one sample at a time as if we have never sequenced anything before. But now we have much more data available and that data can be useful.

### How
Shearwater uses two ingredients:
1. It takes a whole set of samples which are simultaneously analysed to estimate mean and dispersion of the error rate distribution at each base. This helps weed out many artefacts and reduces the number of false positives. 
2. It uses prior information about mutational hot-spots from the [COSMIC database](http://cancer.sanger.ac.uk/) to increase the confidence in some variants that have been reported before. The more frequent a mutation has been previously observed the greater the weight. This helps squeezing out a few more variants on sites likely to be mutated while avoiding to call artefacts on other ends.

### Name
[Shearwaters](http://en.wikipedia.org/wiki/Shearwater) are elegant seabirds flying long distances over the ocean and plunging into the water at times to hunt fish. They often rely on other predatory fish pushing showls of mackerels closer to the surface making it easier to the shearwater to catch. Compared to that, other algorithms are like fish trawlers pulling out half the ocean just to throw 90% back into the water. 

### Results
One very interesting thing was to analyse a large panel of cancer samples with [myelodysplastic syndromes](http://en.wikipedia.org/wiki/Myelodysplasia) (MDS). For our [blood paper](http://dx.doi.org/10.1182/blood-2013-08-518886) Elli had sequenced 111 cancer genes in 738 MDS patients. I reanalysed these with shearwater and found that it calls a reasonable number of additional mutations and avoids many typical rate facts which have to removed manually otherwise. 

What was fascinating to see was that those patiens with newly identified mutations behaved like those with mutations we had seen before - that is extended survival in patients with mutations in *SF3B1* and shorter survival in other genes like *TP53*. That demonstrates two things: First that shearwater calls mutations likely to be real. Second that it should be rather useful in the clinic.

### Code
Code for shearwater is part of the bioconductor package [deepSNV](http://bioconductor.org/packages/release/bioc/html/deepSNV.html). To install it, run the following commands in [R](http://www.r-project.org):

    > library("BiocInstaller")
    > biocLite("deepSNV")

It comes with a vignette describing how to run it:

    > vignette("shearwater")