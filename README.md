# DFFNDDS

DFFNDDS: PREDICTION OF SYNERGISTIC DRUG COMBINATIONS WITH DUAL FEATURE FUSION NETWORKS

In the "Comparison between different types of models" experiment of the study "A Review of Deep Learning Approaches for Drug Synergy Prediction in Cancer", DFFNDDS is retrained using the DrugComb dataset, and the hyperparameters are readjusted to ensure a fair comparison under consistent experimental conditions:

* batchsize=256
* learning rate=0.0001
* epoch=200

## requirements:

DFFNDDS requires:
* torch : 1.10.2
* cuda :  11.3
* python : 3.8.12

## Steps:
1. The input SMILES string is encoded by a fine-tuned BERT model, converting the features into vectors. The code of the fine-tuned BERT model is showed in simcse.py
2. The output of the SMILES encoder, hashed atom pair fingerpints and gene expressions of cancer cell lines are input into the projector module, mapping the inputs to the same dimension. The dataset.py handles the input data , in model_h.py the inputs are mapped into the same dimension.   
3. To fuse the features, we utilize two networks (multi-head attention mechanism and highway network) to extract and combine the input features in the dual fusion block. The dual feature fusion mechanism is utilized in the construction of neural networks, which in the model_h.py. 
4. The outputs of the two networks are concatenated to obtain the final feature representation, which is propagated through the linear layer, the model_h.py contains the concatenation. The output of the model_h.py is the input of the prediction of the drug pairs in main-split.py.


## Running Code:
python main-split.py
