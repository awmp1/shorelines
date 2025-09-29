## Compile
```
mcc -m functions/runShorelineS.m
```
# Run
Go to https://github.com/fernanqv/shorelines --> Log in GitHub --> Code --> Codespaces --> + (New codespaces) --> Wait untill the VSCode environment is loaded.

Go to the VSCode terminal and run:

```
bash
cd compiled
chmod +x launchShorelineS.sh runShorelineS.exe 
./launchShorelineS.sh /opt/matlabruntime/R2025b/ 'input.txt' 
```