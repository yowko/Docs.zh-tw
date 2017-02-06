---
title: "csproj 參考 | Microsoft Docs"
description: "深入了解現有和 .NET Core csproj 檔案之間的差異"
keywords: "參考, csproj, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 10/12/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: bdc29497-64f2-4d11-a21b-4097e0bdf5c9
translationtype: Human Translation
ms.sourcegitcommit: 2ad428dcda9ef213a8487c35a48b33929259abba
ms.openlocfilehash: dfa7cc0f7005269b4e2560c8bbc8b049ed02cc1a

---

# <a name="additions-to-the-csproj-format-for-net-core"></a>適用於 .NET Core 之 csproj 格式的新增項目

[!INCLUDE[preview-warning](../../../includes/warning.md)]

此文件概述從 `project.json` 移動到 `csproj` 和 [MSBuild](https://github.com/Microsoft/MSBuild) 時，新增至 csproj 檔案的變更。 如需一般專案檔語法以及參考的詳細資訊，請參閱 [MSBuild 專案檔](https://docs.microsoft.com/visualstudio/msbuild/msbuild-project-file-schema-reference)文件。  

## <a name="additions"></a>新增項目

### <a name="packagereference"></a>PackageReference
在專案中指定 NuGet 相依性。 `Include` 屬性會指定套件識別碼。 

```xml
<PackageReference Include="<package-id>">
    <Version></Version>
    <PrivateAssets></PrivateAssets>
    <IncludeAssets></IncludeAssets>
    <ExcludeAssets></ExcludeAssets>
</PackageReference>
```

#### <a name="version"></a>版本
`<Version>` 指定要還原的套件版本。 該元素採用 NuGet 版本設定配置的規則。

#### <a name="includeassets"></a>IncludeAssets
`<IncludeAssets>` 子元素指定應該取用屬於由父代 `<PackageReference>` 所指定之套件的何種資產。 

該元素可包含一或多個下列值：

* Compile – lib 資料夾的內容可供編譯。
* Runtime – 會散發 runtime 資料夾的內容。
* ContentFiles – 會使用 contentfiles 資料夾的內容。
* Build – 會使用 build 資料夾中的屬性/目標。
* Native – 原生資產內容會複製到執行階段輸出資料夾。
* Analyzers – 會使用分析器。

另外，該元素也可以包含︰

* None - 未使用任何資產。
* All - 會使用所有資產。

#### <a name="excludeassets"></a>ExcludeAssets
`<ExcludeAssets>` 子元素指定不應該取用屬於由父代 `<PackageReference>` 所指定之套件的何種資產。

該元素可包含一或多個下列值：

* Compile – lib 資料夾的內容可供編譯。
* Runtime – 會散發 runtime 資料夾的內容。
* ContentFiles – 會使用 contentfiles 資料夾的內容。
* Build – 會使用 build 資料夾中的屬性/目標。
* Native – 原生資產內容會複製到執行階段輸出資料夾。
* Analyzers – 會使用分析器。

另外，該元素也可以包含︰

* None - 未使用任何資產。
* All - 會使用所有資產。

#### <a name="privateassets"></a>PrivateAssets
`<PrivateAssets>` 子元素指定應該取用屬於由父代 `<PackageReference>` 所指定之套件的何種資產，但是它們不應該傳遞至下一個專案。 

> [!NOTE]
> 這是 project.json/xproj `SuppressParent` 元素的新詞彙。 

該元素可包含一或多個下列值：

* Compile – lib 資料夾的內容可供編譯。
* Runtime – 會散發 runtime 資料夾的內容。
* ContentFiles – 會使用 contentfiles 資料夾的內容。
* Build – 會使用 build 資料夾中的屬性/目標。
* Native – 原生資產內容會複製到執行階段輸出資料夾。
* Analyzers – 會使用分析器。

另外，該元素也可以包含︰

* None - 未使用任何資產。
* All - 會使用所有資產。

### <a name="dotnetclitoolreference"></a>DotnetCliToolReference
`<DotnetCliToolReference>` 元素指定使用者想要在專案內容中還原的 CLI 工具。 它會取代 `project.json` 中的 `tools` 節點。 

#### <a name="version"></a>版本
`<Version>` 指定要還原的套件版本。 該元素採用 NuGet 版本設定配置的規則。

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers
`<RuntimeIdentifiers>` 項目可讓您針對專案指定以分號分隔的[執行階段識別碼 (RID)](../../rid-catalog.md) 清單。 RID 允許發行獨立部署。 


<!--HONumber=Jan17_HO3-->


