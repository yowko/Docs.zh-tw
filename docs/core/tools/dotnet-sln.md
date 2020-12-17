---
title: dotnet sln 命令
description: dotnet-sln 命令提供方便在方案檔中新增、移除及列出專案的選項。
ms.date: 12/07/2020
ms.openlocfilehash: af502efe842e9c9610137738d86c05e00a3b37df
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633646"
---
# <a name="dotnet-sln"></a><span data-ttu-id="d828d-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="d828d-103">dotnet sln</span></span>

<span data-ttu-id="d828d-104">本文 **適用于：** ✔️ .net CORE 2.x SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="d828d-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="d828d-105">Name</span><span class="sxs-lookup"><span data-stu-id="d828d-105">Name</span></span>

<span data-ttu-id="d828d-106">`dotnet sln` -列出或修改 .NET 方案檔中的專案。</span><span class="sxs-lookup"><span data-stu-id="d828d-106">`dotnet sln` - Lists or modifies the projects in a .NET solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d828d-107">概要</span><span class="sxs-lookup"><span data-stu-id="d828d-107">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command]

dotnet sln [command] -h|--help
```

## <a name="description"></a><span data-ttu-id="d828d-108">Description</span><span class="sxs-lookup"><span data-stu-id="d828d-108">Description</span></span>

<span data-ttu-id="d828d-109">此 `dotnet sln` 命令提供一個便利的方式來列出和修改方案檔中的專案。</span><span class="sxs-lookup"><span data-stu-id="d828d-109">The `dotnet sln` command provides a convenient way to list and modify projects in a solution file.</span></span>

<span data-ttu-id="d828d-110">若要使用 `dotnet sln` 命令，方案檔必須已經存在。</span><span class="sxs-lookup"><span data-stu-id="d828d-110">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="d828d-111">如果您需要建立一個，請使用 [dotnet new](dotnet-new.md) 命令，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="d828d-111">If you need to create one, use the [dotnet new](dotnet-new.md) command, as in the following example:</span></span>

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a><span data-ttu-id="d828d-112">引數</span><span class="sxs-lookup"><span data-stu-id="d828d-112">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="d828d-113">要使用的方案檔。</span><span class="sxs-lookup"><span data-stu-id="d828d-113">The solution file to use.</span></span> <span data-ttu-id="d828d-114">如果省略這個引數，則命令會在目前的目錄中搜尋一個。</span><span class="sxs-lookup"><span data-stu-id="d828d-114">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="d828d-115">如果找不到解決方案檔或多個方案檔，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="d828d-115">If it finds no solution file or multiple solution files, the command fails.</span></span>

## <a name="options"></a><span data-ttu-id="d828d-116">選項</span><span class="sxs-lookup"><span data-stu-id="d828d-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="d828d-117">印出如何使用命令的描述。</span><span class="sxs-lookup"><span data-stu-id="d828d-117">Prints out a description of how to use the command.</span></span>

## <a name="commands"></a><span data-ttu-id="d828d-118">命令</span><span class="sxs-lookup"><span data-stu-id="d828d-118">Commands</span></span>

### `list`

<span data-ttu-id="d828d-119">列出方案檔中的所有專案。</span><span class="sxs-lookup"><span data-stu-id="d828d-119">Lists all projects in a solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="d828d-120">概要</span><span class="sxs-lookup"><span data-stu-id="d828d-120">Synopsis</span></span>

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="d828d-121">引數</span><span class="sxs-lookup"><span data-stu-id="d828d-121">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="d828d-122">要使用的方案檔。</span><span class="sxs-lookup"><span data-stu-id="d828d-122">The solution file to use.</span></span> <span data-ttu-id="d828d-123">如果省略這個引數，則命令會在目前的目錄中搜尋一個。</span><span class="sxs-lookup"><span data-stu-id="d828d-123">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="d828d-124">如果找不到解決方案檔或多個方案檔，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="d828d-124">If it finds no solution file or multiple solution files, the command fails.</span></span>

#### <a name="options"></a><span data-ttu-id="d828d-125">選項</span><span class="sxs-lookup"><span data-stu-id="d828d-125">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="d828d-126">印出如何使用命令的描述。</span><span class="sxs-lookup"><span data-stu-id="d828d-126">Prints out a description of how to use the command.</span></span>
  
### `add`

<span data-ttu-id="d828d-127">將一或多個專案加入至方案檔。</span><span class="sxs-lookup"><span data-stu-id="d828d-127">Adds one or more projects to the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="d828d-128">概要</span><span class="sxs-lookup"><span data-stu-id="d828d-128">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder <PATH>] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="d828d-129">引數</span><span class="sxs-lookup"><span data-stu-id="d828d-129">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="d828d-130">要使用的方案檔。</span><span class="sxs-lookup"><span data-stu-id="d828d-130">The solution file to use.</span></span> <span data-ttu-id="d828d-131">如果未指定，命令會在目前的目錄中搜尋一個目錄，如果有多個方案檔，則會失敗。</span><span class="sxs-lookup"><span data-stu-id="d828d-131">If it is unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="d828d-132">要加入至方案之專案或專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="d828d-132">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="d828d-133">Unix/Linux shell [萬用字元模式](https://en.wikipedia.org/wiki/Glob_(programming)) 擴充會由命令正確處理 `dotnet sln` 。</span><span class="sxs-lookup"><span data-stu-id="d828d-133">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="d828d-134">選項</span><span class="sxs-lookup"><span data-stu-id="d828d-134">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="d828d-135">印出如何使用命令的描述。</span><span class="sxs-lookup"><span data-stu-id="d828d-135">Prints out a description of how to use the command.</span></span>

- **`--in-root`**

  <span data-ttu-id="d828d-136">將專案放在解決方案的根目錄，而不是建立方案資料夾。</span><span class="sxs-lookup"><span data-stu-id="d828d-136">Places the projects in the root of the solution, rather than creating a solution folder.</span></span> <span data-ttu-id="d828d-137">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="d828d-137">Available since .NET Core 3.0 SDK.</span></span>

- **`-s|--solution-folder <PATH>`**

  <span data-ttu-id="d828d-138">要加入專案的目的地 [方案資料夾](/visualstudio/ide/solutions-and-projects-in-visual-studio#solution-folder) 路徑。</span><span class="sxs-lookup"><span data-stu-id="d828d-138">The destination [solution folder](/visualstudio/ide/solutions-and-projects-in-visual-studio#solution-folder) path to add the projects to.</span></span> <span data-ttu-id="d828d-139">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="d828d-139">Available since .NET Core 3.0 SDK.</span></span>

### `remove`

<span data-ttu-id="d828d-140">從方案檔中移除一個專案或多個專案。</span><span class="sxs-lookup"><span data-stu-id="d828d-140">Removes a project or multiple projects from the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="d828d-141">概要</span><span class="sxs-lookup"><span data-stu-id="d828d-141">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="d828d-142">引數</span><span class="sxs-lookup"><span data-stu-id="d828d-142">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="d828d-143">要使用的方案檔。</span><span class="sxs-lookup"><span data-stu-id="d828d-143">The solution file to use.</span></span> <span data-ttu-id="d828d-144">如果未指定，則命令會在目前的目錄中搜尋一個目錄，如果有多個方案檔，則會失敗。</span><span class="sxs-lookup"><span data-stu-id="d828d-144">If is left unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="d828d-145">要加入至方案之專案或專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="d828d-145">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="d828d-146">Unix/Linux shell [萬用字元模式](https://en.wikipedia.org/wiki/Glob_(programming)) 擴充會由命令正確處理 `dotnet sln` 。</span><span class="sxs-lookup"><span data-stu-id="d828d-146">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="d828d-147">選項</span><span class="sxs-lookup"><span data-stu-id="d828d-147">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="d828d-148">印出如何使用命令的描述。</span><span class="sxs-lookup"><span data-stu-id="d828d-148">Prints out a description of how to use the command.</span></span>

## <a name="examples"></a><span data-ttu-id="d828d-149">範例</span><span class="sxs-lookup"><span data-stu-id="d828d-149">Examples</span></span>

- <span data-ttu-id="d828d-150">列出方案中的專案：</span><span class="sxs-lookup"><span data-stu-id="d828d-150">List the projects in a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln list
  ```

