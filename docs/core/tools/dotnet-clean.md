---
title: dotnet clean 命令
description: dotnet clean 命令會清除目前的目錄。
ms.date: 12/04/2018
ms.openlocfilehash: a25b7930794795e3dff5051a8ca1dd1b9c261dfd
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169855"
---
# <a name="dotnet-clean"></a><span data-ttu-id="a7b44-103">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="a7b44-103">dotnet clean</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a7b44-104">名稱</span><span class="sxs-lookup"><span data-stu-id="a7b44-104">Name</span></span>

<span data-ttu-id="a7b44-105">`dotnet clean` - 清除專案的輸出。</span><span class="sxs-lookup"><span data-stu-id="a7b44-105">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a7b44-106">概要</span><span class="sxs-lookup"><span data-stu-id="a7b44-106">Synopsis</span></span>

```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a><span data-ttu-id="a7b44-107">說明</span><span class="sxs-lookup"><span data-stu-id="a7b44-107">Description</span></span>

<span data-ttu-id="a7b44-108">`dotnet clean` 命令會清除前一個組建的輸出。</span><span class="sxs-lookup"><span data-stu-id="a7b44-108">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="a7b44-109">它會實作為 [MSBuild 目標](/visualstudio/msbuild/msbuild-targets)，因此命令在執行的時候會評估專案。</span><span class="sxs-lookup"><span data-stu-id="a7b44-109">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="a7b44-110">只會清除在建置期間建立的輸出。</span><span class="sxs-lookup"><span data-stu-id="a7b44-110">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="a7b44-111">中繼 (*obj*) 和最後輸出 (*bin*) 這兩個資料夾都會清除。</span><span class="sxs-lookup"><span data-stu-id="a7b44-111">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="a7b44-112">引數</span><span class="sxs-lookup"><span data-stu-id="a7b44-112">Arguments</span></span>

`PROJECT`

<span data-ttu-id="a7b44-113">要清除的 MSBuild 專案。</span><span class="sxs-lookup"><span data-stu-id="a7b44-113">The MSBuild project to clean.</span></span> <span data-ttu-id="a7b44-114">如果未指定專案檔，MSBuild 會搜尋目前工作目錄中副檔名結尾為 *proj* 的檔案，並使用該檔案。</span><span class="sxs-lookup"><span data-stu-id="a7b44-114">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="a7b44-115">選項</span><span class="sxs-lookup"><span data-stu-id="a7b44-115">Options</span></span>

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="a7b44-116">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="a7b44-116">Defines the build configuration.</span></span> <span data-ttu-id="a7b44-117">預設值為 `Debug`。</span><span class="sxs-lookup"><span data-stu-id="a7b44-117">The default value is `Debug`.</span></span> <span data-ttu-id="a7b44-118">如果在建置階段指定此選項，清除時才需要使用它。</span><span class="sxs-lookup"><span data-stu-id="a7b44-118">This option is only required when cleaning if you specified it during build time.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="a7b44-119">在建置時間指定的[架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="a7b44-119">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="a7b44-120">架構必須定義於[專案檔](csproj.md)中。</span><span class="sxs-lookup"><span data-stu-id="a7b44-120">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="a7b44-121">如果在建置階段指定架構，則您必須在清除時指定該架構。</span><span class="sxs-lookup"><span data-stu-id="a7b44-121">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

* **`-h|--help`**

  <span data-ttu-id="a7b44-122">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="a7b44-122">Prints out a short help for the command.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="a7b44-123">在其中放置建置輸出的目錄。</span><span class="sxs-lookup"><span data-stu-id="a7b44-123">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="a7b44-124">如果您在建置專案時指定架構，請搭配輸出目錄參數來指定 `-f|--framework <FRAMEWORK>` 參數。</span><span class="sxs-lookup"><span data-stu-id="a7b44-124">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="a7b44-125">清除指定執行階段的輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="a7b44-125">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="a7b44-126">建立[獨立性部署 (SCD)](../deploying/index.md#self-contained-deployments-scd) 時會使用此選項。</span><span class="sxs-lookup"><span data-stu-id="a7b44-126">This is used when a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd) was created.</span></span> <span data-ttu-id="a7b44-127">自 .NET Core 2.0 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="a7b44-127">Option available since .NET Core 2.0 SDK.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="a7b44-128">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="a7b44-128">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a7b44-129">允許的層級為 q[uiet]、m[inimal]、n[ormal]、d[etailed] 和 diag[nostic]。</span><span class="sxs-lookup"><span data-stu-id="a7b44-129">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

## <a name="examples"></a><span data-ttu-id="a7b44-130">範例</span><span class="sxs-lookup"><span data-stu-id="a7b44-130">Examples</span></span>

* <span data-ttu-id="a7b44-131">清除專案的預設組建︰</span><span class="sxs-lookup"><span data-stu-id="a7b44-131">Clean a default build of the project:</span></span>

  ```console
  dotnet clean
  ```

* <span data-ttu-id="a7b44-132">清除使用發行組態來建置的專案︰</span><span class="sxs-lookup"><span data-stu-id="a7b44-132">Clean a project built using the Release configuration:</span></span>

  ```console
  dotnet clean --configuration Release
  ```