---
title: dotnet sln 命令
description: dotnet-sln 命令提供方便在方案檔中新增、移除及列出專案的選項。
ms.date: 02/14/2020
ms.openlocfilehash: 231287477d986f9ec4a5404cc5278e76c297faa4
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463404"
---
# <a name="dotnet-sln"></a><span data-ttu-id="37aa4-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="37aa4-103">dotnet sln</span></span>

<span data-ttu-id="37aa4-104">**本文適用於:✔️** .NET Core 2.x SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="37aa4-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="37aa4-105">名稱</span><span class="sxs-lookup"><span data-stu-id="37aa4-105">Name</span></span>

<span data-ttu-id="37aa4-106">`dotnet sln`- 列出或修改 .NET Core 解決方案檔中的專案。</span><span class="sxs-lookup"><span data-stu-id="37aa4-106">`dotnet sln` - Lists or modifies the projects in a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="37aa4-107">概要</span><span class="sxs-lookup"><span data-stu-id="37aa4-107">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command]

dotnet sln [command] -h|--help
```

## <a name="description"></a><span data-ttu-id="37aa4-108">描述</span><span class="sxs-lookup"><span data-stu-id="37aa4-108">Description</span></span>

<span data-ttu-id="37aa4-109">該`dotnet sln`命令提供了一種在解決方案檔中列出和修改專案的便捷方法。</span><span class="sxs-lookup"><span data-stu-id="37aa4-109">The `dotnet sln` command provides a convenient way to list and modify projects in a solution file.</span></span>

<span data-ttu-id="37aa4-110">若要使用 `dotnet sln` 命令，方案檔必須已經存在。</span><span class="sxs-lookup"><span data-stu-id="37aa4-110">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="37aa4-111">如果需要建立指令,請使用[dotnet 新](dotnet-new.md)指令,如以下範例所示:</span><span class="sxs-lookup"><span data-stu-id="37aa4-111">If you need to create one, use the [dotnet new](dotnet-new.md) command, as in the following example:</span></span>

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a><span data-ttu-id="37aa4-112">引數</span><span class="sxs-lookup"><span data-stu-id="37aa4-112">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="37aa4-113">要使用的解決方案檔。</span><span class="sxs-lookup"><span data-stu-id="37aa4-113">The solution file to use.</span></span> <span data-ttu-id="37aa4-114">如果省略此參數,該命令將搜索當前目錄。</span><span class="sxs-lookup"><span data-stu-id="37aa4-114">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="37aa4-115">如果找不到解決方案檔或多個解決方案檔,則命令將失敗。</span><span class="sxs-lookup"><span data-stu-id="37aa4-115">If it finds no solution file or multiple solution files, the command fails.</span></span>

## <a name="options"></a><span data-ttu-id="37aa4-116">選項。</span><span class="sxs-lookup"><span data-stu-id="37aa4-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="37aa4-117">列印出如何使用命令的說明。</span><span class="sxs-lookup"><span data-stu-id="37aa4-117">Prints out a description of how to use the command.</span></span>

## <a name="commands"></a><span data-ttu-id="37aa4-118">命令</span><span class="sxs-lookup"><span data-stu-id="37aa4-118">Commands</span></span>

### `list`

<span data-ttu-id="37aa4-119">列出方案檔中的所有專案。</span><span class="sxs-lookup"><span data-stu-id="37aa4-119">Lists all projects in a solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="37aa4-120">概要</span><span class="sxs-lookup"><span data-stu-id="37aa4-120">Synopsis</span></span>

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="37aa4-121">引數</span><span class="sxs-lookup"><span data-stu-id="37aa4-121">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="37aa4-122">要使用的解決方案檔。</span><span class="sxs-lookup"><span data-stu-id="37aa4-122">The solution file to use.</span></span> <span data-ttu-id="37aa4-123">如果省略此參數,該命令將搜索當前目錄。</span><span class="sxs-lookup"><span data-stu-id="37aa4-123">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="37aa4-124">如果找不到解決方案檔或多個解決方案檔,則命令將失敗。</span><span class="sxs-lookup"><span data-stu-id="37aa4-124">If it finds no solution file or multiple solution files, the command fails.</span></span>

#### <a name="options"></a><span data-ttu-id="37aa4-125">選項。</span><span class="sxs-lookup"><span data-stu-id="37aa4-125">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="37aa4-126">列印出如何使用命令的說明。</span><span class="sxs-lookup"><span data-stu-id="37aa4-126">Prints out a description of how to use the command.</span></span>
  
### `add`

<span data-ttu-id="37aa4-127">將一個或多個專案添加到解決方案檔中。</span><span class="sxs-lookup"><span data-stu-id="37aa4-127">Adds one or more projects to the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="37aa4-128">概要</span><span class="sxs-lookup"><span data-stu-id="37aa4-128">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder <PATH>] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="37aa4-129">引數</span><span class="sxs-lookup"><span data-stu-id="37aa4-129">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="37aa4-130">要使用的解決方案檔。</span><span class="sxs-lookup"><span data-stu-id="37aa4-130">The solution file to use.</span></span> <span data-ttu-id="37aa4-131">如果未指定,該命令將搜索當前目錄,如果有多個解決方案檔,則該命令將失敗。</span><span class="sxs-lookup"><span data-stu-id="37aa4-131">If it is unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="37aa4-132">要添加到解決方案的專案或專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="37aa4-132">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="37aa4-133">命令正確處理`dotnet sln`Unix/Linux 外殼[globing 模式](https://en.wikipedia.org/wiki/Glob_(programming))擴展。</span><span class="sxs-lookup"><span data-stu-id="37aa4-133">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="37aa4-134">選項。</span><span class="sxs-lookup"><span data-stu-id="37aa4-134">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="37aa4-135">列印出如何使用命令的說明。</span><span class="sxs-lookup"><span data-stu-id="37aa4-135">Prints out a description of how to use the command.</span></span>

- **`--in-root`**

  <span data-ttu-id="37aa4-136">將專案放在解決方案的根目錄中,而不是創建解決方案資料夾。</span><span class="sxs-lookup"><span data-stu-id="37aa4-136">Places the projects in the root of the solution, rather than creating a solution folder.</span></span> <span data-ttu-id="37aa4-137">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="37aa4-137">Available since .NET Core 3.0 SDK.</span></span>

- **`-s|--solution-folder <PATH>`**

  <span data-ttu-id="37aa4-138">要將專案添加到的目標解決方案資料夾路徑。</span><span class="sxs-lookup"><span data-stu-id="37aa4-138">The destination solution folder path to add the projects to.</span></span> <span data-ttu-id="37aa4-139">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="37aa4-139">Available since .NET Core 3.0 SDK.</span></span>

### `remove`

<span data-ttu-id="37aa4-140">從方案檔中移除一個專案或多個專案。</span><span class="sxs-lookup"><span data-stu-id="37aa4-140">Removes a project or multiple projects from the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="37aa4-141">概要</span><span class="sxs-lookup"><span data-stu-id="37aa4-141">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="37aa4-142">引數</span><span class="sxs-lookup"><span data-stu-id="37aa4-142">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="37aa4-143">要使用的解決方案檔。</span><span class="sxs-lookup"><span data-stu-id="37aa4-143">The solution file to use.</span></span> <span data-ttu-id="37aa4-144">如果未指定,該命令將搜索當前目錄,如果有多個解決方案檔,則該目錄將失敗。</span><span class="sxs-lookup"><span data-stu-id="37aa4-144">If is left unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="37aa4-145">要添加到解決方案的專案或專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="37aa4-145">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="37aa4-146">命令正確處理`dotnet sln`Unix/Linux 外殼[globing 模式](https://en.wikipedia.org/wiki/Glob_(programming))擴展。</span><span class="sxs-lookup"><span data-stu-id="37aa4-146">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="37aa4-147">選項。</span><span class="sxs-lookup"><span data-stu-id="37aa4-147">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="37aa4-148">列印出如何使用命令的說明。</span><span class="sxs-lookup"><span data-stu-id="37aa4-148">Prints out a description of how to use the command.</span></span>

## <a name="examples"></a><span data-ttu-id="37aa4-149">範例</span><span class="sxs-lookup"><span data-stu-id="37aa4-149">Examples</span></span>

- <span data-ttu-id="37aa4-150">在解決方案中列出專案:</span><span class="sxs-lookup"><span data-stu-id="37aa4-150">List the projects in a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln list
  ```

