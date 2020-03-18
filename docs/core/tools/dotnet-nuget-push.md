---
title: dotnet nuget push 命令
description: dotnet nuget push 命令會將套件推送至伺服器並發行。
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: d4ef8e58908fe488c712debff3b313ac0908b43e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503667"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="b8312-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="b8312-103">dotnet nuget push</span></span>

<span data-ttu-id="b8312-104">**本文適用于：✔️** .NET Core 2.x SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="b8312-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="b8312-105">名稱</span><span class="sxs-lookup"><span data-stu-id="b8312-105">Name</span></span>

<span data-ttu-id="b8312-106">`dotnet nuget push` - 將套件推送至伺服器並發行。</span><span class="sxs-lookup"><span data-stu-id="b8312-106">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b8312-107">概要</span><span class="sxs-lookup"><span data-stu-id="b8312-107">Synopsis</span></span>

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [--skip-duplicate] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

## <a name="description"></a><span data-ttu-id="b8312-108">描述</span><span class="sxs-lookup"><span data-stu-id="b8312-108">Description</span></span>

<span data-ttu-id="b8312-109">`dotnet nuget push` 命令會將套件推送至伺服器並發行。</span><span class="sxs-lookup"><span data-stu-id="b8312-109">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="b8312-110">推送命令會使用在系統 NuGet 組態檔案或組態檔案鏈中找到的伺服器及認證詳細資料。</span><span class="sxs-lookup"><span data-stu-id="b8312-110">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="b8312-111">如需組態檔的詳細資訊，請參閱[設定 NuGet 行為](/nuget/consume-packages/configuring-nuget-behavior)。</span><span class="sxs-lookup"><span data-stu-id="b8312-111">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="b8312-112">NuGet 預設組態的取得方式如下：載入 *%AppData%\NuGet\NuGet.config* (Windows) 或 *$HOME/.local/share* (Linux/macOS)，接著從磁碟機根目錄開始直到目前目錄，載入其中的任何 *nuget.config* 或 *.nuget\nuget.config*。</span><span class="sxs-lookup"><span data-stu-id="b8312-112">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="b8312-113">引數</span><span class="sxs-lookup"><span data-stu-id="b8312-113">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="b8312-114">指定套件推送目標的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="b8312-114">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="b8312-115">選項。</span><span class="sxs-lookup"><span data-stu-id="b8312-115">Options</span></span>

- **`-d|--disable-buffering`**

  <span data-ttu-id="b8312-116">推送至 HTTP(S) 伺服器時停用緩衝處理以減少記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="b8312-116">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

- **`--force-english-output`**

  <span data-ttu-id="b8312-117">強制使用非變異英文文化特性來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="b8312-117">Forces the application to run using an invariant, English-based culture.</span></span>

- **`-h|--help`**

  <span data-ttu-id="b8312-118">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="b8312-118">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="b8312-119">允許命令進行封鎖及要求對驗證之類的作業採取手動動作。</span><span class="sxs-lookup"><span data-stu-id="b8312-119">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="b8312-120">自 .NET Core 2.2 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="b8312-120">Option available since .NET Core 2.2 SDK.</span></span>

- **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="b8312-121">伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="b8312-121">The API key for the server.</span></span>

- **`-n|--no-symbols`**

  <span data-ttu-id="b8312-122">不推送符號 (即使存在)。</span><span class="sxs-lookup"><span data-stu-id="b8312-122">Doesn't push symbols (even if present).</span></span>

- **`--no-service-endpoint`**

  <span data-ttu-id="b8312-123">不會將 "api/v2/package" 附加至來源 URL。</span><span class="sxs-lookup"><span data-stu-id="b8312-123">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="b8312-124">自 .NET Core 2.1 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="b8312-124">Option available since .NET Core 2.1 SDK.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="b8312-125">指定伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="b8312-125">Specifies the server URL.</span></span> <span data-ttu-id="b8312-126">除非在 NuGet 組態檔中設定 `DefaultPushSource` 設定值，否則此選項為必要。</span><span class="sxs-lookup"><span data-stu-id="b8312-126">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

