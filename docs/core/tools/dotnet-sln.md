---
title: dotnet sln 命令
description: dotnet-sln 命令提供方便在方案檔中新增、移除及列出專案的選項。
ms.date: 10/29/2019
ms.openlocfilehash: e344deaae0867202a79a3c38df48a2be8d4d7d13
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733079"
---
# <a name="dotnet-sln"></a><span data-ttu-id="9f00e-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="9f00e-103">dotnet sln</span></span>

<span data-ttu-id="9f00e-104">**本文適用于：** ✔️ .net CORE 1.x SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="9f00e-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="9f00e-105">Name</span><span class="sxs-lookup"><span data-stu-id="9f00e-105">Name</span></span>

<span data-ttu-id="9f00e-106">`dotnet sln` - 修改.NET Core 方案檔。</span><span class="sxs-lookup"><span data-stu-id="9f00e-106">`dotnet sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9f00e-107">概要</span><span class="sxs-lookup"><span data-stu-id="9f00e-107">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command] [-h|--help]
```

## <a name="description"></a><span data-ttu-id="9f00e-108">描述</span><span class="sxs-lookup"><span data-stu-id="9f00e-108">Description</span></span>

<span data-ttu-id="9f00e-109">`dotnet sln` 命令提供方便在方案檔中新增、移除及列出專案的方式。</span><span class="sxs-lookup"><span data-stu-id="9f00e-109">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

<span data-ttu-id="9f00e-110">若要使用 `dotnet sln` 命令，方案檔必須已經存在。</span><span class="sxs-lookup"><span data-stu-id="9f00e-110">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="9f00e-111">如果您需要建立一個，請使用 [dotnet new](dotnet-new.md) 命令，如下列範例：</span><span class="sxs-lookup"><span data-stu-id="9f00e-111">If you need to create one, use the [dotnet new](dotnet-new.md) command, like in the following example:</span></span>

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a><span data-ttu-id="9f00e-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="9f00e-112">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="9f00e-113">要使用的方案檔。</span><span class="sxs-lookup"><span data-stu-id="9f00e-113">The solution file to use.</span></span> <span data-ttu-id="9f00e-114">如果未指定，命令會在目前的目錄中搜尋一個專案檔。</span><span class="sxs-lookup"><span data-stu-id="9f00e-114">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="9f00e-115">如果目錄中有多個方案檔，請務必指定一個方案檔。</span><span class="sxs-lookup"><span data-stu-id="9f00e-115">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="9f00e-116">選項</span><span class="sxs-lookup"><span data-stu-id="9f00e-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="9f00e-117">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="9f00e-117">Prints out a short help for the command.</span></span>

## <a name="commands"></a><span data-ttu-id="9f00e-118">命令</span><span class="sxs-lookup"><span data-stu-id="9f00e-118">Commands</span></span>

### `add`