- <span data-ttu-id="37aa4-151">將 C# 專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="37aa4-151">Add a C# project to a solution:</span></span>

  ```dotnetcli
  dotnet sln add todo-app/todo-app.csproj
  ```

- <span data-ttu-id="37aa4-152">移除方案中的 C# 專案：</span><span class="sxs-lookup"><span data-stu-id="37aa4-152">Remove a C# project from a solution:</span></span>

  ```dotnetcli
  dotnet sln remove todo-app/todo-app.csproj
  ```

- <span data-ttu-id="37aa4-153">新增 C# 專案到解決方案的根目錄:</span><span class="sxs-lookup"><span data-stu-id="37aa4-153">Add multiple C# projects to the root of a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj --in-root
  ```

- <span data-ttu-id="37aa4-154">將多個 C# 專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="37aa4-154">Add multiple C# projects to a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="37aa4-155">從方案中移除多個 C# 專案：</span><span class="sxs-lookup"><span data-stu-id="37aa4-155">Remove multiple C# projects from a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="37aa4-156">使用 globing 模式(僅限 Unix/Linux)將多個 C# 專案新增到解決方案中:</span><span class="sxs-lookup"><span data-stu-id="37aa4-156">Add multiple C# projects to a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- <span data-ttu-id="37aa4-157">使用 globing 模式(僅限 Windows PowerShell)將多個 C# 專案新增到解決方案中:</span><span class="sxs-lookup"><span data-stu-id="37aa4-157">Add multiple C# projects to a solution using a globbing pattern (Windows PowerShell only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add (ls **/*.csproj)
  ```

- <span data-ttu-id="37aa4-158">使用 globing 模式從解決方案中移除多個 C# 專案(僅限 Unix/Linux):</span><span class="sxs-lookup"><span data-stu-id="37aa4-158">Remove multiple C# projects from a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```

- <span data-ttu-id="37aa4-159">使用 globing 模式從解決方案中移除多個 C# 專案(只有限制 Windows PowerShell):</span><span class="sxs-lookup"><span data-stu-id="37aa4-159">Remove multiple C# projects from a solution using a globbing pattern (Windows PowerShell only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove (ls **/*.csproj)
  ```