- <span data-ttu-id="d828d-151">將 C# 專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="d828d-151">Add a C# project to a solution:</span></span>

  ```dotnetcli
  dotnet sln add todo-app/todo-app.csproj
  ```

- <span data-ttu-id="d828d-152">移除方案中的 C# 專案：</span><span class="sxs-lookup"><span data-stu-id="d828d-152">Remove a C# project from a solution:</span></span>

  ```dotnetcli
  dotnet sln remove todo-app/todo-app.csproj
  ```

- <span data-ttu-id="d828d-153">將多個 c # 專案新增至方案的根目錄：</span><span class="sxs-lookup"><span data-stu-id="d828d-153">Add multiple C# projects to the root of a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj --in-root
  ```

- <span data-ttu-id="d828d-154">將多個 C# 專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="d828d-154">Add multiple C# projects to a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="d828d-155">從方案中移除多個 C# 專案：</span><span class="sxs-lookup"><span data-stu-id="d828d-155">Remove multiple C# projects from a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="d828d-156">使用萬用字元模式將多個 c # 專案新增至方案 (僅限 Unix/Linux) ：</span><span class="sxs-lookup"><span data-stu-id="d828d-156">Add multiple C# projects to a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- <span data-ttu-id="d828d-157">使用萬用字元模式將多個 c # 專案新增至方案 (只 Windows PowerShell) ：</span><span class="sxs-lookup"><span data-stu-id="d828d-157">Add multiple C# projects to a solution using a globbing pattern (Windows PowerShell only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add (ls -r **/*.csproj)
  ```

