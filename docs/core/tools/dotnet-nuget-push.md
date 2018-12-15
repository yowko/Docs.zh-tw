---
title: dotnet nuget push 命令 - .NET Core CLI
description: dotnet nuget push 命令會將套件推送至伺服器並發行。
author: karann-msft
ms.date: 12/04/2018
ms.openlocfilehash: 090dbfbe3db83b2bb234867aed295ac416b27865
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143057"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="7ecd7-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="7ecd7-103">dotnet nuget push</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="7ecd7-104">名稱</span><span class="sxs-lookup"><span data-stu-id="7ecd7-104">Name</span></span>

<span data-ttu-id="7ecd7-105">`dotnet nuget push` - 將套件推送至伺服器並發行。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-105">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7ecd7-106">概要</span><span class="sxs-lookup"><span data-stu-id="7ecd7-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7ecd7-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="7ecd7-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7ecd7-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="7ecd7-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="7ecd7-109">說明</span><span class="sxs-lookup"><span data-stu-id="7ecd7-109">Description</span></span>

<span data-ttu-id="7ecd7-110">`dotnet nuget push` 命令會將套件推送至伺服器並發行。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-110">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="7ecd7-111">推送命令會使用在系統 NuGet 組態檔案或組態檔案鏈中找到的伺服器及認證詳細資料。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-111">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="7ecd7-112">如需組態檔的詳細資訊，請參閱[設定 NuGet 行為](/nuget/consume-packages/configuring-nuget-behavior)。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-112">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="7ecd7-113">NuGet 預設組態的取得方式如下：載入 *%AppData%\NuGet\NuGet.config* (Windows) 或 *$HOME/.local/share* (Linux/macOS)，接著從磁碟機根目錄開始直到目前目錄，載入其中的任何 *nuget.config* 或 *.nuget\nuget.config*。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-113">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="7ecd7-114">引數</span><span class="sxs-lookup"><span data-stu-id="7ecd7-114">Arguments</span></span>

* **`ROOT`**

  <span data-ttu-id="7ecd7-115">指定套件推送目標的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-115">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="7ecd7-116">選項</span><span class="sxs-lookup"><span data-stu-id="7ecd7-116">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7ecd7-117">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="7ecd7-117">.NET Core 2.x</span></span>](#tab/netcore2x)

* **`-d|--disable-buffering`**

  <span data-ttu-id="7ecd7-118">推送至 HTTP(S) 伺服器時停用緩衝處理以減少記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-118">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

* **`--force-english-output`**

  <span data-ttu-id="7ecd7-119">強制使用非變異英文文化特性來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-119">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

<span data-ttu-id="7ecd7-120">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-120">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="7ecd7-121">允許命令進行封鎖及要求對驗證之類的作業採取手動動作。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-121">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="7ecd7-122">自 .NET Core 2.2 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-122">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="7ecd7-123">伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-123">The API key for the server.</span></span>

* **`-n|--no-symbols`**

  <span data-ttu-id="7ecd7-124">不推送符號 (即使存在)。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-124">Doesn't push symbols (even if present).</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="7ecd7-125">不會將 "api/v2/package" 附加至來源 URL。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-125">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="7ecd7-126">自 .NET Core 2.1 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-126">Option available since .NET Core 2.1 SDK.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="7ecd7-127">指定伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-127">Specifies the server URL.</span></span> <span data-ttu-id="7ecd7-128">除非在 NuGet 組態檔中設定 `DefaultPushSource` 設定值，否則此選項為必要。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-128">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

* **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="7ecd7-129">符號伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-129">The API key for the symbol server.</span></span>

* **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="7ecd7-130">指定符號伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-130">Specifies the symbol server URL.</span></span>

* **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="7ecd7-131">指定推送至伺服器的逾時 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-131">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="7ecd7-132">預設為 300 秒 (5 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-132">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="7ecd7-133">指定 0 (零秒) 會套用預設值。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-133">Specifying 0 (zero seconds) applies the default value.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7ecd7-134">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="7ecd7-134">.NET Core 1.x</span></span>](#tab/netcore1x)

* **`-d|--disable-buffering`**

  <span data-ttu-id="7ecd7-135">推送至 HTTP(S) 伺服器時停用緩衝處理以減少記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-135">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

* **`--force-english-output`**

  <span data-ttu-id="7ecd7-136">強制使用非變異英文文化特性來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-136">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="7ecd7-137">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-137">Prints out a short help for the command.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="7ecd7-138">伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-138">The API key for the server.</span></span>

* **`-n|--no-symbols`**

  <span data-ttu-id="7ecd7-139">不推送符號 (即使存在)。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-139">Doesn't push symbols (even if present).</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="7ecd7-140">指定伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-140">Specifies the server URL.</span></span> <span data-ttu-id="7ecd7-141">除非在 NuGet 組態檔中設定 `DefaultPushSource` 設定值，否則此選項為必要。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-141">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

* **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="7ecd7-142">符號伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-142">The API key for the symbol server.</span></span>

* **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="7ecd7-143">指定符號伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-143">Specifies the symbol server URL.</span></span>

* **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="7ecd7-144">指定推送至伺服器的逾時 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-144">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="7ecd7-145">預設為 300 秒 (5 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-145">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="7ecd7-146">指定 0 (零秒) 會套用預設值。</span><span class="sxs-lookup"><span data-stu-id="7ecd7-146">Specifying 0 (zero seconds) applies the default value.</span></span>

---

## <a name="examples"></a><span data-ttu-id="7ecd7-147">範例</span><span class="sxs-lookup"><span data-stu-id="7ecd7-147">Examples</span></span>

* <span data-ttu-id="7ecd7-148">將 *foo.nupkg* 推送至預設推送來源，指定 API 金鑰：</span><span class="sxs-lookup"><span data-stu-id="7ecd7-148">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

  ```console
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

* <span data-ttu-id="7ecd7-149">將 *foo.nupkg* 推送至自訂推送來源 `https://customsource`，指定 API 金鑰：</span><span class="sxs-lookup"><span data-stu-id="7ecd7-149">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```console
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

* <span data-ttu-id="7ecd7-150">將 *foo.nupkg* 推送至預設推送來源：</span><span class="sxs-lookup"><span data-stu-id="7ecd7-150">Pushes *foo.nupkg* to the default push source:</span></span>

  ```console
  dotnet nuget push foo.nupkg
  ```

* <span data-ttu-id="7ecd7-151">將 *foo.symbols.nupkg* 推送至預設符號來源：</span><span class="sxs-lookup"><span data-stu-id="7ecd7-151">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```console
  dotnet nuget push foo.symbols.nupkg
  ```

* <span data-ttu-id="7ecd7-152">將 *foo.nupkg* 推送至預設推送來源，指定 360 秒逾時：</span><span class="sxs-lookup"><span data-stu-id="7ecd7-152">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

  ```console
  dotnet nuget push foo.nupkg --timeout 360
  ```

* <span data-ttu-id="7ecd7-153">將目前目錄中的所有 *.nupkg* 檔案推送至預設推送來源：</span><span class="sxs-lookup"><span data-stu-id="7ecd7-153">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

  ```console
  dotnet nuget push *.nupkg
  ```