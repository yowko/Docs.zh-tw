---
title: 管理 .NET 核心中的依賴項
description: 說明如何管理 .NET Core 應用程式的專案依賴項。
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.date: 02/25/2020
ms.openlocfilehash: 367be7eb04d58bffc0846de1d035a5801e8d9376
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399144"
---
# <a name="manage-dependencies-in-net-core-applications"></a>管理 .NET Core 應用程式中的依賴項

本文介紹如何通過編輯專案檔案或使用 CLI 來添加和刪除依賴項。

## <a name="the-packagereference-element"></a>包\<參考>元素

專案`<PackageReference>`檔元素具有以下結構：

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

該`Include`屬性指定要添加到專案的包的 ID。 該`Version`屬性指定要獲取的版本。 版本根據[NuGet 版本規則](/nuget/create-packages/dependency-versions#version-ranges)指定。

> [!NOTE]
> 如果您不熟悉專案檔案語法，請參閱[MSBuild 專案參考](/visualstudio/msbuild/msbuild-project-file-schema-reference)文檔以瞭解更多資訊。

使用條件添加僅在特定目標中可用的依賴項，如以下示例所示：

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

僅當生成針對該給定目標時，上例中的依賴項才有效。 條件`$(TargetFramework)`中的是正在專案中設置的 MSBuild 屬性。 對於大多數常見的 .NET Core 應用程式，您無需執行此操作。

## <a name="add-a-dependency-by-editing-the-project-file"></a>通過編輯專案檔案添加依賴項

要添加依賴項，在`<PackageReference>``<ItemGroup>`元素中添加元素。 您可以添加到現有`<ItemGroup>`或創建新的。 下面的示例使用由 創建的`dotnet new console`預設主控台應用程式專案。

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

## <a name="add-a-dependency-by-using-the-cli"></a>使用 CLI 添加依賴項

要添加依賴項，運行命令[dotnet add package](dotnet-add-package.md)，如以下示例所示：

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a>通過編輯專案檔案刪除依賴項

要刪除依賴項，請從`<PackageReference>`專案檔案中刪除其元素。

## <a name="remove-a-dependency-by-using-the-cli"></a>使用 CLI 刪除依賴項

要刪除依賴項，請運行[dotnet remove package](dotnet-remove-package.md)該命令，如以下示例所示：

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a>另請參閱

* [專案檔案中的 NuGet 包](../project-sdk/msbuild-props.md#nuget-packages)
* [dotnet list package命令](dotnet-remove-package.md)
