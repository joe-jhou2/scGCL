# scGCL: Graph contrastive Learning on scRNAseq data

This repository is for the reproduced implementation of [scGCL: an imputation method for scRNA-seq data based on graph contrastive learning ](https://doi.org/10.1093/bioinformatics/btad098).

![fram1 (1)](https://github.com/zehaoxiong123/scGCL/blob/main/scGCL.png)

The paper proposes a method known as scGCL, which stands for single-cell Graph Contrastive Learning. By employing contrastive learning within a graph theory framework, scGCL is adept at capturing both the global and local semantic information between the cells, enhancing both the prediction and reconstruction of missing gene expression values. Additionally, it utilizes an autoencoder framework based on the ZINB distribution, which is designed to model the global probability distribution of gene expression data. This approach provides a solution to measure dropout more accurately.
scGCL not only diminishes noise in the data but also enhances the precision of clustering and classification efforts. It increases the accuracy of differential expression analyses, and aids in the integration of data from various sources, therefore simplifying the overall complexity of handling these scRNA-seq datasets.
For our reproduction of the paper, we chose to focus on one hypothesis which is that we hypothesize that scGCL will exhibit better clustering performance and imputation performance than other existing methods.
## System Requirements

- Python: 3.10
- numpy: 1.25.2
- pandas: 2.0.3
- sklearn: 1.2.2
- h5py 3.9.0
- scipy: 1.11.4
- torch: 2.2.1+cu121
- faiss 1.8.0
- argparse: 1.1
- anndata: 0.10.7
- scanpy: 1.10.1
- torch_geometric: 2.5.2
- tensorboardX: 2.6.2.2
- matplotlib: 3.7.1

## Hyperparameters

- Learning Rate: 0.001
- k-value: 15
- Distance measurement: cosine

## Arguments
|    Parameter    | Introduction                                                 |
| :-------------: | ------------------------------------------------------------ |
|    dataset     | A h5 file. Contains a matrix of scRNA-seq expression values,true labels, and other information. |
|  task  | Downstream task. Supported tasks are: node, clustering, similarity                                     |
| es | Early Stopping Criterion                                   |
|     epochs     | Number of training epochs                                    |

## Computational Requirements

- Number of epochs: 300
- Average run time of one epoch: ~24 seconds per epoch
- Total run time for 300 epochs: 1 hour 59 minutes 46 seconds
- Type of hardware used: GPU (on google colab)

## Code Execution

To execute the code, run all cells in Google Colab [here](https://colab.research.google.com/drive/1Xt6CvyWiQBu_v8UwNq5uxTFqmuC2yxS8?usp=sharing).

## Data and Pre-Trained Model
Although the original paper compared 14 different datasets, we focused our efforts on dataset Adam.
The Adam dataset is stored in data.tgz and our pre-trained model is stored in model_checkpoints.tgz. Both are downloaded by executing the code in section (2) Data.

## Training

For efficiency purposes, we pre-trained the model and stored the checkpoint to use in evaluation. Executing the code in section (5) Training will train the model for 1 epoch for demonstration purposes.

## Evaluation

Evaluation is done on the pre-trained model by executing the code in section (6) Evaluation.

## Results

Our model achieves the following performance on the Adam dataset:

| NMI  | ARI |
| ---------------- | -------------- |
|  0.84      |      0.83      |