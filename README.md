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



## Repository description

