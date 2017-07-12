# oxy-snapshot
A bash script to automate backing up the OXYCOIN blockchain<br>
Version: v0.1<br>
For more information about OXYCOIN, please visit - https://oxycoin.io

## Prerequisites
    - You need to have (not run as) sudo privileges

## Installation
Execute the following commands:
```
cd
git clone https://github.com/Oxycoin/oxy-snapshot
cd oxy-snapshot/
bash oxy-snapshot.sh help
```

## Note
when using oxy-checker the following commands are not needed, oxy-checker will make the daily snapshots

## Available commands

    - create
    - restore
    - log
    - schedule
		- hourly
		- daily
		- weekly
		- monthly

### Create
Command _create_ is for create new snapshot, example of usage:<br>
`bash oxy-snapshot.sh create`<br>
Automaticly will create a snapshot file in new folder called snapshot/.<br>
Don't require to stop you node app.js instance.<br>
Example of output:<br>
```
   + Creating snapshot                                
  --------------------------------------------------
  OK snapshot created successfully at block  49037 ( 43 MB).
```
Also will create a line in the log, there you can see your snapshot at what block height was created.<br>

### Restore
Command _restore_ is for restore the last snapshot found it in snapshot/ folder.<br>
Example of usage:<br>
`bash oxy-snapshot.sh restore`<br>
<br>
Automaticly will pick the latest snapshot file in snapshot/ folder to restore the OXYCOIN database.<br>
If you want to restore a specific file please (for this version) delete or move the other files in snapshot/ folder.<br>
You can use the _log_ command to better pick up your restore file.<br>

### Log
Display all the snapshots created. <br>
Example of usage:<br>
`bash oxy-snapshot.sh log`<br>
<br>
Example of output:<br>
```
   + Snapshot Log                                                                  
  --------------------------------------------------                               
  20-10-2016 - 20:59:06 -- Snapshot created successfully at block  48967 ( 43 MB)  
  20-10-2016 - 21:36:07 -- Snapshot created successfully at block  49037 ( 43 MB)  
  --------------------------------------------------END                            
```

### Schedule
Schedule snapshot creation periodically, with the available parameters:

    - hourly
    - daily
    - weekly
    - monthly

Example: `bash oxy-snapshot.sh schedule daily`
<br>

-------------------------------------------------------------

### Notice
You will have a folder in ~/oxy-snapshot/ called `snapshot/` where all your snapshots will be created and stored.
If you want to use a snapshot from different place (official snapshot for example or other node) you will need to download the snapshot file (with prefix: oxycoin_db*) and copy it to the `~/oxy-snapshot/snapshot/` folder.
After you copy the oxycoin_db*.tar file you can restore the blockchain with: `bash oxy-snapshot.sh restore` and will use the last file found in the snapshot/ folder.<br>
If you use the `schedule` command be aware you will have a log file located in `~/oxy-snapshot/cron.log` with this you will know what is happened with your schedule.

### Upgrade
If you are in a version prior to v0.1 you can upgrade with the following commands:
```
cd ~/oxy-snapshot/
git checkout .
git pull
```

## Contributions
* [MrGr](https://github.com/mrgrshift/)
* [Lepetitjan](https://github.com/lepetitjan/)
