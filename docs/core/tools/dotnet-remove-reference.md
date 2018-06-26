---
title: dotnet remove reference 命令 - .NET Core CLI
description: dotnet remove reference 命令提供方便的選項，以移除專案對專案參考。
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: b281b255be7f49a99a6b4928c340cd4fb085f085
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696227"
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="63b49-103">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="63b49-103">dotnet remove reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="63b49-104">名稱</span><span class="sxs-lookup"><span data-stu-id="63b49-104">Name</span></span>

<span data-ttu-id="63b49-105">`dotnet remove reference` - 移除專案對專案參考。</span><span class="sxs-lookup"><span data-stu-id="63b49-105">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="63b49-106">概要</span><span class="sxs-lookup"><span data-stu-id="63b49-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="63b49-107">描述</span><span class="sxs-lookup"><span data-stu-id="63b49-107">Description</span></span>

<span data-ttu-id="63b49-108">`dotnet remove reference` 命令提供方便的選項，以從專案中移除專案參考。</span><span class="sxs-lookup"><span data-stu-id="63b49-108">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="63b49-109">引數</span><span class="sxs-lookup"><span data-stu-id="63b49-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="63b49-110">目標專案檔。</span><span class="sxs-lookup"><span data-stu-id="63b49-110">Target project file.</span></span> <span data-ttu-id="63b49-111">如果未指定，命令會在目前的目錄中搜尋一個專案檔。</span><span class="sxs-lookup"><span data-stu-id="63b49-111">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="63b49-112">要移除的專案對專案 (P2P) 參考。</span><span class="sxs-lookup"><span data-stu-id="63b49-112">Project-to-project (P2P) references to remove.</span></span> <span data-ttu-id="63b49-113">您可以指定一或多個專案。</span><span class="sxs-lookup"><span data-stu-id="63b49-113">You can specify one or multiple projects.</span></span> <span data-ttu-id="63b49-114">以 Unix/Linux 為基礎的終端機上支援 [Glob 模式 (英文)](https://en.wikipedia.org/wiki/Glob_(programming))。</span><span class="sxs-lookup"><span data-stu-id="63b49-114">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="63b49-115">選項</span><span class="sxs-lookup"><span data-stu-id="63b49-115">Options</span></span>

`-h|--help`

<span data-ttu-id="63b49-116">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="63b49-116">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="63b49-117">只有在以特定[架構](../../standard/frameworks.md)為目標時，才能移除參考。</span><span class="sxs-lookup"><span data-stu-id="63b49-117">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="63b49-118">範例</span><span class="sxs-lookup"><span data-stu-id="63b49-118">Examples</span></span>

<span data-ttu-id="63b49-119">從指定的專案中移除專案參考：</span><span class="sxs-lookup"><span data-stu-id="63b49-119">Remove a project reference from the specified project:</span></span>

`dotnet remove app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="63b49-120">從目前目錄中的專案移除多個專案參考：</span><span class="sxs-lookup"><span data-stu-id="63b49-120">Remove multiple project references from the project in the current directory:</span></span>

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="63b49-121">在 Unix/Linux 上使用 Glob 模式移除多個專案參考︰</span><span class="sxs-lookup"><span data-stu-id="63b49-121">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

`dotnet remove app/app.csproj reference **/*.csproj`
