##### Necesita los siguientes paquetes
```
ant compat-gcc-34-g77 java-1.6.0-openjdk java-1.6.0-openjdk-devel freetype freetype-devel zlib-devel mpich2 readline-devel zeromq zeromq-devel gsl gsl-devel libxslt libpng libpng-devel libgfortran mysql mysql-devel libXt libXt-devel libX11-devel mpich2 mpich2-devel libxml2 xorg-x11-server-Xorg dejavu* python-devel python-pip sqlite-devel tcl-devel tk-devel R R-devel ghc
```
##### QIIME v 1.9.1
```
https://github.com/biocore/qiime/archive/1.9.1.tar.gz
```
##### Dependencias python
```
pip install setuptools
pip install numpy
pip install qiime
```
##### Compilar e instalar
```
python setup.py build
python setup.py install --install-scripts=/path/to/bin/ --install-purelib=/path/to/lib/
```
##### Dependencias R (Version ≥ 3.0.0)
```
install.packages(c('ape', 'biom', 'optparse', 'RColorBrewer', 'randomForest', 'vegan'))
source('http://bioconductor.org/biocLite.R')
biocLite(c('DESeq2', 'metagenomeSeq'))
q()
```

##### Dependencias QIIME 1.9.0
```
git clone git://github.com/qiime/qiime-deploy.git
git clone git://github.com/qiime/qiime-deploy-conf.git
cd qiime-deploy/
python qiime-deploy.py $HOME/bin/qiime_software/ -f $HOME/bin/qiime-deploy-conf/qiime-1.9.0/qiime.conf --force-remove-failed-dirs
source $HOME/.bashrc
```
##### Test instalación
```
print_qiime_config.py -tf
```
