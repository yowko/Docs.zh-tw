---
title: dotnet list package 命令
description: "'dotnet list package' 命令提供一個便利選項，可列出適用於專案或解決方案的套件參考。"
ms.date: 02/14/2020
ms.openlocfilehash: 1cb52b8de10b2eef2ef7465f04316e9446318763
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157228"
---
# <a name="dotnet-list-package"></a><span data-ttu-id="2095c-103">dotnet list package</span><span class="sxs-lookup"><span data-stu-id="2095c-103">dotnet list package</span></span>

<span data-ttu-id="2095c-104">**本文適用于：** ✔️ .net CORE 2.2 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="2095c-104">**This article applies to:** ✔️ .NET Core 2.2 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="2095c-105">名稱</span><span class="sxs-lookup"><span data-stu-id="2095c-105">Name</span></span>

<span data-ttu-id="2095c-106">`dotnet list package` - 列出適用於專案或解決方案的套件參考。</span><span class="sxs-lookup"><span data-stu-id="2095c-106">`dotnet list package` - Lists the package references for a project or solution.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2095c-107">概要</span><span class="sxs-lookup"><span data-stu-id="2095c-107">Synopsis</span></span>

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] package [--config] [--framework] [--highest-minor] [--highest-patch]
   [--include-prerelease] [--include-transitive] [--interactive] [--outdated] [--source]
dotnet list package [-h|--help]
```

## <a name="description"></a><span data-ttu-id="2095c-108">描述</span><span class="sxs-lookup"><span data-stu-id="2095c-108">Description</span></span>

<span data-ttu-id="2095c-109">`dotnet list package` 命令提供一個便利選項，可列出適用於特定專案或解決方案的所有 NuGet 套件參考。</span><span class="sxs-lookup"><span data-stu-id="2095c-109">The `dotnet list package` command provides a convenient option to list all NuGet package references for a specific project or a solution.</span></span> <span data-ttu-id="2095c-110">您需要先建置專案，才能具備處理此命令所需的資產。</span><span class="sxs-lookup"><span data-stu-id="2095c-110">You first need to build the project in order to have the assets needed for this command to process.</span></span> <span data-ttu-id="2095c-111">下列範例會針對 `dotnet list package`SentimentAnalysis[ 專案顯示 ](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) 命令的輸出：</span><span class="sxs-lookup"><span data-stu-id="2095c-111">The following example shows the output of the `dotnet list package` command for the [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) project:</span></span>

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  1.4.0       1.4.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

<span data-ttu-id="2095c-112">**Requested** 欄會參考專案檔中所指定的套件版本，而且可以是一個範圍。</span><span class="sxs-lookup"><span data-stu-id="2095c-112">The **Requested** column refers to the package version specified in the project file and can be a range.</span></span> <span data-ttu-id="2095c-113">**Resolved** 欄會列出專案目前正在使用的版本，且一律為單一值。</span><span class="sxs-lookup"><span data-stu-id="2095c-113">The **Resolved** column lists the version that the project is currently using and is always a single value.</span></span> <span data-ttu-id="2095c-114">名稱旁邊顯示 `(A)` 的套件代表[隱含的套件參考](csproj.md#implicit-package-references)，可從您的專案設定 (`Sdk` 類型、`<TargetFramework>` 或 `<TargetFrameworks>` 屬性等) 進行推斷。</span><span class="sxs-lookup"><span data-stu-id="2095c-114">The packages displaying an `(A)` right next to their names represent [implicit package references](csproj.md#implicit-package-references) that are inferred from your project settings (`Sdk` type, `<TargetFramework>` or `<TargetFrameworks>` property, etc.)</span></span>

<span data-ttu-id="2095c-115">使用 `--outdated` 選項，以找出您在專案中所使用的套件是否有較新版本可供使用。</span><span class="sxs-lookup"><span data-stu-id="2095c-115">Use the `--outdated` option to find out if there are newer versions available of the packages you're using in your projects.</span></span> <span data-ttu-id="2095c-116">除非已解析的版本也是發行前版本，否則 `--outdated` 預設會列出最新的穩定套件。</span><span class="sxs-lookup"><span data-stu-id="2095c-116">By default, `--outdated` lists the latest stable packages unless the resolved version is also a prerelease version.</span></span> <span data-ttu-id="2095c-117">若要在列出較新的版本時包含發行前版本，也需指定 `--include-prerelease` 選項。</span><span class="sxs-lookup"><span data-stu-id="2095c-117">To include prerelease versions when listing newer versions, also specify the `--include-prerelease` option.</span></span> <span data-ttu-id="2095c-118">下列範例會針對與上一個範例相同的專案顯示 `dotnet list package --outdated --include-prerelease` 命令的輸出：</span><span class="sxs-lookup"><span data-stu-id="2095c-118">The following examples shows the output of the `dotnet list package --outdated --include-prerelease` command for the same project as the previous example:</span></span>

```output
The following sources were used:
   https://api.nuget.org/v3/index.json
   C:\Program Files (x86)\Microsoft SDKs\NuGetPackages\

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         1.4.0       1.4.0      1.5.0-preview
```

<span data-ttu-id="2095c-119">如果您需要找出專案是否有可轉移的相依性，請使用 `--include-transitive` 選項。</span><span class="sxs-lookup"><span data-stu-id="2095c-119">If you need to find out whether your project has transitive dependencies, use the `--include-transitive` option.</span></span> <span data-ttu-id="2095c-120">當您在之後將依賴另一個套件的專案中新增套件時，就會發生可轉移的相依性。</span><span class="sxs-lookup"><span data-stu-id="2095c-120">Transitive dependencies occur when you add a package to your project that in turn relies on another package.</span></span> <span data-ttu-id="2095c-121">下列範例會針對 `dotnet list package --include-transitive`HelloPlugin[ 專案顯示執行 ](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) 命令的輸出，其會顯示最上層套件及其相依的套件：</span><span class="sxs-lookup"><span data-stu-id="2095c-121">The following example shows the output from running the `dotnet list package --include-transitive` command for the [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) project, which displays top-level packages and the packages they depend on:</span></span>

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Transitive Package      Resolved
   > PluginBase            1.0.0
```

