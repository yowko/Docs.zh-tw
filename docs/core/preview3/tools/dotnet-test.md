---
title: "dotnet-test 命令 | .NET Core SDK"
description: "`dotnet test` 命令是用來在指定的專案中執行單元測試。"
keywords: "dotnet-test, CLI, CLI 命令, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 3a0fa917-eb0a-4d7e-9217-d06e65455675
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: 66c9f949980612f6e21b6d441c004cc09f4eb7d3

---

#<a name="dotnet-test"></a>dotnet-test

## <a name="name"></a>名稱

`dotnet-test` - .NET 測試驅動程式

## <a name="synopsis"></a>概要

`dotnet test [project] [--help] 
    [--settings] [--listTests] [--testCaseFilter] 
    [--testAdapterPath] [--logger] 
    [--configuration] [--output] [--framework] [--diag]
    [--noBuild]`  

## <a name="description"></a>描述

`dotnet test` 命令是用來在指定的專案中執行單元測試。 單元測試是與單元測試架構 (例如 NUnit 或 xUnit) 具有相依性的類別庫專案，以及該單元測試架構的 dotnet test 執行器。 這些會封裝為 NuGet 套件，並還原為專案的一般相依性。

測試專案也需要指定測試執行器。 這是使用一般 `<PackageReference>` 元素所指定，如下列範例專案檔中所示：

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <Compile Include="**\*.cs" />
    <EmbeddedResource Include="**\*.resx" />
  </ItemGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.NETCore.App">
      <Version>1.0.1</Version>
    </PackageReference>
    <PackageReference Include="Microsoft.NET.Sdk">
      <Version>1.0.0-alpha-20161104-2</Version>
      <PrivateAssets>All</PrivateAssets>
    </PackageReference>
    <PackageReference Include="Microsoft.NET.Test.Sdk">
      <Version>15.0.0-preview-20161024-02</Version>
    </PackageReference>
    <PackageReference Include="xunit">
      <Version>2.2.0-beta3-build3402</Version>
    </PackageReference>
    <PackageReference Include="xunit.runner.visualstudio">
      <Version>2.2.0-beta4-build1188</Version>
    </PackageReference>
  </ItemGroup>

  <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
</Project>
```

## <a name="options"></a>選項

`[project]`
    
指定測試專案的路徑。 如果省略，則會預設為目前目錄。

`-h|--help`

印出命令的簡短說明。

`-s | --settings <SETTINGS_FILE>`

執行測試時要使用的設定。 

`-lt | --listTests`

列出在目前專案中探索到的所有測試。 

`-tcf | --testCaseFilter <EXPRESSION>`

使用指定的運算式篩選出目前專案中的測試。 

`-tap | --testAdapterPath <TEST_ADAPTER_PATH>`

在此測試執行中從指定的路徑使用自訂測試配接器。 

`--logger <LOGGER>`

指定測試結果的記錄器。 

`-c|--configuration <Debug|Release>`

用來建置的組態。 預設值是 `Release`。 

`-o|--output [OUTPUT_DIRECTORY]`

在其中尋找要執行的二進位檔的目錄。

`-f|--framework [FRAMEWORK]`

尋找特定架構的測試二進位檔。

`-r|--runtime [RUNTIME_IDENTIFIER]`

尋找所指定執行階段的測試二進位檔。

`--noBuild` 

請不要在執行之前建置測試專案。 

`-d | --diag <DIAGNOSTICS_FILE>`

針對測試平台啟用診斷模式，並將診斷訊息寫入至指定的檔案。 

## <a name="examples"></a>範例

執行目前目錄之專案中的測試：

`dotnet test` 

執行 test1 專案中的測試︰

`dotnet test ~/projects/test1/test1.csproj` 

## <a name="see-also"></a>請參閱

[架構](../../../standard/frameworks.md)

[執行階段識別項 (RID) 目錄](../../rid-catalog.md)



<!--HONumber=Nov16_HO3-->


