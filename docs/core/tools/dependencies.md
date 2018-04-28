---
title: 管理 .NET Core 工具中的相依性
description: 說明如何利用 .NET Core 工具來管理相依性。
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 5da4f5e4d837be874323ef700093b0d01c8ac98f
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="managing-dependencies-with-net-core-sdk-10"></a>使用 .NET Core SDK 1.0 管理相依性

隨著 .NET Core 專案從 project.json 改為使用 csproj 和 MSBuild，也需要投入大量心力以確保專案檔與資產的統一，進而允許追蹤相依性。 針對 .NET Core 專案，這類似於 project.json。 沒有會追蹤 NuGet 相依性的個別 JSON 或 XML 檔案。 透過此變更，我們也將另一種型別的*參考*引進稱為 `<PackageReference>` 的 csproj 語法中。 

此文件說明新的參考型別。 它也會說明如何使用這個新的參考型別，將套件相依性新增至您的專案。 

## <a name="the-new-packagereference-element"></a>新的 \<PackageReference> 項目
`<PackageReference>` 具有下列基本結構︰

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

如果您熟悉 MSBuild，它看起來會類似其他已經存在的參考型別。 索引鍵是 `Include` 陳述式，它指定了您希望新增至專案的套件識別碼。 `<Version>` 子項目指定要取得的版本。 版本是依各 [NuGet 版本規則](/nuget/create-packages/dependency-versions#version-ranges)指定。

> [!NOTE]
> 如果您不熟悉整體的 `csproj` 語法，您可以使用 [MSBuild 專案參考](/visualstudio/msbuild/msbuild-project-file-schema-reference)文件來取得詳細資訊。  

您可以使用下例中條件來新增只能在特定目標中使用的相依性：

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp1.0'" />
```

上面的內容表示只有當建置是針對該給定目標產生時，相依性才有效。 條件中的 `$(TargetFramework)` 是要在專案中設定的 MSBuild 屬性。 針對最常見的 .NET Core 應用程式，您將不需要執行此動作。 

## <a name="adding-a-dependency-to-your-project"></a>新增相依性至您的專案
新增相依性至您的專案相當直覺化。 以下是如何將 Json.NET `9.0.1` 版新增至您專案的方式。 當然，這適用於任何其他的 NuGet 相依性。 

當您開啟專案檔時，您會看到兩個或多個 `<ItemGroup>` 節點。 您會發現其中一個節點已具備 `<PackageReference>` 元素。 您可以將新的相依性新增至此節點，或建立一個新的節點；結果將會完全相同。 

在此範例中，我們將使用由 `dotnet new console` 置放的預設範本。 這是一個簡單的主控台應用程式。 當我們開啟專案時，我們首先會尋找 `<ItemGroup>` (其中已經有 `<PackageReference>` 存在)。 然後，新增下列內容到其中：

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```
在此之後，儲存專案並執行 `dotnet restore` 命令以安裝相依性。 

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

完整的專案看起來像這樣︰

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
</Project>
```

## <a name="removing-a-dependency-from-the-project"></a>從專案移除相依性
從專案檔移除相依性只牽涉到從專案檔移除 `<PackageReference>`。
