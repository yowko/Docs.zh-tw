---
title: "dotnet-add reference 命令 - .NET Core CLI"
description: "dotnet add reference 命令提供方便的選項，以新增專案對專案參考。"
author: mairaw
ms.author: mairaw
ms.date: 09/19/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 9c6b0f434a9d6b1431e375ec6a437497aaddfc61
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="92b68-103">dotnet-add reference</span><span class="sxs-lookup"><span data-stu-id="92b68-103">dotnet-add reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="92b68-104">名稱</span><span class="sxs-lookup"><span data-stu-id="92b68-104">Name</span></span>

<span data-ttu-id="92b68-105">`dotnet add reference` - 新增專案對專案 (P2P) 參考。</span><span class="sxs-lookup"><span data-stu-id="92b68-105">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="92b68-106">概要</span><span class="sxs-lookup"><span data-stu-id="92b68-106">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="92b68-107">說明</span><span class="sxs-lookup"><span data-stu-id="92b68-107">Description</span></span>

<span data-ttu-id="92b68-108">`dotnet add reference` 命令提供方便的選項，將專案參考新增至專案。</span><span class="sxs-lookup"><span data-stu-id="92b68-108">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="92b68-109">執行命令之後，系統就會將 [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) 元素新增至專案檔。</span><span class="sxs-lookup"><span data-stu-id="92b68-109">After running the command, the [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="92b68-110">引數</span><span class="sxs-lookup"><span data-stu-id="92b68-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="92b68-111">指定專案檔。</span><span class="sxs-lookup"><span data-stu-id="92b68-111">Specifies the project file.</span></span> <span data-ttu-id="92b68-112">如果未指定，命令會在目前的目錄中搜尋一個專案檔。</span><span class="sxs-lookup"><span data-stu-id="92b68-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="92b68-113">要新增的專案對專案 (P2P) 參考。</span><span class="sxs-lookup"><span data-stu-id="92b68-113">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="92b68-114">指定一個或多個專案。</span><span class="sxs-lookup"><span data-stu-id="92b68-114">Specify one or more projects.</span></span> <span data-ttu-id="92b68-115">Unix/Linux 系統支援 [Glob 模式 (英文)](https://en.wikipedia.org/wiki/Glob_(programming))。</span><span class="sxs-lookup"><span data-stu-id="92b68-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="92b68-116">選項</span><span class="sxs-lookup"><span data-stu-id="92b68-116">Options</span></span>

`-h|--help`

<span data-ttu-id="92b68-117">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="92b68-117">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="92b68-118">只有在以特定[架構](../../standard/frameworks.md)為目標時，才能新增專案參考。</span><span class="sxs-lookup"><span data-stu-id="92b68-118">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="92b68-119">範例</span><span class="sxs-lookup"><span data-stu-id="92b68-119">Examples</span></span>

<span data-ttu-id="92b68-120">新增專案參考：</span><span class="sxs-lookup"><span data-stu-id="92b68-120">Add a project reference:</span></span>

`dotnet add app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="92b68-121">目前目錄中加入多個專案的專案參考：</span><span class="sxs-lookup"><span data-stu-id="92b68-121">Add multiple project references to the project in the current directory:</span></span>

`dotnet add reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="92b68-122">在 Linux/Unix 上使用 Glob 模式新增多個專案參考：</span><span class="sxs-lookup"><span data-stu-id="92b68-122">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

`dotnet add app/app.csproj reference **/*.csproj`
