---
title: 管理 .NET Core 工具中的相依性
description: 說明如何利用 .NET Core 工具來管理相依性。
ms.date: 03/06/2017
ms.custom: seodec18
ms.openlocfilehash: ef2de666ee3e6a06ab62f45afe3c624bbbb44ac4
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611914"
---
# <a name="managing-dependencies-with-net-core-sdk-10"></a><span data-ttu-id="68a54-103">使用 .NET Core SDK 1.0 管理相依性</span><span class="sxs-lookup"><span data-stu-id="68a54-103">Managing dependencies with .NET Core SDK 1.0</span></span>

<span data-ttu-id="68a54-104">隨著 .NET Core 專案從 project.json 改為使用 csproj 和 MSBuild，也需要投入大量心力以確保專案檔與資產的統一，進而允許追蹤相依性。</span><span class="sxs-lookup"><span data-stu-id="68a54-104">With the move of .NET Core projects from project.json to csproj and MSBuild, a significant investment also happened that resulted in unification of the project file and assets that allow tracking of dependencies.</span></span> <span data-ttu-id="68a54-105">針對 .NET Core 專案，這類似於 project.json。</span><span class="sxs-lookup"><span data-stu-id="68a54-105">For .NET Core projects this is similar to what project.json did.</span></span> <span data-ttu-id="68a54-106">沒有會追蹤 NuGet 相依性的個別 JSON 或 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="68a54-106">There is no separate JSON or XML file that tracks NuGet dependencies.</span></span> <span data-ttu-id="68a54-107">透過此變更，我們也將另一種型別的*參考*引進稱為 `<PackageReference>` 的 csproj 語法中。</span><span class="sxs-lookup"><span data-stu-id="68a54-107">With this change, we've also introduced another type of *reference* into the csproj syntax called the `<PackageReference>`.</span></span> 

<span data-ttu-id="68a54-108">此文件說明新的參考型別。</span><span class="sxs-lookup"><span data-stu-id="68a54-108">This document describes the new reference type.</span></span> <span data-ttu-id="68a54-109">它也會說明如何使用這個新的參考型別，將套件相依性新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="68a54-109">It also shows how to add a package dependency using this new reference type to your project.</span></span> 

