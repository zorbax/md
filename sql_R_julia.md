# JuPyteR
## R

```r
%load_ext rpy2.ipython
```
Block code
```r
%%R
R.version.string
```

Cell mode
```
Z = np.array([1,4,5,10])

### -i input
%R -i Z mean(Z)

### -o output

%R -o W W=Z*mean(Z)

print(W)
```

##SQL

```
pip install ipython-sql 
%load_ext sql 
%sql sqlite:// 
mysql://scott:tiger@localhost/foo
```
