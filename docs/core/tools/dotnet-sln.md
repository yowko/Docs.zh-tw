---
title: dotnet sln 命令
description: dotnet-sln 命令提供方便在方案檔中新增、移除及列出專案的選項。
ms.date: 02/14/2020
ms.openlocfilehash: efe52f64a29c8825070bae9ee96b430b32176ffa
ms.sourcegitcommit: 2560a355c76b0a04cba0d34da870df9ad94ceca3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2020
ms.locfileid: "89053027"
---
# <a name="dotnet-sln"></a><span data-ttu-id="f0ee0-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="f0ee0-103">dotnet sln</span></span>

<span data-ttu-id="f0ee0-104">本文**適用于：** ✔️ .net CORE 2.x SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="f0ee0-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f0ee0-105">名稱</span><span class="sxs-lookup"><span data-stu-id="f0ee0-105">Name</span></span>

<span data-ttu-id="f0ee0-106">`dotnet sln` -列出或修改 .NET Core 方案檔中的專案。</span><span class="sxs-lookup"><span data-stu-id="f0ee0-106">`dotnet sln` - Lists or modifies the projects in a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f0ee0-107">概要</span><span class="sxs-lookup"><span data-stu-id="f0ee0-107">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command]

dotnet sln [command] -h|--help
```

## <a name="description"></a><span data-ttu-id="f0ee0-108">描述</span><span class="sxs-lookup"><span data-stu-id="f0ee0-108">Description</span></span>

<span data-ttu-id="f0ee0-109">此 `dotnet sln` 命令提供一個便利的方式來列出和修改方案檔中的專案。</span><span class="sxs-lookup"><span data-stu-id="f0ee0-109">The `dotnet sln` command provides a convenient way to list and modify projects in a solution file.</span></span>

<span data-ttu-id="f0ee0-110">若要使用 `dotnet sln` 命令，方案檔必須已經存在。</span><span class="sxs-lookup"><span data-stu-id="f0ee0-110">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="f0ee0-111">如果您需要建立一個，請使用 [dotnet new](dotnet-new.md) 命令，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="f0ee0-111">If you need to create one, use the [dotnet new](dotnet-new.md) command, as in the following example:</span></span>

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a><span data-ttu-id="f0ee0-112">引數</span><span class="sxs-lookup"><span data-stu-id="f0ee0-112">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="f0ee0-113">要使用的方案檔。</span><span class="sxs-lookup"><span data-stu-id="f0ee0-113">The solution file to use.</span></span> <span data-ttu-id="f0ee0-114">如果省略這個引數，則命令會在目前的目錄中搜尋一個。</span><span class="sxs-lookup"><span data-stu-id="f0ee0-114">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="f0ee0-115">如果找不到解決方案檔或多個方案檔，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="f0ee0-115">If it finds no solution file or multiple solution files, the command fails.</span></span>

## <a name="options"></a><span data-ttu-id="f0ee0-116">選項</span><span class="sxs-lookup"><span data-stu-id="f0ee0-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="f0ee0-117">印出如何使用命令的描述。</span><span class="sxs-lookup"><span data-stu-id="f0ee0-117">Prints out a description of how to use the command.</span></span>

## <a name="commands"></a><span data-ttu-id="f0ee0-118">命令</span><span class="sxs-lookup"><span data-stu-id="f0ee0-118">Commands</span></span>

### `list`

<span data-ttu-id="f0ee0-119">列出方案檔中的所有專案。</span><span class="sxs-lookup"><span data-stu-id="f0ee0-119">Lists all projects in a solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="f0ee0-120">概要</span><span class="sxs-lookup"><span data-stu-id="f0ee0-120">Synopsis</span></span>

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="f0ee0-121">引數</span><span class="sxs-lookup"><span data-stu-id="f0ee0-121">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="f0ee0-122">要使用的方案檔。</span><span class="sxs-lookup"><span data-stu-id="f0ee0-122">The solution file to use.</span></span> <span data-ttu-id="f0ee0-123">如果省略這個引數，則命令會在目前的目錄中搜尋一個。</span><span class="sxs-lookup"><span data-stu-id="f0ee0-123">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="f0ee0-124">如果找不到解決方案檔或多個方案檔，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="f0ee0-124">If it finds no solution file or multiple solution files, the command fails.</span></span>

#### <a name="options"></a><span data-ttu-id="f0ee0-125">選項</span><span class="sxs-lookup"><span data-stu-id="f0ee0-125">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="f0ee0-126">印出如何使用命令的描述。</span><span class="sxs-lookup"><span data-stu-id="f0ee0-126">Prints out a description of how to use the command.</span></span>
  
### `add`

<span data-ttu-id="f0ee0-127">將一或多個專案加入至方案檔。</span><span class="sxs-lookup"><span data-stu-id="f0ee0-127">Adds one or more projects to the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="f0ee0-128">概要</span><span class="sxs-lookup"><span data-stu-id="f0ee0-128">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder <PATH>] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="f0ee0-129">引數</span><span class="sxs-lookup"><span data-stu-id="f0ee0-129">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="f0ee0-130">要使用的方案檔。</span><span class="sxs-lookup"><span data-stu-id="f0ee0-130">The solution file to use.</span></span> <span data-ttu-id="f0ee0-131">如果未指定，命令會在目前的目錄中搜尋一個目錄，如果有多個方案檔，則會失敗。</span><span class="sxs-lookup"><span data-stu-id="f0ee0-131">If it is unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="f0ee0-132">要加入至方案之專案或專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="f0ee0-132">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="f0ee0-133">Unix/Linux shell [萬用字元模式](https://en.wikipedia.org/wiki/Glob_(programming)) 擴充會由命令正確處理 `dotnet sln` 。</span><span class="sxs-lookup"><span data-stu-id="f0ee0-133">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="f0ee0-134">選項</span><span class="sxs-lookup"><span data-stu-id="f0ee0-134">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="f0ee0-135">印出如何使用命令的描述。</span><span class="sxs-lookup"><span data-stu-id="f0ee0-135">Prints out a description of how to use the command.</span></span>

- **`--in-root`**

  <span data-ttu-id="f0ee0-136">將專案放在解決方案的根目錄，而不是建立方案資料夾。</span><span class="sxs-lookup"><span data-stu-id="f0ee0-136">Places the projects in the root of the solution, rather than creating a solution folder.</span></span> <span data-ttu-id="f0ee0-137">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="f0ee0-137">Available since .NET Core 3.0 SDK.</span></span>

- **`-s|--solution-folder <PATH>`**

  <span data-ttu-id="f0ee0-138">要加入專案的目的地方案資料夾路徑。</span><span class="sxs-lookup"><span data-stu-id="f0ee0-138">The destination solution folder path to add the projects to.</span></span> <span data-ttu-id="f0ee0-139">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="f0ee0-139">Available since .NET Core 3.0 SDK.</span></span>

### `remove`

<span data-ttu-id="f0ee0-140">從方案檔中移除一個專案或多個專案。</span><span class="sxs-lookup"><span data-stu-id="f0ee0-140">Removes a project or multiple projects from the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="f0ee0-141">概要</span><span class="sxs-lookup"><span data-stu-id="f0ee0-141">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="f0ee0-142">引數</span><span class="sxs-lookup"><span data-stu-id="f0ee0-142">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="f0ee0-143">要使用的方案檔。</span><span class="sxs-lookup"><span data-stu-id="f0ee0-143">The solution file to use.</span></span> <span data-ttu-id="f0ee0-144">如果未指定，則命令會在目前的目錄中搜尋一個目錄，如果有多個方案檔，則會失敗。</span><span class="sxs-lookup"><span data-stu-id="f0ee0-144">If is left unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="f0ee0-145">要加入至方案之專案或專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="f0ee0-145">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="f0ee0-146">Unix/Linux shell [萬用字元模式](https://en.wikipedia.org/wiki/Glob_(programming)) 擴充會由命令正確處理 `dotnet sln` 。</span><span class="sxs-lookup"><span data-stu-id="f0ee0-146">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="f0ee0-147">選項</span><span class="sxs-lookup"><span data-stu-id="f0ee0-147">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="f0ee0-148">印出如何使用命令的描述。</span><span class="sxs-lookup"><span data-stu-id="f0ee0-148">Prints out a description of how to use the command.</span></span>

## <a name="examples"></a><span data-ttu-id="f0ee0-149">範例</span><span class="sxs-lookup"><span data-stu-id="f0ee0-149">Examples</span></span>

- <span data-ttu-id="f0ee0-150">列出方案中的專案：</span><span class="sxs-lookup"><span data-stu-id="f0ee0-150">List the projects in a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln list
  ```

