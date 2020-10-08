# SeisComP configuration for basic training 
Git versionning system for SeisComP3 configuration files. One branch per system.

# WARNING
Do do switch branch if you're not sure.

# How to backup your system localy

```
scgitinit
git -C $SEISCOMP_ROOT commit
```
You will be asked to describe your last changes in your default text editor. Do it, save and exit to backup your last changes.

# How to add your backup online
Do the follow one time only:
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

# How to optimize bindings from mseed file
Declare the following fonction, eventually in `~/.profile`: 
```bash
function mseed2binding () {
        ls $@ |while read F;
        do
                for CHAN in "Z" "BHZ" "HNZ" "SHZ" "EHZ" "HHZ" :
                do
                        scart -I $F  -v --test 2>&1|awk '$1~/Z$/{print $1}'|sort -u|grep $CHAN|while IFS='.' read N S L C;
                        do
                                K=$SEISCOMP_ROOT/etc/key/station_${N}_$S
                                P=$SEISCOMP_ROOT/etc/key/global/profile_$L$C;
                                grep detecStream $P >/dev/null || echo detecStream >> $P;
                                grep detecLocid $P >/dev/null || echo detecLocid >> $P;
                                sed -i 's;detecStream.*;detecStream = '$C';' $P;
                                sed -i 's;detecLocid.*;detecLocid = \"'$L'\";' $P;
                                grep global $K || echo global >> $K;
                                sed -i 's;global.*;global:'$L$C';' $K;
                                echo $K;
                        done
                done
        done
}
```
Use the function:
```
source ~/.profile
mseed2binding "<mseed file names pattern>"
```
