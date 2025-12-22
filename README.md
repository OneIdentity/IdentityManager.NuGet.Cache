**One Identity open source projects are supported through [One Identity GitHub issues](https://github.com/OneIdentity/IdentityManager.ApiSdk/issues) and the [One Identity Community](https://www.oneidentity.com/community/). This includes all scripts, plugins, SDKs, modules, code snippets or other solutions. For assistance with any One Identity GitHub project, please raise a new Issue on the [One Identity GitHub project](https://github.com/OneIdentity/IdentityManager.ApiSdk/issues) page. You may also visit the [One Identity Community](https://www.oneidentity.com/community/) to ask questions. Requests for assistance made through official One Identity Support will be referred back to GitHub and the One Identity Community forums where those requests can benefit all users.**

# Identity Manager NuGet cache files

This repository contains packages for deploying a local [NuGet](https://www.nuget.org/) cache with the NuGet packages required to compile the Identity Manager database in an air-gapped environment.

## Version information

The NuGet packages provided are for version 9.3.1 (v93-311513) of One Identity Manager.

## Files included

- ExternalNugetPackages_9.3.1-311513.zip (SHA256: 1A468CAC2A65A295E78CB51F5CC2E0DD77FC2A0D51E46B89EA155355487F47F5)
- ExternalNugetPackages_9.3.1-311513.zip.sha256 (SHA256: D9F1F14649DAF84A94CE1C00C2180EFE5D99F44DB943FF6E6BEC263E1AAA04D6)

## Default module coverage

The NuGet packages provided cover all dependencies required for a database with the following modules: AAD, ACN, ADS, AOB, APC, ARS, ATT, CAP, CHS, CIM, CPL, CSM, DPR, DSI, EBS, EPC, EX0, EXH, GAP, HDS, ISM, LDP, MFR, NDO, O3E, O3S, O3T, OLG, PAG, POL, QAM, QBM, QER, RMB, RMS, RPS, SAC, SAP, SBW, SCC, SCN, SHR, SP0, TSB, UCI, UNX

If there are less modules installed or used, the provided cache files can be used as well.

## Hint for customizations

Add additional NuGet packages with their dependencies as needed for your specific customizations.

## Basic usage

### General

Please follow the official documented [NuGet package source configuration](https://docs.oneidentity.com/bundle/one-identity-manager_operational-guide_9.3.1/page/sources/config/dbcompiler/confdbcompilernugetsettings.htm) guide for One Identity Manager.

### Usage during Configuration Wizard

To allow the usage of the NuGet cache during the run of the Configuration Wizard or Database Compiler, you might adapt the `appsettings.json` file within your client setup set and add an entry for `ExternalNugetSource`. This modification must be done before you start the Configuration Wizard or Database Compiler. A sample configuration might look like this:

```json
{
  "RuntimeDirs": {
    // Set the cache directories to a user defined place
    // "Cache": "C:\\Temp\\OneIM\\AppServerCache\\DB",
    // "AssemblyCache": "C:\\Temp\\OneIM\\AppServerCache\\Assemblies"
  },

  "ConnectionBehaviour": {
    // "CacheReloadInterval": "30",
    // "NoReloadBeep": "true"
  },
  
  "CrashRecorder": {
	  "Enabled": "false",
	  "Buffer": "128",		// count of entries to buffer
	  "Level": "Debug"		// NLog.LogLevel e.g. Debug, Trace, Warn, Error
  },
  "Compiler": {
    "ExternalNugetSource": "C:\\temp\\NuGetPackages"
  }
}
```

In the official documentation, you can find more information about the  [`appsettings.json`](https://docs.oneidentity.com/bundle/one-identity-manager_operational-guide_9.3.1/page/sources/config/controlfiles/appsettingsjson.htm).
