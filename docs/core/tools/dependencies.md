---
title: 管理 .NET Core 中的相依性
description: 說明如何管理 .NET Core 應用程式的專案相依性。
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.date: 02/25/2020
ms.openlocfilehash: 367be7eb04d58bffc0846de1d035a5801e8d9376
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157241"
---
# <a name="manage-dependencies-in-net-core-applications"></a><span data-ttu-id="e9e66-103">管理 .NET Core 應用程式中的相依性</span><span class="sxs-lookup"><span data-stu-id="e9e66-103">Manage dependencies in .NET Core applications</span></span>

<span data-ttu-id="e9e66-104">本文說明如何藉由編輯專案檔或使用 CLI 來新增和移除相依性。</span><span class="sxs-lookup"><span data-stu-id="e9e66-104">This article explains how to add and remove dependencies by editing the project file or by using the CLI.</span></span>

## <a name="the-packagereference-element"></a><span data-ttu-id="e9e66-105">\<PackageReference > 元素</span><span class="sxs-lookup"><span data-stu-id="e9e66-105">The \<PackageReference> element</span></span>

<span data-ttu-id="e9e66-106">`<PackageReference>` 專案檔案元素具有下列結構：</span><span class="sxs-lookup"><span data-stu-id="e9e66-106">The `<PackageReference>` project file element has the following structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="e9e66-107">`Include` 屬性會指定要加入至專案的封裝識別碼。</span><span class="sxs-lookup"><span data-stu-id="e9e66-107">The `Include` attribute specifies the ID of the package to add to the project.</span></span> <span data-ttu-id="e9e66-108">`Version` 屬性會指定要取得的版本。</span><span class="sxs-lookup"><span data-stu-id="e9e66-108">The `Version` attribute specifies the version to get.</span></span> <span data-ttu-id="e9e66-109">版本是根據[NuGet 版本規則](/nuget/create-packages/dependency-versions#version-ranges)來指定。</span><span class="sxs-lookup"><span data-stu-id="e9e66-109">Versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="e9e66-110">如果您不熟悉專案檔語法，請參閱[MSBuild 專案參考](/visualstudio/msbuild/msbuild-project-file-schema-reference)檔以取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e9e66-110">If you're not familiar with project-file syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="e9e66-111">使用條件來新增只能在特定目標中使用的相依性，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="e9e66-111">Use conditions to add a dependency that's available only in a specific target, as shown in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="e9e66-112">上述範例中的相依性只有在該指定目標的組建發生時才有效。</span><span class="sxs-lookup"><span data-stu-id="e9e66-112">The dependency in the preceding example will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="e9e66-113">條件中的 `$(TargetFramework)` 是在專案中設定的 MSBuild 屬性。</span><span class="sxs-lookup"><span data-stu-id="e9e66-113">The `$(TargetFramework)` in the condition is an MSBuild property that's being set in the project.</span></span> <span data-ttu-id="e9e66-114">對於最常見的 .NET Core 應用程式，您不需要這麼做。</span><span class="sxs-lookup"><span data-stu-id="e9e66-114">For most common .NET Core applications, you don't need to do this.</span></span>

## <a name="add-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="e9e66-115">藉由編輯專案檔來新增相依性</span><span class="sxs-lookup"><span data-stu-id="e9e66-115">Add a dependency by editing the project file</span></span>

<span data-ttu-id="e9e66-116">若要加入相依性，請在 `<ItemGroup>` 元素內加入 `<PackageReference>` 專案。</span><span class="sxs-lookup"><span data-stu-id="e9e66-116">To add a dependency, add a `<PackageReference>` element inside an `<ItemGroup>` element.</span></span> <span data-ttu-id="e9e66-117">您可以將加入至現有的 `<ItemGroup>`，或建立一個新的。</span><span class="sxs-lookup"><span data-stu-id="e9e66-117">You can add to an existing `<ItemGroup>` or create a new one.</span></span> <span data-ttu-id="e9e66-118">下列範例會使用 `dotnet new console`所建立的預設主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="e9e66-118">The following example uses the default console application project that's created by `dotnet new console`:</span></span>

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

## <a name="add-a-dependency-by-using-the-cli"></a><span data-ttu-id="e9e66-119">使用 CLI 新增相依性</span><span class="sxs-lookup"><span data-stu-id="e9e66-119">Add a dependency by using the CLI</span></span>

<span data-ttu-id="e9e66-120">若要新增相依性，請執行[dotnet add package](dotnet-add-package.md)命令，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="e9e66-120">To add a dependency, run the [dotnet add package](dotnet-add-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="e9e66-121">藉由編輯專案檔來移除相關性</span><span class="sxs-lookup"><span data-stu-id="e9e66-121">Remove a dependency by editing the project file</span></span>

<span data-ttu-id="e9e66-122">若要移除相依性，請從專案檔中移除它的 `<PackageReference>` 元素。</span><span class="sxs-lookup"><span data-stu-id="e9e66-122">To remove a dependency, remove its `<PackageReference>` element from the project file.</span></span>

## <a name="remove-a-dependency-by-using-the-cli"></a><span data-ttu-id="e9e66-123">使用 CLI 移除相依性</span><span class="sxs-lookup"><span data-stu-id="e9e66-123">Remove a dependency by using the CLI</span></span>

<span data-ttu-id="e9e66-124">若要移除相依性，請執行[dotnet remove package](dotnet-remove-package.md)命令，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="e9e66-124">To remove a dependency, run the [dotnet remove package](dotnet-remove-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a><span data-ttu-id="e9e66-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9e66-125">See also</span></span>

* [<span data-ttu-id="e9e66-126">專案檔中的 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="e9e66-126">NuGet packages in project files</span></span>](../project-sdk/msbuild-props.md#nuget-packages)
* <span data-ttu-id="e9e66-127">[dotnet list package 命令](dotnet-remove-package.md)</span><span class="sxs-lookup"><span data-stu-id="e9e66-127">[dotnet list package command](dotnet-remove-package.md)</span></span>
