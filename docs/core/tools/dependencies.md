---
title: 管理 .NET Core 工具中的相依性
description: 說明如何利用 .NET Core 工具來管理相依性。
ms.date: 03/06/2017
ms.openlocfilehash: 916daca0240c10dc63ca96048590a426bc51d450
ms.sourcegitcommit: feb42222f1430ca7b8115ae45e7a38fc4a1ba623
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/02/2020
ms.locfileid: "76965616"
---
# <a name="manage-dependencies-with-net-core-sdk-10"></a>使用 .NET Core SDK 1.0 管理相依性

隨著 .NET Core 專案從 project.json 改為使用 csproj 和 MSBuild，也需要投入大量心力以確保專案檔與資產的統一，進而允許追蹤相依性。 針對 .NET Core 專案，這類似于專案 json。 沒有會追蹤 NuGet 相依性的個別 JSON 或 XML 檔案。 透過此變更，我們也將另一種型別的*參考*引進稱為 `<PackageReference>` 的 csproj 語法中。

此文件說明新的參考型別。 它也會說明如何使用這個新的參考型別，將套件相依性新增至您的專案。

## <a name="the-new-packagereference-element"></a>新的 \<PackageReference> 項目

`<PackageReference>` 具有下列基本結構︰

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

如果您熟悉 MSBuild，它看起來會類似其他已經存在的參考型別。 索引鍵是 `Include` 語句，它會指定您想要加入至專案的封裝識別碼。 `<Version>` 子項目指定要取得的版本。 版本是依各 [NuGet 版本規則](/nuget/create-packages/dependency-versions#version-ranges)指定。

> [!NOTE]
> 如果您不熟悉專案檔語法，請參閱[MSBuild 專案參考](/visualstudio/msbuild/msbuild-project-file-schema-reference)檔以取得詳細資訊。

使用條件來新增只能在特定目標中使用的相依性，如下列範例所示：

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

只有當該指定目標的組建發生時，相依性才有效。 條件中的 `$(TargetFramework)` 是在專案中設定的 MSBuild 屬性。 針對最常見的 .NET Core 應用程式，您將不需要執行此動作。

## <a name="add-a-dependency-to-the-project"></a>將相依性新增至專案

新增相依性至您的專案相當直覺化。 以下是如何將 Json.NET `9.0.1` 版新增至您專案的方式。 當然，這適用於任何其他的 NuGet 相依性。

您的專案檔有兩個以上的 `<ItemGroup>` 節點。 其中一個節點已經有 `<PackageReference>` 元素。 您可以將新的相依性新增至此節點，或建立一個新的相依性;結果會相同。

下列範例會使用 `dotnet new console`所卸載的預設範本。 這是一個簡單的主控台應用程式。 當您開啟專案時，您會發現已經有現有 `<PackageReference>` 的 `<ItemGroup>`。 在其中新增下列內容：

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

在此之後，請儲存專案並執行 `dotnet restore` 命令，以安裝相依性。

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

完整的專案看起來像這樣︰

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
</Project>
```

## <a name="remove-a-dependency-from-the-project"></a>從專案移除相依性

從專案檔移除相依性只牽涉到從專案檔移除 `<PackageReference>`。
