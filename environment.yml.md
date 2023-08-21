name: wordnet
channels:
- anaconda
- pytorch
- defaults
dependencies:
- pip
- python=3.6
- wn
- sklearn
- pytorch=1.0.0
- pandas
- transformers
- sentence_transformers
- tqdm
- lxml
- pip:
  - iopath
