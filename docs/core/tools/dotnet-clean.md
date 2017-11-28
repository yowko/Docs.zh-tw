---
title: "dotnet clean 命令 - .NET Core CLI"
description: "dotnet clean 命令會清除目前的目錄。"
author: mairaw
ms.author: mairaw
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 4836f07ec1a8b59c343b4d0181587e602f61d45e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-clean"></a><span data-ttu-id="7d236-103">dotnet-clean</span><span class="sxs-lookup"><span data-stu-id="7d236-103">dotnet-clean</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="7d236-104">名稱</span><span class="sxs-lookup"><span data-stu-id="7d236-104">Name</span></span>

<span data-ttu-id="7d236-105">`dotnet clean` - 清除專案的輸出。</span><span class="sxs-lookup"><span data-stu-id="7d236-105">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7d236-106">概要</span><span class="sxs-lookup"><span data-stu-id="7d236-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7d236-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="7d236-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7d236-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="7d236-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-v|--verbosity]
dotnet clean [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="7d236-109">說明</span><span class="sxs-lookup"><span data-stu-id="7d236-109">Description</span></span>

<span data-ttu-id="7d236-110">`dotnet clean` 命令會清除前一個組建的輸出。</span><span class="sxs-lookup"><span data-stu-id="7d236-110">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="7d236-111">它會實作為 [MSBuild 目標](/visualstudio/msbuild/msbuild-targets)，因此命令在執行的時候會評估專案。</span><span class="sxs-lookup"><span data-stu-id="7d236-111">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="7d236-112">只會清除在建置期間建立的輸出。</span><span class="sxs-lookup"><span data-stu-id="7d236-112">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="7d236-113">中繼 (*obj*) 和最後輸出 (*bin*) 這兩個資料夾都會清除。</span><span class="sxs-lookup"><span data-stu-id="7d236-113">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="7d236-114">引數</span><span class="sxs-lookup"><span data-stu-id="7d236-114">Arguments</span></span>

`PROJECT`

<span data-ttu-id="7d236-115">要清除的 MSBuild 專案。</span><span class="sxs-lookup"><span data-stu-id="7d236-115">The MSBuild project to clean.</span></span> <span data-ttu-id="7d236-116">如果未指定專案檔，MSBuild 會搜尋目前工作目錄中副檔名結尾為 *proj* 的檔案，並使用該檔案。</span><span class="sxs-lookup"><span data-stu-id="7d236-116">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="7d236-117">選項</span><span class="sxs-lookup"><span data-stu-id="7d236-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7d236-118">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="7d236-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="7d236-119">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="7d236-119">Defines the build configuration.</span></span> <span data-ttu-id="7d236-120">預設值是 `Debug`。</span><span class="sxs-lookup"><span data-stu-id="7d236-120">The default value is `Debug`.</span></span> <span data-ttu-id="7d236-121">如果在建置階段指定此選項，清除時才需要使用它。</span><span class="sxs-lookup"><span data-stu-id="7d236-121">This option is only required when cleaning if you specified it during build time.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="7d236-122">在建置時間指定的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="7d236-122">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="7d236-123">架構必須定義於[專案檔](csproj.md)中。</span><span class="sxs-lookup"><span data-stu-id="7d236-123">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="7d236-124">如果在建置階段指定架構，則您必須在清除時指定該架構。</span><span class="sxs-lookup"><span data-stu-id="7d236-124">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

`-h|--help`

<span data-ttu-id="7d236-125">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="7d236-125">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="7d236-126">在其中放置建置輸出的目錄。</span><span class="sxs-lookup"><span data-stu-id="7d236-126">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="7d236-127">如果您在建置專案時指定架構，請搭配輸出目錄參數來指定 `-f|--framework <FRAMEWORK>` 參數。</span><span class="sxs-lookup"><span data-stu-id="7d236-127">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="7d236-128">清除指定執行階段的輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="7d236-128">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="7d236-129">建立[獨立性部署 (SCD)](../deploying/index.md#self-contained-deployments-scd) 時會使用此選項。</span><span class="sxs-lookup"><span data-stu-id="7d236-129">This is used when a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd) was created.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="7d236-130">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="7d236-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="7d236-131">允許的層級為 q[uiet]、m[inimal]、n[ormal]、d[etailed] 和 diag[nostic]。</span><span class="sxs-lookup"><span data-stu-id="7d236-131">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7d236-132">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="7d236-132">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="7d236-133">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="7d236-133">Defines the build configuration.</span></span> <span data-ttu-id="7d236-134">預設值是 `Debug`。</span><span class="sxs-lookup"><span data-stu-id="7d236-134">The default value is `Debug`.</span></span> <span data-ttu-id="7d236-135">如果在建置階段指定此選項，清除時才需要使用它。</span><span class="sxs-lookup"><span data-stu-id="7d236-135">This option is only required when cleaning if you specified it during build time.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="7d236-136">在建置時間指定的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="7d236-136">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="7d236-137">架構必須定義於[專案檔](csproj.md)中。</span><span class="sxs-lookup"><span data-stu-id="7d236-137">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="7d236-138">如果在建置階段指定架構，則您必須在清除時指定該架構。</span><span class="sxs-lookup"><span data-stu-id="7d236-138">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

`-h|--help`

<span data-ttu-id="7d236-139">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="7d236-139">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="7d236-140">在其中放置建置輸出的目錄。</span><span class="sxs-lookup"><span data-stu-id="7d236-140">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="7d236-141">如果您在建置專案時指定架構，請搭配輸出目錄參數來指定 `-f|--framework <FRAMEWORK>` 參數。</span><span class="sxs-lookup"><span data-stu-id="7d236-141">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="7d236-142">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="7d236-142">Sets the verbosity level of the command.</span></span> <span data-ttu-id="7d236-143">允許的層級為 q[uiet]、m[inimal]、n[ormal]、d[etailed] 和 diag[nostic]。</span><span class="sxs-lookup"><span data-stu-id="7d236-143">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

---

## <a name="examples"></a><span data-ttu-id="7d236-144">範例</span><span class="sxs-lookup"><span data-stu-id="7d236-144">Examples</span></span>

<span data-ttu-id="7d236-145">清除專案的預設組建︰</span><span class="sxs-lookup"><span data-stu-id="7d236-145">Clean a default build of the project:</span></span>

`dotnet clean`

<span data-ttu-id="7d236-146">清除使用發行組態來建置的專案︰</span><span class="sxs-lookup"><span data-stu-id="7d236-146">Clean a project built using the Release configuration:</span></span>

`dotnet clean --configuration Release`
