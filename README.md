# AutoAvatar-Installation-Guide
## DFaust Data Preparation
 - Create "DFaust" folder under `<workspace_folder>`.
```
cd <workspace_folder>
mkdir DFaust
```
 - Download [SMPL+H parameters](https://amass.is.tue.mpg.de/index.html), gets "DFaust.tar.bz2".
   - Move "DFaust.tar.bz2" to `<workspace_folder>/DFaust`, and unzip to get folder `DFaust_67/...`
 - Download [DFaust Scan Data](https://dfaust.is.tue.mpg.de/index.html), gets "50002.tar.xz".
    - Here use 50002 as example for the following steps.
    - Unzip "50002.tar.xz" to `<workspace_folder>/DFaust`, and gets folder `scans/50002/...`
 - Download [SMPL model](https://smpl.is.tue.mpg.de/index.html), gets "basicmodel_m_lbs_10_207_0_v1.0.0.pkl", "basicModel_f_lbs_10_207_0_v1.0.0.pkl".
    - Move "basicmodel_m_lbs_10_207_0_v1.0.0.pkl", "basicModel_f_lbs_10_207_0_v1.0.0.pkl" to `<workspace_folder>/SMPL`
 - Download [SMPL meta data](https://drive.google.com/drive/folders/1ZhS_0FFJ38Mj9pZrkr5HUTurCaofjLSk?usp=sharing), gets "uv_info.npz", "smpl_resample_idxs.npz".
    - Move "uv_info.npz", "smpl_resample_idxs.npz" to `<workspace_folder>/SMPL`
 - Download [SMPL+H](https://mano.is.tue.mpg.de/index.html), gets "smplh.tar.xz".
    - Move "smplh.tar.xz" to `<workspace_folder>/SMPL`, and unzip to get folder `smplh/...`
 - Download [DMPLs](https://smpl.is.tue.mpg.de/), gets "dmpls.tar.xz".
    - Move "dmpls.tar.xz" to `<workspace_folder>/SMPL`, and unzip to get folder `dmpls/...`
 - Clone [AutoAvatar](https://github.com/facebookresearch/AutoAvatar.git) to `<workspace_folder>`
```
cd <workspace_folder>
git clone https://github.com/facebookresearch/AutoAvatar.git
```
 - Create `external` folder under `<workspace_folder>` 
```
cd <workspace_folder>
mkdir external
```
 - Clone [human_body_prior](https://github.com/nghorbani/human_body_prior.git) under `external` folder.
```
cd <workspace_folder>/external
git clone https://github.com/nghorbani/human_body_prior.git
```
 - Now we should have the folder structure as [link](https://github.com/nick8592/AutoAvatar-Installation-Guide/blob/main/folder_structure.md).

## Environment Setup
 - Install Anaconda or Miniconda. Then run the setup script.
```
cd <workspace_folder>/AutoAvatar
conda create -n AutoAvatar python=3.8
conda activate AutoAvatar
bash setup.sh
```
 - Install [human_body_prior](https://github.com/nghorbani/human_body_prior.git) for DFaust data preprocess.
```
cd <workspace_folder>/external
cd human_body_prior
python setup.py develop
```

## Data Preprocess
 - Run `DFaust_generate.py` to preprocess data.
 - Note that this may take a long time due to the mesh simplification.
 - Mesh simplification is to speed up data loading during training.
 ```
cd <workspace_folder>/AutoAvatar
export PYTHONPATH=<workspace_folder>/AutoAvatar
python data/DFaust_generate.py --ws_dir <workspace_folder>
 ```
 