- <span data-ttu-id="d828d-158">使用萬用字元模式從方案中移除多個 c # 專案，只 (Unix/Linux) ：</span><span class="sxs-lookup"><span data-stu-id="d828d-158">Remove multiple C# projects from a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```

- <span data-ttu-id="d828d-159">使用萬用字元模式從方案中移除多個 c # 專案 (只 Windows PowerShell) ：</span><span class="sxs-lookup"><span data-stu-id="d828d-159">Remove multiple C# projects from a solution using a globbing pattern (Windows PowerShell only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove (ls -r **/*.csproj)
  ```

- <span data-ttu-id="d828d-160">建立解決方案、主控台應用程式和兩個類別庫。</span><span class="sxs-lookup"><span data-stu-id="d828d-160">Create a solution, a console app, and two class libraries.</span></span> <span data-ttu-id="d828d-161">將專案加入至方案，並使用的 `--solution-folder` 選項，將 `dotnet sln` 類別庫組織成方案資料夾。</span><span class="sxs-lookup"><span data-stu-id="d828d-161">Add the projects to the solution, and use the `--solution-folder` option of `dotnet sln` to organize the class libraries into a solution folder.</span></span>

  ```dotnetcli
  dotnet new sln -n mysolution
  dotnet new console -o myapp
  dotnet new classlib -o mylib1
  dotnet new classlib -o mylib2
  dotnet sln mysolution.sln add myapp\myapp.csproj
  dotnet sln mysolution.sln add mylib1\mylib1.csproj --solution-folder mylibs
  dotnet sln mysolution.sln add mylib2\mylib2.csproj --solution-folder mylibs
  ```

  <span data-ttu-id="d828d-162">下列螢幕擷取畫面顯示 Visual Studio 2019 **方案總管** 中的結果：</span><span class="sxs-lookup"><span data-stu-id="d828d-162">The following screenshot shows the result in Visual Studio 2019 **Solution Explorer**:</span></span>

  :::image type="content" source="media/dotnet-sln/dotnet-sln-solution-folder.png" alt-text="方案總管顯示分組至方案資料夾的類別庫專案。":::
