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
# <a name="manage-dependencies-with-net-core-sdk-10"></a><span data-ttu-id="03165-103">使用 .NET Core SDK 1.0 管理相依性</span><span class="sxs-lookup"><span data-stu-id="03165-103">Manage dependencies with .NET Core SDK 1.0</span></span>

<span data-ttu-id="03165-104">隨著 .NET Core 專案從 project.json 改為使用 csproj 和 MSBuild，也需要投入大量心力以確保專案檔與資產的統一，進而允許追蹤相依性。</span><span class="sxs-lookup"><span data-stu-id="03165-104">With the move of .NET Core projects from project.json to csproj and MSBuild, a significant investment also happened that resulted in unification of the project file and assets that allow tracking of dependencies.</span></span> <span data-ttu-id="03165-105">針對 .NET Core 專案，這類似于專案 json。</span><span class="sxs-lookup"><span data-stu-id="03165-105">For .NET Core projects, this is similar to what project.json did.</span></span> <span data-ttu-id="03165-106">沒有會追蹤 NuGet 相依性的個別 JSON 或 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="03165-106">There is no separate JSON or XML file that tracks NuGet dependencies.</span></span> <span data-ttu-id="03165-107">透過此變更，我們也將另一種型別的*參考*引進稱為 `<PackageReference>` 的 csproj 語法中。</span><span class="sxs-lookup"><span data-stu-id="03165-107">With this change, we've also introduced another type of *reference* into the csproj syntax called the `<PackageReference>`.</span></span>

<span data-ttu-id="03165-108">此文件說明新的參考型別。</span><span class="sxs-lookup"><span data-stu-id="03165-108">This document describes the new reference type.</span></span> <span data-ttu-id="03165-109">它也會說明如何使用這個新的參考型別，將套件相依性新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="03165-109">It also shows how to add a package dependency using this new reference type to your project.</span></span>

## <a name="the-new-packagereference-element"></a><span data-ttu-id="03165-110">新的 \<PackageReference> 項目</span><span class="sxs-lookup"><span data-stu-id="03165-110">The new \<PackageReference> element</span></span>

