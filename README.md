# resnet-copd

<span style="color:red">This site is under construction.</span>

We currently have posted the model weights of ResNets (Python3.6, Keras 2.2.0) that have been trained to detect spirometrically defined Chronic Obstructive Pulmonary Disease (COPD) from a region of a chest computed tomography (CT) scan.

Details of the entire pipeline and validation experiments conducted on the datasets listed below will be posted in the near future (ETA of Jan 2020).

## Datasets employed for model development and external validation 
1. [Evaluation of COPD Longitudinally to Identify Predictive Surrogate End-points (ECLIPSE)](http://eclipse-copd.com)
2. [Pan-Canadian Early Detection of Lung Cancer (PanCan)](https://www.tfri.ca/our-research/research-project/early-detection-of-lung-cancer---a-pan-canadian-study)
3. [COPDGene](http://www.copdgene.org/)

## Upload schedule ## 
We aim to post the following scripts in the near future:
- spatial normalization (via the ANTS image registration toolkit)
- lung mask generation (Python 3.6)

## Models

| Model variant        | Weights           |  Notes  |
| ------------- |-------------| -----|
| ResNet50  (#3)  | Being uploaded to [here](https://drive.google.com/drive/u/5/folders/1nrT9MfkIMXCon9YYzRfdVwFNH7dlGdZA) | Usage notes below |
| ResNet101 (#4)     |    Being uploaded to [here](https://drive.google.com/drive/u/5/folders/1nrT9MfkIMXCon9YYzRfdVwFNH7dlGdZA)   |  Usage notes below  |
| ResNet152 (#5)     |    Being uploaded to [here](https://drive.google.com/drive/u/5/folders/1nrT9MfkIMXCon9YYzRfdVwFNH7dlGdZA)  |   Usage notes below |

Usage notes:
1. On ROI inputs:

- Filenames with character sequence im:-80 use Region ID A as inputs
- Filenames with character sequence im:-60 use Region ID B as inputs
- Filenames with character sequence im:-40 use Region ID C as inputs

2. Example explaining the coding scheme of filenames:

04-28_diagnose-mx_p_im:-80_2fd:3_md:004_fz:000_op:2_wt:0.0_dc:07_bs:08_da:10_ls:2_dp:0.0_lr:0.000100_sh:3_tr:3_mk:1_pt:0_db:0_HE_best2.h5

| Character sequence  | Brief description of training configuration |
| ------------- |:-------------|
| 04-28  |  date the file was created |
| diagnose-mx | classification task (COPD defined based on FEV1 and FVC measured with maximal values) |
| \_p | Training dataset ID (i.e. PanCan) |
| im:-80 | Region ID (i.e. A) |
| md:004 | model #4, i.e. ResNet101 |
| fz:000 | no freezing of layers|
| op:2| optimization algorithm #2 |
| dc:07 | decay scheme 7|
| bs:08: | batch size of 8|
| da:10 | data augmentation using random spatial transformations parameterized by value of 10 |
| lr:0.000100 | learning rate |
| sh:3 | shuffling scheme |
| mk:1| masking was done|
