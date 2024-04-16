# NLP-Project-Investigating-Bias-in-multilang-Models-Cross-Lingual-Transfer-of-Debiasing-Techniques

Instruction to Run the project 

## Instructions to Run the Project

### 1) Set Up Environment
Create a new environment to install the required files using Conda:


Note: Use Python version 3.7.

### 2) Install Required Libraries
Install all the required libraries:



### 3)Dowload all the dataset 


|Dataset | link|
|--------|----------|
|Wikipedia 2.5 en |[link](https://drive.google.com/file/d/1nGcRFOBep_M7HjvC_qM-9JFee_rWQRQO/view?usp=sharing)|
|Wikipedia 10 en  |[link](https://drive.google.com/file/d/1yQbZMGuUa3taP_xoGThRq0vkb9Kj0uC-/view?usp=sharing)|
|Wikipedia 2.5 fr |[link](https://drive.google.com/file/d/1TAQYkB9kniSX5-2IppPJR8xiTbMFRwrx/view?usp=sharing)|
|Wikipedia 10 fr  |[link](https://drive.google.com/file/d/1HEQ-55kH4BIGBHU_84FsyMZwLg3kgwJX/view?usp=sharing)
|Wikipedia 2.5 de |[link](https://drive.google.com/file/d/1RRizrCShzT7yk8hRMDN6Zj-HoyfqQkPt/view?usp=sharing)| 
|Wikipedia 10 de  |[link](https://drive.google.com/file/d/1pvKXfK-oyfE-_j1M3BL4LD94XT10p4go/view?usp=sharing)|
|Wikipedia 2.5 nl |[link](https://drive.google.com/file/d/1jCUWl0kT0TJsljeMZvZEkC4tEWjSxMM8/view?usp=sharing)|
|Wikipedia 10 nl  |[link](https://drive.google.com/file/d/1Mhn0kG2MZi36CNImBNDhiiNSXh-h9-Uc/view?usp=sharing)| 

### 4) Reproduce Results

   ## Base
      
       1) python experiments/crows.py --persistent_dir="" --model="BertForMaskedLM" --model_name_or_path="bert-base-multilingual-uncased" --bias_type="race" --sample="false" --seed=0 --lang="en"
       2) python experiments/crows.py --persistent_dir="" --model="BertForMaskedLM" --model_name_or_path="bert-base-multilingual-uncased" --bias_type="race" --sample="false" --seed=1 --lang="en"
       3) python experiments/crows.py --persistent_dir="" --model="BertForMaskedLM" --model_name_or_path="bert-base-multilingual-uncased" --bias_type="race" --sample="false" --seed=2 --lang="en"
      
   ##  sentence debias:
      1) python experiments/sentence_debias_subspace.py --persistent_dir="data/" --model="BertModel" --model_name_or_path="bert-base-multilingual-uncased" --bias_type="gender" --lang_debias="en"
      similarly
  ##  densray: 
     1) python experiments/densray_subspace.py --persistent_dir="data/" --model="BertModel" --model_name_or_path="bert-base-multilingual-uncased" --bias_type="gender" --lang_debias="en"
  ## inlp:

      1) python experiments/inlp_projection_matrix.py --persistent_dir='/path/to/directory' --model BertModel --model_name_or_path 'bert-base-multilingual-uncased' --bias_type religion --n_classifiers 80 --seed 0 --         lang_debias fr
      2) python experiments/crows_debias.py --persistent_dir='/path/to/directory' --model INLPBertForMaskedLM --model_name_or_path 'bert-base-multilingual-uncased' --projection_matrix '/path_to_projection_matrix' --         bias_type gender --sample false --seed 0 --lang_eval en --lang_debias fr

   ## CDA & Dropout:
   
      1) python experiments/run_mlm.py --model_name_or_path "bert-base-multilingual-uncased" --cache_dir "[path]/cache/" --do_train --train_file "data/text/wiki-fr_sample_10.txt" --validation_split_percentage 0 --         max_steps 2000 --per_device_train_batch_size 4 --gradient_accumulation_steps 128 --max_seq_length 512 --save_steps 500 --preprocessing_num_workers 4 --counterfactual_augmentation "race" --persi
      2)  python experiments/crows_dropout_cda.py --persistent_dir="[path]" --model="dropout_mbert" --model_name_or_path="[path_to_dir]" --bias_type="gender" --sample='false' --seed=0 --lang_eval='en' --          
         lang_debias='fr' --seed_model=0







   
      