<span data-ttu-id="03165-111">`<PackageReference>` 具有下列基本結構︰</span><span class="sxs-lookup"><span data-stu-id="03165-111">The `<PackageReference>` has the following basic structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="03165-112">如果您熟悉 MSBuild，它看起來會類似其他已經存在的參考型別。</span><span class="sxs-lookup"><span data-stu-id="03165-112">If you are familiar with MSBuild, it will look familiar to the other reference types that already exist.</span></span> <span data-ttu-id="03165-113">索引鍵是 `Include` 語句，它會指定您想要加入至專案的封裝識別碼。</span><span class="sxs-lookup"><span data-stu-id="03165-113">The key is the `Include` statement, which specifies the package ID that you wish to add to the project.</span></span> <span data-ttu-id="03165-114">`<Version>` 子項目指定要取得的版本。</span><span class="sxs-lookup"><span data-stu-id="03165-114">The `<Version>` child element specifies the version to get.</span></span> <span data-ttu-id="03165-115">版本是依各 [NuGet 版本規則](/nuget/create-packages/dependency-versions#version-ranges)指定。</span><span class="sxs-lookup"><span data-stu-id="03165-115">The versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="03165-116">如果您不熟悉專案檔語法，請參閱[MSBuild 專案參考](/visualstudio/msbuild/msbuild-project-file-schema-reference)檔以取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="03165-116">If you're not familiar with the project-file syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="03165-117">使用條件來新增只能在特定目標中使用的相依性，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="03165-117">Use conditions to add a dependency that's available only in a specific target, as shown in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="03165-118">只有當該指定目標的組建發生時，相依性才有效。</span><span class="sxs-lookup"><span data-stu-id="03165-118">The dependency will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="03165-119">條件中的 `$(TargetFramework)` 是在專案中設定的 MSBuild 屬性。</span><span class="sxs-lookup"><span data-stu-id="03165-119">The `$(TargetFramework)` in the condition is an MSBuild property that's being set in the project.</span></span> <span data-ttu-id="03165-120">針對最常見的 .NET Core 應用程式，您將不需要執行此動作。</span><span class="sxs-lookup"><span data-stu-id="03165-120">For most common .NET Core applications, you will not need to do this.</span></span>

## <a name="add-a-dependency-to-the-project"></a><span data-ttu-id="03165-121">將相依性新增至專案</span><span class="sxs-lookup"><span data-stu-id="03165-121">Add a dependency to the project</span></span>

<span data-ttu-id="03165-122">新增相依性至您的專案相當直覺化。</span><span class="sxs-lookup"><span data-stu-id="03165-122">Adding a dependency to your project is straightforward.</span></span> <span data-ttu-id="03165-123">以下是如何將 Json.NET `9.0.1` 版新增至您專案的方式。</span><span class="sxs-lookup"><span data-stu-id="03165-123">Here is an example of how to add Json.NET version `9.0.1` to your project.</span></span> <span data-ttu-id="03165-124">當然，這適用於任何其他的 NuGet 相依性。</span><span class="sxs-lookup"><span data-stu-id="03165-124">Of course, it is applicable to any other NuGet dependency.</span></span>

<span data-ttu-id="03165-125">您的專案檔有兩個以上的 `<ItemGroup>` 節點。</span><span class="sxs-lookup"><span data-stu-id="03165-125">Your project file has two or more `<ItemGroup>` nodes.</span></span> <span data-ttu-id="03165-126">其中一個節點已經有 `<PackageReference>` 元素。</span><span class="sxs-lookup"><span data-stu-id="03165-126">One of the nodes already has `<PackageReference>` elements in it.</span></span> <span data-ttu-id="03165-127">您可以將新的相依性新增至此節點，或建立一個新的相依性;結果會相同。</span><span class="sxs-lookup"><span data-stu-id="03165-127">You can add your new dependency to this node or create a new one; the result will be the same.</span></span>

<span data-ttu-id="03165-128">下列範例會使用 `dotnet new console`所卸載的預設範本。</span><span class="sxs-lookup"><span data-stu-id="03165-128">The following example uses the default template that's dropped by `dotnet new console`.</span></span> <span data-ttu-id="03165-129">這是一個簡單的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="03165-129">This is a simple console application.</span></span> <span data-ttu-id="03165-130">當您開啟專案時，您會發現已經有現有 `<PackageReference>` 的 `<ItemGroup>`。</span><span class="sxs-lookup"><span data-stu-id="03165-130">When you open up the project, you'll find the `<ItemGroup>` with already existing `<PackageReference>` in it.</span></span> <span data-ttu-id="03165-131">在其中新增下列內容：</span><span class="sxs-lookup"><span data-stu-id="03165-131">Add the following to it:</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

<span data-ttu-id="03165-132">在此之後，請儲存專案並執行 `dotnet restore` 命令，以安裝相依性。</span><span class="sxs-lookup"><span data-stu-id="03165-132">After this, save the project and run the `dotnet restore` command to install the dependency.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="03165-133">完整的專案看起來像這樣︰</span><span class="sxs-lookup"><span data-stu-id="03165-133">The full project looks like this:</span></span>

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

## <a name="remove-a-dependency-from-the-project"></a><span data-ttu-id="03165-134">從專案移除相依性</span><span class="sxs-lookup"><span data-stu-id="03165-134">Remove a dependency from the project</span></span>

<span data-ttu-id="03165-135">從專案檔移除相依性只牽涉到從專案檔移除 `<PackageReference>`。</span><span class="sxs-lookup"><span data-stu-id="03165-135">Removing a dependency from the project file involves simply removing the `<PackageReference>` from the project file.</span></span>
