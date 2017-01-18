---
title: "管理 .NET Core Preview 3 工具中的相依性"
description: "Preview 3 變更了相依性管理方式"
keywords: "CLI, 擴充性, 自訂命令, .NET Core"
author: blackdwarf
manager: wpickett
ms.date: 11/12/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 74b87cdb-a244-4c13-908c-539118bfeef9
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: e04d5f3b08c7f6885ed9914a91fc308234e6ce3b

---

<a name="managing-dependencies-in-net-core-preview-3-tooling"></a>管理 .NET Core Preview 3 工具中的相依性
----------------------------------------------------

# <a name="overview"></a>概觀
透過將 .NET Core 專案從 project.json 移動至 csproj 和 MSBuild，專案檔與資產的整合允許相依性的追蹤，而產生重要的投資。 針對 .NET Core 專案，這類似於 project.json。 沒有會追蹤 NuGet 相依性的個別 JSON 或 XML 檔案。 透過此變更，我們也將另一種型別的*參考*引進稱為 `<PackageReference>` 的 csproj 語法中。 

此文件說明新的參考型別。 它也會說明如何使用這個新的參考型別，將套件相依性新增至您的專案。 

# <a name="the-new-packagereference-element"></a>新 <PackageReference> 元素
`<PackageReference>` 具有下列基本結構︰

```xml
<PackageReference Include="<Package_ID>">
    <Version>PACKAGE_VERSION</Version>
</PackageReference>
```

如果您熟悉 MSBuild，它看起來會類似其他已經存在的[參考型別]()。 索引鍵是 `Include` 陳述式，它指定了您希望新增至專案的套件識別碼。 `<Version>` 子元素指定要取得的版本。 版本是依各 [NuGet 版本規則](https://docs.nuget.org/ndocs/create-packages/dependency-versions#version-ranges)指定。  

> **注意︰**如果您不熟悉整體的 `csproj` 語法，您可以使用 [MSBuild 專案參考文件]()來了解。  

您可以使用條件來新增只能在特定目標中使用的相依性：

```xml
<PackageReference Include="<Package_ID>" Condition="'$(TargetFramework)' == 'netcoreapp1.0'">
    <Version>PACKAGE_VERSION</Version>
</PackageReference>
```

上面的內容表示只有當建置是針對該給定目標產生時，相依性才有效。 條件中的 `$(TargetFramework)` 是要在專案中設定的 MSBuild 屬性。 針對最常見的 .NET Core 應用程式，您將不需要執行此動作。 

# <a name="adding-a-dependency-to-your-project"></a>新增相依性至您的專案
新增相依性至您的專案相當直覺化。 以下是如何將 `JSON.net` 版本 `9.0.1` 新增至您專案的方式。 當然，這適用於任何其他的 NuGet 相依性。 

當您開啟專案檔時，您會看到兩個或多個 `<ItemGroup>` 節點。 您會發現其中一個節點已具備 `<PackageReference>` 元素。 您可以將新的相依性新增至此節點，或建立一個新的節點；結果將會完全相同。 

在此範例中，我們將使用由 `dotnet new` 置放的預設範本。 這是一個簡單的主控台應用程式。 當我們開啟專案時，我們首先會尋找 `<ItemGroup>` (其中已經有 `<PackageReference>` 存在)。 然後，新增下列內容到其中：

```xml
<PackageReference Include="Newtonsoft.Json">
    <Version>9.0.1</Version>
</PackageReference>
```
在此之後，儲存專案並執行 `dotnet restore` 命令以安裝相依性。 

完整的專案看起來像這樣︰

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
    <PackageReference Include="Newtonsoft.Json">
        <Version>9.0.1</Version>
    </PackageReference>
    <PackageReference Include="Microsoft.NET.Sdk">
      <Version>1.0.0-alpha-20161104-2</Version>
      <PrivateAssets>All</PrivateAssets>
    </PackageReference>
  </ItemGroup>
  
  <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
</Project>
```

# <a name="removing-a-dependency-from-the-project"></a>從專案移除相依性
從專案檔移除相依性只牽涉到從專案檔移除 `<PackageReference>`。 





<!--HONumber=Nov16_HO3-->


