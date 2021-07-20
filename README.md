# .NET Core SDK

[![Join the chat at https://gitter.im/dotnet/cli](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/dotnet/cli?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
[![GitHub release](https://img.shields.io/github/release/dotnet/installer.svg)](https://GitHub.com/dotnet/installer/releases/)
[![GitHub repo size](https://img.shields.io/github/repo-size/dotnet/installer)](https://github.com/dotnet/installer)
[![GitHub issues-opened](https://img.shields.io/github/issues/dotnet/installer.svg)](https://GitHub.com/dotnet/installer/issues?q=is%3Aissue+is%3Aopened)
[![GitHub issues-closed](https://img.shields.io/github/issues-closed/dotnet/installer.svg)](https://GitHub.com/dotnet/installer/issues?q=is%3Aissue+is%3Aclosed)
[![GitHub pulls-opened](https://img.shields.io/github/issues-pr/dotnet/installer.svg)](https://GitHub.com/dotnet/installer/pulls?q=is%3Aissue+is%3Aopened)
[![GitHub pulls-merged](https://img.shields.io/github/issues-search/dotnet/installer?label=merged%20pull%20requests&query=is%3Apr%20is%3Aclosed%20is%3Amerged&color=darkviolet)](https://github.com/dotnet/installer/pulls?q=is%3Apr+is%3Aclosed+is%3Amerged)
[![GitHub pulls-unmerged](https://img.shields.io/github/issues-search/dotnet/installer?label=unmerged%20pull%20requests&query=is%3Apr%20is%3Aclosed%20is%3Aunmerged&color=red)](https://github.com/dotnet/installer/pulls?q=is%3Apr+is%3Aclosed+is%3Aunmerged)
[![GitHub contributors](https://img.shields.io/github/contributors/dotnet/installer.svg)](https://GitHub.com/dotnet/installer/graphs/contributors/)
[![Commit Activity](https://img.shields.io/github/commit-activity/m/badges/shields)]()


This repo contains the source code for the cross-platform [.NET Core](http://github.com/dotnet/core) SDK. It aggregates the .NET Toolchain, the .NET Core runtime, the templates, and the .NET Core Windows Desktop runtime. It produces zip, tarballs, and native packages for various supported platforms.

Looking for released versions of the .NET Core tooling?
----------------------------------------

Download released versions of the .NET Core tools (CLI, MSBuild and the new csproj) at https://dot.net/core.

Found an issue?
---------------
You can consult the [Documents Index for the SDK repo](https://github.com/dotnet/sdk/blob/main/documentation/README.md) to find out current issues, see workarounds, and to see how to file new issues.

This project has adopted the code of conduct defined by the [Contributor Covenant](http://contributor-covenant.org/) to clarify expected behavior in our community. For more information, see the [.NET Foundation Code of Conduct](http://www.dotnetfoundation.org/code-of-conduct).

# Building 

The repository contains native code project required for the Windows installer. If you intend to build it locally on Windows, you will need to ensure that you have the following items installed.
- Install CMAKE 3.2.0.1 or later
- Install MSVC Build tools for x86/x64/arm64, v14.28-16.9

- `build` for basic build
- `build -pack` to build the installer
- To build in VS, run a command line build first, then run `artifacts\core-sdk-build-env.bat` from a VS command prompt and then `devenv Microsoft.DotNet.Cli.sln`
- To test different languages of the installer, run `artifacts\packages\Debug\Shipping>dotnet-sdk-3.1.412-win-x64.exe /lang 1046` using the LCID of the language you want to test

# Build status

|All legs|
|:------:|
|[![Build Status](https://dev.azure.com/dnceng/internal/_apis/build/status/286)](https://dev.azure.com/dnceng/internal/_build?definitionId=286)|

Installers and Binaries
-----------------------

You can download the .NET Core SDK as either an installer (MSI, PKG) or a zip (zip, tar.gz). The .NET Core SDK contains both the .NET Core runtime and CLI tools.

**Note:** Be aware that the following installers are the **latest bits**. If you
want to install the latest released versions, check out the [preceding section](#looking-for-released-versions-of-the-net-core-tooling).
With development builds, internal NuGet feeds are necessary for some scenarios (for example, to acquire the runtime pack for self-contained apps). You can use the following NuGet.config to configure these feeds. See the following document [Configuring NuGet behavior](https://docs.microsoft.com/en-us/nuget/consume-packages/configuring-nuget-behavior) for more information on where to modify your NuGet.config to apply the changes.
> Example:

**For .NET 6 builds**

```
<configuration>
  <packageSources>
    <add key="dotnet6" value="https://pkgs.dev.azure.com/dnceng/public/_packaging/dotnet6/nuget/v3/index.json" />
  </packageSources>
</configuration>
```
**Note:** that you may need to add the dotnet5 feed for a short period of time while .NET transitions to .NET 6

**For .NET 5 builds**

```
<configuration>
  <packageSources>
    <add key="dotnet5" value="https://pkgs.dev.azure.com/dnceng/public/_packaging/dotnet5/nuget/v3/index.json" />
  </packageSources>
</configuration>
```

**For .NET 3.1 builds**

```
<configuration>
  <packageSources>
    <add key="dotnet3.1" value="https://pkgs.dev.azure.com/dnceng/public/_packaging/dotnet3.1/nuget/v3/index.json" />
  </packageSources>
</configuration>
```

Please do not directly edit the table below. Use https://github.com/dotnet/installer/tree/main/tools/sdk-readme-table-generator to help you generate it. Make sure to run the table generator test and make any changes to the generator along with your changes to the table.

| Platform | main<br>(6.0.x&nbsp;Runtime) | Release/6.0.1XX-preview7<br>(6.0.x&nbsp;Runtime) | Release/5.0.4XX<br>(5.0 Runtime) | Release/5.0.3XX<br>(5.0 Runtime) | Release/5.0.2XX<br>(5.0 Runtime) | Release/3.1.4XX<br>(3.1.x Runtime) | Release/3.1.1XX<br>(3.1.x Runtime) |
| :--------- | :----------: | :----------: | :----------: | :----------: | :----------: | :----------: | :----------: |
| **Windows x64** | [![][win-x64-badge-main]][win-x64-version-main]<br>[Installer][win-x64-installer-main] - [Checksum][win-x64-installer-checksum-main]<br>[zip][win-x64-zip-main] - [Checksum][win-x64-zip-checksum-main] | [![][win-x64-badge-6.0.1XX-preview7]][win-x64-version-6.0.1XX-preview7]<br>[Installer][win-x64-installer-6.0.1XX-preview7] - [Checksum][win-x64-installer-checksum-6.0.1XX-preview7]<br>[zip][win-x64-zip-6.0.1XX-preview7] - [Checksum][win-x64-zip-checksum-6.0.1XX-preview7] | [![][win-x64-badge-5.0.4XX]][win-x64-version-5.0.4XX]<br>[Installer][win-x64-installer-5.0.4XX] - [Checksum][win-x64-installer-checksum-5.0.4XX]<br>[zip][win-x64-zip-5.0.4XX] - [Checksum][win-x64-zip-checksum-5.0.4XX] | [![][win-x64-badge-5.0.3XX]][win-x64-version-5.0.3XX]<br>[Installer][win-x64-installer-5.0.3XX] - [Checksum][win-x64-installer-checksum-5.0.3XX]<br>[zip][win-x64-zip-5.0.3XX] - [Checksum][win-x64-zip-checksum-5.0.3XX] | [![][win-x64-badge-5.0.2XX]][win-x64-version-5.0.2XX]<br>[Installer][win-x64-installer-5.0.2XX] - [Checksum][win-x64-installer-checksum-5.0.2XX]<br>[zip][win-x64-zip-5.0.2XX] - [Checksum][win-x64-zip-checksum-5.0.2XX] | [![][win-x64-badge-3.1.4XX]][win-x64-version-3.1.4XX]<br>[Installer][win-x64-installer-3.1.4XX] - [Checksum][win-x64-installer-checksum-3.1.4XX]<br>[zip][win-x64-zip-3.1.4XX] - [Checksum][win-x64-zip-checksum-3.1.4XX] | [![][win-x64-badge-3.1.1XX]][win-x64-version-3.1.1XX]<br>[Installer][win-x64-installer-3.1.1XX] - [Checksum][win-x64-installer-checksum-3.1.1XX]<br>[zip][win-x64-zip-3.1.1XX] - [Checksum][win-x64-zip-checksum-3.1.1XX] |
| **Windows x86** | [![][win-x86-badge-main]][win-x86-version-main]<br>[Installer][win-x86-installer-main] - [Checksum][win-x86-installer-checksum-main]<br>[zip][win-x86-zip-main] - [Checksum][win-x86-zip-checksum-main] | [![][win-x86-badge-6.0.1XX-preview7]][win-x86-version-6.0.1XX-preview7]<br>[Installer][win-x86-installer-6.0.1XX-preview7] - [Checksum][win-x86-installer-checksum-6.0.1XX-preview7]<br>[zip][win-x86-zip-6.0.1XX-preview7] - [Checksum][win-x86-zip-checksum-6.0.1XX-preview7] | [![][win-x86-badge-5.0.4XX]][win-x86-version-5.0.4XX]<br>[Installer][win-x86-installer-5.0.4XX] - [Checksum][win-x86-installer-checksum-5.0.4XX]<br>[zip][win-x86-zip-5.0.4XX] - [Checksum][win-x86-zip-checksum-5.0.4XX] | [![][win-x86-badge-5.0.3XX]][win-x86-version-5.0.3XX]<br>[Installer][win-x86-installer-5.0.3XX] - [Checksum][win-x86-installer-checksum-5.0.3XX]<br>[zip][win-x86-zip-5.0.3XX] - [Checksum][win-x86-zip-checksum-5.0.3XX] | [![][win-x86-badge-5.0.2XX]][win-x86-version-5.0.2XX]<br>[Installer][win-x86-installer-5.0.2XX] - [Checksum][win-x86-installer-checksum-5.0.2XX]<br>[zip][win-x86-zip-5.0.2XX] - [Checksum][win-x86-zip-checksum-5.0.2XX] | [![][win-x86-badge-3.1.4XX]][win-x86-version-3.1.4XX]<br>[Installer][win-x86-installer-3.1.4XX] - [Checksum][win-x86-installer-checksum-3.1.4XX]<br>[zip][win-x86-zip-3.1.4XX] - [Checksum][win-x86-zip-checksum-3.1.4XX] | [![][win-x86-badge-3.1.1XX]][win-x86-version-3.1.1XX]<br>[Installer][win-x86-installer-3.1.1XX] - [Checksum][win-x86-installer-checksum-3.1.1XX]<br>[zip][win-x86-zip-3.1.1XX] - [Checksum][win-x86-zip-checksum-3.1.1XX] |
| **Windows arm** | **N/A** | **N/A** | **N/A** | **N/A** | **N/A** | [![][win-arm-badge-3.1.4XX]][win-arm-version-3.1.4XX]<br>[zip][win-arm-zip-3.1.4XX] - [Checksum][win-arm-zip-checksum-3.1.4XX] | [![][win-arm-badge-3.1.1XX]][win-arm-version-3.1.1XX]<br>[zip][win-arm-zip-3.1.1XX] - [Checksum][win-arm-zip-checksum-3.1.1XX] |
| **Windows arm64** | [![][win-arm64-badge-main]][win-arm64-version-main]<br>[Installer][win-arm64-installer-main] - [Checksum][win-arm64-installer-checksum-main]<br>[zip][win-arm64-zip-main] | [![][win-arm64-badge-6.0.1XX-preview7]][win-arm64-version-6.0.1XX-preview7]<br>[Installer][win-arm64-installer-6.0.1XX-preview7] - [Checksum][win-arm64-installer-checksum-6.0.1XX-preview7]<br>[zip][win-arm64-zip-6.0.1XX-preview7] | [![][win-arm64-badge-5.0.4XX]][win-arm64-version-5.0.4XX]<br>[Installer][win-arm64-installer-5.0.4XX] - [Checksum][win-arm64-installer-checksum-5.0.4XX]<br>[zip][win-arm64-zip-5.0.4XX] | [![][win-arm64-badge-5.0.3XX]][win-arm64-version-5.0.3XX]<br>[Installer][win-arm64-installer-5.0.3XX] - [Checksum][win-arm64-installer-checksum-5.0.3XX]<br>[zip][win-arm64-zip-5.0.3XX] | [![][win-arm64-badge-5.0.2XX]][win-arm64-version-5.0.2XX]<br>[Installer][win-arm64-installer-5.0.2XX] - [Checksum][win-arm64-installer-checksum-5.0.2XX]<br>[zip][win-arm64-zip-5.0.2XX] | **N/A** | **N/A** |
| **macOS x64** | [![][osx-x64-badge-main]][osx-x64-version-main]<br>[Installer][osx-x64-installer-main] - [Checksum][osx-x64-installer-checksum-main]<br>[tar.gz][osx-x64-targz-main] - [Checksum][osx-x64-targz-checksum-main] | [![][osx-x64-badge-6.0.1XX-preview7]][osx-x64-version-6.0.1XX-preview7]<br>[Installer][osx-x64-installer-6.0.1XX-preview7] - [Checksum][osx-x64-installer-checksum-6.0.1XX-preview7]<br>[tar.gz][osx-x64-targz-6.0.1XX-preview7] - [Checksum][osx-x64-targz-checksum-6.0.1XX-preview7] | [![][osx-x64-badge-5.0.4XX]][osx-x64-version-5.0.4XX]<br>[Installer][osx-x64-installer-5.0.4XX] - [Checksum][osx-x64-installer-checksum-5.0.4XX]<br>[tar.gz][osx-x64-targz-5.0.4XX] - [Checksum][osx-x64-targz-checksum-5.0.4XX] | [![][osx-x64-badge-5.0.3XX]][osx-x64-version-5.0.3XX]<br>[Installer][osx-x64-installer-5.0.3XX] - [Checksum][osx-x64-installer-checksum-5.0.3XX]<br>[tar.gz][osx-x64-targz-5.0.3XX] - [Checksum][osx-x64-targz-checksum-5.0.3XX] | [![][osx-x64-badge-5.0.2XX]][osx-x64-version-5.0.2XX]<br>[Installer][osx-x64-installer-5.0.2XX] - [Checksum][osx-x64-installer-checksum-5.0.2XX]<br>[tar.gz][osx-x64-targz-5.0.2XX] - [Checksum][osx-x64-targz-checksum-5.0.2XX] | [![][osx-x64-badge-3.1.4XX]][osx-x64-version-3.1.4XX]<br>[Installer][osx-x64-installer-3.1.4XX] - [Checksum][osx-x64-installer-checksum-3.1.4XX]<br>[tar.gz][osx-x64-targz-3.1.4XX] - [Checksum][osx-x64-targz-checksum-3.1.4XX] | [![][osx-x64-badge-3.1.1XX]][osx-x64-version-3.1.1XX]<br>[Installer][osx-x64-installer-3.1.1XX] - [Checksum][osx-x64-installer-checksum-3.1.1XX]<br>[tar.gz][osx-x64-targz-3.1.1XX] - [Checksum][osx-x64-targz-checksum-3.1.1XX] |
| **macOS arm64** | [![][osx-arm64-badge-main]][osx-arm64-version-main]<br>[Installer][osx-arm64-installer-main] - [Checksum][osx-arm64-installer-checksum-main]<br>[tar.gz][osx-arm64-targz-main] - [Checksum][osx-arm64-targz-checksum-main] | [![][osx-arm64-badge-6.0.1XX-preview7]][osx-arm64-version-6.0.1XX-preview7]<br>[Installer][osx-arm64-installer-6.0.1XX-preview7] - [Checksum][osx-arm64-installer-checksum-6.0.1XX-preview7]<br>[tar.gz][osx-arm64-targz-6.0.1XX-preview7] - [Checksum][osx-arm64-targz-checksum-6.0.1XX-preview7] | **N/A** | **N/A** | **N/A** | **N/A** | **N/A** |
| **Linux x64** | [![][linux-badge-main]][linux-version-main]<br>[DEB Installer][linux-DEB-installer-main] - [Checksum][linux-DEB-installer-checksum-main]<br>[RPM Installer][linux-RPM-installer-main] - [Checksum][linux-RPM-installer-checksum-main]<br>_see installer note below_<sup>1</sup><br>[tar.gz][linux-targz-main] - [Checksum][linux-targz-checksum-main] | [![][linux-badge-6.0.1XX-preview7]][linux-version-6.0.1XX-preview7]<br>[DEB Installer][linux-DEB-installer-6.0.1XX-preview7] - [Checksum][linux-DEB-installer-checksum-6.0.1XX-preview7]<br>[RPM Installer][linux-RPM-installer-6.0.1XX-preview7] - [Checksum][linux-RPM-installer-checksum-6.0.1XX-preview7]<br>_see installer note below_<sup>1</sup><br>[tar.gz][linux-targz-6.0.1XX-preview7] - [Checksum][linux-targz-checksum-6.0.1XX-preview7] | [![][linux-badge-5.0.4XX]][linux-version-5.0.4XX]<br>[DEB Installer][linux-DEB-installer-5.0.4XX] - [Checksum][linux-DEB-installer-checksum-5.0.4XX]<br>[RPM Installer][linux-RPM-installer-5.0.4XX] - [Checksum][linux-RPM-installer-checksum-5.0.4XX]<br>_see installer note below_<sup>1</sup><br>[tar.gz][linux-targz-5.0.4XX] - [Checksum][linux-targz-checksum-5.0.4XX] | [![][linux-badge-5.0.3XX]][linux-version-5.0.3XX]<br>[DEB Installer][linux-DEB-installer-5.0.3XX] - [Checksum][linux-DEB-installer-checksum-5.0.3XX]<br>[RPM Installer][linux-RPM-installer-5.0.3XX] - [Checksum][linux-RPM-installer-checksum-5.0.3XX]<br>_see installer note below_<sup>1</sup><br>[tar.gz][linux-targz-5.0.3XX] - [Checksum][linux-targz-checksum-5.0.3XX] | [![][linux-badge-5.0.2XX]][linux-version-5.0.2XX]<br>[DEB Installer][linux-DEB-installer-5.0.2XX] - [Checksum][linux-DEB-installer-checksum-5.0.2XX]<br>[RPM Installer][linux-RPM-installer-5.0.2XX] - [Checksum][linux-RPM-installer-checksum-5.0.2XX]<br>_see installer note below_<sup>1</sup><br>[tar.gz][linux-targz-5.0.2XX] - [Checksum][linux-targz-checksum-5.0.2XX] | [![][linux-badge-3.1.4XX]][linux-version-3.1.4XX]<br>[DEB Installer][linux-DEB-installer-3.1.4XX] - [Checksum][linux-DEB-installer-checksum-3.1.4XX]<br>[RPM Installer][linux-RPM-installer-3.1.4XX] - [Checksum][linux-RPM-installer-checksum-3.1.4XX]<br>_see installer note below_<sup>1</sup><br>[tar.gz][linux-targz-3.1.4XX] - [Checksum][linux-targz-checksum-3.1.4XX] | [![][linux-badge-3.1.1XX]][linux-version-3.1.1XX]<br>[DEB Installer][linux-DEB-installer-3.1.1XX] - [Checksum][linux-DEB-installer-checksum-3.1.1XX]<br>[RPM Installer][linux-RPM-installer-3.1.1XX] - [Checksum][linux-RPM-installer-checksum-3.1.1XX]<br>_see installer note below_<sup>1</sup><br>[tar.gz][linux-targz-3.1.1XX] - [Checksum][linux-targz-checksum-3.1.1XX] |
| **Linux arm** | [![][linux-arm-badge-main]][linux-arm-version-main]<br>[tar.gz][linux-arm-targz-main] - [Checksum][linux-arm-targz-checksum-main] | [![][linux-arm-badge-6.0.1XX-preview7]][linux-arm-version-6.0.1XX-preview7]<br>[tar.gz][linux-arm-targz-6.0.1XX-preview7] - [Checksum][linux-arm-targz-checksum-6.0.1XX-preview7] | [![][linux-arm-badge-5.0.4XX]][linux-arm-version-5.0.4XX]<br>[tar.gz][linux-arm-targz-5.0.4XX] - [Checksum][linux-arm-targz-checksum-5.0.4XX] | [![][linux-arm-badge-5.0.3XX]][linux-arm-version-5.0.3XX]<br>[tar.gz][linux-arm-targz-5.0.3XX] - [Checksum][linux-arm-targz-checksum-5.0.3XX] | [![][linux-arm-badge-5.0.2XX]][linux-arm-version-5.0.2XX]<br>[tar.gz][linux-arm-targz-5.0.2XX] - [Checksum][linux-arm-targz-checksum-5.0.2XX] | [![][linux-arm-badge-3.1.4XX]][linux-arm-version-3.1.4XX]<br>[tar.gz][linux-arm-targz-3.1.4XX] - [Checksum][linux-arm-targz-checksum-3.1.4XX] | [![][linux-arm-badge-3.1.1XX]][linux-arm-version-3.1.1XX]<br>[tar.gz][linux-arm-targz-3.1.1XX] - [Checksum][linux-arm-targz-checksum-3.1.1XX] |
| **Linux arm64** | [![][linux-arm64-badge-main]][linux-arm64-version-main]<br>[tar.gz][linux-arm64-targz-main] - [Checksum][linux-arm64-targz-checksum-main] | [![][linux-arm64-badge-6.0.1XX-preview7]][linux-arm64-version-6.0.1XX-preview7]<br>[tar.gz][linux-arm64-targz-6.0.1XX-preview7] - [Checksum][linux-arm64-targz-checksum-6.0.1XX-preview7] | [![][linux-arm64-badge-5.0.4XX]][linux-arm64-version-5.0.4XX]<br>[tar.gz][linux-arm64-targz-5.0.4XX] - [Checksum][linux-arm64-targz-checksum-5.0.4XX] | [![][linux-arm64-badge-5.0.3XX]][linux-arm64-version-5.0.3XX]<br>[tar.gz][linux-arm64-targz-5.0.3XX] - [Checksum][linux-arm64-targz-checksum-5.0.3XX] | [![][linux-arm64-badge-5.0.2XX]][linux-arm64-version-5.0.2XX]<br>[tar.gz][linux-arm64-targz-5.0.2XX] - [Checksum][linux-arm64-targz-checksum-5.0.2XX] | [![][linux-arm64-badge-3.1.4XX]][linux-arm64-version-3.1.4XX]<br>[tar.gz][linux-arm64-targz-3.1.4XX] - [Checksum][linux-arm64-targz-checksum-3.1.4XX] | [![][linux-arm64-badge-3.1.1XX]][linux-arm64-version-3.1.1XX]<br>[tar.gz][linux-arm64-targz-3.1.1XX] - [Checksum][linux-arm64-targz-checksum-3.1.1XX] |
| **Linux-musl-x64** | [![][linux-musl-x64-badge-main]][linux-musl-x64-version-main]<br>[tar.gz][linux-musl-x64-targz-main] - [Checksum][linux-musl-x64-targz-checksum-main] | [![][linux-musl-x64-badge-6.0.1XX-preview7]][linux-musl-x64-version-6.0.1XX-preview7]<br>[tar.gz][linux-musl-x64-targz-6.0.1XX-preview7] - [Checksum][linux-musl-x64-targz-checksum-6.0.1XX-preview7] | [![][linux-musl-x64-badge-5.0.4XX]][linux-musl-x64-version-5.0.4XX]<br>[tar.gz][linux-musl-x64-targz-5.0.4XX] - [Checksum][linux-musl-x64-targz-checksum-5.0.4XX] | [![][linux-musl-x64-badge-5.0.3XX]][linux-musl-x64-version-5.0.3XX]<br>[tar.gz][linux-musl-x64-targz-5.0.3XX] - [Checksum][linux-musl-x64-targz-checksum-5.0.3XX] | [![][linux-musl-x64-badge-5.0.2XX]][linux-musl-x64-version-5.0.2XX]<br>[tar.gz][linux-musl-x64-targz-5.0.2XX] - [Checksum][linux-musl-x64-targz-checksum-5.0.2XX] | [![][linux-musl-x64-badge-3.1.4XX]][linux-musl-x64-version-3.1.4XX]<br>[tar.gz][linux-musl-x64-targz-3.1.4XX] - [Checksum][linux-musl-x64-targz-checksum-3.1.4XX] | [![][linux-musl-x64-badge-3.1.1XX]][linux-musl-x64-version-3.1.1XX]<br>[tar.gz][linux-musl-x64-targz-3.1.1XX] - [Checksum][linux-musl-x64-targz-checksum-3.1.1XX] |
| **Linux-musl-arm** | [![][linux-musl-arm-badge-main]][linux-musl-arm-version-main]<br>[tar.gz][linux-musl-arm-targz-main] - [Checksum][linux-musl-arm-targz-checksum-main] | [![][linux-musl-arm-badge-6.0.1XX-preview7]][linux-musl-arm-version-6.0.1XX-preview7]<br>[tar.gz][linux-musl-arm-targz-6.0.1XX-preview7] - [Checksum][linux-musl-arm-targz-checksum-6.0.1XX-preview7] | [![][linux-musl-arm-badge-5.0.4XX]][linux-musl-arm-version-5.0.4XX]<br>[tar.gz][linux-musl-arm-targz-5.0.4XX] - [Checksum][linux-musl-arm-targz-checksum-5.0.4XX] | [![][linux-musl-arm-badge-5.0.3XX]][linux-musl-arm-version-5.0.3XX]<br>[tar.gz][linux-musl-arm-targz-5.0.3XX] - [Checksum][linux-musl-arm-targz-checksum-5.0.3XX] | [![][linux-musl-arm-badge-5.0.2XX]][linux-musl-arm-version-5.0.2XX]<br>[tar.gz][linux-musl-arm-targz-5.0.2XX] - [Checksum][linux-musl-arm-targz-checksum-5.0.2XX] | **N/A** | **N/A** |
| **Linux-musl-arm64** | [![][linux-musl-arm64-badge-main]][linux-musl-arm64-version-main]<br>[tar.gz][linux-musl-arm64-targz-main] - [Checksum][linux-musl-arm64-targz-checksum-main] | [![][linux-musl-arm64-badge-6.0.1XX-preview7]][linux-musl-arm64-version-6.0.1XX-preview7]<br>[tar.gz][linux-musl-arm64-targz-6.0.1XX-preview7] - [Checksum][linux-musl-arm64-targz-checksum-6.0.1XX-preview7] | [![][linux-musl-arm64-badge-5.0.4XX]][linux-musl-arm64-version-5.0.4XX]<br>[tar.gz][linux-musl-arm64-targz-5.0.4XX] - [Checksum][linux-musl-arm64-targz-checksum-5.0.4XX] | [![][linux-musl-arm64-badge-5.0.3XX]][linux-musl-arm64-version-5.0.3XX]<br>[tar.gz][linux-musl-arm64-targz-5.0.3XX] - [Checksum][linux-musl-arm64-targz-checksum-5.0.3XX] | [![][linux-musl-arm64-badge-5.0.2XX]][linux-musl-arm64-version-5.0.2XX]<br>[tar.gz][linux-musl-arm64-targz-5.0.2XX] - [Checksum][linux-musl-arm64-targz-checksum-5.0.2XX] | **N/A** | **N/A** |
| **RHEL 6** | **N/A** | **N/A** | **N/A** | **N/A** | **N/A** | [![][rhel-6-badge-3.1.4XX]][rhel-6-version-3.1.4XX]<br>[tar.gz][rhel-6-targz-3.1.4XX] - [Checksum][rhel-6-targz-checksum-3.1.4XX] | [![][rhel-6-badge-3.1.1XX]][rhel-6-version-3.1.1XX]<br>[tar.gz][rhel-6-targz-3.1.1XX] - [Checksum][rhel-6-targz-checksum-3.1.1XX] |

Reference notes:
> **1**: Our Debian packages are put together slightly differently than the other OS specific installers. Instead of combining everything, we have separate component packages that depend on each other. If you're installing the SDK from the .deb file (via dpkg or similar), then you'll need to install the corresponding dependencies first:
> * [Host, Host FX Resolver, and Shared Framework](https://github.com/dotnet/runtime#daily-builds)
> * [ASP.NET Core Shared Framework](https://github.com/aspnet/AspNetCore/blob/main/docs/DailyBuilds.md)

.NET Core SDK 2.x downloads can be found here: [.NET Core SDK 2.x Installers and Binaries](Downloads2.x.md)

[win-x64-badge-main]: https://aka.ms/dotnet/6.0/daily/win_x64_Release_version_badge.svg
[win-x64-version-main]: https://aka.ms/dotnet/6.0/daily/productCommit-win-x64.txt
[win-x64-installer-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-win-x64.exe
[win-x64-installer-checksum-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-win-x64.exe.sha
[win-x64-zip-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-win-x64.zip
[win-x64-zip-checksum-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-win-x64.zip.sha

[win-x64-badge-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/win_x64_Release_version_badge.svg
[win-x64-version-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/productCommit-win-x64.txt
[win-x64-installer-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-win-x64.exe
[win-x64-installer-checksum-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-win-x64.exe.sha
[win-x64-zip-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-win-x64.zip
[win-x64-zip-checksum-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-win-x64.zip.sha

[win-x64-badge-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/win_x64_Release_version_badge.svg
[win-x64-version-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/productCommit-win-x64.txt
[win-x64-installer-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-win-x64.exe
[win-x64-installer-checksum-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-win-x64.exe.sha
[win-x64-zip-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-win-x64.zip
[win-x64-zip-checksum-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-win-x64.zip.sha

[win-x64-badge-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/win_x64_Release_version_badge.svg
[win-x64-version-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/productCommit-win-x64.txt
[win-x64-installer-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-win-x64.exe
[win-x64-installer-checksum-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-win-x64.exe.sha
[win-x64-zip-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-win-x64.zip
[win-x64-zip-checksum-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-win-x64.zip.sha

[win-x64-badge-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/win_x64_Release_version_badge.svg
[win-x64-version-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/productCommit-win-x64.txt
[win-x64-installer-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-win-x64.exe
[win-x64-installer-checksum-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-win-x64.exe.sha
[win-x64-zip-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-win-x64.zip
[win-x64-zip-checksum-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-win-x64.zip.sha

[win-x64-badge-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/win_x64_Release_version_badge.svg
[win-x64-version-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/latest.version
[win-x64-installer-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/dotnet-sdk-latest-win-x64.exe
[win-x64-installer-checksum-3.1.4XX]: https://dotnetclichecksums.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/dotnet-sdk-latest-win-x64.exe.sha
[win-x64-zip-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/dotnet-sdk-latest-win-x64.zip
[win-x64-zip-checksum-3.1.4XX]: https://dotnetclichecksums.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/dotnet-sdk-latest-win-x64.zip.sha

[win-x64-badge-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/win_x64_Release_version_badge.svg
[win-x64-version-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/latest.version
[win-x64-installer-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/dotnet-sdk-latest-win-x64.exe
[win-x64-installer-checksum-3.1.1XX]: https://dotnetclichecksums.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/dotnet-sdk-latest-win-x64.exe.sha
[win-x64-zip-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/dotnet-sdk-latest-win-x64.zip
[win-x64-zip-checksum-3.1.1XX]: https://dotnetclichecksums.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/dotnet-sdk-latest-win-x64.zip.sha

[win-x86-badge-main]: https://aka.ms/dotnet/6.0/daily/win_x86_Release_version_badge.svg
[win-x86-version-main]: https://aka.ms/dotnet/6.0/daily/productCommit-win-x86.txt
[win-x86-installer-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-win-x86.exe
[win-x86-installer-checksum-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-win-x86.exe.sha
[win-x86-zip-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-win-x86.zip
[win-x86-zip-checksum-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-win-x86.zip.sha

[win-x86-badge-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/win_x86_Release_version_badge.svg
[win-x86-version-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/productCommit-win-x86.txt
[win-x86-installer-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-win-x86.exe
[win-x86-installer-checksum-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-win-x86.exe.sha
[win-x86-zip-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-win-x86.zip
[win-x86-zip-checksum-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-win-x86.zip.sha

[win-x86-badge-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/win_x86_Release_version_badge.svg
[win-x86-version-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/productCommit-win-x86.txt
[win-x86-installer-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-win-x86.exe
[win-x86-installer-checksum-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-win-x86.exe.sha
[win-x86-zip-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-win-x86.zip
[win-x86-zip-checksum-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-win-x86.zip.sha

[win-x86-badge-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/win_x86_Release_version_badge.svg
[win-x86-version-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/productCommit-win-x86.txt
[win-x86-installer-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-win-x86.exe
[win-x86-installer-checksum-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-win-x86.exe.sha
[win-x86-zip-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-win-x86.zip
[win-x86-zip-checksum-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-win-x86.zip.sha

[win-x86-badge-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/win_x86_Release_version_badge.svg
[win-x86-version-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/productCommit-win-x86.txt
[win-x86-installer-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-win-x86.exe
[win-x86-installer-checksum-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-win-x86.exe.sha
[win-x86-zip-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-win-x86.zip
[win-x86-zip-checksum-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-win-x86.zip.sha

[win-x86-badge-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/win_x86_Release_version_badge.svg
[win-x86-version-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/latest.version
[win-x86-installer-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/dotnet-sdk-latest-win-x86.exe
[win-x86-installer-checksum-3.1.4XX]: https://dotnetclichecksums.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/dotnet-sdk-latest-win-x86.exe.sha
[win-x86-zip-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/dotnet-sdk-latest-win-x86.zip
[win-x86-zip-checksum-3.1.4XX]: https://dotnetclichecksums.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/dotnet-sdk-latest-win-x86.zip.sha

[win-x86-badge-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/win_x86_Release_version_badge.svg
[win-x86-version-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/latest.version
[win-x86-installer-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/dotnet-sdk-latest-win-x86.exe
[win-x86-installer-checksum-3.1.1XX]: https://dotnetclichecksums.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/dotnet-sdk-latest-win-x86.exe.sha
[win-x86-zip-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/dotnet-sdk-latest-win-x86.zip
[win-x86-zip-checksum-3.1.1XX]: https://dotnetclichecksums.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/dotnet-sdk-latest-win-x86.zip.sha

[osx-x64-badge-main]: https://aka.ms/dotnet/6.0/daily/osx_x64_Release_version_badge.svg
[osx-x64-version-main]: https://aka.ms/dotnet/6.0/daily/productCommit-osx-x64.txt
[osx-x64-installer-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-osx-x64.pkg
[osx-x64-installer-checksum-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-osx-x64.pkg.sha
[osx-x64-targz-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-osx-x64.tar.gz
[osx-x64-targz-checksum-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-osx-x64.pkg.tar.gz.sha

[osx-x64-badge-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/osx_x64_Release_version_badge.svg
[osx-x64-version-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/productCommit-osx-x64.txt
[osx-x64-installer-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-osx-x64.pkg
[osx-x64-installer-checksum-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-osx-x64.pkg.sha
[osx-x64-targz-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-osx-x64.tar.gz
[osx-x64-targz-checksum-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-osx-x64.pkg.tar.gz.sha

[osx-x64-badge-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/osx_x64_Release_version_badge.svg
[osx-x64-version-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/productCommit-osx-x64.txt
[osx-x64-installer-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-osx-x64.pkg
[osx-x64-installer-checksum-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-osx-x64.pkg.sha
[osx-x64-targz-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-osx-x64.tar.gz
[osx-x64-targz-checksum-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-osx-x64.pkg.tar.gz.sha

[osx-x64-badge-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/osx_x64_Release_version_badge.svg
[osx-x64-version-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/productCommit-osx-x64.txt
[osx-x64-installer-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-osx-x64.pkg
[osx-x64-installer-checksum-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-osx-x64.pkg.sha
[osx-x64-targz-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-osx-x64.tar.gz
[osx-x64-targz-checksum-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-osx-x64.pkg.tar.gz.sha

[osx-x64-badge-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/osx_x64_Release_version_badge.svg
[osx-x64-version-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/productCommit-osx-x64.txt
[osx-x64-installer-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-osx-x64.pkg
[osx-x64-installer-checksum-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-osx-x64.pkg.sha
[osx-x64-targz-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-osx-x64.tar.gz
[osx-x64-targz-checksum-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-osx-x64.pkg.tar.gz.sha

[osx-x64-badge-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/osx_x64_Release_version_badge.svg
[osx-x64-version-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/latest.version
[osx-x64-installer-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/dotnet-sdk-latest-osx-x64.pkg
[osx-x64-installer-checksum-3.1.4XX]: https://dotnetclichecksums.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/dotnet-sdk-latest-osx-x64.pkg.sha
[osx-x64-targz-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/dotnet-sdk-latest-osx-x64.tar.gz
[osx-x64-targz-checksum-3.1.4XX]: https://dotnetclichecksums.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/dotnet-sdk-latest-osx-x64.tar.gz.sha

[osx-x64-badge-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/osx_x64_Release_version_badge.svg
[osx-x64-version-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/latest.version
[osx-x64-installer-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/dotnet-sdk-latest-osx-x64.pkg
[osx-x64-installer-checksum-3.1.1XX]: https://dotnetclichecksums.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/dotnet-sdk-latest-osx-x64.pkg.sha
[osx-x64-targz-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/dotnet-sdk-latest-osx-x64.tar.gz
[osx-x64-targz-checksum-3.1.1XX]: https://dotnetclichecksums.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/dotnet-sdk-latest-osx-x64.tar.gz.sha

[osx-arm64-badge-main]: https://aka.ms/dotnet/6.0/daily/osx_arm64_Release_version_badge.svg
[osx-arm64-version-main]: https://aka.ms/dotnet/6.0/daily/productCommit-osx-arm64.txt
[osx-arm64-installer-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-osx-arm64.pkg
[osx-arm64-installer-checksum-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-osx-arm64.pkg.sha
[osx-arm64-targz-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-osx-arm64.tar.gz
[osx-arm64-targz-checksum-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-osx-arm64.pkg.tar.gz.sha

[osx-arm64-badge-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/osx_arm64_Release_version_badge.svg
[osx-arm64-version-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/productCommit-osx-arm64.txt
[osx-arm64-installer-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-osx-arm64.pkg
[osx-arm64-installer-checksum-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-osx-arm64.pkg.sha
[osx-arm64-targz-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-osx-arm64.tar.gz
[osx-arm64-targz-checksum-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-osx-arm64.pkg.tar.gz.sha

[linux-badge-main]: https://aka.ms/dotnet/6.0/daily/linux_x64_Release_version_badge.svg
[linux-version-main]: https://aka.ms/dotnet/6.0/daily/productCommit-linux-x64.txt
[linux-DEB-installer-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-x64.deb
[linux-DEB-installer-checksum-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-x64.deb.sha
[linux-RPM-installer-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-x64.rpm
[linux-RPM-installer-checksum-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-x64.rpm.sha
[linux-targz-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-linux-x64.tar.gz
[linux-targz-checksum-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-linux-x64.tar.gz.sha

[linux-badge-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/linux_x64_Release_version_badge.svg
[linux-version-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/productCommit-linux-x64.txt
[linux-DEB-installer-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-x64.deb
[linux-DEB-installer-checksum-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-x64.deb.sha
[linux-RPM-installer-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-x64.rpm
[linux-RPM-installer-checksum-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-x64.rpm.sha
[linux-targz-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-linux-x64.tar.gz
[linux-targz-checksum-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-linux-x64.tar.gz.sha

[linux-badge-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/linux_x64_Release_version_badge.svg
[linux-version-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/productCommit-linux-x64.txt
[linux-DEB-installer-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-x64.deb
[linux-DEB-installer-checksum-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-x64.deb.sha
[linux-RPM-installer-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-x64.rpm
[linux-RPM-installer-checksum-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-x64.rpm.sha
[linux-targz-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-linux-x64.tar.gz
[linux-targz-checksum-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-linux-x64.tar.gz.sha

[linux-badge-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/linux_x64_Release_version_badge.svg
[linux-version-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/productCommit-linux-x64.txt
[linux-DEB-installer-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-x64.deb
[linux-DEB-installer-checksum-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-x64.deb.sha
[linux-RPM-installer-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-x64.rpm
[linux-RPM-installer-checksum-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-x64.rpm.sha
[linux-targz-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-linux-x64.tar.gz
[linux-targz-checksum-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-linux-x64.tar.gz.sha

[linux-badge-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/linux_x64_Release_version_badge.svg
[linux-version-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/productCommit-linux-x64.txt
[linux-DEB-installer-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-x64.deb
[linux-DEB-installer-checksum-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-x64.deb.sha
[linux-RPM-installer-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-x64.rpm
[linux-RPM-installer-checksum-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-x64.rpm.sha
[linux-targz-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-linux-x64.tar.gz
[linux-targz-checksum-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-linux-x64.tar.gz.sha

[linux-badge-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/linux_x64_Release_version_badge.svg
[linux-version-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/latest.version
[linux-DEB-installer-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/dotnet-sdk-latest-x64.deb
[linux-DEB-installer-checksum-3.1.4XX]: https://dotnetclichecksums.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/dotnet-sdk-latest-x64.deb.sha
[linux-RPM-installer-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/dotnet-sdk-latest-x64.rpm
[linux-RPM-installer-checksum-3.1.4XX]: https://dotnetclichecksums.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/dotnet-sdk-latest-x64.rpm.sha
[linux-targz-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/dotnet-sdk-latest-linux-x64.tar.gz
[linux-targz-checksum-3.1.4XX]: https://dotnetclichecksums.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/dotnet-sdk-latest-linux-x64.tar.gz.sha

[linux-badge-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/linux_x64_Release_version_badge.svg
[linux-version-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/latest.version
[linux-DEB-installer-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/dotnet-sdk-latest-x64.deb
[linux-DEB-installer-checksum-3.1.1XX]: https://dotnetclichecksums.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/dotnet-sdk-latest-x64.deb.sha
[linux-RPM-installer-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/dotnet-sdk-latest-x64.rpm
[linux-RPM-installer-checksum-3.1.1XX]: https://dotnetclichecksums.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/dotnet-sdk-latest-x64.rpm.sha
[linux-targz-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/dotnet-sdk-latest-linux-x64.tar.gz
[linux-targz-checksum-3.1.1XX]: https://dotnetclichecksums.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/dotnet-sdk-latest-linux-x64.tar.gz.sha

[linux-arm-badge-main]: https://aka.ms/dotnet/6.0/daily/linux_arm_Release_version_badge.svg
[linux-arm-version-main]: https://aka.ms/dotnet/6.0/daily/productCommit-linux-arm.txt
[linux-arm-targz-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-linux-arm.tar.gz
[linux-arm-targz-checksum-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-linux-arm.tar.gz.sha

[linux-arm-badge-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/linux_arm_Release_version_badge.svg
[linux-arm-version-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/productCommit-linux-arm.txt
[linux-arm-targz-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-linux-arm.tar.gz
[linux-arm-targz-checksum-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-linux-arm.tar.gz.sha

[linux-arm-badge-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/linux_arm_Release_version_badge.svg
[linux-arm-version-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/productCommit-linux-arm.txt
[linux-arm-targz-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-linux-arm.tar.gz
[linux-arm-targz-checksum-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-linux-arm.tar.gz.sha

[linux-arm-badge-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/linux_arm_Release_version_badge.svg
[linux-arm-version-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/productCommit-linux-arm.txt
[linux-arm-targz-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-linux-arm.tar.gz
[linux-arm-targz-checksum-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-linux-arm.tar.gz.sha

[linux-arm-badge-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/linux_arm_Release_version_badge.svg
[linux-arm-version-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/productCommit-linux-arm.txt
[linux-arm-targz-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-linux-arm.tar.gz
[linux-arm-targz-checksum-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-linux-arm.tar.gz.sha

[linux-arm-badge-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/linux_arm_Release_version_badge.svg
[linux-arm-version-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/latest.version
[linux-arm-targz-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/dotnet-sdk-latest-linux-arm.tar.gz
[linux-arm-targz-checksum-3.1.4XX]: https://dotnetclichecksums.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/dotnet-sdk-latest-linux-arm.tar.gz.sha

[linux-arm-badge-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/linux_arm_Release_version_badge.svg
[linux-arm-version-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/latest.version
[linux-arm-targz-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/dotnet-sdk-latest-linux-arm.tar.gz
[linux-arm-targz-checksum-3.1.1XX]: https://dotnetclichecksums.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/dotnet-sdk-latest-linux-arm.tar.gz.sha

[linux-arm64-badge-main]: https://aka.ms/dotnet/6.0/daily/linux_arm64_Release_version_badge.svg
[linux-arm64-version-main]: https://aka.ms/dotnet/6.0/daily/productCommit-linux-arm64.txt
[linux-arm64-targz-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-linux-arm64.tar.gz
[linux-arm64-targz-checksum-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-linux-arm64.tar.gz.sha

[linux-arm64-badge-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/linux_arm64_Release_version_badge.svg
[linux-arm64-version-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/productCommit-linux-arm64.txt
[linux-arm64-targz-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-linux-arm64.tar.gz
[linux-arm64-targz-checksum-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-linux-arm64.tar.gz.sha

[linux-arm64-badge-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/linux_arm64_Release_version_badge.svg
[linux-arm64-version-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/productCommit-linux-arm64.txt
[linux-arm64-targz-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-linux-arm64.tar.gz
[linux-arm64-targz-checksum-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-linux-arm64.tar.gz.sha

[linux-arm64-badge-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/linux_arm64_Release_version_badge.svg
[linux-arm64-version-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/productCommit-linux-arm64.txt
[linux-arm64-targz-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-linux-arm64.tar.gz
[linux-arm64-targz-checksum-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-linux-arm64.tar.gz.sha

[linux-arm64-badge-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/linux_arm64_Release_version_badge.svg
[linux-arm64-version-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/productCommit-linux-arm64.txt
[linux-arm64-targz-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-linux-arm64.tar.gz
[linux-arm64-targz-checksum-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-linux-arm64.tar.gz.sha

[linux-arm64-badge-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/linux_arm64_Release_version_badge.svg
[linux-arm64-version-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/latest.version
[linux-arm64-targz-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/dotnet-sdk-latest-linux-arm64.tar.gz
[linux-arm64-targz-checksum-3.1.4XX]: https://dotnetclichecksums.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/dotnet-sdk-latest-linux-arm64.tar.gz.sha

[linux-arm64-badge-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/linux_arm64_Release_version_badge.svg
[linux-arm64-version-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/latest.version
[linux-arm64-targz-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/dotnet-sdk-latest-linux-arm64.tar.gz
[linux-arm64-targz-checksum-3.1.1XX]: https://dotnetclichecksums.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/dotnet-sdk-latest-linux-arm64.tar.gz.sha

[rhel-6-badge-main]: https://aka.ms/dotnet/6.0/daily/rhel.6_x64_Release_version_badge.svg
[rhel-6-version-main]: https://aka.ms/dotnet/6.0/daily/productCommit-rhel.6-x64.txt
[rhel-6-targz-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-rhel.6-x64.tar.gz
[rhel-6-targz-checksum-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-rhel.6-x64.tar.gz.sha

[rhel-6-badge-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/rhel.6_x64_Release_version_badge.svg
[rhel-6-version-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/productCommit-rhel.6-x64.txt
[rhel-6-targz-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-rhel.6-x64.tar.gz
[rhel-6-targz-checksum-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-rhel.6-x64.tar.gz.sha

[rhel-6-badge-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/rhel.6_x64_Release_version_badge.svg
[rhel-6-version-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/productCommit-rhel.6-x64.txt
[rhel-6-targz-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-rhel.6-x64.tar.gz
[rhel-6-targz-checksum-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-rhel.6-x64.tar.gz.sha

[rhel-6-badge-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/rhel.6_x64_Release_version_badge.svg
[rhel-6-version-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/productCommit-rhel.6-x64.txt
[rhel-6-targz-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-rhel.6-x64.tar.gz
[rhel-6-targz-checksum-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-rhel.6-x64.tar.gz.sha

[rhel-6-badge-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/rhel.6_x64_Release_version_badge.svg
[rhel-6-version-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/productCommit-rhel.6-x64.txt
[rhel-6-targz-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-rhel.6-x64.tar.gz
[rhel-6-targz-checksum-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-rhel.6-x64.tar.gz.sha

[rhel-6-badge-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/rhel.6_x64_Release_version_badge.svg
[rhel-6-version-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/latest.version
[rhel-6-targz-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/dotnet-sdk-latest-rhel.6-x64.tar.gz
[rhel-6-targz-checksum-3.1.4XX]: https://dotnetclichecksums.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/dotnet-sdk-latest-rhel.6-x64.tar.gz.sha

[rhel-6-badge-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/rhel.6_x64_Release_version_badge.svg
[rhel-6-version-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/latest.version
[rhel-6-targz-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/dotnet-sdk-latest-rhel.6-x64.tar.gz
[rhel-6-targz-checksum-3.1.1XX]: https://dotnetclichecksums.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/dotnet-sdk-latest-rhel.6-x64.tar.gz.sha

[linux-musl-x64-badge-main]: https://aka.ms/dotnet/6.0/daily/linux_musl_x64_Release_version_badge.svg
[linux-musl-x64-version-main]: https://aka.ms/dotnet/6.0/daily/productCommit-linux-musl-x64.txt
[linux-musl-x64-targz-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-linux-musl-x64.tar.gz
[linux-musl-x64-targz-checksum-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-linux-musl-x64.tar.gz.sha

[linux-musl-x64-badge-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/linux_musl_x64_Release_version_badge.svg
[linux-musl-x64-version-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/productCommit-linux-musl-x64.txt
[linux-musl-x64-targz-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-linux-musl-x64.tar.gz
[linux-musl-x64-targz-checksum-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-linux-musl-x64.tar.gz.sha

[linux-musl-x64-badge-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/linux_musl_x64_Release_version_badge.svg
[linux-musl-x64-version-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/productCommit-linux-musl-x64.txt
[linux-musl-x64-targz-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-linux-musl-x64.tar.gz
[linux-musl-x64-targz-checksum-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-linux-musl-x64.tar.gz.sha

[linux-musl-x64-badge-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/linux_musl_x64_Release_version_badge.svg
[linux-musl-x64-version-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/productCommit-linux-musl-x64.txt
[linux-musl-x64-targz-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-linux-musl-x64.tar.gz
[linux-musl-x64-targz-checksum-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-linux-musl-x64.tar.gz.sha

[linux-musl-x64-badge-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/linux_musl_x64_Release_version_badge.svg
[linux-musl-x64-version-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/productCommit-linux-musl-x64.txt
[linux-musl-x64-targz-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-linux-musl-x64.tar.gz
[linux-musl-x64-targz-checksum-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-linux-musl-x64.tar.gz.sha

[linux-musl-x64-badge-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/linux_musl_x64_Release_version_badge.svg
[linux-musl-x64-version-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/latest.version
[linux-musl-x64-targz-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/dotnet-sdk-latest-linux-musl-x64.tar.gz
[linux-musl-x64-targz-checksum-3.1.4XX]: https://dotnetclichecksums.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/dotnet-sdk-latest-linux-musl-x64.tar.gz.sha

[linux-musl-x64-badge-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/linux_musl_x64_Release_version_badge.svg
[linux-musl-x64-version-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/latest.version
[linux-musl-x64-targz-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/dotnet-sdk-latest-linux-musl-x64.tar.gz
[linux-musl-x64-targz-checksum-3.1.1XX]: https://dotnetclichecksums.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/dotnet-sdk-latest-linux-musl-x64.tar.gz.sha

[linux-musl-arm-badge-main]: https://aka.ms/dotnet/6.0/daily/linux_musl_arm_Release_version_badge.svg
[linux-musl-arm-version-main]: https://aka.ms/dotnet/6.0/daily/productCommit-linux-musl-arm.txt
[linux-musl-arm-targz-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-linux-musl-arm.tar.gz
[linux-musl-arm-targz-checksum-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-linux-musl-arm.tar.gz.sha

[linux-musl-arm-badge-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/linux_musl_arm_Release_version_badge.svg
[linux-musl-arm-version-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/productCommit-linux-musl-arm.txt
[linux-musl-arm-targz-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-linux-musl-arm.tar.gz
[linux-musl-arm-targz-checksum-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-linux-musl-arm.tar.gz.sha

[linux-musl-arm-badge-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/linux_musl_arm_Release_version_badge.svg
[linux-musl-arm-version-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/productCommit-linux-musl-arm.txt
[linux-musl-arm-targz-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-linux-musl-arm.tar.gz
[linux-musl-arm-targz-checksum-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-linux-musl-arm.tar.gz.sha

[linux-musl-arm-badge-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/linux_musl_arm_Release_version_badge.svg
[linux-musl-arm-version-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/productCommit-linux-musl-arm.txt
[linux-musl-arm-targz-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-linux-musl-arm.tar.gz
[linux-musl-arm-targz-checksum-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-linux-musl-arm.tar.gz.sha

[linux-musl-arm-badge-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/linux_musl_arm_Release_version_badge.svg
[linux-musl-arm-version-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/productCommit-linux-musl-arm.txt
[linux-musl-arm-targz-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-linux-musl-arm.tar.gz
[linux-musl-arm-targz-checksum-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-linux-musl-arm.tar.gz.sha

[linux-musl-arm64-badge-main]: https://aka.ms/dotnet/6.0/daily/linux_musl_arm64_Release_version_badge.svg
[linux-musl-arm64-version-main]: https://aka.ms/dotnet/6.0/daily/productCommit-linux-musl-arm64.txt
[linux-musl-arm64-targz-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-linux-musl-arm64.tar.gz
[linux-musl-arm64-targz-checksum-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-linux-musl-arm64.tar.gz.sha

[linux-musl-arm64-badge-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/linux_musl_arm64_Release_version_badge.svg
[linux-musl-arm64-version-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/productCommit-linux-musl-arm64.txt
[linux-musl-arm64-targz-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-linux-musl-arm64.tar.gz
[linux-musl-arm64-targz-checksum-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-linux-musl-arm64.tar.gz.sha

[linux-musl-arm64-badge-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/linux_musl_arm64_Release_version_badge.svg
[linux-musl-arm64-version-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/productCommit-linux-musl-arm64.txt
[linux-musl-arm64-targz-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-linux-musl-arm64.tar.gz
[linux-musl-arm64-targz-checksum-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-linux-musl-arm64.tar.gz.sha

[linux-musl-arm64-badge-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/linux_musl_arm64_Release_version_badge.svg
[linux-musl-arm64-version-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/productCommit-linux-musl-arm64.txt
[linux-musl-arm64-targz-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-linux-musl-arm64.tar.gz
[linux-musl-arm64-targz-checksum-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-linux-musl-arm64.tar.gz.sha

[linux-musl-arm64-badge-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/linux_musl_arm64_Release_version_badge.svg
[linux-musl-arm64-version-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/productCommit-linux-musl-arm64.txt
[linux-musl-arm64-targz-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-linux-musl-arm64.tar.gz
[linux-musl-arm64-targz-checksum-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-linux-musl-arm64.tar.gz.sha

[win-arm-badge-main]: https://aka.ms/dotnet/6.0/daily/win_arm_Release_version_badge.svg
[win-arm-version-main]: https://aka.ms/dotnet/6.0/daily/productCommit-win-arm.txt
[win-arm-zip-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-win-arm.zip
[win-arm-zip-checksum-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-win-arm.zip.sha

[win-arm-badge-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/win_arm_Release_version_badge.svg
[win-arm-version-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/productCommit-win-arm.txt
[win-arm-zip-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-win-arm.zip
[win-arm-zip-checksum-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-win-arm.zip.sha

[win-arm-badge-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/win_arm_Release_version_badge.svg
[win-arm-version-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/productCommit-win-arm.txt
[win-arm-zip-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-win-arm.zip
[win-arm-zip-checksum-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-win-arm.zip.sha

[win-arm-badge-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/win_arm_Release_version_badge.svg
[win-arm-version-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/productCommit-win-arm.txt
[win-arm-zip-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-win-arm.zip
[win-arm-zip-checksum-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-win-arm.zip.sha

[win-arm-badge-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/win_arm_Release_version_badge.svg
[win-arm-version-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/productCommit-win-arm.txt
[win-arm-zip-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-win-arm.zip
[win-arm-zip-checksum-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-win-arm.zip.sha

[win-arm-badge-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/win_arm_Release_version_badge.svg
[win-arm-version-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/latest.version
[win-arm-zip-3.1.4XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/dotnet-sdk-latest-win-arm.zip
[win-arm-zip-checksum-3.1.4XX]: https://dotnetclichecksums.blob.core.windows.net/dotnet/Sdk/release/3.1.4xx/dotnet-sdk-latest-win-arm.zip.sha

[win-arm-badge-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/win_arm_Release_version_badge.svg
[win-arm-version-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/latest.version
[win-arm-zip-3.1.1XX]: https://dotnetcli.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/dotnet-sdk-latest-win-arm.zip
[win-arm-zip-checksum-3.1.1XX]: https://dotnetclichecksums.blob.core.windows.net/dotnet/Sdk/release/3.1.1xx/dotnet-sdk-latest-win-arm.zip.sha

[win-arm64-badge-main]: https://aka.ms/dotnet/6.0/daily/win_arm64_Release_version_badge.svg
[win-arm64-version-main]: https://aka.ms/dotnet/6.0/daily/productCommit-win-arm64.txt
[win-arm64-installer-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-win-arm64.exe
[win-arm64-installer-checksum-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-win-arm64.exe.sha
[win-arm64-zip-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-win-arm64.zip
[win-arm64-zip-checksum-main]: https://aka.ms/dotnet/6.0/daily/dotnet-sdk-win-arm64.zip.sha

[win-arm64-badge-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/win_arm64_Release_version_badge.svg
[win-arm64-version-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/productCommit-win-arm64.txt
[win-arm64-installer-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-win-arm64.exe
[win-arm64-installer-checksum-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-win-arm64.exe.sha
[win-arm64-zip-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-win-arm64.zip
[win-arm64-zip-checksum-6.0.1XX-preview7]: https://aka.ms/dotnet/6.0.1XX-preview7/daily/dotnet-sdk-win-arm64.zip.sha

[win-arm64-badge-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/win_arm64_Release_version_badge.svg
[win-arm64-version-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/productCommit-win-arm64.txt
[win-arm64-installer-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-win-arm64.exe
[win-arm64-installer-checksum-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-win-arm64.exe.sha
[win-arm64-zip-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-win-arm64.zip
[win-arm64-zip-checksum-5.0.4XX]: https://aka.ms/dotnet/5.0.4xx/daily/dotnet-sdk-win-arm64.zip.sha

[win-arm64-badge-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/win_arm64_Release_version_badge.svg
[win-arm64-version-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/productCommit-win-arm64.txt
[win-arm64-installer-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-win-arm64.exe
[win-arm64-installer-checksum-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-win-arm64.exe.sha
[win-arm64-zip-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-win-arm64.zip
[win-arm64-zip-checksum-5.0.3XX]: https://aka.ms/dotnet/5.0.3xx/daily/dotnet-sdk-win-arm64.zip.sha

[win-arm64-badge-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/win_arm64_Release_version_badge.svg
[win-arm64-version-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/productCommit-win-arm64.txt
[win-arm64-installer-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-win-arm64.exe
[win-arm64-installer-checksum-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-win-arm64.exe.sha
[win-arm64-zip-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-win-arm64.zip
[win-arm64-zip-checksum-5.0.2XX]: https://aka.ms/dotnet/5.0.2xx/daily/Sdk/dotnet-sdk-win-arm64.zip.sha

[sdk-shas-2.2.1XX]: https://github.com/dotnet/versions/tree/master/build-info/dotnet/product/cli/release/2.2#built-repositories

Looking for dotnet-install sources?
-----------------------------------

Sources for dotnet-install.sh and dotnet-install.ps1 are in the [install-scripts repo](https://github.com/dotnet/install-scripts).

Questions & Comments
--------------------

For all feedback, use the Issues on the [.NET CLI](https://github.com/dotnet/cli) repository.

License
-------

By downloading the .zip you are agreeing to the terms in the project [EULA](https://aka.ms/dotnet-core-eula).

