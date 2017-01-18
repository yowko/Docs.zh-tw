---
title: "csproj 參考 | .NET Core SDK"
description: "深入了解現有和 .NET Core csproj 檔案之間的差異"
keywords: "參考, csproj, .NET Core"
author: blackdwarf
ms.author: mairaw
manager: wpickett
ms.date: 10/12/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bdc29497-64f2-4d11-a21b-4097e0bdf5c9
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: af32bc592762d7e8cb4e3b180656d9c3464df4a5

---

<a name="additions-to-csproj-format-for-net-core"></a>適用於 .NET Core 之 csproj 格式的新增項目
----------------------------------------

# <a name="overview"></a>概觀 
此文件概述從 project.json 移動到 csproj 和 [MSBuild](https://github.com/Microsoft/MSBuild) 時，新增至 csproj 檔案的變更。 此文件僅概述**與非核心 csproj 檔案之間的差異**。 如果您需要有關一般專案檔語法以及參考的詳細資訊，請參閱 [MSBuild 專案檔]()文件。 

> **注意︰**此文件未來會持續增加內容，所以請回來確認以查看新增的項目。 

# <a name="additions"></a>新增項目

## <a name="packagereference"></a>PackageReference
在專案中指定 NuGet 相依性。 `Include` 屬性會指定套件識別碼。 

```xml
<PackageReference Include="<package-id>">
    <Version></Version>
    <PrivateAssets></PrivateAssets>
    <IncludeAssets></IncludeAssets>
    <ExcludeAssets></ExcludeAssets>
</PackageReference>
```

### <a name="version"></a>版本
`<Version>` 指定要還原的套件版本。 該元素採用 NuGet 版本設定配置的規則。

### <a name="includeassets"></a>IncludeAssets
`<IncludeAssets>` 子元素指定應該取用屬於由父代 `<PackageReference>` 所指定之套件的何種資產。 

該元素可包含一或多個下列值：

* 編譯：可供編譯之 lib 資料夾的內容
* 執行階段：已散發之執行階段資料夾的內容
* ContentFiles：所使用之 contentfiles 資料夾的內容
* 組建：使用組建資料夾中的 props/targets
* 原生：複製到執行階段輸出資料夾的原生資產內容
* 分析器：使用分析器

另外，該元素也可以包含︰

* 無：不使用任何這些項目
* 全部：使用所有這些項目

### <a name="excludeassets"></a>ExcludeAssets
`<ExcluseAssets>` 子元素指定不應該取用屬於由父代 `<PackageReference>` 所指定之套件的何種資產。

該元素可包含一或多個下列值：

* 編譯：可供編譯之 lib 資料夾的內容
* 執行階段：已散發之執行階段資料夾的內容
* ContentFiles：所使用之 contentfiles 資料夾的內容
* 組建：使用組建資料夾中的 props/targets
* 原生：複製到執行階段輸出資料夾的原生資產內容
* 分析器：使用分析器

另外，該元素也可以包含︰

* 無：不使用任何這些項目
* 全部：使用所有這些項目

### <a name="privateassets"></a>PrivateAssets
`<PrivateAssets>` 子元素指定應該取用屬於由父代 `<PackageReference>` 所指定之套件的何種資產，但是它們不應該傳遞至下一個專案。 

> **注意︰**這是 project.json/xproj `SupressParent` 元素的新詞彙。 

該元素可包含一或多個下列值：

* 編譯：可供編譯之 lib 資料夾的內容
* 執行階段：已散發之執行階段資料夾的內容
* ContentFiles：所使用之 contentfiles 資料夾的內容
* 組建：使用組建資料夾中的 props/targets
* 原生：複製到執行階段輸出資料夾的原生資產內容
* 分析器：使用分析器

另外，該元素也可以包含︰

* 無：不使用任何這些項目
* 全部：使用所有這些項目

## <a name="dotnetclitoolreference"></a>DotnetCliToolReference
`<DotnetCliToolReference>` 元素指定使用者想要在專案內容中還原的 CLI 工具。 它會取代 `project.json` 中的 `tools` 節點。 

### <a name="version"></a>版本
`<Version>` 指定要還原的套件版本。 該元素採用 NuGet 版本設定配置的規則。

## <a name="runtimeidentifiers"></a>RuntimeIdentifiers
`<RuntimeIdentifiers>` 元素允許針對專案指定以分號分隔的[執行階段識別碼](../../rid-catalog.md)清單。 這些行為允許發行自封式部署。 




<!--HONumber=Nov16_HO3-->


