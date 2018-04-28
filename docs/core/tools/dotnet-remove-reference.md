---
title: dotnet remove reference 命令 - .NET Core CLI
description: dotnet remove reference 命令提供方便的選項，以移除專案對專案參考。
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 0b7fb2788ccc04b54bf02f0387141d501612c16d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="91a2c-103">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="91a2c-103">dotnet remove reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="91a2c-104">名稱</span><span class="sxs-lookup"><span data-stu-id="91a2c-104">Name</span></span>

<span data-ttu-id="91a2c-105">`dotnet remove reference` - 移除專案對專案參考。</span><span class="sxs-lookup"><span data-stu-id="91a2c-105">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="91a2c-106">概要</span><span class="sxs-lookup"><span data-stu-id="91a2c-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="91a2c-107">描述</span><span class="sxs-lookup"><span data-stu-id="91a2c-107">Description</span></span>

<span data-ttu-id="91a2c-108">`dotnet remove reference` 命令提供方便的選項，以從專案中移除專案參考。</span><span class="sxs-lookup"><span data-stu-id="91a2c-108">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="91a2c-109">引數</span><span class="sxs-lookup"><span data-stu-id="91a2c-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="91a2c-110">目標專案檔。</span><span class="sxs-lookup"><span data-stu-id="91a2c-110">Target project file.</span></span> <span data-ttu-id="91a2c-111">如果未指定，命令會在目前的目錄中搜尋一個專案檔。</span><span class="sxs-lookup"><span data-stu-id="91a2c-111">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="91a2c-112">要移除的專案對專案 (P2P) 參考。</span><span class="sxs-lookup"><span data-stu-id="91a2c-112">Project to project (P2P references to remove.</span></span> <span data-ttu-id="91a2c-113">您可以指定一或多個專案。</span><span class="sxs-lookup"><span data-stu-id="91a2c-113">You can specify one or multiple projects.</span></span> <span data-ttu-id="91a2c-114">以 Unix/Linux 為基礎的終端機上支援 [Glob 模式 (英文)](https://en.wikipedia.org/wiki/Glob_(programming))。</span><span class="sxs-lookup"><span data-stu-id="91a2c-114">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="91a2c-115">選項</span><span class="sxs-lookup"><span data-stu-id="91a2c-115">Options</span></span>

`-h|--help`

<span data-ttu-id="91a2c-116">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="91a2c-116">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="91a2c-117">只有在以特定[架構](../../standard/frameworks.md)為目標時，才能移除參考。</span><span class="sxs-lookup"><span data-stu-id="91a2c-117">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="91a2c-118">範例</span><span class="sxs-lookup"><span data-stu-id="91a2c-118">Examples</span></span>

<span data-ttu-id="91a2c-119">從指定的專案中移除專案參考：</span><span class="sxs-lookup"><span data-stu-id="91a2c-119">Remove a project reference from the specified project:</span></span>

`dotnet remove app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="91a2c-120">從目前目錄中的專案移除多個專案參考：</span><span class="sxs-lookup"><span data-stu-id="91a2c-120">Remove multiple project references from the project in the current directory:</span></span>

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="91a2c-121">在 Unix/Linux 上使用 Glob 模式移除多個專案參考︰</span><span class="sxs-lookup"><span data-stu-id="91a2c-121">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

`dotnet remove app/app.csproj reference **/*.csproj`
