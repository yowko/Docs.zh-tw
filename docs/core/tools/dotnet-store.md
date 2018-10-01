---
title: dotnet store 命令
description: "'dotnet store' 命令會在執行階段套件存放區中儲存指定的組件。"
author: bleroy
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: a12738d0cc8edcbb65d5b6fab6e7c8b209b0f4b5
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2018
ms.locfileid: "47208061"
---
# <a name="dotnet-store"></a><span data-ttu-id="b5e61-103">dotnet store</span><span class="sxs-lookup"><span data-stu-id="b5e61-103">dotnet store</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a><span data-ttu-id="b5e61-104">名稱</span><span class="sxs-lookup"><span data-stu-id="b5e61-104">Name</span></span>

<span data-ttu-id="b5e61-105">`dotnet store` - 會在[執行階段套件存放區](../deploying/runtime-store.md)中儲存指定的組件。</span><span class="sxs-lookup"><span data-stu-id="b5e61-105">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="b5e61-106">概要</span><span class="sxs-lookup"><span data-stu-id="b5e61-106">Synopsis</span></span>

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a><span data-ttu-id="b5e61-107">描述</span><span class="sxs-lookup"><span data-stu-id="b5e61-107">Description</span></span>

<span data-ttu-id="b5e61-108">`dotnet store` 會在[執行階段套件存放區](../deploying/runtime-store.md)中儲存指定的組件。</span><span class="sxs-lookup"><span data-stu-id="b5e61-108">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="b5e61-109">根據預設，會針對目標執行階段和架構最佳化組件。</span><span class="sxs-lookup"><span data-stu-id="b5e61-109">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="b5e61-110">如需詳細資訊，請參閱[執行階段套件存放區](../deploying/runtime-store.md)主題。</span><span class="sxs-lookup"><span data-stu-id="b5e61-110">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="b5e61-111">必要選項</span><span class="sxs-lookup"><span data-stu-id="b5e61-111">Required options</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="b5e61-112">指定[目標 Framework](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="b5e61-112">Specifies the [target framework](../../standard/frameworks.md).</span></span>

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="b5e61-113">「套件存放區資訊清單檔」是 XML 檔，包含要儲存的套件清單。</span><span class="sxs-lookup"><span data-stu-id="b5e61-113">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="b5e61-114">資訊清單檔的格式相容於 SDK 樣式專案格式。</span><span class="sxs-lookup"><span data-stu-id="b5e61-114">The format of the manifest file is compatible with the SDK-style project format.</span></span> <span data-ttu-id="b5e61-115">因此，參考所需套件的專案檔可以搭配 `-m|--manifest` 選項，將組件儲存在執行階段套件存放區中。</span><span class="sxs-lookup"><span data-stu-id="b5e61-115">So, a project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="b5e61-116">若要指定多個資訊清單檔，請為每個檔案重複選項和路徑。</span><span class="sxs-lookup"><span data-stu-id="b5e61-116">To specify multiple manifest files, repeat the option and path for each file.</span></span> <span data-ttu-id="b5e61-117">例如：`--manifest packages1.csproj --manifest packages2.csproj`。</span><span class="sxs-lookup"><span data-stu-id="b5e61-117">For example: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="b5e61-118">目標的[執行階段識別碼](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="b5e61-118">The [runtime identifier](../rid-catalog.md) to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="b5e61-119">選擇性的選項</span><span class="sxs-lookup"><span data-stu-id="b5e61-119">Optional options</span></span>

`--framework-version <FRAMEWORK_VERSION>`

<span data-ttu-id="b5e61-120">指定 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="b5e61-120">Specifies the .NET Core SDK version.</span></span> <span data-ttu-id="b5e61-121">此選項可讓您在 `-f|--framework` 選項指定的 Framework 之外，選取特定的 Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="b5e61-121">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

`-h|--help`

<span data-ttu-id="b5e61-122">顯示說明資訊。</span><span class="sxs-lookup"><span data-stu-id="b5e61-122">Shows help information.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="b5e61-123">指定執行階段套件存放區的路徑。</span><span class="sxs-lookup"><span data-stu-id="b5e61-123">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="b5e61-124">如未指定，則預設為使用者設定檔 .NET Core 安裝目錄的 *store* 子目錄。</span><span class="sxs-lookup"><span data-stu-id="b5e61-124">If not specified, it defaults to the *store* subdirectory of the user profile .NET Core installation directory.</span></span>

`--skip-optimization`

<span data-ttu-id="b5e61-125">略過最佳化階段。</span><span class="sxs-lookup"><span data-stu-id="b5e61-125">Skips the optimization phase.</span></span>

`--skip-symbols`

<span data-ttu-id="b5e61-126">略過符號產生。</span><span class="sxs-lookup"><span data-stu-id="b5e61-126">Skips symbol generation.</span></span> <span data-ttu-id="b5e61-127">目前，只能在 Windows 和 Linux 產生符號。</span><span class="sxs-lookup"><span data-stu-id="b5e61-127">Currently, you can only generate symbols on Windows and Linux.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="b5e61-128">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="b5e61-128">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b5e61-129">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="b5e61-129">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

<span data-ttu-id="b5e61-130">命令使用的工作目錄。</span><span class="sxs-lookup"><span data-stu-id="b5e61-130">The working directory used by the command.</span></span> <span data-ttu-id="b5e61-131">如未指定，則使用目前目錄的 *obj* 子目錄。</span><span class="sxs-lookup"><span data-stu-id="b5e61-131">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="b5e61-132">範例</span><span class="sxs-lookup"><span data-stu-id="b5e61-132">Examples</span></span>

<span data-ttu-id="b5e61-133">儲存 .NET Core 2.0.0 的 *packages.csproj* 專案中指定的套件：</span><span class="sxs-lookup"><span data-stu-id="b5e61-133">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

<span data-ttu-id="b5e61-134">儲存 *packages.csproj* 中指定的套件，不需要最佳化：</span><span class="sxs-lookup"><span data-stu-id="b5e61-134">Store the packages specified in the *packages.csproj* without optimization:</span></span>

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a><span data-ttu-id="b5e61-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5e61-135">See also</span></span>

* [<span data-ttu-id="b5e61-136">執行階段套件存放區</span><span class="sxs-lookup"><span data-stu-id="b5e61-136">Runtime package store</span></span>](../deploying/runtime-store.md)