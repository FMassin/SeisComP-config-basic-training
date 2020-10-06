# SeisComP configuration for basic training 
Git versionning system for SeisComP3 configuration files. One branch per system.

# WARNING
Do do switch branch if you're not sure.

# How to add system

```
scgitinit
cd $SEISCOMP_ROOT
git checkout -b basic-training-<YOUR NAME>
scgitinit
git commit -m "Adds <YOUR NAME>"
git remote add origin https://github.com/FMassin/SeisComP-config-basic-training.git
git push origin basic-training-<YOUR NAME>
```
