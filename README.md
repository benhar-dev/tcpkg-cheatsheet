# Common TwinCAT TcPkg Commands

Further commands can be found [here](https://infosys.beckhoff.com/english.php?content=../content/1033/tc3_installation/15698626059.html&id=)

## Uninstallation

### Full Uninstallation of 4026.x

```bash
tcpkg uninstall all
```

### Full Uninstallation of 4024.x

You must first install the migrate tool, then use this to clean the installation. You may need to restart your PC after the first step.

```bash
tcpkg install TwinCAT.XAE.MigrateCli

## to test the uninstall
TcMigrateCmd.exe clean

## or to progress with the uninstall
TcMigrateCmd.exe clean --whatif false
```

## Working with packages: Installing, upgrading, and uninstalling

### List all installed packages

```bash
tcpkg list -i
```

### Install a package with a specific version

```bash
tcpkg install TwinCAT.XAE.PLC=3.6.16
```
