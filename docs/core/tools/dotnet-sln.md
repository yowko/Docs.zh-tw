---
title: "dotnet sln 命令 - .NET Core CLI"
description: "dotnet-sln 命令提供方便在方案檔中新增、移除及列出專案的選項。"
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: deb66ff52074630616c7be47f1a9751246db501d
ms.sourcegitcommit: 70dcc89737127e4d5f20500242409b687e51b07e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2018
---
# <a name="dotnet-sln"></a><span data-ttu-id="7f50b-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="7f50b-103">dotnet sln</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="7f50b-104">名稱</span><span class="sxs-lookup"><span data-stu-id="7f50b-104">Name</span></span>

<span data-ttu-id="7f50b-105">`dotnet sln` - 修改.NET Core 方案檔。</span><span class="sxs-lookup"><span data-stu-id="7f50b-105">`dotnet sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7f50b-106">概要</span><span class="sxs-lookup"><span data-stu-id="7f50b-106">Synopsis</span></span>

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a><span data-ttu-id="7f50b-107">描述</span><span class="sxs-lookup"><span data-stu-id="7f50b-107">Description</span></span>

<span data-ttu-id="7f50b-108">`dotnet sln` 命令提供方便在方案檔中新增、移除及列出專案的方式。</span><span class="sxs-lookup"><span data-stu-id="7f50b-108">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

## <a name="commands"></a><span data-ttu-id="7f50b-109">命令</span><span class="sxs-lookup"><span data-stu-id="7f50b-109">Commands</span></span>

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

<span data-ttu-id="7f50b-110">將一個專案或多個專案加入至方案檔。</span><span class="sxs-lookup"><span data-stu-id="7f50b-110">Adds a project or multiple projects to the solution file.</span></span> <span data-ttu-id="7f50b-111">以 Unix/Linux 為基礎的終端機上支援 [Globbing 模式 (英文)](https://en.wikipedia.org/wiki/Glob_(programming))。</span><span class="sxs-lookup"><span data-stu-id="7f50b-111">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

<span data-ttu-id="7f50b-112">從方案檔中移除一個專案或多個專案。</span><span class="sxs-lookup"><span data-stu-id="7f50b-112">Removes a project or multiple projects from the solution file.</span></span> <span data-ttu-id="7f50b-113">以 Unix/Linux 為基礎的終端機上支援 [Globbing 模式 (英文)](https://en.wikipedia.org/wiki/Glob_(programming))。</span><span class="sxs-lookup"><span data-stu-id="7f50b-113">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`list`

<span data-ttu-id="7f50b-114">列出方案檔中的所有專案。</span><span class="sxs-lookup"><span data-stu-id="7f50b-114">Lists all projects in a solution file.</span></span>

## <a name="arguments"></a><span data-ttu-id="7f50b-115">引數</span><span class="sxs-lookup"><span data-stu-id="7f50b-115">Arguments</span></span>

`SOLUTION_NAME`

<span data-ttu-id="7f50b-116">要使用的方案檔。</span><span class="sxs-lookup"><span data-stu-id="7f50b-116">Solution file to use.</span></span> <span data-ttu-id="7f50b-117">如果未指定，命令會在目前的目錄中搜尋一個專案檔。</span><span class="sxs-lookup"><span data-stu-id="7f50b-117">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="7f50b-118">如果目錄中有多個方案檔，請務必指定一個方案檔。</span><span class="sxs-lookup"><span data-stu-id="7f50b-118">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="7f50b-119">選項</span><span class="sxs-lookup"><span data-stu-id="7f50b-119">Options</span></span>

`-h|--help`

<span data-ttu-id="7f50b-120">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="7f50b-120">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="7f50b-121">範例</span><span class="sxs-lookup"><span data-stu-id="7f50b-121">Examples</span></span>

<span data-ttu-id="7f50b-122">將 C# 專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="7f50b-122">Add a C# project to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj`

<span data-ttu-id="7f50b-123">移除方案中的 C# 專案：</span><span class="sxs-lookup"><span data-stu-id="7f50b-123">Remove a C# project from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

<span data-ttu-id="7f50b-124">將多個 C# 專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="7f50b-124">Add multiple C# projects to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="7f50b-125">從方案中移除多個 C# 專案：</span><span class="sxs-lookup"><span data-stu-id="7f50b-125">Remove multiple C# projects from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="7f50b-126">使用 Glob 模式將多個 C# 專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="7f50b-126">Add multiple C# projects to a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln add **/*.csproj`

<span data-ttu-id="7f50b-127">使用 Glob 模式從方案中移除多個 C# 專案：</span><span class="sxs-lookup"><span data-stu-id="7f50b-127">Remove multiple C# projects from a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln remove **/*.csproj`
