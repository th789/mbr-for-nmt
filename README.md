# mbr-for-nmt



## Characterizing minimum Bayes risk (MBR) decoding for neural machine translation (NMT)

This project characterizes the performance of MBR decoding for NMT when using various candidate generation methods, by examining BLEU score, length bias, and token frequency bias in resulting translations. The project motivation, goals, and results are described below. The final project paper, which contains a full project description, can be found [here](https://drive.google.com/file/d/1VmS6ebEfjTXjNV_h-IiPGqyr74eaB_ky/view?usp=sharing).

This repository contains the dataset used for the project, code to reproduce results and analyses, and saved results. The folders and files of this repository are described in detail below.



## Motivation

The aim of NMT is to output the best possible translation of a given input text.  Given a trained model, this has  historically  been  accomplished  through maximum a posteriori (MAP) decoding, which seeks  to find  the  mode of  the  generated conditional  distribution  over  all  possible  output sequences.  However, recent work has shown that  MAP  decoding  may  not  be  the  optimal decoding  rule.    A  new  approach,  known  as MBR decoding, shows promise  in  addressing  the  shortcomings  of MAP  decoding,  though  it  has  not  yet  been shown  to  fix  length  bias  and  token  probability  bias.  



## Aims

In this project, we:

- Apply  several  classic  sampling methods (beam search, ancestral sampling, top-k sampling, and top-p sampling) to generate candidate translations for the MBR decoding algorithm 
- Compare and contrast the performance of classic beam search and MBR decoding with different candidate generation methods
- Provide a robust  characterization  of  the  biases  present in  each  method’s  selected  translations (length bias and token frequency bias)



## Results

The results of our project:

- Suggest that classic beam search marginally outperforms all forms of MBR decoding in terms of BLEU score, length bias, and token frequency bias
- Confirm  that  classic  beam  search  and  MBR decoding with all candidate generation methods explored exhibit length bias and token frequency bias
- Indicate that the direction and magnitude of length bias strongly correlates with the length of the reference sentence



## Repository description

This repository contains the dataset used for the project, code to reproduce results and analyses, and saved results. Specifically, the repository contains the following folders and files:


### ```dataset``` folder

We use a subset of the English-French parallel corpus from the [Tatoeba Project](https://tatoeba.org/en), downloading the processed tab-delimited parallel corpus from http://www.manythings.org/anki/. The subset contains 2,500 English-French sentence pairs, randomly sampled from the top 5\% longest sentences in the full English-French parallel corpus. We sampled accordingly to upsample longer sentences in order to study length bias. In the subset, English sentence lengths range between 6-34 words, with an average of 12.48 words, and French sentence lengths range between 6-37 words, with an average of 13.22 words.

- ```fra.txt```: Full English-French parallel corpus from the Tatoeba Project

- ```tatoeba_df_subset.pkl```: Subset of English-French parallel corpus from the Tatoeba Project. Code to obtain this subset can be found at ```code/generate-candidates-and-samples.ipynb```.



### ```code``` folder

This folder contains code files to reproduce results and analyses. 

- ```generate-candidates-and-samples.ipynb```: Processes data. Generates candidate translations (via beam search, ancestral sampling, top-k sampling, and top-p sampling) and sample translations (via ancestral sampling) to be used in MBR decoding. Also performs beam search decoding as a baseline. Code outputs are stored in ```results/candidate-and-sample-translations```. Uses the [Unified Text-to-Text Transformer model (Raffel et al., 2020)](https://arxiv.org/abs/1910.10683) accessed through Hugging Face (call to model included in notebook).

- ```mbr-decoding.ipynb```: Performs MBR decoding using candidate and sample translations outputted by generate-candidates-and-samples.ipynb. MBR decoding selects the best translation among the candidate translations. Code outputs are stored in results/final-translations. Uses the [mbr-nmt package](https://github.com/Roxot/mbr-nmt) by [Eikema and Aziz (2021)](https://arxiv.org/abs/2108.04718) (installation and runs included in notebook).

- ```analysis-calculate-bleu-scores.ipynb```: Calculates BLEU scores for translations produced using beam search decoding and MBR decoding (using various candidate generation methods).

- ```analysis-bleu-and-length-bias.ipynb```: Analyzes BLEU score performance and length bias in the translations produced by beam search decoding and MBR decoding (using various candidate generation methods).

- ```analysis-token-frequency-bias.ipynb```: Analyzes token frequency bias in the translations produced by beam search decoding and MBR decoding (using various candidate generation methods).


### ```results``` folder

This folder contains saved results.

- ```candidate-and-sample-translations``` folder: Contains candidate translations and sample translations outputted by ```code/generate-candidates-and-samples.ipynb```. Each file contains a ```_c.txt``` counterpart, a reformatted version of the file used by the [mbr-nmt package](https://github.com/Roxot/mbr-nmt).

- ```final-translations``` folder: Contains final translations from beam search decoding (```baseline_beam_X.txt``` files) and MBR decoding using various candidate generation methods (```samples_ancestral_n200_candidates_X.txt``` files). Output of ```code/mbr-decoding.ipynb```.









