---
title: dotnet list package 命令
description: "'dotnet list package' 命令提供一個便利選項，可列出適用於專案或解決方案的套件參考。"
ms.date: 06/26/2019
ms.openlocfilehash: 48eef0ccc6acf2bbd6c1acf748870882d2480ce5
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168026"
---
# <a name="dotnet-list-package"></a><span data-ttu-id="f83ab-103">dotnet list package</span><span class="sxs-lookup"><span data-stu-id="f83ab-103">dotnet list package</span></span>

[!INCLUDE [topic-appliesto-net-core-22plus](../../../includes/topic-appliesto-net-core-22plus.md)]

## <a name="name"></a><span data-ttu-id="f83ab-104">名稱</span><span class="sxs-lookup"><span data-stu-id="f83ab-104">Name</span></span>

<span data-ttu-id="f83ab-105">`dotnet list package` - 列出適用於專案或解決方案的套件參考。</span><span class="sxs-lookup"><span data-stu-id="f83ab-105">`dotnet list package` - Lists the package references for a project or solution.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f83ab-106">概要</span><span class="sxs-lookup"><span data-stu-id="f83ab-106">Synopsis</span></span>

```console
dotnet list [<PROJECT>|<SOLUTION>] package [--config] [--framework] [--highest-minor] [--highest-patch] 
   [--include-prerelease] [--include-transitive] [--interactive] [--outdated] [--source]
dotnet list package [-h|--help]
```

## <a name="description"></a><span data-ttu-id="f83ab-107">說明</span><span class="sxs-lookup"><span data-stu-id="f83ab-107">Description</span></span>

<span data-ttu-id="f83ab-108">`dotnet list package` 命令提供一個便利選項，可列出適用於特定專案或解決方案的所有 NuGet 套件參考。</span><span class="sxs-lookup"><span data-stu-id="f83ab-108">The `dotnet list package` command provides a convenient option to list all NuGet package references for a specific project or a solution.</span></span> <span data-ttu-id="f83ab-109">您需要先建置專案，才能具備處理此命令所需的資產。</span><span class="sxs-lookup"><span data-stu-id="f83ab-109">You first need to build the project in order to have the assets needed for this command to process.</span></span> <span data-ttu-id="f83ab-110">下列範例會針對 [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) 專案顯示 `dotnet list package` 命令的輸出：</span><span class="sxs-lookup"><span data-stu-id="f83ab-110">The following example shows the output of the `dotnet list package` command for the [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) project:</span></span>

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  0.11.0      0.11.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

