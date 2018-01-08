---
title: "dotnet remove reference 命令 - .NET Core CLI"
description: "dotnet remove reference 命令提供方便的選項，以移除專案對專案參考。"
keywords: "dotnet-remove, CLI, CLI 命令, .NET Core"
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 691fd77c7605b6476adc764f20e59b51abd7d914
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="0a0f5-104">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="0a0f5-104">dotnet remove reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="0a0f5-105">名稱</span><span class="sxs-lookup"><span data-stu-id="0a0f5-105">Name</span></span>

<span data-ttu-id="0a0f5-106">`dotnet remove reference` - 移除專案對專案參考。</span><span class="sxs-lookup"><span data-stu-id="0a0f5-106">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0a0f5-107">概要</span><span class="sxs-lookup"><span data-stu-id="0a0f5-107">Synopsis</span></span>

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="0a0f5-108">描述</span><span class="sxs-lookup"><span data-stu-id="0a0f5-108">Description</span></span>

<span data-ttu-id="0a0f5-109">`dotnet remove reference` 命令提供方便的選項，以從專案中移除專案參考。</span><span class="sxs-lookup"><span data-stu-id="0a0f5-109">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="0a0f5-110">引數</span><span class="sxs-lookup"><span data-stu-id="0a0f5-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="0a0f5-111">目標專案檔。</span><span class="sxs-lookup"><span data-stu-id="0a0f5-111">Target project file.</span></span> <span data-ttu-id="0a0f5-112">如果未指定，命令會在目前的目錄中搜尋一個專案檔。</span><span class="sxs-lookup"><span data-stu-id="0a0f5-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="0a0f5-113">要移除的專案對專案 (P2P) 參考。</span><span class="sxs-lookup"><span data-stu-id="0a0f5-113">Project to project (P2P references to remove.</span></span> <span data-ttu-id="0a0f5-114">您可以指定一或多個專案。</span><span class="sxs-lookup"><span data-stu-id="0a0f5-114">You can specify one or multiple projects.</span></span> <span data-ttu-id="0a0f5-115">以 Unix/Linux 為基礎的終端機上支援 [Glob 模式 (英文)](https://en.wikipedia.org/wiki/Glob_(programming))。</span><span class="sxs-lookup"><span data-stu-id="0a0f5-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="0a0f5-116">選項</span><span class="sxs-lookup"><span data-stu-id="0a0f5-116">Options</span></span>

`-h|--help`

<span data-ttu-id="0a0f5-117">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="0a0f5-117">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="0a0f5-118">只有在以特定[架構](../../standard/frameworks.md)為目標時，才能移除參考。</span><span class="sxs-lookup"><span data-stu-id="0a0f5-118">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="0a0f5-119">範例</span><span class="sxs-lookup"><span data-stu-id="0a0f5-119">Examples</span></span>

<span data-ttu-id="0a0f5-120">從指定的專案中移除專案參考：</span><span class="sxs-lookup"><span data-stu-id="0a0f5-120">Remove a project reference from the specified project:</span></span>

`dotnet remove app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="0a0f5-121">從目前目錄中的專案移除多個專案參考：</span><span class="sxs-lookup"><span data-stu-id="0a0f5-121">Remove multiple project references from the project in the current directory:</span></span>

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="0a0f5-122">在 Unix/Linux 上使用 Glob 模式移除多個專案參考︰</span><span class="sxs-lookup"><span data-stu-id="0a0f5-122">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

`dotnet remove app/app.csproj reference **/*.csproj`
