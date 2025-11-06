### Setup:
2. Install requirements:

```
conda env remove -n xplainer_env
conda create -n xplainer_env python=3.9 -y
conda activate xplainer_env
pip install uv
uv pip install hi-ml-multimodal
uv pip install pandas==2.0.3 numpy==1.24.3 scikit-learn
```
   
3. Download data
   
CheXpert:
- download data from https://stanfordaimi.azurewebsites.net/datasets/23c56a0d-15de-405b-87c8-99c30138950c
- copy 'test_labels.csv' and the image folder 'test' into 'data/chexpert'

ChestXRay14:
- download data from 'https://nihcc.app.box.com/v/ChestXray-NIHCC/folder/36938765345'
- use the script 'preprocess_chestxray14' to download the data
- copy 'images', 'test_list.txt' and 'Data_Entry_2017_v2020.csv' into 'data/chestxray14'
- run
```
python -m preprocesss_chestxray14
```

### Reproduce our results:

srun --partition=agpu06 --time=01:00:00 --cpus-per-task=32 --nodelist=c1905 --pty bash

run
```
python -m inference --dataset chexpert
```
or
```
python -m inference --dataset chestxray14
```
