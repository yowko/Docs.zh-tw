---
title: dotnet nuget 更新來源命令
description: Dotnet nuget 更新來源命令會更新您 NuGet 設定檔中的現有來源。
ms.date: 03/20/2020
ms.openlocfilehash: a8658c78c095ad4b9272d97200e1d6466cbe658b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537850"
---
# <a name="dotnet-nuget-update-source"></a><span data-ttu-id="3e655-103">dotnet nuget update source</span><span class="sxs-lookup"><span data-stu-id="3e655-103">dotnet nuget update source</span></span>

<span data-ttu-id="3e655-104">本文**適用于：** ✔️ .net CORE 3.1.200 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="3e655-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="3e655-105">名稱</span><span class="sxs-lookup"><span data-stu-id="3e655-105">Name</span></span>

<span data-ttu-id="3e655-106">`dotnet nuget update source` -更新 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="3e655-106">`dotnet nuget update source` - Update a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3e655-107">概要</span><span class="sxs-lookup"><span data-stu-id="3e655-107">Synopsis</span></span>

```dotnetcli
dotnet nuget update source <NAME> [--source <SOURCE>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget update source -h|--help
```

## <a name="description"></a><span data-ttu-id="3e655-108">描述</span><span class="sxs-lookup"><span data-stu-id="3e655-108">Description</span></span>

<span data-ttu-id="3e655-109">此 `dotnet nuget update source` 命令會更新您 NuGet 設定檔中的現有來源。</span><span class="sxs-lookup"><span data-stu-id="3e655-109">The `dotnet nuget update source` command updates an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="3e655-110">引數</span><span class="sxs-lookup"><span data-stu-id="3e655-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="3e655-111">來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="3e655-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="3e655-112">選項</span><span class="sxs-lookup"><span data-stu-id="3e655-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="3e655-113">NuGet 設定檔案。</span><span class="sxs-lookup"><span data-stu-id="3e655-113">The NuGet configuration file.</span></span> <span data-ttu-id="3e655-114">如果指定，則只會使用來自此檔案的設定。</span><span class="sxs-lookup"><span data-stu-id="3e655-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="3e655-115">如果未指定，將會使用目前目錄中的設定檔階層。</span><span class="sxs-lookup"><span data-stu-id="3e655-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="3e655-116">如需詳細資訊，請參閱 [常見的 NuGet](/nuget/consume-packages/configuring-nuget-behavior)設定。</span><span class="sxs-lookup"><span data-stu-id="3e655-116">For more information, see [Common NuGet Configurations](/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`-p|--password <PASSWORD>`**

  <span data-ttu-id="3e655-117">連接到已驗證的來源時，所要使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="3e655-117">Password to be used when connecting to an authenticated source.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="3e655-118">套件來源的路徑。</span><span class="sxs-lookup"><span data-stu-id="3e655-118">Path to the package source.</span></span>

- **`--store-password-in-clear-text`**

  <span data-ttu-id="3e655-119">藉由停用密碼加密，啟用儲存便攜套件來源認證。</span><span class="sxs-lookup"><span data-stu-id="3e655-119">Enables storing portable package source credentials by disabling password encryption.</span></span>

- **`-u|--username <USER>`**

  <span data-ttu-id="3e655-120">連接到已驗證的來源時，所要使用的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="3e655-120">Username to be used when connecting to an authenticated source.</span></span>

- **`--valid-authentication-types <TYPES>`**

  <span data-ttu-id="3e655-121">此來源的有效驗證類型清單（以逗號分隔）。</span><span class="sxs-lookup"><span data-stu-id="3e655-121">Comma-separated list of valid authentication types for this source.</span></span> <span data-ttu-id="3e655-122">將此設定為， `basic` 如果伺服器通告 NTLM 或 Negotiate，而且您的認證必須使用基本機制傳送，例如，搭配內部部署 Azure DevOps Server 使用 PAT。</span><span class="sxs-lookup"><span data-stu-id="3e655-122">Set this to `basic` if the server advertises NTLM or Negotiate and your credentials must be sent using the Basic mechanism, for instance when using a PAT with on-premises Azure DevOps Server.</span></span> <span data-ttu-id="3e655-123">其他有效的值包括 `negotiate` 、 `kerberos` 、 `ntlm` 和 `digest` ，但這些值不太可能很有用。</span><span class="sxs-lookup"><span data-stu-id="3e655-123">Other valid values include `negotiate`, `kerberos`, `ntlm`, and `digest`, but these values are unlikely to be useful.</span></span>

## <a name="examples"></a><span data-ttu-id="3e655-124">範例</span><span class="sxs-lookup"><span data-stu-id="3e655-124">Examples</span></span>

- <span data-ttu-id="3e655-125">以下列名稱更新來源 `mySource` ：</span><span class="sxs-lookup"><span data-stu-id="3e655-125">Update a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget update source mySource --source c:\packages
  ```

## <a name="see-also"></a><span data-ttu-id="3e655-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e655-126">See also</span></span>

- [<span data-ttu-id="3e655-127">NuGet.config 檔案中的套件來源區段</span><span class="sxs-lookup"><span data-stu-id="3e655-127">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="3e655-128">來源命令 ( # A0) </span><span class="sxs-lookup"><span data-stu-id="3e655-128">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
