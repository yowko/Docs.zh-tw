---
title: dotnet clean 命令
description: dotnet clean 命令會清除目前的目錄。
ms.date: 02/14/2020
ms.openlocfilehash: 186f1ea07718a8e178f88c3d079cf6e2f1f8660b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503749"
---
# <a name="dotnet-clean"></a><span data-ttu-id="76017-103">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="76017-103">dotnet clean</span></span>

<span data-ttu-id="76017-104">**本文適用于：✔️** .NET Core 2.x SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="76017-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="76017-105">名稱</span><span class="sxs-lookup"><span data-stu-id="76017-105">Name</span></span>

<span data-ttu-id="76017-106">`dotnet clean` - 清除專案的輸出。</span><span class="sxs-lookup"><span data-stu-id="76017-106">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="76017-107">概要</span><span class="sxs-lookup"><span data-stu-id="76017-107">Synopsis</span></span>

```dotnetcli
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--interactive]
    [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a><span data-ttu-id="76017-108">描述</span><span class="sxs-lookup"><span data-stu-id="76017-108">Description</span></span>

<span data-ttu-id="76017-109">`dotnet clean` 命令會清除前一個組建的輸出。</span><span class="sxs-lookup"><span data-stu-id="76017-109">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="76017-110">它會實作為 [MSBuild 目標](/visualstudio/msbuild/msbuild-targets)，因此命令在執行的時候會評估專案。</span><span class="sxs-lookup"><span data-stu-id="76017-110">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="76017-111">只會清除在建置期間建立的輸出。</span><span class="sxs-lookup"><span data-stu-id="76017-111">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="76017-112">中繼 (*obj*) 和最後輸出 (*bin*) 這兩個資料夾都會清除。</span><span class="sxs-lookup"><span data-stu-id="76017-112">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="76017-113">引數</span><span class="sxs-lookup"><span data-stu-id="76017-113">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="76017-114">要清除的 MSBuild 專案或方案。</span><span class="sxs-lookup"><span data-stu-id="76017-114">The MSBuild project or solution to clean.</span></span> <span data-ttu-id="76017-115">MSBuild 會在目前工作目錄中搜尋副檔名以 *proj* 或 *sln* 結尾的檔案，並使用該檔案。</span><span class="sxs-lookup"><span data-stu-id="76017-115">If a project or solution file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* or *sln*, and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="76017-116">選項。</span><span class="sxs-lookup"><span data-stu-id="76017-116">Options</span></span>

* **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="76017-117">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="76017-117">Defines the build configuration.</span></span> <span data-ttu-id="76017-118">大多數專案的預設值為 ，`Debug`但您可以覆蓋專案中的組建組態設置。</span><span class="sxs-lookup"><span data-stu-id="76017-118">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span> <span data-ttu-id="76017-119">如果在建置階段指定此選項，清除時才需要使用它。</span><span class="sxs-lookup"><span data-stu-id="76017-119">This option is only required when cleaning if you specified it during build time.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="76017-120">在建置時間指定的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="76017-120">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="76017-121">架構必須定義於[專案檔](csproj.md)中。</span><span class="sxs-lookup"><span data-stu-id="76017-121">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="76017-122">如果在建置階段指定架構，則您必須在清除時指定該架構。</span><span class="sxs-lookup"><span data-stu-id="76017-122">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

* **`-h|--help`**

  <span data-ttu-id="76017-123">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="76017-123">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="76017-124">可讓命令停止，並等候使用者輸入或進行動作。</span><span class="sxs-lookup"><span data-stu-id="76017-124">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="76017-125">例如完成驗證。</span><span class="sxs-lookup"><span data-stu-id="76017-125">For example, to complete authentication.</span></span> <span data-ttu-id="76017-126">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="76017-126">Available since .NET Core 3.0 SDK.</span></span>

* **`--nologo`**

  <span data-ttu-id="76017-127">不要顯示程式啟始橫幅或著作權訊息。</span><span class="sxs-lookup"><span data-stu-id="76017-127">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="76017-128">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="76017-128">Available since .NET Core 3.0 SDK.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="76017-129">包含要清除組建成品的目錄。</span><span class="sxs-lookup"><span data-stu-id="76017-129">The directory that contains the build artifacts to clean.</span></span> <span data-ttu-id="76017-130">如果您在建置專案時指定架構，請搭配輸出目錄參數來指定 `-f|--framework <FRAMEWORK>` 參數。</span><span class="sxs-lookup"><span data-stu-id="76017-130">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="76017-131">清除指定執行階段的輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="76017-131">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="76017-132">建立[獨立性部署 (SCD)](../deploying/index.md#publish-self-contained) 時會使用此選項。</span><span class="sxs-lookup"><span data-stu-id="76017-132">This is used when a [self-contained deployment](../deploying/index.md#publish-self-contained) was created.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="76017-133">設定 MSBuild 詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="76017-133">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="76017-134">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="76017-134">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="76017-135">預設值為 `normal`。</span><span class="sxs-lookup"><span data-stu-id="76017-135">The default is `normal`.</span></span>

## <a name="examples"></a><span data-ttu-id="76017-136">範例</span><span class="sxs-lookup"><span data-stu-id="76017-136">Examples</span></span>

* <span data-ttu-id="76017-137">清除專案的預設組建︰</span><span class="sxs-lookup"><span data-stu-id="76017-137">Clean a default build of the project:</span></span>

  ```dotnetcli
  dotnet clean
  ```

* <span data-ttu-id="76017-138">清除使用發行組態來建置的專案︰</span><span class="sxs-lookup"><span data-stu-id="76017-138">Clean a project built using the Release configuration:</span></span>

  ```dotnetcli
  dotnet clean --configuration Release
  ```
