---
title: "管理 .NET Core 工具中的相依性"
description: "說明如何利用 .NET Core 工具來管理相依性。"
keywords: "CLI, 擴充性, 自訂命令, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 74b87cdb-a244-4c13-908c-539118bfeef9
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b982d72b92cefb015c584ea6827dc60999ca9a00
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="managing-dependencies-with-net-core-sdk-10"></a><span data-ttu-id="181ac-104">使用 .NET Core SDK 1.0 管理相依性</span><span class="sxs-lookup"><span data-stu-id="181ac-104">Managing dependencies with .NET Core SDK 1.0</span></span>

<span data-ttu-id="181ac-105">隨著 .NET Core 專案從 project.json 改為使用 csproj 和 MSBuild，也需要投入大量心力以確保專案檔與資產的統一，進而允許追蹤相依性。</span><span class="sxs-lookup"><span data-stu-id="181ac-105">With the move of .NET Core projects from project.json to csproj and MSBuild, a significant investment also happened that resulted in unification of the project file and assets that allow tracking of dependencies.</span></span> <span data-ttu-id="181ac-106">針對 .NET Core 專案，這類似於 project.json。</span><span class="sxs-lookup"><span data-stu-id="181ac-106">For .NET Core projects this is similar to what project.json did.</span></span> <span data-ttu-id="181ac-107">沒有會追蹤 NuGet 相依性的個別 JSON 或 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="181ac-107">There is no separate JSON or XML file that tracks NuGet dependencies.</span></span> <span data-ttu-id="181ac-108">透過此變更，我們也將另一種型別的*參考*引進稱為 `<PackageReference>` 的 csproj 語法中。</span><span class="sxs-lookup"><span data-stu-id="181ac-108">With this change, we've also introduced another type of *reference* into the csproj syntax called the `<PackageReference>`.</span></span> 

<span data-ttu-id="181ac-109">此文件說明新的參考型別。</span><span class="sxs-lookup"><span data-stu-id="181ac-109">This document describes the new reference type.</span></span> <span data-ttu-id="181ac-110">它也會說明如何使用這個新的參考型別，將套件相依性新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="181ac-110">It also shows how to add a package dependency using this new reference type to your project.</span></span> 

