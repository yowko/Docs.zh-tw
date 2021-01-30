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
# <a name="manage-dependencies-in-net-applications"></a><span data-ttu-id="2d356-103">管理 .NET 應用程式中的相依性</span><span class="sxs-lookup"><span data-stu-id="2d356-103">Manage dependencies in .NET applications</span></span>

<span data-ttu-id="2d356-104">本文說明如何藉由編輯專案檔或使用 CLI 來新增和移除相依性。</span><span class="sxs-lookup"><span data-stu-id="2d356-104">This article explains how to add and remove dependencies by editing the project file or by using the CLI.</span></span>

## <a name="the-packagereference-element"></a><span data-ttu-id="2d356-105">\<PackageReference> 項目</span><span class="sxs-lookup"><span data-stu-id="2d356-105">The \<PackageReference> element</span></span>

<span data-ttu-id="2d356-106">`<PackageReference>`專案檔案元素具有下列結構：</span><span class="sxs-lookup"><span data-stu-id="2d356-106">The `<PackageReference>` project file element has the following structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="2d356-107">`Include`屬性會指定要加入至專案的封裝識別碼。</span><span class="sxs-lookup"><span data-stu-id="2d356-107">The `Include` attribute specifies the ID of the package to add to the project.</span></span> <span data-ttu-id="2d356-108">`Version`屬性會指定要取得的版本。</span><span class="sxs-lookup"><span data-stu-id="2d356-108">The `Version` attribute specifies the version to get.</span></span> <span data-ttu-id="2d356-109">版本是依據 [NuGet 版本規則](/nuget/create-packages/dependency-versions#version-ranges)來指定。</span><span class="sxs-lookup"><span data-stu-id="2d356-109">Versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="2d356-110">如果您不熟悉專案檔語法，請參閱 [MSBuild 專案參考](/visualstudio/msbuild/msbuild-project-file-schema-reference) 檔，以取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2d356-110">If you're not familiar with project-file syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="2d356-111">使用條件來新增只能在特定目標中使用的相依性，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="2d356-111">Use conditions to add a dependency that's available only in a specific target, as shown in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="2d356-112">上述範例中的相依性只有在針對該指定目標進行組建時，才會是有效的。</span><span class="sxs-lookup"><span data-stu-id="2d356-112">The dependency in the preceding example will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="2d356-113">`$(TargetFramework)`條件中的是在專案中設定的 MSBuild 屬性。</span><span class="sxs-lookup"><span data-stu-id="2d356-113">The `$(TargetFramework)` in the condition is an MSBuild property that's being set in the project.</span></span> <span data-ttu-id="2d356-114">針對大部分常見的 .NET 應用程式，您不需要這麼做。</span><span class="sxs-lookup"><span data-stu-id="2d356-114">For most common .NET applications, you don't need to do this.</span></span>

## <a name="add-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="2d356-115">藉由編輯專案檔案來新增相依性</span><span class="sxs-lookup"><span data-stu-id="2d356-115">Add a dependency by editing the project file</span></span>

<span data-ttu-id="2d356-116">若要加入相依性，請 `<PackageReference>` 在元素內新增專案 `<ItemGroup>` 。</span><span class="sxs-lookup"><span data-stu-id="2d356-116">To add a dependency, add a `<PackageReference>` element inside an `<ItemGroup>` element.</span></span> <span data-ttu-id="2d356-117">您可以加入現有的 `<ItemGroup>` 或建立一個新的。</span><span class="sxs-lookup"><span data-stu-id="2d356-117">You can add to an existing `<ItemGroup>` or create a new one.</span></span> <span data-ttu-id="2d356-118">下列範例會使用由建立的預設主控台應用程式專案 `dotnet new console` ：</span><span class="sxs-lookup"><span data-stu-id="2d356-118">The following example uses the default console application project that's created by `dotnet new console`:</span></span>

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

## <a name="add-a-dependency-by-using-the-cli"></a><span data-ttu-id="2d356-119">使用 CLI 新增相依性</span><span class="sxs-lookup"><span data-stu-id="2d356-119">Add a dependency by using the CLI</span></span>

<span data-ttu-id="2d356-120">若要新增相依性，請執行 [dotnet add package](dotnet-add-package.md) 命令，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="2d356-120">To add a dependency, run the [dotnet add package](dotnet-add-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="2d356-121">藉由編輯專案檔案來移除相依性</span><span class="sxs-lookup"><span data-stu-id="2d356-121">Remove a dependency by editing the project file</span></span>

<span data-ttu-id="2d356-122">若要移除相依性，請 `<PackageReference>` 從專案檔中移除其元素。</span><span class="sxs-lookup"><span data-stu-id="2d356-122">To remove a dependency, remove its `<PackageReference>` element from the project file.</span></span>

## <a name="remove-a-dependency-by-using-the-cli"></a><span data-ttu-id="2d356-123">使用 CLI 移除相依性</span><span class="sxs-lookup"><span data-stu-id="2d356-123">Remove a dependency by using the CLI</span></span>

<span data-ttu-id="2d356-124">若要移除相依性，請執行 [dotnet remove package](dotnet-remove-package.md) 命令，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="2d356-124">To remove a dependency, run the [dotnet remove package](dotnet-remove-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a><span data-ttu-id="2d356-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d356-125">See also</span></span>

* [<span data-ttu-id="2d356-126">專案檔中的套件參考</span><span class="sxs-lookup"><span data-stu-id="2d356-126">Package references in project files</span></span>](../project-sdk/msbuild-props.md#reference-properties-and-items)
* [<span data-ttu-id="2d356-127">dotnet list package 命令</span><span class="sxs-lookup"><span data-stu-id="2d356-127">dotnet list package command</span></span>](dotnet-list-package.md)