- **`--skip-duplicate`**

  <span data-ttu-id="b8312-127">將多個包推送到 HTTP（S） 伺服器時，將任何 409 衝突回應視為警告，以便推送可以繼續。</span><span class="sxs-lookup"><span data-stu-id="b8312-127">When pushing multiple packages to an HTTP(S) server, treats any 409 Conflict response as a warning so that the push can continue.</span></span> <span data-ttu-id="b8312-128">自 .NET 核心 3.1 SDK 以來可用。</span><span class="sxs-lookup"><span data-stu-id="b8312-128">Available since .NET Core 3.1 SDK.</span></span>

- **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="b8312-129">符號伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="b8312-129">The API key for the symbol server.</span></span>

- **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="b8312-130">指定符號伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="b8312-130">Specifies the symbol server URL.</span></span>

- **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="b8312-131">指定推送至伺服器的逾時 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="b8312-131">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="b8312-132">預設為 300 秒 (5 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="b8312-132">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="b8312-133">指定 0 (零秒) 會套用預設值。</span><span class="sxs-lookup"><span data-stu-id="b8312-133">Specifying 0 (zero seconds) applies the default value.</span></span>

## <a name="examples"></a><span data-ttu-id="b8312-134">範例</span><span class="sxs-lookup"><span data-stu-id="b8312-134">Examples</span></span>

- <span data-ttu-id="b8312-135">將 *foo.nupkg* 推送至預設推送來源，指定 API 金鑰：</span><span class="sxs-lookup"><span data-stu-id="b8312-135">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

- <span data-ttu-id="b8312-136">將*foo.nupkg*推送到正式的 NuGet 伺服器，指定 API 金鑰：</span><span class="sxs-lookup"><span data-stu-id="b8312-136">Push *foo.nupkg* to the official NuGet server, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://api.nuget.org/v3/index.json
  ```
  
  * <span data-ttu-id="b8312-137">將 *foo.nupkg* 推送至自訂推送來源 `https://customsource`，指定 API 金鑰：</span><span class="sxs-lookup"><span data-stu-id="b8312-137">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

- <span data-ttu-id="b8312-138">將 *foo.nupkg* 推送至預設推送來源：</span><span class="sxs-lookup"><span data-stu-id="b8312-138">Pushes *foo.nupkg* to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

- <span data-ttu-id="b8312-139">將 *foo.symbols.nupkg* 推送至預設符號來源：</span><span class="sxs-lookup"><span data-stu-id="b8312-139">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

- <span data-ttu-id="b8312-140">將 *foo.nupkg* 推送至預設推送來源，指定 360 秒逾時：</span><span class="sxs-lookup"><span data-stu-id="b8312-140">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

- <span data-ttu-id="b8312-141">將目前目錄中的所有 *.nupkg* 檔案推送至預設推送來源：</span><span class="sxs-lookup"><span data-stu-id="b8312-141">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg
  ```

  > [!NOTE]
  > <span data-ttu-id="b8312-142">如果此命令無法運作，可能是舊版 SDK (.NET Core 2.1 SDK 及更舊版本) 中有 Bug 所致。</span><span class="sxs-lookup"><span data-stu-id="b8312-142">If this command doesn't work, it might be due to a bug that existed in older versions of the SDK (.NET Core 2.1 SDK and earlier versions).</span></span>
  > <span data-ttu-id="b8312-143">若要修正此問題，請升級您的 SDK 版本，或改為執行下列命令：`dotnet nuget push **/*.nupkg`</span><span class="sxs-lookup"><span data-stu-id="b8312-143">To fix this, upgrade your SDK version or run the following command instead: `dotnet nuget push **/*.nupkg`</span></span>

- <span data-ttu-id="b8312-144">即使 HTTP（S） 伺服器返回 409 衝突回應，也會推送所有 *.nupkg*檔：</span><span class="sxs-lookup"><span data-stu-id="b8312-144">Pushes all *.nupkg* files even if a 409 Conflict response is returned by an HTTP(S) server:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg --skip-duplicate
  ```
