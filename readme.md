## Geolocalisation of DNA chimpanzee samples using machine learning

### 1. Background
Humans have been traditionally fascinated by their closest related species, the chimpanzees, though at the same time, human activities have led to a drastic decline in the population size of the chimpanzees. This has been mainly caused by the wildlife trade, habitat destruction, poaching for local consumption and human linked disease outbreaks, among many others. In this regard, genetic information has proven useful to infer the populations of origin of confiscated individuals from illegal trade, detect poaching hotspots, and guide repatriation planning. Taking advantage of the most complete chimpanzee genetic map ever generated, here we implement a machine-learning geolocalisation approach, demonstrating its precision and robustness in determining the origin of confiscated chimpanzees.

![alt text]( https://ars.els-cdn.com/content/image/1-s2.0-S2666979X22000623-fx1_lrg.jpg)


### 2. Objectives
To take advantage of an extensive dataset on genomic variation in georeferenced chimpanzees to develop a machine-learning-based tool for the geolocation of chimpanzee samples which can be further implemented in other species.

### 3. Overview of the data
The dataset used for this project was obtained from [Fontsere et al. 2022](https://www.sciencedirect.com/science/article/pii/S2666979X22000623) and consists of a non-invasive geolocalised catalog of genomic diversity by capturing chromosome 21 from 828 non-invasive samples collected at 48 sampling sites across Africa. The data used for this project corresponds to the genome information of positions in chromosome 21 derived from fecal samples. This is a geolocalized non-invasive sample for which it is hard to retrieve good quality genomic information. For each of the positions in the chromosome, two nucleotides (A, T, C or G) are present, each of which deriving from one of the parents. Genomic data is stored as it compares to the genomic information of the so-called reference genome of the chimpanzee. A reference genome is a sequence of DNA used as the reference or gold-standard of genomic information of a certain species. These reference genomes only contain one copy of each chromosome (as opposed to the two copies a biological sample would have) and so, only one nucleotide is chosen to be the representative for each position (eg. position 1 is A, position 2 is T, position 3 is G, position 4 is T…). The genomic information of the chimpanzee sample is stored in relation to the one in the reference. In our dataset if the sample had the same information as the one in the reference genome, it was denoted with a 0, if it had one of the two nucleotides like the one in the reference, it would denoted with a 1. Finally, if the two nucleotides were different from the one in the reference, this position would be denoted with a 2 in our dataset. Finally, positions for which no genomic information was available were denoted with a 9. Since the data used in this project comes from feces, it is low quality, and so for many samples and positions there will not be genomic information, and so the value will be 9. Since the data used in this project comes from feces, it is low quality, and so for many samples and positions there will not be genomic information, and so the value will be 9. Each of these samples is georeferenced, which means that the exact coordinates of the place the feces was found are known. Because of this, for each of the samples, we have information about its GPS coordinates, sampling site, country or origin, and also the chimpanzee subspecies.

If you want to know more about what it means to work with fecal samples, you can have a look at this [video](https://www.youtube.com/watch?v=NMmWA3a83gs). It explain the protocol and aim of this project in Gorillas instead of Chimpanzees (and it is less than 4 minutes-long!) *Catalan only*



### 3. Data processing

#### 3.1. Quality control plots

### 4. Modelling

#### 4.1. Classification of subspecies

#### 4.2. Classification of sampling site

#### 4.3. Geographic prediction
