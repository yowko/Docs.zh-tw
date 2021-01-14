---
title: dotnet list package 命令
description: "'dotnet list package' 命令提供一個便利選項，可列出適用於專案或解決方案的套件參考。"
ms.date: 11/11/2020
ms.openlocfilehash: 684b73dec553a424252e1368c265847622fb7850
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189892"
---
# <a name="dotnet-list-package"></a><span data-ttu-id="a46b0-103">dotnet list package</span><span class="sxs-lookup"><span data-stu-id="a46b0-103">dotnet list package</span></span>

<span data-ttu-id="a46b0-104">本文 **適用于：** ✔️ .net CORE 2.2 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="a46b0-104">**This article applies to:** ✔️ .NET Core 2.2 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="a46b0-105">名稱</span><span class="sxs-lookup"><span data-stu-id="a46b0-105">Name</span></span>

<span data-ttu-id="a46b0-106">`dotnet list package` - 列出適用於專案或解決方案的套件參考。</span><span class="sxs-lookup"><span data-stu-id="a46b0-106">`dotnet list package` - Lists the package references for a project or solution.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a46b0-107">概要</span><span class="sxs-lookup"><span data-stu-id="a46b0-107">Synopsis</span></span>

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] package [--config <SOURCE>]
    [--deprecated]
    [--framework <FRAMEWORK>] [--highest-minor] [--highest-patch]
    [--include-prerelease] [--include-transitive] [--interactive]
    [--outdated] [--source <SOURCE>] [-v|--verbosity <LEVEL>]

dotnet list package -h|--help
```

## <a name="description"></a><span data-ttu-id="a46b0-108">Description</span><span class="sxs-lookup"><span data-stu-id="a46b0-108">Description</span></span>

<span data-ttu-id="a46b0-109">`dotnet list package` 命令提供一個便利選項，可列出適用於特定專案或解決方案的所有 NuGet 套件參考。</span><span class="sxs-lookup"><span data-stu-id="a46b0-109">The `dotnet list package` command provides a convenient option to list all NuGet package references for a specific project or a solution.</span></span> <span data-ttu-id="a46b0-110">您需要先建置專案，才能具備處理此命令所需的資產。</span><span class="sxs-lookup"><span data-stu-id="a46b0-110">You first need to build the project in order to have the assets needed for this command to process.</span></span> <span data-ttu-id="a46b0-111">下列範例會針對 [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) 專案顯示 `dotnet list package` 命令的輸出：</span><span class="sxs-lookup"><span data-stu-id="a46b0-111">The following example shows the output of the `dotnet list package` command for the [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) project:</span></span>

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  1.4.0       1.4.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

<span data-ttu-id="a46b0-112">**Requested** 欄會參考專案檔中所指定的套件版本，而且可以是一個範圍。</span><span class="sxs-lookup"><span data-stu-id="a46b0-112">The **Requested** column refers to the package version specified in the project file and can be a range.</span></span> <span data-ttu-id="a46b0-113">**Resolved** 欄會列出專案目前正在使用的版本，且一律為單一值。</span><span class="sxs-lookup"><span data-stu-id="a46b0-113">The **Resolved** column lists the version that the project is currently using and is always a single value.</span></span> <span data-ttu-id="a46b0-114">在名稱旁邊顯示的封裝 `(A)` 代表隱含的封裝參考，這些參考是從專案設定 (`Sdk` 類型或 `<TargetFramework>` 屬性) 推斷而來 `<TargetFrameworks>` 。</span><span class="sxs-lookup"><span data-stu-id="a46b0-114">The packages displaying an `(A)` right next to their names represent implicit package references that are inferred from your project settings (`Sdk` type, or `<TargetFramework>` or `<TargetFrameworks>` property).</span></span>

<span data-ttu-id="a46b0-115">使用 `--outdated` 選項，以找出您在專案中所使用的套件是否有較新版本可供使用。</span><span class="sxs-lookup"><span data-stu-id="a46b0-115">Use the `--outdated` option to find out if there are newer versions available of the packages you're using in your projects.</span></span> <span data-ttu-id="a46b0-116">除非已解析的版本也是發行前版本，否則 `--outdated` 預設會列出最新的穩定套件。</span><span class="sxs-lookup"><span data-stu-id="a46b0-116">By default, `--outdated` lists the latest stable packages unless the resolved version is also a prerelease version.</span></span> <span data-ttu-id="a46b0-117">若要在列出較新的版本時包含發行前版本，也需指定 `--include-prerelease` 選項。</span><span class="sxs-lookup"><span data-stu-id="a46b0-117">To include prerelease versions when listing newer versions, also specify the `--include-prerelease` option.</span></span> <span data-ttu-id="a46b0-118">下列範例會針對與上一個範例相同的專案顯示 `dotnet list package --outdated --include-prerelease` 命令的輸出：</span><span class="sxs-lookup"><span data-stu-id="a46b0-118">The following examples shows the output of the `dotnet list package --outdated --include-prerelease` command for the same project as the previous example:</span></span>

```output
The following sources were used:
   https://api.nuget.org/v3/index.json
   C:\Program Files (x86)\Microsoft SDKs\NuGetPackages\

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         1.4.0       1.4.0      1.5.0-preview
```

<span data-ttu-id="a46b0-119">如果您需要找出專案是否有可轉移的相依性，請使用 `--include-transitive` 選項。</span><span class="sxs-lookup"><span data-stu-id="a46b0-119">If you need to find out whether your project has transitive dependencies, use the `--include-transitive` option.</span></span> <span data-ttu-id="a46b0-120">當您在之後將依賴另一個套件的專案中新增套件時，就會發生可轉移的相依性。</span><span class="sxs-lookup"><span data-stu-id="a46b0-120">Transitive dependencies occur when you add a package to your project that in turn relies on another package.</span></span> <span data-ttu-id="a46b0-121">下列範例會針對 [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) 專案顯示執行 `dotnet list package --include-transitive` 命令的輸出，其會顯示最上層套件及其相依的套件：</span><span class="sxs-lookup"><span data-stu-id="a46b0-121">The following example shows the output from running the `dotnet list package --include-transitive` command for the [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) project, which displays top-level packages and the packages they depend on:</span></span>

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Transitive Package      Resolved
   > PluginBase            1.0.0
```

