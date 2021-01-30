---
title: 管理 .NET 中的相依性
description: 說明如何管理 .NET 應用程式的專案相依性。
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.topic: how-to
ms.date: 01/28/2021
ms.openlocfilehash: 9f5f814d0b4dc7aa3ff1a938c172475169a55bf2
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216124"
---
# <a name="manage-dependencies-in-net-applications"></a>管理 .NET 應用程式中的相依性

本文說明如何藉由編輯專案檔或使用 CLI 來新增和移除相依性。

## <a name="the-packagereference-element"></a>\<PackageReference> 項目

`<PackageReference>`專案檔案元素具有下列結構：

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

`Include`屬性會指定要加入至專案的封裝識別碼。 `Version`屬性會指定要取得的版本。 版本是依據 [NuGet 版本規則](/nuget/create-packages/dependency-versions#version-ranges)來指定。

> [!NOTE]
> 如果您不熟悉專案檔語法，請參閱 [MSBuild 專案參考](/visualstudio/msbuild/msbuild-project-file-schema-reference) 檔，以取得詳細資訊。

使用條件來新增只能在特定目標中使用的相依性，如下列範例所示：

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

上述範例中的相依性只有在針對該指定目標進行組建時，才會是有效的。 `$(TargetFramework)`條件中的是在專案中設定的 MSBuild 屬性。 針對大部分常見的 .NET 應用程式，您不需要這麼做。

## <a name="add-a-dependency-by-editing-the-project-file"></a>藉由編輯專案檔案來新增相依性

若要加入相依性，請 `<PackageReference>` 在元素內新增專案 `<ItemGroup>` 。 您可以加入現有的 `<ItemGroup>` 或建立一個新的。 下列範例會使用由建立的預設主控台應用程式專案 `dotnet new console` ：

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.EntityFrameworkCore" Version="3.1.2" />
  </ItemGroup>

</Project>
```

## <a name="add-a-dependency-by-using-the-cli"></a>使用 CLI 新增相依性

若要新增相依性，請執行 [dotnet add package](dotnet-add-package.md) 命令，如下列範例所示：

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a>藉由編輯專案檔案來移除相依性

若要移除相依性，請 `<PackageReference>` 從專案檔中移除其元素。

## <a name="remove-a-dependency-by-using-the-cli"></a>使用 CLI 移除相依性

若要移除相依性，請執行 [dotnet remove package](dotnet-remove-package.md) 命令，如下列範例所示：

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a>另請參閱

* [專案檔中的套件參考](../project-sdk/msbuild-props.md#reference-properties-and-items)
* [dotnet list package 命令](dotnet-list-package.md)
