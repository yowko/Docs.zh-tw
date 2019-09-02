---
title: dotnet nuget push 命令
description: dotnet nuget push 命令會將套件推送至伺服器並發行。
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 87557f606dead921961349fec4575394e6d359fd
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202542"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="41019-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="41019-103">dotnet nuget push</span></span>

<span data-ttu-id="41019-104">**本主題適用於：✓** .NET Core 1.x SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="41019-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="41019-105">名稱</span><span class="sxs-lookup"><span data-stu-id="41019-105">Name</span></span>

<span data-ttu-id="41019-106">`dotnet nuget push` - 將套件推送至伺服器並發行。</span><span class="sxs-lookup"><span data-stu-id="41019-106">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="41019-107">概要</span><span class="sxs-lookup"><span data-stu-id="41019-107">Synopsis</span></span>

```console
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

## <a name="description"></a><span data-ttu-id="41019-108">說明</span><span class="sxs-lookup"><span data-stu-id="41019-108">Description</span></span>

<span data-ttu-id="41019-109">`dotnet nuget push` 命令會將套件推送至伺服器並發行。</span><span class="sxs-lookup"><span data-stu-id="41019-109">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="41019-110">推送命令會使用在系統 NuGet 組態檔案或組態檔案鏈中找到的伺服器及認證詳細資料。</span><span class="sxs-lookup"><span data-stu-id="41019-110">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="41019-111">如需組態檔的詳細資訊，請參閱[設定 NuGet 行為](/nuget/consume-packages/configuring-nuget-behavior)。</span><span class="sxs-lookup"><span data-stu-id="41019-111">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="41019-112">NuGet 預設組態的取得方式如下：載入 *%AppData%\NuGet\NuGet.config* (Windows) 或 *$HOME/.local/share* (Linux/macOS)，接著從磁碟機根目錄開始直到目前目錄，載入其中的任何 *nuget.config* 或 *.nuget\nuget.config*。</span><span class="sxs-lookup"><span data-stu-id="41019-112">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="41019-113">引數</span><span class="sxs-lookup"><span data-stu-id="41019-113">Arguments</span></span>

* **`ROOT`**

  <span data-ttu-id="41019-114">指定套件推送目標的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="41019-114">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="41019-115">選項</span><span class="sxs-lookup"><span data-stu-id="41019-115">Options</span></span>

* **`-d|--disable-buffering`**

  <span data-ttu-id="41019-116">推送至 HTTP(S) 伺服器時停用緩衝處理以減少記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="41019-116">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

* **`--force-english-output`**

  <span data-ttu-id="41019-117">強制使用非變異英文文化特性來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="41019-117">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

<span data-ttu-id="41019-118">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="41019-118">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="41019-119">允許命令進行封鎖及要求對驗證之類的作業採取手動動作。</span><span class="sxs-lookup"><span data-stu-id="41019-119">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="41019-120">自 .NET Core 2.2 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="41019-120">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="41019-121">伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="41019-121">The API key for the server.</span></span>

* **`-n|--no-symbols`**

  <span data-ttu-id="41019-122">不推送符號 (即使存在)。</span><span class="sxs-lookup"><span data-stu-id="41019-122">Doesn't push symbols (even if present).</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="41019-123">不會將 "api/v2/package" 附加至來源 URL。</span><span class="sxs-lookup"><span data-stu-id="41019-123">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="41019-124">自 .NET Core 2.1 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="41019-124">Option available since .NET Core 2.1 SDK.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="41019-125">指定伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="41019-125">Specifies the server URL.</span></span> <span data-ttu-id="41019-126">除非在 NuGet 組態檔中設定 `DefaultPushSource` 設定值，否則此選項為必要。</span><span class="sxs-lookup"><span data-stu-id="41019-126">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

* **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="41019-127">符號伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="41019-127">The API key for the symbol server.</span></span>

* **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="41019-128">指定符號伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="41019-128">Specifies the symbol server URL.</span></span>

* **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="41019-129">指定推送至伺服器的逾時 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="41019-129">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="41019-130">預設為 300 秒 (5 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="41019-130">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="41019-131">指定 0 (零秒) 會套用預設值。</span><span class="sxs-lookup"><span data-stu-id="41019-131">Specifying 0 (zero seconds) applies the default value.</span></span>

## <a name="examples"></a><span data-ttu-id="41019-132">範例</span><span class="sxs-lookup"><span data-stu-id="41019-132">Examples</span></span>

* <span data-ttu-id="41019-133">將 *foo.nupkg* 推送至預設推送來源，指定 API 金鑰：</span><span class="sxs-lookup"><span data-stu-id="41019-133">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

  ```console
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

* <span data-ttu-id="41019-134">將 *foo.nupkg* 推送至自訂推送來源 `https://customsource`，指定 API 金鑰：</span><span class="sxs-lookup"><span data-stu-id="41019-134">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```console
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

* <span data-ttu-id="41019-135">將 *foo.nupkg* 推送至預設推送來源：</span><span class="sxs-lookup"><span data-stu-id="41019-135">Pushes *foo.nupkg* to the default push source:</span></span>

  ```console
  dotnet nuget push foo.nupkg
  ```

* <span data-ttu-id="41019-136">將 *foo.symbols.nupkg* 推送至預設符號來源：</span><span class="sxs-lookup"><span data-stu-id="41019-136">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```console
  dotnet nuget push foo.symbols.nupkg
  ```

* <span data-ttu-id="41019-137">將 *foo.nupkg* 推送至預設推送來源，指定 360 秒逾時：</span><span class="sxs-lookup"><span data-stu-id="41019-137">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

  ```console
  dotnet nuget push foo.nupkg --timeout 360
  ```

* <span data-ttu-id="41019-138">將目前目錄中的所有 *.nupkg* 檔案推送至預設推送來源：</span><span class="sxs-lookup"><span data-stu-id="41019-138">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

  ```console
  dotnet nuget push *.nupkg
  ```
  
  > [!NOTE]
  > <span data-ttu-id="41019-139">如果此命令無法運作，可能是舊版 SDK (.NET Core 2.1 SDK 及更舊版本) 中有 Bug 所致。</span><span class="sxs-lookup"><span data-stu-id="41019-139">If this command doesn't work, it might be due to a bug that existed in older versions of the SDK (.NET Core 2.1 SDK and earlier versions).</span></span>
  > <span data-ttu-id="41019-140">若要修正此問題，請升級您的 SDK 版本，或改為執行下列命令：`dotnet nuget push **/*.nupkg`</span><span class="sxs-lookup"><span data-stu-id="41019-140">To fix this, upgrade your SDK version or run the following command instead: `dotnet nuget push **/*.nupkg`</span></span>
