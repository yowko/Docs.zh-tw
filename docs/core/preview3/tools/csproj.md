---
title: "csproj 參考 | Microsoft Docs"
description: "深入了解現有和 .NET Core csproj 檔案之間的差異"
keywords: "參考, csproj, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 07/02/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: bdc29497-64f2-4d11-a21b-4097e0bdf5c9
translationtype: Human Translation
ms.sourcegitcommit: 0402707f98af8b716b041ba1260162cd227918cc
ms.openlocfilehash: 98f6ced2a199bdbe2f91f46e48ffd3ac52438cf8

---

# <a name="additions-to-the-csproj-format-for-net-core"></a>適用於 .NET Core 之 csproj 格式的新增項目

[!INCLUDE[preview-warning](../../../includes/warning.md)]

此文件概述從 `project.json` 移動到 `csproj` 和 [MSBuild](https://github.com/Microsoft/MSBuild) 時，新增至 csproj 檔案的變更。 如需一般專案檔語法以及參考的詳細資訊，請參閱 [MSBuild 專案檔](https://docs.microsoft.com/visualstudio/msbuild/msbuild-project-file-schema-reference)文件。  

## <a name="additions"></a>新增項目

* 在專案中指定 NuGet 相依性的 PackageReference 項目。 `Include` 屬性會指定套件識別碼。 

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

## <a name="version"></a>版本
`Version` 指定要還原的套件版本。 該元素採用 NuGet 版本設定配置的規則。

## <a name="includeassets"></a>IncludeAssets
`IncludeAssets` 屬性指定應取用由 `<PackageReference>` 所指定屬於套件的何種資產。 

屬性可包含下列一或多個值：

* `Compile` – lib 資料夾的內容可供編譯。
* `Runtime` – 會散發 runtime 資料夾的內容。
* `ContentFiles` – 會使用 contentfiles 資料夾的內容。
* `Build` – 會使用組建資料夾中的屬性/目標。
* `Native` – 原生資產內容會複製到執行階段輸出資料夾。
* `Analyzers` – 會使用分析器。

另外，該屬性也可以包含︰

* `None` – 未使用任何資產。
* `All` – 會使用所有資產。

## <a name="excludeassets"></a>ExcludeAssets
`ExcludeAssets` 屬性指定不應取用屬於由 `<PackageReference>` 所指定套件的何種資產。

屬性可包含下列一或多個值：

* `Compile` – lib 資料夾的內容可供編譯。
* `Runtime` – 會散發 runtime 資料夾的內容。
* `ContentFiles` – 會使用 contentfiles 資料夾的內容。
* `Build` – 會使用組建資料夾中的屬性/目標。
* `Native` – 原生資產內容會複製到執行階段輸出資料夾。
* `Analyzers` – 會使用分析器。

另外，該元素也可以包含︰

* `None` – 未使用任何資產。
* `All` – 會使用所有資產。

## <a name="privateassets"></a>PrivateAssets
`PrivateAssets` 屬性指定應取用屬於由 `<PackageReference>` 所指定套件的何種資產，但是它們不應該傳遞至下一個專案。 

> [!NOTE]
> 這是 project.json/xproj `SuppressParent` 元素的新詞彙。 

屬性可包含下列一或多個值：

* `Compile` – lib 資料夾的內容可供編譯。
* `Runtime` – 會散發 runtime 資料夾的內容。
* `ContentFiles` – 會使用 contentfiles 資料夾的內容。
* `Build` – 會使用組建資料夾中的屬性/目標。
* `Native` – 原生資產內容會複製到執行階段輸出資料夾。
* `Analyzers` – 會使用分析器。

另外，該屬性也可以包含︰

* `None` – 未使用任何資產。
* `All` – 會使用所有資產。

* DotnetCliToolReference `<DotnetCliToolReference>` 項目元素會指定使用者想要在專案內容中還原的 CLI 工具。 它會取代 `project.json` 中的 `tools` 節點。 

```xml
<DotnetCliToolReference Include="<package-id>" Version="" />
```

## <a name="version"></a>版本
`Version` 指定要還原的套件版本。 該屬性採用 NuGet 版本控制配置的規則。

* RuntimeIdentifiers `<RuntimeIdentifiers>` 項目可讓您針對專案指定以分號分隔的[執行階段識別碼 (RID)](../../rid-catalog.md) 清單。 RID 允許發行獨立部署。 

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```


* RuntimeIdentifier `<RuntieIdentifier>` 元素可讓您針對專案只指定一個[執行階段識別項 (RID)](../../rid-catalog.md)。 RID 允許發行獨立部署。 

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```


* PackageTargetFallback `<PackageTargetFallback>` 項目可讓您指定一組要在還原套件時使用的相容目標。 其設計目的是為了讓使用 dotnet TxM 的套件能和未宣告 dotnet TxM 的套件一起運作。 如果您的專案使用 dotnet TxM，除非您將 `<PackageTargetFallback>` 加入至專案，以讓非 dotnet 平台變成能與 dotnet 相容，否則您相依的所有套件也必須要有 dotnet TxM。 

下列範例可為專案中的所有目標提供後援： 

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

下列範例只會為 `netcoreapp1.0` 目標指定後援︰

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp1.0'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a>NuGet 中繼資料屬性
隨著移動到 MSbuild，我們已經將封裝 NuGet 套件時使用的輸入中繼資料從 project.json 移動到 csproj 檔。 輸入為 MSBuild 屬性。 使用 `dotnet pack` 命令或屬於 SDK 一部分的 `Pack` MSBuild 目標時，會將下列的屬性清單當成封裝處理序的輸入使用。 

* IsPackable
* PackageVersion
* PackageId
* 標題
* 作者
* 說明
* Copyright
* PackageRequireLicenseAcceptance
* PackageLicenseUrl
* PackageProjectUrl
* PackageIconUrl
* PackageReleaseNotes
* PackageTags
* PackageOutputPath
* IncludeSymbols
* IncludeSource
* PackageTypes
* IsTool
* RepositoryUrl
* RepositoryType
* NoPackageAnalysis
* MinClientVersion
* IncludeBuildOutput
* IncludeContentInPack
* BuildOutputTargetFolder
* ContentTargetFolders
* NuspecFile
* NuspecBasePath
* NuspecProperties


<!--HONumber=Feb17_HO2-->