- <span data-ttu-id="f0ee0-151">將 C# 專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="f0ee0-151">Add a C# project to a solution:</span></span>

  ```dotnetcli
  dotnet sln add todo-app/todo-app.csproj
  ```

- <span data-ttu-id="f0ee0-152">移除方案中的 C# 專案：</span><span class="sxs-lookup"><span data-stu-id="f0ee0-152">Remove a C# project from a solution:</span></span>

  ```dotnetcli
  dotnet sln remove todo-app/todo-app.csproj
  ```

- <span data-ttu-id="f0ee0-153">將多個 c # 專案新增至方案的根目錄：</span><span class="sxs-lookup"><span data-stu-id="f0ee0-153">Add multiple C# projects to the root of a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj --in-root
  ```

- <span data-ttu-id="f0ee0-154">將多個 C# 專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="f0ee0-154">Add multiple C# projects to a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="f0ee0-155">從方案中移除多個 C# 專案：</span><span class="sxs-lookup"><span data-stu-id="f0ee0-155">Remove multiple C# projects from a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="f0ee0-156">使用萬用字元模式將多個 c # 專案新增至方案 (僅限 Unix/Linux) ：</span><span class="sxs-lookup"><span data-stu-id="f0ee0-156">Add multiple C# projects to a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- <span data-ttu-id="f0ee0-157">使用萬用字元模式將多個 c # 專案新增至方案 (只 Windows PowerShell) ：</span><span class="sxs-lookup"><span data-stu-id="f0ee0-157">Add multiple C# projects to a solution using a globbing pattern (Windows PowerShell only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add (ls -r **/*.csproj)
  ```

- <span data-ttu-id="f0ee0-158">使用萬用字元模式從方案中移除多個 c # 專案，只 (Unix/Linux) ：</span><span class="sxs-lookup"><span data-stu-id="f0ee0-158">Remove multiple C# projects from a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```

- <span data-ttu-id="f0ee0-159">使用萬用字元模式從方案中移除多個 c # 專案 (只 Windows PowerShell) ：</span><span class="sxs-lookup"><span data-stu-id="f0ee0-159">Remove multiple C# projects from a solution using a globbing pattern (Windows PowerShell only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove (ls -r **/*.csproj)
  ```