## <a name="arguments"></a><span data-ttu-id="2095c-122">引數</span><span class="sxs-lookup"><span data-stu-id="2095c-122">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="2095c-123">要在其上運作的專案或解決方案檔。</span><span class="sxs-lookup"><span data-stu-id="2095c-123">The project or solution file to operate on.</span></span> <span data-ttu-id="2095c-124">如果未指定，命令會在目前的目錄中搜尋一個專案檔。</span><span class="sxs-lookup"><span data-stu-id="2095c-124">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="2095c-125">如果找到一個以上的解決方案或專案，則會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="2095c-125">If more than one solution or project is found, an error is thrown.</span></span>

## <a name="options"></a><span data-ttu-id="2095c-126">選項。</span><span class="sxs-lookup"><span data-stu-id="2095c-126">Options</span></span>

- **`--config <SOURCE>`**

  <span data-ttu-id="2095c-127">搜尋較新的套件時要使用的 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="2095c-127">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="2095c-128">需要 `--outdated` 選項。</span><span class="sxs-lookup"><span data-stu-id="2095c-128">Requires the `--outdated` option.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="2095c-129">只顯示適用於所指定[目標 Framework](../../standard/frameworks.md) 的套件。</span><span class="sxs-lookup"><span data-stu-id="2095c-129">Displays only the packages applicable for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="2095c-130">若要指定多個架構，請多次指定該選項。</span><span class="sxs-lookup"><span data-stu-id="2095c-130">To specify multiple frameworks, repeat the option multiple times.</span></span> <span data-ttu-id="2095c-131">例如： `--framework netcoreapp2.2 --framework netstandard2.0` 。</span><span class="sxs-lookup"><span data-stu-id="2095c-131">For example: `--framework netcoreapp2.2 --framework netstandard2.0`.</span></span>

- **`-h|--help`**

  <span data-ttu-id="2095c-132">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="2095c-132">Prints out a short help for the command.</span></span>

