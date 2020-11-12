---
title: dotnet 工具搜尋命令
description: Dotnet 工具搜尋命令會搜尋發行至 NuGet.org 的 .NET Core 工具。
ms.date: 11/11/2020
ms.openlocfilehash: 4357ce4864cad386968e4a76466066fbf2ce4060
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2020
ms.locfileid: "94558069"
---
# <a name="dotnet-tool-search"></a><span data-ttu-id="d825e-103">dotnet 工具搜尋</span><span class="sxs-lookup"><span data-stu-id="d825e-103">dotnet tool search</span></span>

<span data-ttu-id="d825e-104">本文 **適用于：** ✔️ .NET 5.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="d825e-104">**This article applies to:** ✔️ .NET 5.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="d825e-105">名稱</span><span class="sxs-lookup"><span data-stu-id="d825e-105">Name</span></span>

<span data-ttu-id="d825e-106">`dotnet tool search` -搜尋已發佈至 NuGet 的所有 [.Net Core 工具](global-tools.md) 。</span><span class="sxs-lookup"><span data-stu-id="d825e-106">`dotnet tool search` - Searches all [.NET Core tools](global-tools.md) that are published to NuGet.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d825e-107">概要</span><span class="sxs-lookup"><span data-stu-id="d825e-107">Synopsis</span></span>

```dotnetcli
dotnet tool search [--detail]  [--prerelease]
    [--skip <NUMBER>] [--take <NUMBER>] <SEARCH TERM>

dotnet tool search -h|--help
```

## <a name="description"></a><span data-ttu-id="d825e-108">描述</span><span class="sxs-lookup"><span data-stu-id="d825e-108">Description</span></span>

<span data-ttu-id="d825e-109">此 `dotnet tool search` 命令會提供一種方式，讓您在 NuGet 中搜尋可作為 .net 全域、工具路徑或本機工具使用的工具。</span><span class="sxs-lookup"><span data-stu-id="d825e-109">The `dotnet tool search` command provides a way for you to search NuGet for tools that can be used as .NET global, tool-path, or local tools.</span></span> <span data-ttu-id="d825e-110">此命令會搜尋工具名稱和中繼資料，例如標題、描述和標記。</span><span class="sxs-lookup"><span data-stu-id="d825e-110">The command searches the tool names and metadata such as titles, descriptions, and tags.</span></span>

<span data-ttu-id="d825e-111">此命令會使用 [NuGet 搜尋 API](/nuget/api/search-query-service-resource#search-for-packages)。</span><span class="sxs-lookup"><span data-stu-id="d825e-111">The command uses the [NuGet Search API](/nuget/api/search-query-service-resource#search-for-packages).</span></span> <span data-ttu-id="d825e-112">它會篩選 `packageType=dotnettool` 以僅選取 .net 工具套件。</span><span class="sxs-lookup"><span data-stu-id="d825e-112">It filters on `packageType=dotnettool` to select only .NET tool packages.</span></span>

## <a name="options"></a><span data-ttu-id="d825e-113">選項</span><span class="sxs-lookup"><span data-stu-id="d825e-113">Options</span></span>

- **`--detail`**

  <span data-ttu-id="d825e-114">顯示查詢的詳細結果。</span><span class="sxs-lookup"><span data-stu-id="d825e-114">Shows detailed results from the query.</span></span>

- **`--prerelease`**

  <span data-ttu-id="d825e-115">包含發行前版本的套件。</span><span class="sxs-lookup"><span data-stu-id="d825e-115">Includes pre-release packages.</span></span>

- **`--skip <NUMBER>`**

  <span data-ttu-id="d825e-116">指定要略過的查詢結果數目。</span><span class="sxs-lookup"><span data-stu-id="d825e-116">Specifies the number of query results to skip.</span></span> <span data-ttu-id="d825e-117">用於分頁。</span><span class="sxs-lookup"><span data-stu-id="d825e-117">Used for pagination.</span></span>

- **`--take <NUMBER>`**

  <span data-ttu-id="d825e-118">指定要顯示的查詢結果數目。</span><span class="sxs-lookup"><span data-stu-id="d825e-118">Specifies the number of query results to show.</span></span> <span data-ttu-id="d825e-119">用於分頁。</span><span class="sxs-lookup"><span data-stu-id="d825e-119">Used for pagination.</span></span>

- **`-h|--help`**

  <span data-ttu-id="d825e-120">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="d825e-120">Shows command-line help.</span></span>

## <a name="examples"></a><span data-ttu-id="d825e-121">範例</span><span class="sxs-lookup"><span data-stu-id="d825e-121">Examples</span></span>

- <span data-ttu-id="d825e-122">在套件名稱或描述中使用 "format" 的 .NET 工具搜尋 NuGet.org：</span><span class="sxs-lookup"><span data-stu-id="d825e-122">Search NuGet.org for .NET tools that have "format" in their package name or description:</span></span>

  ```dotnetcli
  dotnet tool search format
  ```

  <span data-ttu-id="d825e-123">輸出看起來會像下列範例：</span><span class="sxs-lookup"><span data-stu-id="d825e-123">The output looks like the following example:</span></span>

  ```output
  Package ID                              Latest Version      Authors                                                                     Downloads      Verified
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------
  dotnet-format                           4.1.131201          Microsoft                                                                   496746
  bsoa.generator                          1.0.0               Microsoft                                                                   533
  ```

- <span data-ttu-id="d825e-124">在套件名稱或中繼資料中使用 "format" 的 .NET 工具搜尋 NuGet.org，只顯示第一個結果，並顯示詳細的觀點。</span><span class="sxs-lookup"><span data-stu-id="d825e-124">Search NuGet.org for .NET tools that have "format" in their package name or metadata, show only the first result, and show a detailed view.</span></span>

  ```dotnetcli
  dotnet tool search format --take 1 --detail
  ```

  <span data-ttu-id="d825e-125">輸出看起來會像下列範例：</span><span class="sxs-lookup"><span data-stu-id="d825e-125">The output looks like the following example:</span></span>

  ```output
  ----------------
  dotnet-format
  Latest Version: 4.1.131201
  Authors: Microsoft
  Tags:
  Downloads: 496746
  Verified: False
  Description: Command line tool for formatting C# and Visual Basic code files based on .editorconfig settings.
  Versions:
          3.0.2 Downloads: 1973
          3.0.4 Downloads: 9064
          3.1.37601 Downloads: 114730
          3.2.107702 Downloads: 13423
          3.3.111304 Downloads: 131195
          4.0.130203 Downloads: 78610
          4.1.131201 Downloads: 145927
  ```

## <a name="see-also"></a><span data-ttu-id="d825e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d825e-126">See also</span></span>

- [<span data-ttu-id="d825e-127">.NET Core 工具</span><span class="sxs-lookup"><span data-stu-id="d825e-127">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="d825e-128">教學課程：使用 .NET Core CLI 安裝和使用 .NET Core 通用工具</span><span class="sxs-lookup"><span data-stu-id="d825e-128">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="d825e-129">教學課程：使用 .NET Core CLI 安裝和使用 .NET Core 本機工具</span><span class="sxs-lookup"><span data-stu-id="d825e-129">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
