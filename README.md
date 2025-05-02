# Common TwinCAT TcPkg Commands

## Disclaimer

This is a personal guide not a peer reviewed journal or a sponsored publication. We make
no representations as to accuracy, completeness, correctness, suitability, or validity of any
information and will not be liable for any errors, omissions, or delays in this information or any
losses injuries, or damages arising from its display or use. All information is provided on an as
is basis. It is the reader’s responsibility to verify their own facts.

The views and opinions expressed in this guide are those of the authors and do not
necessarily reflect the official policy or position of any other agency, organization, employer or
company. Assumptions made in the analysis are not reflective of the position of any entity
other than the author(s) and, since we are critically thinking human beings, these views are
always subject to change, revision, and rethinking at any time. Please do not hold us to them
in perpetuity.

Further commands can be found [here](https://infosys.beckhoff.com/english.php?content=../content/1033/tc3_installation/15698626059.html&id=)

## Installation 

### Offline installation of 4026 (i.e. no internet connection)
Notes can be found [here...](https://github.com/benhar-dev/tc4026-offline-install)

### Full Migration installation of 4026.x using only CLI

```bash
# start cmd as admin
tcpkg install TwinCAT.XAE.MigrateCli
# once installed restart cmd as admin
TcMigrateCmd upgrade --whatIf False
```

## Uninstallation

### Full Uninstallation of 4026.x

```bash
tcpkg uninstall all
```

### Full Uninstallation of 4024.x

You must first install the migrate tool, then use this to clean the installation. You may need to restart your PC after the first step.

```bash
################################
#                              #
#  Read the full instructions  #
#    first before starting     #
#                              #
################################

## Install the package manager from the main beckhoff website.

## Once installed, do not open the package manager from the UI.
## Instead follow the instructions below using a CMD window
## with admin rights.

## Add the source, you will be prompted to enter your myBeckhoff password
tcpkg source add -n "Beckhoff Stable Feed" -s "https://public.tcpkg.beckhoff-cloud.com/api/v1/feeds/stable/" --priority=1 -u "<your myBeckhoff email>"

## Install the migrate tool
tcpkg install TwinCAT.XAE.MigrateCli

################################
#                              #
#    Now close and reopen      #
#         cmd as admin         #
#                              #
################################

## progress with the uninstall
TcMigrateCmd.exe clean --whatIf False

## once done, you can restart your pc and uninstall the package manager using add/remove programs
```

## Working with sources

### List all configured sources
```bash
tcpkg source list
```
### Verify the stable source is available
```bash
tcpkg source verify "Beckhoff Stable Feed"
```
### Typical Sources
```bash
# all current packages and workloads
tcpkg source add -n "Beckhoff Stable Feed" -s "https://public.tcpkg.beckhoff-cloud.com/api/v1/feeds/stable/" --priority=1 -u "<your myBeckhoff email>"

# all outdated versions 
tcpkg source add -n "Beckhoff Outdated Feed" -s "https://public.tcpkg.beckhoff-cloud.com/api/v1/feeds/outdated/" --priority=2 -u "<your myBeckhoff email>"

# Soon to be released packages and workloads (i.e. Beta versions).   
tcpkg source add -n "Beckhoff Testing Feed" -s "https://public.tcpkg.beckhoff-cloud.com/api/v1/feeds/testing/" --priority=3 -u "<your myBeckhoff email>"
```

## Working with packages and workloads: Installing, upgrading, and uninstalling

### List all installed packages

```bash
tcpkg list -i
```

### List all of the available workloads on the system

```bash
tcpkg list -t workload
```

### Install a package with a specific version

```bash
tcpkg install TwinCAT.XAE.PLC=3.6.16
```

### Repairing a package

```bash
tcpkg repair twincat.xae.plc
```

### Downgrading a package

```bash
 tcpkg upgrade twincat.standard.xae=4026.13.0 --allow-downgrade
```