- **`--highest-minor`**

  <span data-ttu-id="2095c-133">在搜尋較新的套件時，建議只搜尋主要版本號碼相符的套件。</span><span class="sxs-lookup"><span data-stu-id="2095c-133">Considers only the packages with a matching major version number when searching for newer packages.</span></span> <span data-ttu-id="2095c-134">需要 `--outdated` 選項。</span><span class="sxs-lookup"><span data-stu-id="2095c-134">Requires the `--outdated` option.</span></span>

- **`--highest-patch`**

  <span data-ttu-id="2095c-135">在搜尋較新的套件時，建議只搜尋主要和次要版本號碼相符的套件。</span><span class="sxs-lookup"><span data-stu-id="2095c-135">Considers only the packages with a matching major and minor version numbers when searching for newer packages.</span></span> <span data-ttu-id="2095c-136">需要 `--outdated` 選項。</span><span class="sxs-lookup"><span data-stu-id="2095c-136">Requires the `--outdated` option.</span></span>

- **`--include-prerelease`**

  <span data-ttu-id="2095c-137">在搜尋較新的套件時，建議搜尋具有發行前版本的套件。</span><span class="sxs-lookup"><span data-stu-id="2095c-137">Considers packages with prerelease versions when searching for newer packages.</span></span> <span data-ttu-id="2095c-138">需要 `--outdated` 選項。</span><span class="sxs-lookup"><span data-stu-id="2095c-138">Requires the `--outdated` option.</span></span>

- **`--include-transitive`**

  <span data-ttu-id="2095c-139">列出可轉移的套件 (除了最上層套件)。</span><span class="sxs-lookup"><span data-stu-id="2095c-139">Lists transitive packages, in addition to the top-level packages.</span></span> <span data-ttu-id="2095c-140">指定此選項時，您會取得最上層套件所依存的套件清單。</span><span class="sxs-lookup"><span data-stu-id="2095c-140">When specifying this option, you get a list of packages that the top-level packages depend on.</span></span>

- **`--interactive`**

  <span data-ttu-id="2095c-141">可讓命令停止，並等候使用者輸入或進行動作。</span><span class="sxs-lookup"><span data-stu-id="2095c-141">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="2095c-142">例如完成驗證。</span><span class="sxs-lookup"><span data-stu-id="2095c-142">For example, to complete authentication.</span></span> <span data-ttu-id="2095c-143">自 .NET Core 3.0 SDK 起提供使用。</span><span class="sxs-lookup"><span data-stu-id="2095c-143">Available since .NET Core 3.0 SDK.</span></span>

- **`--outdated`**

  <span data-ttu-id="2095c-144">列出有較新版本可供使用的套件。</span><span class="sxs-lookup"><span data-stu-id="2095c-144">Lists packages that have newer versions available.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="2095c-145">搜尋較新的套件時要使用的 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="2095c-145">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="2095c-146">需要 `--outdated` 選項。</span><span class="sxs-lookup"><span data-stu-id="2095c-146">Requires the `--outdated` option.</span></span>

## <a name="examples"></a><span data-ttu-id="2095c-147">範例</span><span class="sxs-lookup"><span data-stu-id="2095c-147">Examples</span></span>

- <span data-ttu-id="2095c-148">列出特定專案的套件參考：</span><span class="sxs-lookup"><span data-stu-id="2095c-148">List package references of a specific project:</span></span>

  ```dotnetcli
  dotnet list SentimentAnalysis.csproj package
  ```

- <span data-ttu-id="2095c-149">列出有較新版本可供使用 (包括發行前版本) 的套件參考：</span><span class="sxs-lookup"><span data-stu-id="2095c-149">List package references that have newer versions available, including prerelease versions:</span></span>

  ```dotnetcli
  dotnet list package --outdated --include-prerelease
  ```

- <span data-ttu-id="2095c-150">列出適用於特定目標 Framework 的套件參考：</span><span class="sxs-lookup"><span data-stu-id="2095c-150">List package references for a specific target framework:</span></span>

  ```dotnetcli
  dotnet list package --framework netcoreapp3.0
  ```
