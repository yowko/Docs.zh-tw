---
title: dotnet nuget push 命令 - .NET Core CLI
description: dotnet nuget push 命令會將套件推送至伺服器並發行。
author: karann-msft
ms.author: mairaw
ms.date: 09/04/2018
ms.openlocfilehash: 23d27cef29008955850f9ed9f4a8baed9e7ad982
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44186457"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="38005-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="38005-103">dotnet nuget push</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="38005-104">名稱</span><span class="sxs-lookup"><span data-stu-id="38005-104">Name</span></span>

<span data-ttu-id="38005-105">`dotnet nuget push` - 將套件推送至伺服器並發行。</span><span class="sxs-lookup"><span data-stu-id="38005-105">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="38005-106">概要</span><span class="sxs-lookup"><span data-stu-id="38005-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="38005-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="38005-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="38005-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="38005-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="38005-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="38005-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="38005-110">描述</span><span class="sxs-lookup"><span data-stu-id="38005-110">Description</span></span>

<span data-ttu-id="38005-111">`dotnet nuget push` 命令會將套件推送至伺服器並發行。</span><span class="sxs-lookup"><span data-stu-id="38005-111">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="38005-112">推送命令會使用在系統 NuGet 組態檔案或組態檔案鏈中找到的伺服器及認證詳細資料。</span><span class="sxs-lookup"><span data-stu-id="38005-112">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="38005-113">如需組態檔的詳細資訊，請參閱[設定 NuGet 行為](/nuget/consume-packages/configuring-nuget-behavior)。</span><span class="sxs-lookup"><span data-stu-id="38005-113">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="38005-114">NuGet 預設組態的取得方式如下：載入 *%AppData%\NuGet\NuGet.config* (Windows) 或 *$HOME/.local/share* (Linux/macOS)，接著從磁碟機根目錄開始直到目前目錄，載入其中的任何 *nuget.config* 或 *.nuget\nuget.config*。</span><span class="sxs-lookup"><span data-stu-id="38005-114">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="38005-115">引數</span><span class="sxs-lookup"><span data-stu-id="38005-115">Arguments</span></span>

`ROOT`

