## Geolocalisation of DNA chimpanzee samples using machine learning

### 1. Background
As humans we have always been fascinated by our closest related species, the chimpanzees. At the same time, human activities have led to a drastic decline in the population size of this species, mainly caused by the illegal wildlife trade, habitat destruction, poaching for local consumption and human linked disease outbreaks, among many others. In this regard, genetic information could be useful to infer the populations of origin of confiscated individuals from illegal trade, detect poaching hotspots, and guide repatriation planning. Taking advantage of the most complete chimpanzee genetic map ever generated, here we implement a machine-learning geolocalisation approach, demonstrating its precision and robustness in determining the origin of confiscated chimpanzees.

<p align="center"> Summary image of the project</p>

<p align="center">
<img width="400" height="400" src="https://ars.els-cdn.com/content/image/1-s2.0-S2666979X22000623-fx1_lrg.jpg">
</p>
<p align="center"> <sub>Left panel: Dataset generated within the PanAf project. Right top panel: Study of chimpanzee history through population genomics.<br/> Right bottom panel: Geolocalisation of confiscated chimpanzees. Graphical abstract from Fontsere et al. 2022 designed by Marina Alvarez-Estape.</sub></p>

### 2. Objectives
To take advantage of an extensive dataset on genomic variation in georeferenced chimpanzees to develop a machine-learning-based tool for the geolocation of chimpanzee samples which can be further implemented in other species.

### 3. Overview of the data
The dataset used for this project was retrieved from [Fontsere et al. 2022](https://www.sciencedirect.com/science/article/pii/S2666979X22000623) and consists of a catalog of genomic diversity obtained by capturing chromosome 21 from 828 non-invasively collected samples at 48 sampling sites across Africa. This dataset contains the genomic information along chromosome 21 derived from fecal samples. Due to the nature of non-invasive samples (feces and hair) retrieving good quality genomic information is challenging. For each position in the chromosome, two nucleotides (A, T, C or G) are present, each of which deriving from one of the parents. Genomic data is mapped and referenced to the genomic information of the so-called reference genome. A reference genome is a sequence of DNA used as the reference or gold-standard of genomic information of a certain species. These reference genomes only contain one copy of each chromosome (as opposed to the two copies a biological sample would have) and so, only one nucleotide is chosen to be the representative for each position (eg. position 1 is A, position 2 is T, position 3 is G, position 4 is T…). The genomic information of the chimpanzee sample is stored in relation to the one in the reference. To simplify, in our dataset if the sample has the same information as the one in the reference genome, it is denoted with a *0*, if it has one of the two nucleotides like the one in the reference and the other is different, it would be denoted with a *1*. Finally, if the two nucleotides are different from the one in the reference, this position would be denoted with a *2* in our dataset. Finally, positions for which no genomic information is available are denoted with a *9*. Since the data used in this project comes from feces, it is low quality, and so for many samples and positions there will not be genomic information, and so the value will be *9*. Each of these samples is georeferenced, which means that the exact coordinates of the place of collection of the feces are known. Because of this, for each sample, we have information about its GPS coordinates, sampling site, country or origin, and also the chimpanzee subspecies it belongs.

To know more about what it means to work with fecal samples, please have a look at the following [video](https://www.youtube.com/watch?v=Fv_LzqCeFoI&t=1457s) (in Catalan). It explains the methodology and main aim of geoposition in the context of Gorillas instead of Chimpanzees and it is less than 4 minutes-long!

### 4. Data processing
This section includes the data processing steps for filtering the data before modelling. This has been done by using two Notebooks:
+ *Notebooks/Geolocalisation - Notebook 1.1. Data preprocessing.ipynb*: this Notebook includes the pre-processing and filtering steps applied to the data.
+ *Notebooks/Geolocalisation - Notebook 1.2. Quality Control.Rmd*: this R Notebook includes code used for plotting the data after filtering.

All data needed to replicate these results, either raw or filtered, can be found in the following [link](https://drive.google.com/drive/folders/1wroGkFZRI2MDLKRSgFWfLus0v7Kj9W94?usp=sharing).

### 5. Modelling
The modelling section has been divided into three different subsections, each of which aimed at evaluating different approaches.

#### 5.1. Classification of subspecies
This section has been aimed at implementing classifiers that can predict the subspecies of the samples. The classifiers that have been evaluated are:
1. Random Forest
2. Nearest Neighbor
3. Support Vector Machine
4. Naive Bayes

The code used in this section can be found in *Notebooks/Geolocalisation - Notebook 2.1. Modelling genomic data - SUBSPECIES.ipynb*

#### 5.2. Classification of sampling site
In this section we have assessed the perfomance of different classifiers to predict the sampling site of the chimpanzee samples. Based on the performance of the different classifiers in Section 5.1, the classifiers that have been evaluated are:
1. Random Forest
2. Nearest Neighbor
3. Support Vector Machine

The code used in this section can be found in *Notebooks/Geolocalisation - Notebook 2.2. Modelling genomic data - SAMPLINGSITE.ipynb*

#### 5.3. Geographic prediction

As we have the information regarding the coordinates of each sample, we used it to create regression models and predict the relative area where a sample was taken from. We used the following models:
1. Linear Regression
2. K Nearest Neighbors Regression

The code used in this section can be found in *Notebooks/Geolocalisation - Notebook 2.3. Modelling genomic data - Geographical prediction
.ipynb*

