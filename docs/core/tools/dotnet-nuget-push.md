---
title: dotnet nuget push 命令
description: dotnet nuget push 命令會將套件推送至伺服器並發行。
author: karann-msft
ms.date: 12/04/2019
ms.openlocfilehash: a483c559dee8b4a82cc2c792f5c2c5e4a8ff3f87
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733103"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="e8924-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="e8924-103">dotnet nuget push</span></span>

<span data-ttu-id="e8924-104">**本文適用于：** ✔️ .net CORE 1.x SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="e8924-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="e8924-105">Name</span><span class="sxs-lookup"><span data-stu-id="e8924-105">Name</span></span>

<span data-ttu-id="e8924-106">`dotnet nuget push` - 將套件推送至伺服器並發行。</span><span class="sxs-lookup"><span data-stu-id="e8924-106">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e8924-107">概要</span><span class="sxs-lookup"><span data-stu-id="e8924-107">Synopsis</span></span>

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [--skip-duplicate] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

## <a name="description"></a><span data-ttu-id="e8924-108">描述</span><span class="sxs-lookup"><span data-stu-id="e8924-108">Description</span></span>

<span data-ttu-id="e8924-109">`dotnet nuget push` 命令會將套件推送至伺服器並發行。</span><span class="sxs-lookup"><span data-stu-id="e8924-109">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="e8924-110">推送命令會使用在系統 NuGet 組態檔案或組態檔案鏈中找到的伺服器及認證詳細資料。</span><span class="sxs-lookup"><span data-stu-id="e8924-110">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="e8924-111">如需組態檔的詳細資訊，請參閱[設定 NuGet 行為](/nuget/consume-packages/configuring-nuget-behavior)。</span><span class="sxs-lookup"><span data-stu-id="e8924-111">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="e8924-112">NuGet 預設組態的取得方式如下：載入 *%AppData%\NuGet\NuGet.config* (Windows) 或 *$HOME/.local/share* (Linux/macOS)，接著從磁碟機根目錄開始直到目前目錄，載入其中的任何 *nuget.config* 或 *.nuget\nuget.config*。</span><span class="sxs-lookup"><span data-stu-id="e8924-112">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="e8924-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="e8924-113">Arguments</span></span>

* **`ROOT`**

  <span data-ttu-id="e8924-114">指定套件推送目標的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="e8924-114">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="e8924-115">選項</span><span class="sxs-lookup"><span data-stu-id="e8924-115">Options</span></span>

* **`-d|--disable-buffering`**

  <span data-ttu-id="e8924-116">推送至 HTTP(S) 伺服器時停用緩衝處理以減少記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="e8924-116">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

* **`--force-english-output`**

  <span data-ttu-id="e8924-117">強制使用非變異英文文化特性來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="e8924-117">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="e8924-118">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="e8924-118">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="e8924-119">允許命令進行封鎖及要求對驗證之類的作業採取手動動作。</span><span class="sxs-lookup"><span data-stu-id="e8924-119">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="e8924-120">自 .NET Core 2.2 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="e8924-120">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="e8924-121">伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="e8924-121">The API key for the server.</span></span>

* **`-n|--no-symbols`**

  <span data-ttu-id="e8924-122">不推送符號 (即使存在)。</span><span class="sxs-lookup"><span data-stu-id="e8924-122">Doesn't push symbols (even if present).</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="e8924-123">不會將 "api/v2/package" 附加至來源 URL。</span><span class="sxs-lookup"><span data-stu-id="e8924-123">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="e8924-124">自 .NET Core 2.1 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="e8924-124">Option available since .NET Core 2.1 SDK.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="e8924-125">指定伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="e8924-125">Specifies the server URL.</span></span> <span data-ttu-id="e8924-126">除非在 NuGet 組態檔中設定 `DefaultPushSource` 設定值，否則此選項為必要。</span><span class="sxs-lookup"><span data-stu-id="e8924-126">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

* **`--skip-duplicate`**

  <span data-ttu-id="e8924-127">將多個封裝推送至 HTTP （S）伺服器時，會將任何409衝突回應視為警告，讓推送可以繼續進行。</span><span class="sxs-lookup"><span data-stu-id="e8924-127">When pushing multiple packages to an HTTP(S) server, treats any 409 Conflict response as a warning so that the push can continue.</span></span> <span data-ttu-id="e8924-128">自 .NET Core 3.1 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="e8924-128">Available since .NET Core 3.1 SDK.</span></span>

* **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="e8924-129">符號伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="e8924-129">The API key for the symbol server.</span></span>

* **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="e8924-130">指定符號伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="e8924-130">Specifies the symbol server URL.</span></span>

* **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="e8924-131">指定推送至伺服器的逾時 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="e8924-131">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="e8924-132">預設為 300 秒 (5 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="e8924-132">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="e8924-133">指定 0 (零秒) 會套用預設值。</span><span class="sxs-lookup"><span data-stu-id="e8924-133">Specifying 0 (zero seconds) applies the default value.</span></span>

## <a name="examples"></a><span data-ttu-id="e8924-134">範例</span><span class="sxs-lookup"><span data-stu-id="e8924-134">Examples</span></span>

* <span data-ttu-id="e8924-135">將 *foo.nupkg* 推送至預設推送來源，指定 API 金鑰：</span><span class="sxs-lookup"><span data-stu-id="e8924-135">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

* <span data-ttu-id="e8924-136">將 *foo.nupkg* 推送至自訂推送來源 `https://customsource`，指定 API 金鑰：</span><span class="sxs-lookup"><span data-stu-id="e8924-136">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

* <span data-ttu-id="e8924-137">將 *foo.nupkg* 推送至預設推送來源：</span><span class="sxs-lookup"><span data-stu-id="e8924-137">Pushes *foo.nupkg* to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

* <span data-ttu-id="e8924-138">將 *foo.symbols.nupkg* 推送至預設符號來源：</span><span class="sxs-lookup"><span data-stu-id="e8924-138">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

* <span data-ttu-id="e8924-139">將 *foo.nupkg* 推送至預設推送來源，指定 360 秒逾時：</span><span class="sxs-lookup"><span data-stu-id="e8924-139">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

* <span data-ttu-id="e8924-140">將目前目錄中的所有 *.nupkg* 檔案推送至預設推送來源：</span><span class="sxs-lookup"><span data-stu-id="e8924-140">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg
  ```

  > [!NOTE]
  > <span data-ttu-id="e8924-141">如果此命令無法運作，可能是舊版 SDK (.NET Core 2.1 SDK 及更舊版本) 中有 Bug 所致。</span><span class="sxs-lookup"><span data-stu-id="e8924-141">If this command doesn't work, it might be due to a bug that existed in older versions of the SDK (.NET Core 2.1 SDK and earlier versions).</span></span>
  > <span data-ttu-id="e8924-142">若要修正此問題，請升級您的 SDK 版本，或改為執行下列命令：`dotnet nuget push **/*.nupkg`</span><span class="sxs-lookup"><span data-stu-id="e8924-142">To fix this, upgrade your SDK version or run the following command instead: `dotnet nuget push **/*.nupkg`</span></span>

* <span data-ttu-id="e8924-143">會推送所有*的 nupkg*檔案，即使 HTTP （S）伺服器傳回409衝突回應也一樣：</span><span class="sxs-lookup"><span data-stu-id="e8924-143">Pushes all *.nupkg* files even if a 409 Conflict response is returned by an HTTP(S) server:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg --skip-duplicate
  ```