<span data-ttu-id="f83ab-111">**Requested** 欄會參考專案檔中所指定的套件版本，而且可以是一個範圍。</span><span class="sxs-lookup"><span data-stu-id="f83ab-111">The **Requested** column refers to the package version specified in the project file and can be a range.</span></span> <span data-ttu-id="f83ab-112">**Resolved** 欄會列出專案目前正在使用的版本，且一律為單一值。</span><span class="sxs-lookup"><span data-stu-id="f83ab-112">The **Resolved** column lists the version that the project is currently using and is always a single value.</span></span> <span data-ttu-id="f83ab-113">名稱旁邊顯示 `(A)` 的套件代表[隱含的套件參考](csproj.md#implicit-package-references)，可從您的專案設定 (`Sdk` 類型、`<TargetFramework>` 或 `<TargetFrameworks>` 屬性等) 進行推斷。</span><span class="sxs-lookup"><span data-stu-id="f83ab-113">The packages displaying an `(A)` right next to their names represent [implicit package references](csproj.md#implicit-package-references) that are inferred from your project settings (`Sdk` type, `<TargetFramework>` or `<TargetFrameworks>` property, etc.)</span></span>

<span data-ttu-id="f83ab-114">使用 `--outdated` 選項，以找出您在專案中所使用的套件是否有較新版本可供使用。</span><span class="sxs-lookup"><span data-stu-id="f83ab-114">Use the `--outdated` option to find out if there are newer versions available of the packages you're using in your projects.</span></span> <span data-ttu-id="f83ab-115">除非已解析的版本也是發行前版本，否則 `--outdated` 預設會列出最新的穩定套件。</span><span class="sxs-lookup"><span data-stu-id="f83ab-115">By default, `--outdated` lists the latest stable packages unless the resolved version is also a prerelease version.</span></span> <span data-ttu-id="f83ab-116">若要在列出較新的版本時包含發行前版本，也需指定 `--include-prerelease` 選項。</span><span class="sxs-lookup"><span data-stu-id="f83ab-116">To include prerelease versions when listing newer versions, also specify the `--include-prerelease` option.</span></span> <span data-ttu-id="f83ab-117">下列範例會針對與上一個範例相同的專案顯示 `dotnet list package --outdated --include-prerelease` 命令的輸出：</span><span class="sxs-lookup"><span data-stu-id="f83ab-117">The following examples shows the output of the `dotnet list package --outdated --include-prerelease` command for the same project as the previous example:</span></span>

```output
The following sources were used:
   https://api.nuget.org/v3/index.json

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         0.11.0      0.11.0     1.0.0-preview
```

<span data-ttu-id="f83ab-118">如果您需要找出專案是否有可轉移的相依性，請使用 `--include-transitive` 選項。</span><span class="sxs-lookup"><span data-stu-id="f83ab-118">If you need to find out whether your project has transitive dependencies, use the `--include-transitive` option.</span></span> <span data-ttu-id="f83ab-119">當您在之後將依賴另一個套件的專案中新增套件時，就會發生可轉移的相依性。</span><span class="sxs-lookup"><span data-stu-id="f83ab-119">Transitive dependencies occur when you add a package to your project that in turn relies on another package.</span></span> <span data-ttu-id="f83ab-120">下列範例會針對 [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) 專案顯示執行 `dotnet list package --include-transitive` 命令的輸出，其會顯示最上層套件及其相依的套件：</span><span class="sxs-lookup"><span data-stu-id="f83ab-120">The following example shows the output from running the `dotnet list package --include-transitive` command for the [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) project, which displays top-level packages and the packages they depend on:</span></span>

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Top-level Package                      Requested                    Resolved
   > Microsoft.NETCore.Platforms    (A)   [3.0.0-preview3.19128.7, )   3.0.0-preview3.19128.7
   > Microsoft.WindowsDesktop.App   (A)   [3.0.0-preview3-27504-2, )   3.0.0-preview3-27504-2

   Transitive Package               Resolved
   > Microsoft.NETCore.Targets      2.0.0
   > PluginBase                     1.0.0

(A) : Auto-referenced package.
```

## <a name="arguments"></a><span data-ttu-id="f83ab-121">引數</span><span class="sxs-lookup"><span data-stu-id="f83ab-121">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="f83ab-122">要在其上運作的專案或解決方案檔。</span><span class="sxs-lookup"><span data-stu-id="f83ab-122">The project or solution file to operate on.</span></span> <span data-ttu-id="f83ab-123">如果未指定，命令會在目前的目錄中搜尋一個專案檔。</span><span class="sxs-lookup"><span data-stu-id="f83ab-123">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="f83ab-124">如果找到一個以上的解決方案或專案，則會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="f83ab-124">If more than one solution or project is found, an error is thrown.</span></span>

## <a name="options"></a><span data-ttu-id="f83ab-125">選項</span><span class="sxs-lookup"><span data-stu-id="f83ab-125">Options</span></span>

* **`--config <SOURCE>`**

  <span data-ttu-id="f83ab-126">搜尋較新的套件時要使用的 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="f83ab-126">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="f83ab-127">需要 `--outdated` 選項。</span><span class="sxs-lookup"><span data-stu-id="f83ab-127">Requires the `--outdated` option.</span></span>

* **`--framework <FRAMEWORK>`**

  <span data-ttu-id="f83ab-128">只顯示適用於所指定[目標 Framework](../../standard/frameworks.md) 的套件。</span><span class="sxs-lookup"><span data-stu-id="f83ab-128">Displays only the packages applicable for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="f83ab-129">若要指定多個架構，請多次指定該選項。</span><span class="sxs-lookup"><span data-stu-id="f83ab-129">To specify multiple frameworks, repeat the option multiple times.</span></span> <span data-ttu-id="f83ab-130">例如：`--framework netcoreapp2.2 --framework netstandard2.0`。</span><span class="sxs-lookup"><span data-stu-id="f83ab-130">For example: `--framework netcoreapp2.2 --framework netstandard2.0`.</span></span>

* **`-h|--help`**

  <span data-ttu-id="f83ab-131">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="f83ab-131">Prints out a short help for the command.</span></span>

* **`--highest-minor`**

  <span data-ttu-id="f83ab-132">在搜尋較新的套件時，建議只搜尋主要版本號碼相符的套件。</span><span class="sxs-lookup"><span data-stu-id="f83ab-132">Considers only the packages with a matching major version number when searching for newer packages.</span></span> <span data-ttu-id="f83ab-133">需要 `--outdated` 選項。</span><span class="sxs-lookup"><span data-stu-id="f83ab-133">Requires the `--outdated` option.</span></span>

* **`--highest-patch`**

  <span data-ttu-id="f83ab-134">在搜尋較新的套件時，建議只搜尋主要和次要版本號碼相符的套件。</span><span class="sxs-lookup"><span data-stu-id="f83ab-134">Considers only the packages with a matching major and minor version numbers when searching for newer packages.</span></span> <span data-ttu-id="f83ab-135">需要 `--outdated` 選項。</span><span class="sxs-lookup"><span data-stu-id="f83ab-135">Requires the `--outdated` option.</span></span>

* **`--include-prerelease`**

  <span data-ttu-id="f83ab-136">在搜尋較新的套件時，建議搜尋具有發行前版本的套件。</span><span class="sxs-lookup"><span data-stu-id="f83ab-136">Considers packages with prerelease versions when searching for newer packages.</span></span> <span data-ttu-id="f83ab-137">需要 `--outdated` 選項。</span><span class="sxs-lookup"><span data-stu-id="f83ab-137">Requires the `--outdated` option.</span></span>

* **`--include-transitive`**

  <span data-ttu-id="f83ab-138">列出可轉移的套件 (除了最上層套件)。</span><span class="sxs-lookup"><span data-stu-id="f83ab-138">Lists transitive packages, in addition to the top-level packages.</span></span> <span data-ttu-id="f83ab-139">指定此選項時，您會取得最上層套件所依存的套件清單。</span><span class="sxs-lookup"><span data-stu-id="f83ab-139">When specifying this option, you get a list of packages that the top-level packages depend on.</span></span>

* **`--interactive`**

  <span data-ttu-id="f83ab-140">可讓命令停止，並等候使用者輸入或進行動作。</span><span class="sxs-lookup"><span data-stu-id="f83ab-140">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="f83ab-141">例如完成驗證。</span><span class="sxs-lookup"><span data-stu-id="f83ab-141">For example, to complete authentication.</span></span> <span data-ttu-id="f83ab-142">自 .NET Core 3.0 SDK 起提供使用。</span><span class="sxs-lookup"><span data-stu-id="f83ab-142">Available since .NET Core 3.0 SDK.</span></span>

* **`--outdated`**

  <span data-ttu-id="f83ab-143">列出有較新版本可供使用的套件。</span><span class="sxs-lookup"><span data-stu-id="f83ab-143">Lists packages that have newer versions available.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="f83ab-144">搜尋較新的套件時要使用的 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="f83ab-144">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="f83ab-145">需要 `--outdated` 選項。</span><span class="sxs-lookup"><span data-stu-id="f83ab-145">Requires the `--outdated` option.</span></span>

## <a name="examples"></a><span data-ttu-id="f83ab-146">範例</span><span class="sxs-lookup"><span data-stu-id="f83ab-146">Examples</span></span>

* <span data-ttu-id="f83ab-147">列出特定專案的套件參考：</span><span class="sxs-lookup"><span data-stu-id="f83ab-147">List package references of a specific project:</span></span>

  ```console
  dotnet list SentimentAnalysis.csproj package
  ```

* <span data-ttu-id="f83ab-148">列出有較新版本可供使用 (包括發行前版本) 的套件參考：</span><span class="sxs-lookup"><span data-stu-id="f83ab-148">List package references that have newer versions available, including prerelease versions:</span></span>

  ```console
  dotnet list package --outdated --include-prerelease
  ```

* <span data-ttu-id="f83ab-149">列出適用於特定目標 Framework 的套件參考：</span><span class="sxs-lookup"><span data-stu-id="f83ab-149">List package references for a specific target framework:</span></span>

  ```console
  dotnet list package --framework netcoreapp3.0
  ```