<span data-ttu-id="9f00e-119">將一個專案或多個專案加入至方案檔。</span><span class="sxs-lookup"><span data-stu-id="9f00e-119">Adds a project or multiple projects to the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="9f00e-120">概要</span><span class="sxs-lookup"><span data-stu-id="9f00e-120">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder] <PROJECT_PATH>
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="9f00e-121">Arguments</span><span class="sxs-lookup"><span data-stu-id="9f00e-121">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="9f00e-122">要使用的方案檔。</span><span class="sxs-lookup"><span data-stu-id="9f00e-122">The solution file to use.</span></span> <span data-ttu-id="9f00e-123">如果未指定，命令會在目前的目錄中搜尋一個專案檔。</span><span class="sxs-lookup"><span data-stu-id="9f00e-123">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="9f00e-124">如果目錄中有多個方案檔，請務必指定一個方案檔。</span><span class="sxs-lookup"><span data-stu-id="9f00e-124">If there are multiple solution files in the directory, one must be specified.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="9f00e-125">要加入至方案之專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="9f00e-125">The path to the project to add to the solution.</span></span> <span data-ttu-id="9f00e-126">加入多個專案，方法是在另一個後面加上空格分隔。</span><span class="sxs-lookup"><span data-stu-id="9f00e-126">Add multiple projects by adding one after the other separated by spaces.</span></span> <span data-ttu-id="9f00e-127">Unix/Linux shell[萬用字元模式](https://en.wikipedia.org/wiki/Glob_(programming))擴充會由 `dotnet sln` 命令正確處理。</span><span class="sxs-lookup"><span data-stu-id="9f00e-127">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="9f00e-128">選項</span><span class="sxs-lookup"><span data-stu-id="9f00e-128">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="9f00e-129">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="9f00e-129">Prints out a short help for the command.</span></span>

- **`--in-root`**

  <span data-ttu-id="9f00e-130">將專案放在方案的根目錄中，而不是建立方案資料夾。</span><span class="sxs-lookup"><span data-stu-id="9f00e-130">Places the projects in the root of the solution, rather than creating a solution folder.</span></span> <span data-ttu-id="9f00e-131">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="9f00e-131">Available since .NET Core 3.0 SDK.</span></span>

- **`-s|--solution-folder`**

  <span data-ttu-id="9f00e-132">要加入專案的目的地解決方案資料夾路徑。</span><span class="sxs-lookup"><span data-stu-id="9f00e-132">The destination solution folder path to add the projects to.</span></span> <span data-ttu-id="9f00e-133">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="9f00e-133">Available since .NET Core 3.0 SDK.</span></span>

### `remove`

<span data-ttu-id="9f00e-134">從方案檔中移除一個專案或多個專案。</span><span class="sxs-lookup"><span data-stu-id="9f00e-134">Removes a project or multiple projects from the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="9f00e-135">概要</span><span class="sxs-lookup"><span data-stu-id="9f00e-135">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH>
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="9f00e-136">Arguments</span><span class="sxs-lookup"><span data-stu-id="9f00e-136">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="9f00e-137">要使用的方案檔。</span><span class="sxs-lookup"><span data-stu-id="9f00e-137">The solution file to use.</span></span> <span data-ttu-id="9f00e-138">如果未指定，命令會在目前的目錄中搜尋一個專案檔。</span><span class="sxs-lookup"><span data-stu-id="9f00e-138">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="9f00e-139">如果目錄中有多個方案檔，請務必指定一個方案檔。</span><span class="sxs-lookup"><span data-stu-id="9f00e-139">If there are multiple solution files in the directory, one must be specified.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="9f00e-140">要從方案中移除之專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="9f00e-140">The path to the project to remove from the solution.</span></span> <span data-ttu-id="9f00e-141">藉由在另一個專案後面加上空格，以移除多個專案。</span><span class="sxs-lookup"><span data-stu-id="9f00e-141">Remove multiple projects by adding one after the other separated by spaces.</span></span> <span data-ttu-id="9f00e-142">Unix/Linux shell[萬用字元模式](https://en.wikipedia.org/wiki/Glob_(programming))擴充會由 `dotnet sln` 命令正確處理。</span><span class="sxs-lookup"><span data-stu-id="9f00e-142">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="9f00e-143">選項</span><span class="sxs-lookup"><span data-stu-id="9f00e-143">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="9f00e-144">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="9f00e-144">Prints out a short help for the command.</span></span>

### `list`

<span data-ttu-id="9f00e-145">列出方案檔中的所有專案。</span><span class="sxs-lookup"><span data-stu-id="9f00e-145">Lists all projects in a solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="9f00e-146">概要</span><span class="sxs-lookup"><span data-stu-id="9f00e-146">Synopsis</span></span>

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="9f00e-147">Arguments</span><span class="sxs-lookup"><span data-stu-id="9f00e-147">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="9f00e-148">要使用的方案檔。</span><span class="sxs-lookup"><span data-stu-id="9f00e-148">The solution file to use.</span></span> <span data-ttu-id="9f00e-149">如果未指定，命令會在目前的目錄中搜尋一個專案檔。</span><span class="sxs-lookup"><span data-stu-id="9f00e-149">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="9f00e-150">如果目錄中有多個方案檔，請務必指定一個方案檔。</span><span class="sxs-lookup"><span data-stu-id="9f00e-150">If there are multiple solution files in the directory, one must be specified.</span></span>

#### <a name="options"></a><span data-ttu-id="9f00e-151">選項</span><span class="sxs-lookup"><span data-stu-id="9f00e-151">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="9f00e-152">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="9f00e-152">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="9f00e-153">範例</span><span class="sxs-lookup"><span data-stu-id="9f00e-153">Examples</span></span>

- <span data-ttu-id="9f00e-154">將 C# 專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="9f00e-154">Add a C# project to a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj
  ```

- <span data-ttu-id="9f00e-155">移除方案中的 C# 專案：</span><span class="sxs-lookup"><span data-stu-id="9f00e-155">Remove a C# project from a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj
  ```

- <span data-ttu-id="9f00e-156">將多個 C# 專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="9f00e-156">Add multiple C# projects to a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="9f00e-157">從方案中移除多個 C# 專案：</span><span class="sxs-lookup"><span data-stu-id="9f00e-157">Remove multiple C# projects from a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="9f00e-158">使用萬用字元C#模式將多個專案新增至解決方案（僅限 Unix/Linux）：</span><span class="sxs-lookup"><span data-stu-id="9f00e-158">Add multiple C# projects to a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- <span data-ttu-id="9f00e-159">使用萬用字元C#模式從方案中移除多個專案（僅限 Unix/Linux）：</span><span class="sxs-lookup"><span data-stu-id="9f00e-159">Remove multiple C# projects from a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```
