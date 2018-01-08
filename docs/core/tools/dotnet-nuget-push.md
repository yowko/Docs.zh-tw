---
title: "dotnet nuget push 命令 - .NET Core CLI"
description: "dotnet nuget push 命令會將套件推送至伺服器並發行。"
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 52aac5ff1862397616287a77eac063582703d509
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="bc0f4-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="bc0f4-103">dotnet nuget push</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="bc0f4-104">名稱</span><span class="sxs-lookup"><span data-stu-id="bc0f4-104">Name</span></span>

<span data-ttu-id="bc0f4-105">`dotnet nuget push` - 將套件推送至伺服器並發行。</span><span class="sxs-lookup"><span data-stu-id="bc0f4-105">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="bc0f4-106">概要</span><span class="sxs-lookup"><span data-stu-id="bc0f4-106">Synopsis</span></span>

`dotnet nuget push [<ROOT>] [-s|--source] [-ss|--symbol-source] [-t|--timeout] [-k|--api-key] [-sk|--symbol-api-key] [-d|--disable-buffering] [-n|--no-symbols] [--force-english-output] [-h|--help]`

## <a name="description"></a><span data-ttu-id="bc0f4-107">描述</span><span class="sxs-lookup"><span data-stu-id="bc0f4-107">Description</span></span>

<span data-ttu-id="bc0f4-108">`dotnet nuget push` 命令會將套件推送至伺服器並發行。</span><span class="sxs-lookup"><span data-stu-id="bc0f4-108">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="bc0f4-109">推送命令會使用在系統 NuGet 組態檔案或組態檔案鏈中找到的伺服器及認證詳細資料。</span><span class="sxs-lookup"><span data-stu-id="bc0f4-109">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="bc0f4-110">如需組態檔的詳細資訊，請參閱[設定 NuGet 行為](/nuget/consume-packages/configuring-nuget-behavior)。</span><span class="sxs-lookup"><span data-stu-id="bc0f4-110">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="bc0f4-111">NuGet 預設組態的取得方式如下：載入 *%AppData%\NuGet\NuGet.config* (Windows) 或 *$HOME/.local/share* (Linux/macOS)，接著從磁碟機根目錄開始直到目前目錄，載入其中的任何 *nuget.config* 或 *.nuget\nuget.config*。</span><span class="sxs-lookup"><span data-stu-id="bc0f4-111">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="bc0f4-112">引數</span><span class="sxs-lookup"><span data-stu-id="bc0f4-112">Arguments</span></span>

`ROOT`

<span data-ttu-id="bc0f4-113">指定套件和 API 金鑰的路徑，以推送套件至伺服器。</span><span class="sxs-lookup"><span data-stu-id="bc0f4-113">Specify the path to the package and your API key to push the package to the server.</span></span>

## <a name="options"></a><span data-ttu-id="bc0f4-114">選項</span><span class="sxs-lookup"><span data-stu-id="bc0f4-114">Options</span></span>

`-h|--help`

<span data-ttu-id="bc0f4-115">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="bc0f4-115">Prints out a short help for the command.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="bc0f4-116">指定伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="bc0f4-116">Specifies the server URL.</span></span> <span data-ttu-id="bc0f4-117">除非在 NuGet 組態檔中設定 `DefaultPushSource` 設定值，否則此選項為必要。</span><span class="sxs-lookup"><span data-stu-id="bc0f4-117">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`--symbol-source <SOURCE>`

<span data-ttu-id="bc0f4-118">指定符號伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="bc0f4-118">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="bc0f4-119">指定推送至伺服器的逾時 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="bc0f4-119">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="bc0f4-120">預設為 300 秒 (5 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="bc0f4-120">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="bc0f4-121">指定 0 (零秒) 會套用預設值。</span><span class="sxs-lookup"><span data-stu-id="bc0f4-121">Specifying 0 (zero seconds) applies the default value.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="bc0f4-122">伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="bc0f4-122">The API key for the server.</span></span>

`--symbol-api-key <API_KEY>`

<span data-ttu-id="bc0f4-123">符號伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="bc0f4-123">The API key for the symbol server.</span></span>

`-d|--disable-buffering`

<span data-ttu-id="bc0f4-124">推送至 HTTP(S) 伺服器時停用緩衝處理以減少記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="bc0f4-124">Disables buffering when pushing to an HTTP(S) server to decrease memory usage.</span></span>

`-n|--no-symbols`

<span data-ttu-id="bc0f4-125">不推送符號 (即使存在)。</span><span class="sxs-lookup"><span data-stu-id="bc0f4-125">Doesn't push symbols (even if present).</span></span>

`--force-english-output`

<span data-ttu-id="bc0f4-126">強制所有記錄的輸出採用英文。</span><span class="sxs-lookup"><span data-stu-id="bc0f4-126">Forces all logged output in English.</span></span>

## <a name="examples"></a><span data-ttu-id="bc0f4-127">範例</span><span class="sxs-lookup"><span data-stu-id="bc0f4-127">Examples</span></span>

<span data-ttu-id="bc0f4-128">若有 API 金鑰，將 *foo.nupkg* 推送至預設推送來源：</span><span class="sxs-lookup"><span data-stu-id="bc0f4-128">Pushes *foo.nupkg* to the default push source, providing an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

<span data-ttu-id="bc0f4-129">若有 API 金鑰，將 *foo.nupkg* 推送至自訂推送來源 `http://customsource`：</span><span class="sxs-lookup"><span data-stu-id="bc0f4-129">Push *foo.nupkg* to the custom push source `http://customsource`, providing an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/`

<span data-ttu-id="bc0f4-130">將 *foo.nupkg* 推送至預設推送來源：</span><span class="sxs-lookup"><span data-stu-id="bc0f4-130">Pushes *foo.nupkg* to the default push source:</span></span>

`dotnet nuget push foo.nupkg`

<span data-ttu-id="bc0f4-131">將 *foo.symbols.nupkg* 推送至預設符號來源：</span><span class="sxs-lookup"><span data-stu-id="bc0f4-131">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

`dotnet nuget push foo.symbols.nupkg`

<span data-ttu-id="bc0f4-132">將 *foo.nupkg* 推送至預設推送來源，指定 360 秒逾時：</span><span class="sxs-lookup"><span data-stu-id="bc0f4-132">Pushes *foo.nupkg* to the default push source, specifying a 360 second timeout:</span></span>

`dotnet nuget push foo.nupkg --timeout 360`

<span data-ttu-id="bc0f4-133">將目前目錄中的所有 *.nupkg* 檔案推送至預設推送來源：</span><span class="sxs-lookup"><span data-stu-id="bc0f4-133">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

`dotnet nuget push *.nupkg`

<span data-ttu-id="bc0f4-134">將目前目錄中的所有 *.nupkg* 檔案推送至預設推送來源，指定自訂組態檔 *./config/My.Config*：</span><span class="sxs-lookup"><span data-stu-id="bc0f4-134">Pushes all *.nupkg* files in the current directory to the default push source, specifying a custom config file *./config/My.Config*:</span></span>

`dotnet nuget push *.nupkg --config-file ./config/My.Config`