## <a name="the-new-packagereference-element"></a><span data-ttu-id="181ac-111">新的 \<PackageReference> 項目</span><span class="sxs-lookup"><span data-stu-id="181ac-111">The new \<PackageReference> element</span></span>
<span data-ttu-id="181ac-112">`<PackageReference>` 具有下列基本結構︰</span><span class="sxs-lookup"><span data-stu-id="181ac-112">The `<PackageReference>` has the following basic structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="181ac-113">如果您熟悉 MSBuild，它看起來會類似其他已經存在的參考型別。</span><span class="sxs-lookup"><span data-stu-id="181ac-113">If you are familiar with MSBuild, it will look familiar to the other reference types that already exist.</span></span> <span data-ttu-id="181ac-114">索引鍵是 `Include` 陳述式，它指定了您希望新增至專案的套件識別碼。</span><span class="sxs-lookup"><span data-stu-id="181ac-114">The key is the `Include` statement which specifies the package id that you wish to add to the project.</span></span> <span data-ttu-id="181ac-115">`<Version>` 子項目指定要取得的版本。</span><span class="sxs-lookup"><span data-stu-id="181ac-115">The `<Version>` child element specifies the version to get.</span></span> <span data-ttu-id="181ac-116">版本是依各 [NuGet 版本規則](/nuget/create-packages/dependency-versions#version-ranges)指定。</span><span class="sxs-lookup"><span data-stu-id="181ac-116">The versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="181ac-117">如果您不熟悉整體的 `csproj` 語法，您可以使用 [MSBuild 專案參考](/visualstudio/msbuild/msbuild-project-file-schema-reference)文件來取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="181ac-117">If you are not familiar with the overall `csproj` syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>  

<span data-ttu-id="181ac-118">您可以使用下例中條件來新增只能在特定目標中使用的相依性：</span><span class="sxs-lookup"><span data-stu-id="181ac-118">Adding a dependency that is available only in a specific target is done using conditions like in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp1.0'" />
```

<span data-ttu-id="181ac-119">上面的內容表示只有當建置是針對該給定目標產生時，相依性才有效。</span><span class="sxs-lookup"><span data-stu-id="181ac-119">The above means that the dependency will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="181ac-120">條件中的 `$(TargetFramework)` 是要在專案中設定的 MSBuild 屬性。</span><span class="sxs-lookup"><span data-stu-id="181ac-120">The `$(TargetFramework)` in the condition is a MSBuild property that is being set in the project.</span></span> <span data-ttu-id="181ac-121">針對最常見的 .NET Core 應用程式，您將不需要執行此動作。</span><span class="sxs-lookup"><span data-stu-id="181ac-121">For most common .NET Core applications, you will not need to do this.</span></span> 

## <a name="adding-a-dependency-to-your-project"></a><span data-ttu-id="181ac-122">新增相依性至您的專案</span><span class="sxs-lookup"><span data-stu-id="181ac-122">Adding a dependency to your project</span></span>
<span data-ttu-id="181ac-123">新增相依性至您的專案相當直覺化。</span><span class="sxs-lookup"><span data-stu-id="181ac-123">Adding a dependency to your project is straightforward.</span></span> <span data-ttu-id="181ac-124">以下是如何將 Json.NET `9.0.1` 版新增至您專案的方式。</span><span class="sxs-lookup"><span data-stu-id="181ac-124">Here is an example of how to add Json.NET version `9.0.1` to your project.</span></span> <span data-ttu-id="181ac-125">當然，這適用於任何其他的 NuGet 相依性。</span><span class="sxs-lookup"><span data-stu-id="181ac-125">Of course, it is applicable to any other NuGet dependency.</span></span> 

<span data-ttu-id="181ac-126">當您開啟專案檔時，您會看到兩個或多個 `<ItemGroup>` 節點。</span><span class="sxs-lookup"><span data-stu-id="181ac-126">When you open your project file, you will see two or more `<ItemGroup>` nodes.</span></span> <span data-ttu-id="181ac-127">您會發現其中一個節點已具備 `<PackageReference>` 元素。</span><span class="sxs-lookup"><span data-stu-id="181ac-127">You will notice that one of the nodes already has `<PackageReference>` elements in it.</span></span> <span data-ttu-id="181ac-128">您可以將新的相依性新增至此節點，或建立一個新的節點；結果將會完全相同。</span><span class="sxs-lookup"><span data-stu-id="181ac-128">You can add your new dependency to this node, or create a new one; it is completely up to you as the result will be the same.</span></span> 

<span data-ttu-id="181ac-129">在此範例中，我們將使用由 `dotnet new console` 置放的預設範本。</span><span class="sxs-lookup"><span data-stu-id="181ac-129">In this example we will use the default template that is dropped by `dotnet new console`.</span></span> <span data-ttu-id="181ac-130">這是一個簡單的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="181ac-130">This is a simple console application.</span></span> <span data-ttu-id="181ac-131">當我們開啟專案時，我們首先會尋找 `<ItemGroup>` (其中已經有 `<PackageReference>` 存在)。</span><span class="sxs-lookup"><span data-stu-id="181ac-131">When we open up the project, we first find the `<ItemGroup>` with already existing `<PackageReference>` in it.</span></span> <span data-ttu-id="181ac-132">然後，新增下列內容到其中：</span><span class="sxs-lookup"><span data-stu-id="181ac-132">We then add the following to it:</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```
<span data-ttu-id="181ac-133">在此之後，儲存專案並執行 `dotnet restore` 命令以安裝相依性。</span><span class="sxs-lookup"><span data-stu-id="181ac-133">After this, we save the project and run the `dotnet restore` command to install the dependency.</span></span> 

<span data-ttu-id="181ac-134">完整的專案看起來像這樣︰</span><span class="sxs-lookup"><span data-stu-id="181ac-134">The full project looks like this:</span></span>

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

## <a name="removing-a-dependency-from-the-project"></a><span data-ttu-id="181ac-135">從專案移除相依性</span><span class="sxs-lookup"><span data-stu-id="181ac-135">Removing a dependency from the project</span></span>
<span data-ttu-id="181ac-136">從專案檔移除相依性只牽涉到從專案檔移除 `<PackageReference>`。</span><span class="sxs-lookup"><span data-stu-id="181ac-136">Removing a dependency from the project file involves simply removing the `<PackageReference>` from the project file.</span></span>

