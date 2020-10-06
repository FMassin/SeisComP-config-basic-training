# SeisComP configuration for basic training 
Git versionning system for SeisComP3 configuration files. One branch per system.

# WARNING
Do do switch branch if you're not sure.

# How to backup your system localy

```
scgitinit
git -C $SEISCOMP_ROOT commit
```
You will be asked to described your last changes in your default text editor. Do it, save and exit to save your changes.

# How to add your backup online

```
cd $SEISCOMP_ROOT
git checkout -b basic-training-<YOUR NAME>
git commit -m "Adds <YOUR NAME>"
git remote add origin https://github.com/FMassin/SeisComP-config-basic-training.git
git push origin basic-training-<YOUR NAME>
```

# How to update your backup and sync online

```
scgitinit
git -C $SEISCOMP_ROOT commit 
git -C $SEISCOMP_ROOT push origin basic-training-<YOUR NAME>
```
