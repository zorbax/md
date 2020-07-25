# Conda
### Miniconda conf

cd $HOME/bin
wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh -b -p $HOME/bin/miniconda3

### Clean and update all
conda clean --all
conda update conda
conda update --all

### Remove env
conda env remove -n qiime

### Upgrade Conda
conda update -n base conda

### Create a env in a specific channel with a particular python version with specific version package
conda create -y -n qiime python=2.7 qiime matplotlib==1.4.3 numpy==1.10.4 h5py==2.6.0 mock nose -c bioconda

### Python 2.7 env
conda create -y -n py27 python=2.7


### Biostar
conda create -y -n biostar python=3
source activate biostar
source info --envs

### Add channels
conda config --add channels r
conda config --add channels conda-forge
conda config --add channels bioconda
curl http://data.biostarhandbook.com/install/conda.txt | xargs conda install -y


### Data science
conda create -y -n data python=3
conda install -y numpy pandas scikit-learn matplotlib seaborn ipython-notebook

### Export an environment
conda env export -n course-env -f course-env.yml


# conda create --name environment_name python=3.6
# conda env export > environment.yml
# conda env create -f environment.yml

# remove (base) from prompt
conda config --set changeps1 False