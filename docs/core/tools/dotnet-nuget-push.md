---
title: dotnet nuget push 命令
description: dotnet nuget push 命令會將套件推送至伺服器並發行。
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 1e7831de4c041591b3602e405418f89f1d1d27d1
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895462"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="2f71c-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="2f71c-103">dotnet nuget push</span></span>

<span data-ttu-id="2f71c-104">**本文適用于：** ✔️ .net CORE 2.x SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="2f71c-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="2f71c-105">名稱</span><span class="sxs-lookup"><span data-stu-id="2f71c-105">Name</span></span>

<span data-ttu-id="2f71c-106">`dotnet nuget push` - 將套件推送至伺服器並發行。</span><span class="sxs-lookup"><span data-stu-id="2f71c-106">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2f71c-107">概要</span><span class="sxs-lookup"><span data-stu-id="2f71c-107">Synopsis</span></span>

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output]
    [--interactive] [-k|--api-key <API_KEY>] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source <SOURCE>] [--skip-duplicate]
    [-sk|--symbol-api-key <API_KEY>] [-ss|--symbol-source <SOURCE>]
    [-t|--timeout <TIMEOUT>]

dotnet nuget push -h|--help
```

## <a name="description"></a><span data-ttu-id="2f71c-108">描述</span><span class="sxs-lookup"><span data-stu-id="2f71c-108">Description</span></span>

<span data-ttu-id="2f71c-109">`dotnet nuget push` 命令會將套件推送至伺服器並發行。</span><span class="sxs-lookup"><span data-stu-id="2f71c-109">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="2f71c-110">推送命令會使用在系統 NuGet 組態檔案或組態檔案鏈中找到的伺服器及認證詳細資料。</span><span class="sxs-lookup"><span data-stu-id="2f71c-110">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="2f71c-111">如需組態檔的詳細資訊，請參閱[設定 NuGet 行為](/nuget/consume-packages/configuring-nuget-behavior)。</span><span class="sxs-lookup"><span data-stu-id="2f71c-111">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="2f71c-112">NuGet 預設組態的取得方式如下：載入 *%AppData%\NuGet\NuGet.config* (Windows) 或 *$HOME/.local/share* (Linux/macOS)，接著從磁碟機根目錄開始直到目前目錄，載入其中的任何 *nuget.config* 或 *.nuget\nuget.config*。</span><span class="sxs-lookup"><span data-stu-id="2f71c-112">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

<span data-ttu-id="2f71c-113">命令會推送現有的封裝。</span><span class="sxs-lookup"><span data-stu-id="2f71c-113">The command pushes an existing package.</span></span> <span data-ttu-id="2f71c-114">它不會建立封裝。</span><span class="sxs-lookup"><span data-stu-id="2f71c-114">It doesn't create a package.</span></span> <span data-ttu-id="2f71c-115">若要建立封裝，請[`dotnet pack`](dotnet-pack.md)使用。</span><span class="sxs-lookup"><span data-stu-id="2f71c-115">To create a package, use [`dotnet pack`](dotnet-pack.md).</span></span>

## <a name="arguments"></a><span data-ttu-id="2f71c-116">引數</span><span class="sxs-lookup"><span data-stu-id="2f71c-116">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="2f71c-117">指定套件推送目標的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="2f71c-117">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="2f71c-118">選項</span><span class="sxs-lookup"><span data-stu-id="2f71c-118">Options</span></span>

- **`-d|--disable-buffering`**

  <span data-ttu-id="2f71c-119">推送至 HTTP(S) 伺服器時停用緩衝處理以減少記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="2f71c-119">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

- **`--force-english-output`**

  <span data-ttu-id="2f71c-120">強制使用非變異英文文化特性來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="2f71c-120">Forces the application to run using an invariant, English-based culture.</span></span>

- **`-h|--help`**

  <span data-ttu-id="2f71c-121">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="2f71c-121">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="2f71c-122">允許命令進行封鎖及要求對驗證之類的作業採取手動動作。</span><span class="sxs-lookup"><span data-stu-id="2f71c-122">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="2f71c-123">自 .NET Core 2.2 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-123">Option available since .NET Core 2.2 SDK.</span></span>

- **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="2f71c-124">伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="2f71c-124">The API key for the server.</span></span>

- **`-n|--no-symbols`**

  <span data-ttu-id="2f71c-125">不推送符號 (即使存在)。</span><span class="sxs-lookup"><span data-stu-id="2f71c-125">Doesn't push symbols (even if present).</span></span>

- **`--no-service-endpoint`**

  <span data-ttu-id="2f71c-126">不會將 "api/v2/package" 附加至來源 URL。</span><span class="sxs-lookup"><span data-stu-id="2f71c-126">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="2f71c-127">自 .NET Core 2.1 SDK 起可用的選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-127">Option available since .NET Core 2.1 SDK.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="2f71c-128">指定伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="2f71c-128">Specifies the server URL.</span></span> <span data-ttu-id="2f71c-129">除非在 NuGet 組態檔中設定 `DefaultPushSource` 設定值，否則此選項為必要。</span><span class="sxs-lookup"><span data-stu-id="2f71c-129">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

- **`--skip-duplicate`**

  <span data-ttu-id="2f71c-130">將多個封裝推送至 HTTP （S）伺服器時，會將任何409衝突回應視為警告，讓推送可以繼續進行。</span><span class="sxs-lookup"><span data-stu-id="2f71c-130">When pushing multiple packages to an HTTP(S) server, treats any 409 Conflict response as a warning so that the push can continue.</span></span> <span data-ttu-id="2f71c-131">自 .NET Core 3.1 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="2f71c-131">Available since .NET Core 3.1 SDK.</span></span>

- **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="2f71c-132">符號伺服器的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="2f71c-132">The API key for the symbol server.</span></span>

- **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="2f71c-133">指定符號伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="2f71c-133">Specifies the symbol server URL.</span></span>

- **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="2f71c-134">指定推送至伺服器的逾時 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="2f71c-134">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="2f71c-135">預設為 300 秒 (5 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="2f71c-135">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="2f71c-136">指定 0 (零秒) 會套用預設值。</span><span class="sxs-lookup"><span data-stu-id="2f71c-136">Specifying 0 (zero seconds) applies the default value.</span></span>

## <a name="examples"></a><span data-ttu-id="2f71c-137">範例</span><span class="sxs-lookup"><span data-stu-id="2f71c-137">Examples</span></span>

- <span data-ttu-id="2f71c-138">將*foo. nupkg*推送至預設推送來源，並指定 API 金鑰：</span><span class="sxs-lookup"><span data-stu-id="2f71c-138">Push *foo.nupkg* to the default push source, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

- <span data-ttu-id="2f71c-139">將*foo. nupkg*推送至官方 NuGet 伺服器，並指定 API 金鑰：</span><span class="sxs-lookup"><span data-stu-id="2f71c-139">Push *foo.nupkg* to the official NuGet server, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://api.nuget.org/v3/index.json
  ```
  
  * <span data-ttu-id="2f71c-140">將 *foo.nupkg* 推送至自訂推送來源 `https://customsource`，指定 API 金鑰：</span><span class="sxs-lookup"><span data-stu-id="2f71c-140">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

