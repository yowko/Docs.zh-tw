---
title: dotnet store 命令
description: "'dotnet store' 命令會在執行階段套件存放區中儲存指定的組件。"
author: bleroy
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 6baa28256535d6a9d653d9df743cd3cdf45ab910
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-store"></a><span data-ttu-id="6cc29-103">dotnet store</span><span class="sxs-lookup"><span data-stu-id="6cc29-103">dotnet store</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a><span data-ttu-id="6cc29-104">名稱</span><span class="sxs-lookup"><span data-stu-id="6cc29-104">Name</span></span>

<span data-ttu-id="6cc29-105">`dotnet store` - 會在[執行階段套件存放區](../deploying/runtime-store.md)中儲存指定的組件。</span><span class="sxs-lookup"><span data-stu-id="6cc29-105">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="6cc29-106">概要</span><span class="sxs-lookup"><span data-stu-id="6cc29-106">Synopsis</span></span>

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a><span data-ttu-id="6cc29-107">描述</span><span class="sxs-lookup"><span data-stu-id="6cc29-107">Description</span></span>

<span data-ttu-id="6cc29-108">`dotnet store` 會在[執行階段套件存放區](../deploying/runtime-store.md)中儲存指定的組件。</span><span class="sxs-lookup"><span data-stu-id="6cc29-108">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="6cc29-109">根據預設，會針對目標執行階段和架構最佳化組件。</span><span class="sxs-lookup"><span data-stu-id="6cc29-109">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="6cc29-110">如需詳細資訊，請參閱[執行階段套件存放區](../deploying/runtime-store.md)主題。</span><span class="sxs-lookup"><span data-stu-id="6cc29-110">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="6cc29-111">必要選項</span><span class="sxs-lookup"><span data-stu-id="6cc29-111">Required options</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="6cc29-112">指定[目標 Framework](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="6cc29-112">Specifies the [target framework](../../standard/frameworks.md).</span></span>

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="6cc29-113">「套件存放區資訊清單檔」是 XML 檔，包含要儲存的套件清單。</span><span class="sxs-lookup"><span data-stu-id="6cc29-113">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="6cc29-114">資訊清單檔的格式相容於 *csproj* 格式。</span><span class="sxs-lookup"><span data-stu-id="6cc29-114">The format of the manifest file is compatible with the *csproj* format.</span></span> <span data-ttu-id="6cc29-115">因此，參考所需套件的 *csproj* 專案檔可以搭配 `-m|--manifest` 選項，將組件儲存在執行階段套件存放區中。</span><span class="sxs-lookup"><span data-stu-id="6cc29-115">So, a *csproj* project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="6cc29-116">若要指定多個資訊清單檔，請為每個檔案重複選項和路徑：`--manifest packages1.csproj --manifest packages2.csproj`。</span><span class="sxs-lookup"><span data-stu-id="6cc29-116">To specify multiple manifest files, repeat the option and path for each file: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="6cc29-117">目標的[執行階段識別碼](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="6cc29-117">The [runtime identifier](../rid-catalog.md) to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="6cc29-118">選擇性的選項</span><span class="sxs-lookup"><span data-stu-id="6cc29-118">Optional options</span></span>

`--framework-version <FRAMEWORK_VERSION>`

<span data-ttu-id="6cc29-119">指定 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="6cc29-119">Specifies the .NET Core SDK version.</span></span> <span data-ttu-id="6cc29-120">此選項可讓您在 `-f|--framework` 選項指定的 Framework 之外，選取特定的 Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="6cc29-120">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

`-h|--help`

<span data-ttu-id="6cc29-121">顯示說明資訊。</span><span class="sxs-lookup"><span data-stu-id="6cc29-121">Shows help information.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="6cc29-122">指定執行階段套件存放區的路徑。</span><span class="sxs-lookup"><span data-stu-id="6cc29-122">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="6cc29-123">如未指定，則預設為使用者設定檔 .NET Core 安裝目錄的 *store* 子目錄。</span><span class="sxs-lookup"><span data-stu-id="6cc29-123">If not specified, it defaults to the *store* subdirectory of the user profile .NET Core installation directory.</span></span>

`--skip-optimization`

<span data-ttu-id="6cc29-124">略過最佳化階段。</span><span class="sxs-lookup"><span data-stu-id="6cc29-124">Skips the optimization phase.</span></span>

`--skip-symbols`

<span data-ttu-id="6cc29-125">略過符號產生。</span><span class="sxs-lookup"><span data-stu-id="6cc29-125">Skips symbol generation.</span></span> <span data-ttu-id="6cc29-126">目前，只能在 Windows 和 Linux 產生符號。</span><span class="sxs-lookup"><span data-stu-id="6cc29-126">Currently, you can only generate symbols on Windows and Linux.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="6cc29-127">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="6cc29-127">Sets the verbosity level of the command.</span></span> <span data-ttu-id="6cc29-128">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="6cc29-128">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

<span data-ttu-id="6cc29-129">命令使用的工作目錄。</span><span class="sxs-lookup"><span data-stu-id="6cc29-129">The working directory used by the command.</span></span> <span data-ttu-id="6cc29-130">如未指定，則使用目前目錄的 *obj* 子目錄。</span><span class="sxs-lookup"><span data-stu-id="6cc29-130">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="6cc29-131">範例</span><span class="sxs-lookup"><span data-stu-id="6cc29-131">Examples</span></span>

<span data-ttu-id="6cc29-132">儲存 .NET Core 2.0.0 的 *packages.csproj* 專案中指定的套件：</span><span class="sxs-lookup"><span data-stu-id="6cc29-132">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

<span data-ttu-id="6cc29-133">儲存 *packages.csproj* 中指定的套件，不需要最佳化：</span><span class="sxs-lookup"><span data-stu-id="6cc29-133">Store the packages specified in the *packages.csproj* without optimization:</span></span>

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a><span data-ttu-id="6cc29-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6cc29-134">See also</span></span>

[<span data-ttu-id="6cc29-135">執行階段套件存放區</span><span class="sxs-lookup"><span data-stu-id="6cc29-135">Runtime package store</span></span>](../deploying/runtime-store.md)   
