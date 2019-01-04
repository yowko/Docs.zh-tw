---
title: dotnet sln 命令
description: dotnet-sln 命令提供方便在方案檔中新增、移除及列出專案的選項。
ms.date: 06/13/2018
ms.openlocfilehash: a88e22c68f639f2a42e59f9a271e431f04e24a2b
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169140"
---
# <a name="dotnet-sln"></a><span data-ttu-id="ec0ba-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="ec0ba-103">dotnet sln</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="ec0ba-104">名稱</span><span class="sxs-lookup"><span data-stu-id="ec0ba-104">Name</span></span>

<span data-ttu-id="ec0ba-105">`dotnet sln` - 修改.NET Core 方案檔。</span><span class="sxs-lookup"><span data-stu-id="ec0ba-105">`dotnet sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ec0ba-106">概要</span><span class="sxs-lookup"><span data-stu-id="ec0ba-106">Synopsis</span></span>

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a><span data-ttu-id="ec0ba-107">說明</span><span class="sxs-lookup"><span data-stu-id="ec0ba-107">Description</span></span>

<span data-ttu-id="ec0ba-108">`dotnet sln` 命令提供方便在方案檔中新增、移除及列出專案的方式。</span><span class="sxs-lookup"><span data-stu-id="ec0ba-108">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

<span data-ttu-id="ec0ba-109">若要使用 `dotnet sln` 命令，方案檔必須已經存在。</span><span class="sxs-lookup"><span data-stu-id="ec0ba-109">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="ec0ba-110">如果您需要建立一個，請使用 [dotnet new](dotnet-new.md) 命令，如下列範例：</span><span class="sxs-lookup"><span data-stu-id="ec0ba-110">If you need to create one, use the [dotnet new](dotnet-new.md) command, like in the following example:</span></span>

```
dotnet new sln
```

## <a name="commands"></a><span data-ttu-id="ec0ba-111">命令</span><span class="sxs-lookup"><span data-stu-id="ec0ba-111">Commands</span></span>

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

<span data-ttu-id="ec0ba-112">將一個專案或多個專案加入至方案檔。</span><span class="sxs-lookup"><span data-stu-id="ec0ba-112">Adds a project or multiple projects to the solution file.</span></span> <span data-ttu-id="ec0ba-113">以 Unix/Linux 為基礎的終端機上支援 [Globbing 模式 (英文)](https://en.wikipedia.org/wiki/Glob_(programming))。</span><span class="sxs-lookup"><span data-stu-id="ec0ba-113">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

<span data-ttu-id="ec0ba-114">從方案檔中移除一個專案或多個專案。</span><span class="sxs-lookup"><span data-stu-id="ec0ba-114">Removes a project or multiple projects from the solution file.</span></span> <span data-ttu-id="ec0ba-115">以 Unix/Linux 為基礎的終端機上支援 [Globbing 模式 (英文)](https://en.wikipedia.org/wiki/Glob_(programming))。</span><span class="sxs-lookup"><span data-stu-id="ec0ba-115">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`list`

<span data-ttu-id="ec0ba-116">列出方案檔中的所有專案。</span><span class="sxs-lookup"><span data-stu-id="ec0ba-116">Lists all projects in a solution file.</span></span>

## <a name="arguments"></a><span data-ttu-id="ec0ba-117">引數</span><span class="sxs-lookup"><span data-stu-id="ec0ba-117">Arguments</span></span>

`SOLUTION_NAME`

<span data-ttu-id="ec0ba-118">要使用的方案檔。</span><span class="sxs-lookup"><span data-stu-id="ec0ba-118">Solution file to use.</span></span> <span data-ttu-id="ec0ba-119">如果未指定，命令會在目前的目錄中搜尋一個專案檔。</span><span class="sxs-lookup"><span data-stu-id="ec0ba-119">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="ec0ba-120">如果目錄中有多個方案檔，請務必指定一個方案檔。</span><span class="sxs-lookup"><span data-stu-id="ec0ba-120">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="ec0ba-121">選項</span><span class="sxs-lookup"><span data-stu-id="ec0ba-121">Options</span></span>

`-h|--help`

<span data-ttu-id="ec0ba-122">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="ec0ba-122">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="ec0ba-123">範例</span><span class="sxs-lookup"><span data-stu-id="ec0ba-123">Examples</span></span>

<span data-ttu-id="ec0ba-124">將 C# 專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="ec0ba-124">Add a C# project to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj`

<span data-ttu-id="ec0ba-125">移除方案中的 C# 專案：</span><span class="sxs-lookup"><span data-stu-id="ec0ba-125">Remove a C# project from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

<span data-ttu-id="ec0ba-126">將多個 C# 專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="ec0ba-126">Add multiple C# projects to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="ec0ba-127">從方案中移除多個 C# 專案：</span><span class="sxs-lookup"><span data-stu-id="ec0ba-127">Remove multiple C# projects from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="ec0ba-128">使用 Glob 模式將多個 C# 專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="ec0ba-128">Add multiple C# projects to a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln add **/*.csproj`

<span data-ttu-id="ec0ba-129">使用 Glob 模式從方案中移除多個 C# 專案：</span><span class="sxs-lookup"><span data-stu-id="ec0ba-129">Remove multiple C# projects from a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln remove **/*.csproj`

> [!NOTE]
> <span data-ttu-id="ec0ba-130">萬用字元不是 CLI 功能，而是命令殼層的功能。</span><span class="sxs-lookup"><span data-stu-id="ec0ba-130">Globbing is not a CLI feature but rather a feature of the command shell.</span></span> <span data-ttu-id="ec0ba-131">若要成功擴充檔案，您必須使用支援萬用字元的殼層。</span><span class="sxs-lookup"><span data-stu-id="ec0ba-131">To successfully expand the files, you must use a shell that supports globbing.</span></span> <span data-ttu-id="ec0ba-132">如需萬用字元的詳細資訊，請參閱[維基百科](https://en.wikipedia.org/wiki/Glob_(programming)) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="ec0ba-132">For more information about globbing, see [Wikipedia](https://en.wikipedia.org/wiki/Glob_(programming)).</span></span>