<span data-ttu-id="38005-116">指定套件推送目標的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="38005-116">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="38005-117">選項</span><span class="sxs-lookup"><span data-stu-id="38005-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="38005-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="38005-118">.NET Core 2.1</span></span>](#tab/netcore21)

`-d|--disable-buffering`

<span data-ttu-id="38005-119">推送至 HTTP(S) 伺服器時停用緩衝處理以減少記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="38005-119">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

`--force-english-output`

<span data-ttu-id="38005-120">強制使用非變異英文文化特性來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="38005-120">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="38005-121">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="38005-121">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="38005-122">伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="38005-122">The API key for the server.</span></span>

`-n|--no-symbols`

<span data-ttu-id="38005-123">不推送符號 (即使存在)。</span><span class="sxs-lookup"><span data-stu-id="38005-123">Doesn't push symbols (even if present).</span></span>

`--no-service-endpoint`

<span data-ttu-id="38005-124">不會將 "api/v2/package" 附加至來源 URL。</span><span class="sxs-lookup"><span data-stu-id="38005-124">Doesn't append "api/v2/package" to the source URL.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="38005-125">指定伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="38005-125">Specifies the server URL.</span></span> <span data-ttu-id="38005-126">除非在 NuGet 組態檔中設定 `DefaultPushSource` 設定值，否則此選項為必要。</span><span class="sxs-lookup"><span data-stu-id="38005-126">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`-sk|--symbol-api-key <API_KEY>`

<span data-ttu-id="38005-127">符號伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="38005-127">The API key for the symbol server.</span></span>

`-ss|--symbol-source <SOURCE>`

<span data-ttu-id="38005-128">指定符號伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="38005-128">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="38005-129">指定推送至伺服器的逾時 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="38005-129">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="38005-130">預設為 300 秒 (5 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="38005-130">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="38005-131">指定 0 (零秒) 會套用預設值。</span><span class="sxs-lookup"><span data-stu-id="38005-131">Specifying 0 (zero seconds) applies the default value.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="38005-132">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="38005-132">.NET Core 2.0</span></span>](#tab/netcore20)

`-d|--disable-buffering`

<span data-ttu-id="38005-133">推送至 HTTP(S) 伺服器時停用緩衝處理以減少記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="38005-133">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

`--force-english-output`

<span data-ttu-id="38005-134">強制使用非變異英文文化特性來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="38005-134">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="38005-135">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="38005-135">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="38005-136">伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="38005-136">The API key for the server.</span></span>

`-n|--no-symbols`

<span data-ttu-id="38005-137">不推送符號 (即使存在)。</span><span class="sxs-lookup"><span data-stu-id="38005-137">Doesn't push symbols (even if present).</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="38005-138">指定伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="38005-138">Specifies the server URL.</span></span> <span data-ttu-id="38005-139">除非在 NuGet 組態檔中設定 `DefaultPushSource` 設定值，否則此選項為必要。</span><span class="sxs-lookup"><span data-stu-id="38005-139">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`-sk|--symbol-api-key <API_KEY>`

<span data-ttu-id="38005-140">符號伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="38005-140">The API key for the symbol server.</span></span>

`-ss|--symbol-source <SOURCE>`

<span data-ttu-id="38005-141">指定符號伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="38005-141">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="38005-142">指定推送至伺服器的逾時 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="38005-142">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="38005-143">預設為 300 秒 (5 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="38005-143">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="38005-144">指定 0 (零秒) 會套用預設值。</span><span class="sxs-lookup"><span data-stu-id="38005-144">Specifying 0 (zero seconds) applies the default value.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="38005-145">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="38005-145">.NET Core 1.x</span></span>](#tab/netcore1x)

`-d|--disable-buffering`

<span data-ttu-id="38005-146">推送至 HTTP(S) 伺服器時停用緩衝處理以減少記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="38005-146">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

`--force-english-output`

<span data-ttu-id="38005-147">強制使用非變異英文文化特性來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="38005-147">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="38005-148">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="38005-148">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="38005-149">伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="38005-149">The API key for the server.</span></span>

`-n|--no-symbols`

<span data-ttu-id="38005-150">不推送符號 (即使存在)。</span><span class="sxs-lookup"><span data-stu-id="38005-150">Doesn't push symbols (even if present).</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="38005-151">指定伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="38005-151">Specifies the server URL.</span></span> <span data-ttu-id="38005-152">除非在 NuGet 組態檔中設定 `DefaultPushSource` 設定值，否則此選項為必要。</span><span class="sxs-lookup"><span data-stu-id="38005-152">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`-sk|--symbol-api-key <API_KEY>`

<span data-ttu-id="38005-153">符號伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="38005-153">The API key for the symbol server.</span></span>

`-ss|--symbol-source <SOURCE>`

<span data-ttu-id="38005-154">指定符號伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="38005-154">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="38005-155">指定推送至伺服器的逾時 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="38005-155">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="38005-156">預設為 300 秒 (5 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="38005-156">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="38005-157">指定 0 (零秒) 會套用預設值。</span><span class="sxs-lookup"><span data-stu-id="38005-157">Specifying 0 (zero seconds) applies the default value.</span></span>

---

## <a name="examples"></a><span data-ttu-id="38005-158">範例</span><span class="sxs-lookup"><span data-stu-id="38005-158">Examples</span></span>

<span data-ttu-id="38005-159">將 *foo.nupkg* 推送至預設推送來源，指定 API 金鑰：</span><span class="sxs-lookup"><span data-stu-id="38005-159">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

<span data-ttu-id="38005-160">將 *foo.nupkg* 推送至自訂推送來源 `http://customsource`，指定 API 金鑰：</span><span class="sxs-lookup"><span data-stu-id="38005-160">Push *foo.nupkg* to the custom push source `http://customsource`, specifying an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/`

<span data-ttu-id="38005-161">將 *foo.nupkg* 推送至預設推送來源：</span><span class="sxs-lookup"><span data-stu-id="38005-161">Pushes *foo.nupkg* to the default push source:</span></span>

`dotnet nuget push foo.nupkg`

<span data-ttu-id="38005-162">將 *foo.symbols.nupkg* 推送至預設符號來源：</span><span class="sxs-lookup"><span data-stu-id="38005-162">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

`dotnet nuget push foo.symbols.nupkg`

<span data-ttu-id="38005-163">將 *foo.nupkg* 推送至預設推送來源，指定 360 秒逾時：</span><span class="sxs-lookup"><span data-stu-id="38005-163">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

`dotnet nuget push foo.nupkg --timeout 360`

<span data-ttu-id="38005-164">將目前目錄中的所有 *.nupkg* 檔案推送至預設推送來源：</span><span class="sxs-lookup"><span data-stu-id="38005-164">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

`dotnet nuget push *.nupkg`
