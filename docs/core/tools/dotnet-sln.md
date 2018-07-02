---
title: dotnet sln 命令 - .NET Core CLI
description: dotnet-sln 命令提供方便在方案檔中新增、移除及列出專案的選項。
author: mairaw
ms.author: mairaw
ms.date: 06/13/2018
ms.openlocfilehash: 65ae402ef5519863886c8cf833598f5314b4bdad
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207772"
---
# <a name="dotnet-sln"></a><span data-ttu-id="ff9a7-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="ff9a7-103">dotnet sln</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="ff9a7-104">名稱</span><span class="sxs-lookup"><span data-stu-id="ff9a7-104">Name</span></span>

<span data-ttu-id="ff9a7-105">`dotnet sln` - 修改.NET Core 方案檔。</span><span class="sxs-lookup"><span data-stu-id="ff9a7-105">`dotnet sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ff9a7-106">概要</span><span class="sxs-lookup"><span data-stu-id="ff9a7-106">Synopsis</span></span>

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a><span data-ttu-id="ff9a7-107">描述</span><span class="sxs-lookup"><span data-stu-id="ff9a7-107">Description</span></span>

<span data-ttu-id="ff9a7-108">`dotnet sln` 命令提供方便在方案檔中新增、移除及列出專案的方式。</span><span class="sxs-lookup"><span data-stu-id="ff9a7-108">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

<span data-ttu-id="ff9a7-109">若要使用 `dotnet sln` 命令，方案檔必須已經存在。</span><span class="sxs-lookup"><span data-stu-id="ff9a7-109">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="ff9a7-110">如果您需要建立一個，請使用 [dotnet new](dotnet-new.md) 命令，如下列範例：</span><span class="sxs-lookup"><span data-stu-id="ff9a7-110">If you need to create one, use the [dotnet new](dotnet-new.md) command, like in the following example:</span></span>

```
dotnet new sln
```

## <a name="commands"></a><span data-ttu-id="ff9a7-111">命令</span><span class="sxs-lookup"><span data-stu-id="ff9a7-111">Commands</span></span>

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

<span data-ttu-id="ff9a7-112">將一個專案或多個專案加入至方案檔。</span><span class="sxs-lookup"><span data-stu-id="ff9a7-112">Adds a project or multiple projects to the solution file.</span></span> <span data-ttu-id="ff9a7-113">以 Unix/Linux 為基礎的終端機上支援 [Globbing 模式 (英文)](https://en.wikipedia.org/wiki/Glob_(programming))。</span><span class="sxs-lookup"><span data-stu-id="ff9a7-113">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

<span data-ttu-id="ff9a7-114">從方案檔中移除一個專案或多個專案。</span><span class="sxs-lookup"><span data-stu-id="ff9a7-114">Removes a project or multiple projects from the solution file.</span></span> <span data-ttu-id="ff9a7-115">以 Unix/Linux 為基礎的終端機上支援 [Globbing 模式 (英文)](https://en.wikipedia.org/wiki/Glob_(programming))。</span><span class="sxs-lookup"><span data-stu-id="ff9a7-115">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`list`

<span data-ttu-id="ff9a7-116">列出方案檔中的所有專案。</span><span class="sxs-lookup"><span data-stu-id="ff9a7-116">Lists all projects in a solution file.</span></span>

## <a name="arguments"></a><span data-ttu-id="ff9a7-117">引數</span><span class="sxs-lookup"><span data-stu-id="ff9a7-117">Arguments</span></span>

`SOLUTION_NAME`

<span data-ttu-id="ff9a7-118">要使用的方案檔。</span><span class="sxs-lookup"><span data-stu-id="ff9a7-118">Solution file to use.</span></span> <span data-ttu-id="ff9a7-119">如果未指定，命令會在目前的目錄中搜尋一個專案檔。</span><span class="sxs-lookup"><span data-stu-id="ff9a7-119">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="ff9a7-120">如果目錄中有多個方案檔，請務必指定一個方案檔。</span><span class="sxs-lookup"><span data-stu-id="ff9a7-120">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="ff9a7-121">選項</span><span class="sxs-lookup"><span data-stu-id="ff9a7-121">Options</span></span>

`-h|--help`

<span data-ttu-id="ff9a7-122">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="ff9a7-122">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="ff9a7-123">範例</span><span class="sxs-lookup"><span data-stu-id="ff9a7-123">Examples</span></span>

<span data-ttu-id="ff9a7-124">將 C# 專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="ff9a7-124">Add a C# project to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj`

<span data-ttu-id="ff9a7-125">移除方案中的 C# 專案：</span><span class="sxs-lookup"><span data-stu-id="ff9a7-125">Remove a C# project from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

<span data-ttu-id="ff9a7-126">將多個 C# 專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="ff9a7-126">Add multiple C# projects to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="ff9a7-127">從方案中移除多個 C# 專案：</span><span class="sxs-lookup"><span data-stu-id="ff9a7-127">Remove multiple C# projects from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="ff9a7-128">使用 Glob 模式將多個 C# 專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="ff9a7-128">Add multiple C# projects to a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln add **/*.csproj`

<span data-ttu-id="ff9a7-129">使用 Glob 模式從方案中移除多個 C# 專案：</span><span class="sxs-lookup"><span data-stu-id="ff9a7-129">Remove multiple C# projects from a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln remove **/*.csproj`