## <a name="the-new-packagereference-element"></a><span data-ttu-id="68a54-110">新的 \<PackageReference> 項目</span><span class="sxs-lookup"><span data-stu-id="68a54-110">The new \<PackageReference> element</span></span>
<span data-ttu-id="68a54-111">`<PackageReference>` 具有下列基本結構︰</span><span class="sxs-lookup"><span data-stu-id="68a54-111">The `<PackageReference>` has the following basic structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="68a54-112">如果您熟悉 MSBuild，它看起來會類似其他已經存在的參考型別。</span><span class="sxs-lookup"><span data-stu-id="68a54-112">If you are familiar with MSBuild, it will look familiar to the other reference types that already exist.</span></span> <span data-ttu-id="68a54-113">索引鍵是 `Include` 陳述式，它指定了您希望新增至專案的套件識別碼。</span><span class="sxs-lookup"><span data-stu-id="68a54-113">The key is the `Include` statement which specifies the package id that you wish to add to the project.</span></span> <span data-ttu-id="68a54-114">`<Version>` 子項目指定要取得的版本。</span><span class="sxs-lookup"><span data-stu-id="68a54-114">The `<Version>` child element specifies the version to get.</span></span> <span data-ttu-id="68a54-115">版本是依各 [NuGet 版本規則](/nuget/create-packages/dependency-versions#version-ranges)指定。</span><span class="sxs-lookup"><span data-stu-id="68a54-115">The versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="68a54-116">如果您不熟悉整體的 `csproj` 語法，您可以使用 [MSBuild 專案參考](/visualstudio/msbuild/msbuild-project-file-schema-reference)文件來取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="68a54-116">If you are not familiar with the overall `csproj` syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>  

<span data-ttu-id="68a54-117">您可以使用下例中條件來新增只能在特定目標中使用的相依性：</span><span class="sxs-lookup"><span data-stu-id="68a54-117">Adding a dependency that is available only in a specific target is done using conditions like in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="68a54-118">上面的內容表示只有當建置是針對該給定目標產生時，相依性才有效。</span><span class="sxs-lookup"><span data-stu-id="68a54-118">The above means that the dependency will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="68a54-119">條件中的 `$(TargetFramework)` 是要在專案中設定的 MSBuild 屬性。</span><span class="sxs-lookup"><span data-stu-id="68a54-119">The `$(TargetFramework)` in the condition is a MSBuild property that is being set in the project.</span></span> <span data-ttu-id="68a54-120">針對最常見的 .NET Core 應用程式，您將不需要執行此動作。</span><span class="sxs-lookup"><span data-stu-id="68a54-120">For most common .NET Core applications, you will not need to do this.</span></span> 

## <a name="adding-a-dependency-to-your-project"></a><span data-ttu-id="68a54-121">新增相依性至您的專案</span><span class="sxs-lookup"><span data-stu-id="68a54-121">Adding a dependency to your project</span></span>
<span data-ttu-id="68a54-122">新增相依性至您的專案相當直覺化。</span><span class="sxs-lookup"><span data-stu-id="68a54-122">Adding a dependency to your project is straightforward.</span></span> <span data-ttu-id="68a54-123">以下是如何將 Json.NET `9.0.1` 版新增至您專案的方式。</span><span class="sxs-lookup"><span data-stu-id="68a54-123">Here is an example of how to add Json.NET version `9.0.1` to your project.</span></span> <span data-ttu-id="68a54-124">當然，這適用於任何其他的 NuGet 相依性。</span><span class="sxs-lookup"><span data-stu-id="68a54-124">Of course, it is applicable to any other NuGet dependency.</span></span> 

<span data-ttu-id="68a54-125">當您開啟專案檔時，您會看到兩個或多個 `<ItemGroup>` 節點。</span><span class="sxs-lookup"><span data-stu-id="68a54-125">When you open your project file, you will see two or more `<ItemGroup>` nodes.</span></span> <span data-ttu-id="68a54-126">您會發現其中一個節點已具備 `<PackageReference>` 元素。</span><span class="sxs-lookup"><span data-stu-id="68a54-126">You will notice that one of the nodes already has `<PackageReference>` elements in it.</span></span> <span data-ttu-id="68a54-127">您可以將新的相依性新增至此節點，或建立一個新的節點；結果將會完全相同。</span><span class="sxs-lookup"><span data-stu-id="68a54-127">You can add your new dependency to this node, or create a new one; it is completely up to you as the result will be the same.</span></span> 

<span data-ttu-id="68a54-128">在此範例中，我們將使用由 `dotnet new console` 置放的預設範本。</span><span class="sxs-lookup"><span data-stu-id="68a54-128">In this example we will use the default template that is dropped by `dotnet new console`.</span></span> <span data-ttu-id="68a54-129">這是一個簡單的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="68a54-129">This is a simple console application.</span></span> <span data-ttu-id="68a54-130">當我們開啟專案時，我們首先會尋找 `<ItemGroup>` (其中已經有 `<PackageReference>` 存在)。</span><span class="sxs-lookup"><span data-stu-id="68a54-130">When we open up the project, we first find the `<ItemGroup>` with already existing `<PackageReference>` in it.</span></span> <span data-ttu-id="68a54-131">然後，新增下列內容到其中：</span><span class="sxs-lookup"><span data-stu-id="68a54-131">We then add the following to it:</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

<span data-ttu-id="68a54-132">在此之後，儲存專案並執行 `dotnet restore` 命令以安裝相依性。</span><span class="sxs-lookup"><span data-stu-id="68a54-132">After this, we save the project and run the `dotnet restore` command to install the dependency.</span></span> 

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="68a54-133">完整的專案看起來像這樣︰</span><span class="sxs-lookup"><span data-stu-id="68a54-133">The full project looks like this:</span></span>

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

## <a name="removing-a-dependency-from-the-project"></a><span data-ttu-id="68a54-134">從專案移除相依性</span><span class="sxs-lookup"><span data-stu-id="68a54-134">Removing a dependency from the project</span></span>
<span data-ttu-id="68a54-135">從專案檔移除相依性只牽涉到從專案檔移除 `<PackageReference>`。</span><span class="sxs-lookup"><span data-stu-id="68a54-135">Removing a dependency from the project file involves simply removing the `<PackageReference>` from the project file.</span></span>
