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
# <a name="manage-dependencies-in-net-core-applications"></a><span data-ttu-id="3ace9-103">管理 .NET Core 應用程式中的依賴項</span><span class="sxs-lookup"><span data-stu-id="3ace9-103">Manage dependencies in .NET Core applications</span></span>

<span data-ttu-id="3ace9-104">本文介紹如何通過編輯專案檔案或使用 CLI 來添加和刪除依賴項。</span><span class="sxs-lookup"><span data-stu-id="3ace9-104">This article explains how to add and remove dependencies by editing the project file or by using the CLI.</span></span>

## <a name="the-packagereference-element"></a><span data-ttu-id="3ace9-105">包\<參考>元素</span><span class="sxs-lookup"><span data-stu-id="3ace9-105">The \<PackageReference> element</span></span>

<span data-ttu-id="3ace9-106">專案`<PackageReference>`檔元素具有以下結構：</span><span class="sxs-lookup"><span data-stu-id="3ace9-106">The `<PackageReference>` project file element has the following structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="3ace9-107">該`Include`屬性指定要添加到專案的包的 ID。</span><span class="sxs-lookup"><span data-stu-id="3ace9-107">The `Include` attribute specifies the ID of the package to add to the project.</span></span> <span data-ttu-id="3ace9-108">該`Version`屬性指定要獲取的版本。</span><span class="sxs-lookup"><span data-stu-id="3ace9-108">The `Version` attribute specifies the version to get.</span></span> <span data-ttu-id="3ace9-109">版本根據[NuGet 版本規則](/nuget/create-packages/dependency-versions#version-ranges)指定。</span><span class="sxs-lookup"><span data-stu-id="3ace9-109">Versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="3ace9-110">如果您不熟悉專案檔案語法，請參閱[MSBuild 專案參考](/visualstudio/msbuild/msbuild-project-file-schema-reference)文檔以瞭解更多資訊。</span><span class="sxs-lookup"><span data-stu-id="3ace9-110">If you're not familiar with project-file syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="3ace9-111">使用條件添加僅在特定目標中可用的依賴項，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="3ace9-111">Use conditions to add a dependency that's available only in a specific target, as shown in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="3ace9-112">僅當生成針對該給定目標時，上例中的依賴項才有效。</span><span class="sxs-lookup"><span data-stu-id="3ace9-112">The dependency in the preceding example will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="3ace9-113">條件`$(TargetFramework)`中的是正在專案中設置的 MSBuild 屬性。</span><span class="sxs-lookup"><span data-stu-id="3ace9-113">The `$(TargetFramework)` in the condition is an MSBuild property that's being set in the project.</span></span> <span data-ttu-id="3ace9-114">對於大多數常見的 .NET Core 應用程式，您無需執行此操作。</span><span class="sxs-lookup"><span data-stu-id="3ace9-114">For most common .NET Core applications, you don't need to do this.</span></span>

## <a name="add-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="3ace9-115">通過編輯專案檔案添加依賴項</span><span class="sxs-lookup"><span data-stu-id="3ace9-115">Add a dependency by editing the project file</span></span>

<span data-ttu-id="3ace9-116">要添加依賴項，在`<PackageReference>``<ItemGroup>`元素中添加元素。</span><span class="sxs-lookup"><span data-stu-id="3ace9-116">To add a dependency, add a `<PackageReference>` element inside an `<ItemGroup>` element.</span></span> <span data-ttu-id="3ace9-117">您可以添加到現有`<ItemGroup>`或創建新的。</span><span class="sxs-lookup"><span data-stu-id="3ace9-117">You can add to an existing `<ItemGroup>` or create a new one.</span></span> <span data-ttu-id="3ace9-118">下面的示例使用由 創建的`dotnet new console`預設主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="3ace9-118">The following example uses the default console application project that's created by `dotnet new console`:</span></span>

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

## <a name="add-a-dependency-by-using-the-cli"></a><span data-ttu-id="3ace9-119">使用 CLI 添加依賴項</span><span class="sxs-lookup"><span data-stu-id="3ace9-119">Add a dependency by using the CLI</span></span>

<span data-ttu-id="3ace9-120">要添加依賴項，運行命令[dotnet add package](dotnet-add-package.md)，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="3ace9-120">To add a dependency, run the [dotnet add package](dotnet-add-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="3ace9-121">通過編輯專案檔案刪除依賴項</span><span class="sxs-lookup"><span data-stu-id="3ace9-121">Remove a dependency by editing the project file</span></span>

<span data-ttu-id="3ace9-122">要刪除依賴項，請從`<PackageReference>`專案檔案中刪除其元素。</span><span class="sxs-lookup"><span data-stu-id="3ace9-122">To remove a dependency, remove its `<PackageReference>` element from the project file.</span></span>

## <a name="remove-a-dependency-by-using-the-cli"></a><span data-ttu-id="3ace9-123">使用 CLI 刪除依賴項</span><span class="sxs-lookup"><span data-stu-id="3ace9-123">Remove a dependency by using the CLI</span></span>

<span data-ttu-id="3ace9-124">要刪除依賴項，請運行[dotnet remove package](dotnet-remove-package.md)該命令，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="3ace9-124">To remove a dependency, run the [dotnet remove package](dotnet-remove-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a><span data-ttu-id="3ace9-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ace9-125">See also</span></span>

* [<span data-ttu-id="3ace9-126">專案檔案中的 NuGet 包</span><span class="sxs-lookup"><span data-stu-id="3ace9-126">NuGet packages in project files</span></span>](../project-sdk/msbuild-props.md#nuget-packages)
* <span data-ttu-id="3ace9-127">[dotnet list package命令](dotnet-remove-package.md)</span><span class="sxs-lookup"><span data-stu-id="3ace9-127">[dotnet list package command](dotnet-remove-package.md)</span></span>
