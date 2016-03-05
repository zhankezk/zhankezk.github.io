--- 
layout: post
title: "TDS project build fail in Teamcity with VS 2012 runner"
author: "Ke"
comments: true
---
I'm sorry, don't have a solution yet. Still finding.

Other projects build on this agent, this project builds on other agents.

However .Net framework all looks fine. Teamcity is set to use Visual Studio 2012 runner. I thought it's because this agent doesn't have VS 2012 installed, but another agent doesn't have VS 2012 builds this project fine.

I did notice although other agents don't have VS installed, but they all have VS folders in program files folders. However it didn't work when I copied the folder across, but I feel I was close.

>[17:45:29][MSBuild] xx.scproj: Build target: Rebuild
[17:45:29][xx.scproj] Rebuild
[17:45:29][Rebuild] CallTarget
[17:45:29][CallTarget] GeneratePackage
[17:45:29][GeneratePackage] Building package with files in folder .\bin\Development\
[17:45:29][GeneratePackage] GeneratePackage
[17:45:29][GeneratePackage] ProjectFilePath: E:\buildAgent\work\xxx.scproj
[17:45:29][GeneratePackage] PackageOutputDirectory: .\bin\Development\..\Package_Development\
[17:45:29][GeneratePackage] ConfigurationToBuild: Development
[17:45:29][GeneratePackage] CompiledFiles: .\bin\Development\
[17:45:29][GeneratePackage] SeperateFilesAndItems: True
[17:45:29][GeneratePackage] SitecoreAssemblyPath: ..\..\lib\Sitecore\Assemblies
[17:45:29][GeneratePackage] Looking for Sitecore DLL's in E:\buildAgent\work\xx\xx\..\..\lib\Sitecore\Assemblies
[17:45:29][GeneratePackage] Exception Could not load file or assembly 'file:///xx\lib\Sitecore\Assemblies\Sitecore.Kernel.dll' or one of its dependencies. This assembly is built by a runtime newer than the currently loaded runtime and cannot be loaded.(HedgehogDevelopment.SitecoreProject.PackageBuilder.PackageBuilderException):
[17:45:29][GeneratePackage] at HedgehogDevelopment.SitecoreProject.PackageBuilder.Program.CheckForAssembly(String assemblyName, String assemblyRoot)
[17:45:29][GeneratePackage] at HedgehogDevelopment.SitecoreProject.PackageBuilder.Program.LoadSitecoreAssemblies(BuildContext ctx)
[17:45:29][GeneratePackage] at HedgehogDevelopment.SitecoreProject.PackageBuilder.Program.Main(String[] args)
[17:45:29][GeneratePackage] C:\Program Files (x86)\MSBuild\HedgehogDevelopment\SitecoreProject\v9.0\HedgehogDevelopment.SitecoreProject.targets(92, 5): Could not find required components. The Sitecore.Kernel.Dll, Sitecore.Update.dll, Sitecore.Zip.dll and Sitecore.Logging.dll are needed to build update packages. The path to these files must be set in the "Update Package" tab of the project property page.