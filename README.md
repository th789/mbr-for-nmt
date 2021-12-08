# mbr-for-nmt



## Characterizing minimum Bayes risk (MBR) decoding for neural machine translation (NMT)

This project characterizes the performance of MBR decoding for NMT when using various candidate generation methods, by examining BLEU score, length bias, and token frequency bias in resulting translations. The project motivation, goals, and results are described below. The final project paper, which contains a full project description, can be found [XXXhereXXX](insert-link-here).

This repository contains the dataset used for the project, code to reproduce results and analyses, and saved results. The folders and files of this repository are described in detail below.



## Motivation

The aim of NMT is to output the best possible translation of a given input text.  Given a trained model, this has  historically  been  accomplished  through maximum a posteriori (MAP) decoding, which seeks  to find  the  mode of  the  generated conditional  distribution  over  all  possible  output sequences.  However, recent work has shown that  MAP  decoding  may  not  be  the  optimal decoding  rule.    A  new  approach,  known  as MBR decoding, shows promise  in  addressing  the  shortcomings  of MAP  decoding,  though  it  has  not  yet  been shown  to  fix  length  bias  and  token  probability  bias.  



## Aims

In this project, we seek to:

- Apply  several  classic  sampling methods (beam search, ancestral sampling, top-k sampling, and top-p sampling) to produce candidate translations for the MBR decoding algorithm 
- Compare and contrast the performance of classic beam search and MBR decoding with different candidate generation methods
- Provide a robust  characterization  of  the  biases  present in  each  method’s  selected  translations



## Results

The results of our project:

- Confirm  that  classic  beam  search  and  MBR decoding with all candidate generation methods explored exhibit length bias and token frequency bias
- Suggest that classic beam search marginally outperforms all forms of MBR decoding  in  those  areas
- Indicate that the direction and magnitude of length bias strongly correlates with the length of the reference sentence



## Repository description

This repository contains the dataset used for the project, code to reproduce results and analyses, and saved results. Specifically, the repository contains the following folders and files:


### ```dataset``` folder

We use a subset of the English-French parallel corpus from the [Tatoeba Project](https://tatoeba.org/en), downloading the processed tab-delimited parallel corpus from http://www.manythings.org/anki/. The subset contains 2,500 English-French sentence pairs, randomly sampled from the top 5\% longest sentences in the full English-French parallel corpus. We sampled accordingly to upsample longer sentences in order to study length bias. In the subset, English sentence lengths range between 6-34 words, with an average of 12.48 words, and French sentence lengths range between 6-37 words, with an average of 13.22 words.