- <span data-ttu-id="2f71c-141">將*foo. nupkg*推送至預設推送來源：</span><span class="sxs-lookup"><span data-stu-id="2f71c-141">Push *foo.nupkg* to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

- <span data-ttu-id="2f71c-142">將*foo. nupkg*推送至預設符號來源：</span><span class="sxs-lookup"><span data-stu-id="2f71c-142">Push *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

- <span data-ttu-id="2f71c-143">將*foo. nupkg*推送至預設推送來源，並指定360秒的超時時間：</span><span class="sxs-lookup"><span data-stu-id="2f71c-143">Push *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

- <span data-ttu-id="2f71c-144">將目前目錄中的所有*nupkg*檔案推送至預設推送來源：</span><span class="sxs-lookup"><span data-stu-id="2f71c-144">Push all *.nupkg* files in the current directory to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg
  ```

  > [!NOTE]
  > <span data-ttu-id="2f71c-145">如果此命令無法運作，可能是舊版 SDK (.NET Core 2.1 SDK 及更舊版本) 中有 Bug 所致。</span><span class="sxs-lookup"><span data-stu-id="2f71c-145">If this command doesn't work, it might be due to a bug that existed in older versions of the SDK (.NET Core 2.1 SDK and earlier versions).</span></span>
  > <span data-ttu-id="2f71c-146">若要修正此問題，請升級您的 SDK 版本，或改為執行下列命令：`dotnet nuget push **/*.nupkg`</span><span class="sxs-lookup"><span data-stu-id="2f71c-146">To fix this, upgrade your SDK version or run the following command instead: `dotnet nuget push **/*.nupkg`</span></span>

- <span data-ttu-id="2f71c-147">推送所有*的 nupkg*檔案，即使 HTTP （S）伺服器傳回409衝突回應也一樣：</span><span class="sxs-lookup"><span data-stu-id="2f71c-147">Push all *.nupkg* files even if a 409 Conflict response is returned by an HTTP(S) server:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg --skip-duplicate
  ```

- <span data-ttu-id="2f71c-148">將目前目錄中的所有*nupkg*檔案推送至本機摘要目錄：</span><span class="sxs-lookup"><span data-stu-id="2f71c-148">Push all *.nupkg* files in the current directory to a local feed directory:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg -s c:\mydir
  ```

  <span data-ttu-id="2f71c-149">此命令不會將封裝儲存在階層式資料夾結構中，這是建議用來優化效能的方式。</span><span class="sxs-lookup"><span data-stu-id="2f71c-149">This command doesn't store packages in a hierarchical folder structure, which is recommended to optimize performance.</span></span> <span data-ttu-id="2f71c-150">如需詳細資訊，請參閱[本機](/nuget/hosting-packages/local-feeds)摘要。</span><span class="sxs-lookup"><span data-stu-id="2f71c-150">For more information, see [Local feeds](/nuget/hosting-packages/local-feeds).</span></span>  