## <a name="arguments"></a><span data-ttu-id="a46b0-122">引數</span><span class="sxs-lookup"><span data-stu-id="a46b0-122">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="a46b0-123">要在其上運作的專案或解決方案檔。</span><span class="sxs-lookup"><span data-stu-id="a46b0-123">The project or solution file to operate on.</span></span> <span data-ttu-id="a46b0-124">如果未指定，命令會在目前的目錄中搜尋一個專案檔。</span><span class="sxs-lookup"><span data-stu-id="a46b0-124">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="a46b0-125">如果找到一個以上的解決方案或專案，則會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="a46b0-125">If more than one solution or project is found, an error is thrown.</span></span>

## <a name="options"></a><span data-ttu-id="a46b0-126">選項</span><span class="sxs-lookup"><span data-stu-id="a46b0-126">Options</span></span>

- **`--config <SOURCE>`**

  <span data-ttu-id="a46b0-127">搜尋較新的套件時要使用的 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="a46b0-127">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="a46b0-128">需要 `--outdated` 選項。</span><span class="sxs-lookup"><span data-stu-id="a46b0-128">Requires the `--outdated` option.</span></span>

- **`--deprecated`**

  <span data-ttu-id="a46b0-129">顯示已淘汰的封裝。</span><span class="sxs-lookup"><span data-stu-id="a46b0-129">Displays packages that have been deprecated.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="a46b0-130">只顯示適用於所指定[目標 Framework](../../standard/frameworks.md) 的套件。</span><span class="sxs-lookup"><span data-stu-id="a46b0-130">Displays only the packages applicable for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="a46b0-131">若要指定多個架構，請多次指定該選項。</span><span class="sxs-lookup"><span data-stu-id="a46b0-131">To specify multiple frameworks, repeat the option multiple times.</span></span> <span data-ttu-id="a46b0-132">例如：`--framework netcoreapp2.2 --framework netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="a46b0-132">For example: `--framework netcoreapp2.2 --framework netstandard2.0`.</span></span>

- **`-h|--help`**

  <span data-ttu-id="a46b0-133">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="a46b0-133">Prints out a short help for the command.</span></span>

- **`--highest-minor`**

  <span data-ttu-id="a46b0-134">在搜尋較新的套件時，建議只搜尋主要版本號碼相符的套件。</span><span class="sxs-lookup"><span data-stu-id="a46b0-134">Considers only the packages with a matching major version number when searching for newer packages.</span></span> <span data-ttu-id="a46b0-135">需要 `--outdated` 或 `--deprecated` 選項。</span><span class="sxs-lookup"><span data-stu-id="a46b0-135">Requires the `--outdated` or `--deprecated` option.</span></span>

- **`--highest-patch`**

  <span data-ttu-id="a46b0-136">在搜尋較新的套件時，建議只搜尋主要和次要版本號碼相符的套件。</span><span class="sxs-lookup"><span data-stu-id="a46b0-136">Considers only the packages with a matching major and minor version numbers when searching for newer packages.</span></span> <span data-ttu-id="a46b0-137">需要 `--outdated` 或 `--deprecated` 選項。</span><span class="sxs-lookup"><span data-stu-id="a46b0-137">Requires the `--outdated` or `--deprecated` option.</span></span>

- **`--include-prerelease`**

  <span data-ttu-id="a46b0-138">在搜尋較新的套件時，建議搜尋具有發行前版本的套件。</span><span class="sxs-lookup"><span data-stu-id="a46b0-138">Considers packages with prerelease versions when searching for newer packages.</span></span> <span data-ttu-id="a46b0-139">需要 `--outdated` 或 `--deprecated` 選項。</span><span class="sxs-lookup"><span data-stu-id="a46b0-139">Requires the `--outdated` or `--deprecated` option.</span></span>

- **`--include-transitive`**

  <span data-ttu-id="a46b0-140">列出可轉移的套件 (除了最上層套件)。</span><span class="sxs-lookup"><span data-stu-id="a46b0-140">Lists transitive packages, in addition to the top-level packages.</span></span> <span data-ttu-id="a46b0-141">指定此選項時，您會取得最上層套件所依存的套件清單。</span><span class="sxs-lookup"><span data-stu-id="a46b0-141">When specifying this option, you get a list of packages that the top-level packages depend on.</span></span>

- **`--interactive`**

  <span data-ttu-id="a46b0-142">可讓命令停止，並等候使用者輸入或進行動作。</span><span class="sxs-lookup"><span data-stu-id="a46b0-142">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="a46b0-143">例如完成驗證。</span><span class="sxs-lookup"><span data-stu-id="a46b0-143">For example, to complete authentication.</span></span> <span data-ttu-id="a46b0-144">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="a46b0-144">Available since .NET Core 3.0 SDK.</span></span>

- **`--outdated`**

  <span data-ttu-id="a46b0-145">列出有較新版本可供使用的套件。</span><span class="sxs-lookup"><span data-stu-id="a46b0-145">Lists packages that have newer versions available.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="a46b0-146">搜尋較新的套件時要使用的 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="a46b0-146">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="a46b0-147">需要 `--outdated` 或 `--deprecated` 選項。</span><span class="sxs-lookup"><span data-stu-id="a46b0-147">Requires the `--outdated` or `--deprecated` option.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="a46b0-148">設定 MSBuild 詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="a46b0-148">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="a46b0-149">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="a46b0-149">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="a46b0-150">預設為 `minimal`。</span><span class="sxs-lookup"><span data-stu-id="a46b0-150">The default is `minimal`.</span></span>

## <a name="examples"></a><span data-ttu-id="a46b0-151">範例</span><span class="sxs-lookup"><span data-stu-id="a46b0-151">Examples</span></span>

- <span data-ttu-id="a46b0-152">列出特定專案的套件參考：</span><span class="sxs-lookup"><span data-stu-id="a46b0-152">List package references of a specific project:</span></span>

  ```dotnetcli
  dotnet list SentimentAnalysis.csproj package
  ```

- <span data-ttu-id="a46b0-153">列出有較新版本可供使用 (包括發行前版本) 的套件參考：</span><span class="sxs-lookup"><span data-stu-id="a46b0-153">List package references that have newer versions available, including prerelease versions:</span></span>

  ```dotnetcli
  dotnet list package --outdated --include-prerelease
  ```

- <span data-ttu-id="a46b0-154">列出適用於特定目標 Framework 的套件參考：</span><span class="sxs-lookup"><span data-stu-id="a46b0-154">List package references for a specific target framework:</span></span>

  ```dotnetcli
  dotnet list package --framework netcoreapp3.0
  ```
