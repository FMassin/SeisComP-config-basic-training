# SeisComP configuration for basic training 
Git versionning system for SeisComP3 configuration files. One branch per system.

# WARNING
Do do switch branch if you're not sure.

# How to back your system locally
```
scgitinit
git -C $SEISCOMP_ROOT commit
`Ã```
You will be prompt to described your last changes, do it, save and exit to save your changes.

# How to add your system

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
