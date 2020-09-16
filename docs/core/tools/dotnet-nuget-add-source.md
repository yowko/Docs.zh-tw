---
title: dotnet nuget add source 命令
description: Dotnet nuget add source 命令會將新的套件來源新增至您的 NuGet 設定檔。
ms.date: 03/20/2020
ms.openlocfilehash: b847d987de2d88cb3452d32d1bc84232a1e20b6e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537969"
---
# <a name="dotnet-nuget-add-source"></a><span data-ttu-id="8372c-103">dotnet nuget add source</span><span class="sxs-lookup"><span data-stu-id="8372c-103">dotnet nuget add source</span></span>

<span data-ttu-id="8372c-104">本文**適用于：** ✔️ .net CORE 3.1.200 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="8372c-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="8372c-105">名稱</span><span class="sxs-lookup"><span data-stu-id="8372c-105">Name</span></span>

<span data-ttu-id="8372c-106">`dotnet nuget add source` -新增 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="8372c-106">`dotnet nuget add source` - Add a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8372c-107">概要</span><span class="sxs-lookup"><span data-stu-id="8372c-107">Synopsis</span></span>

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name <SOURCE_NAME>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget add source -h|--help
```

## <a name="description"></a><span data-ttu-id="8372c-108">描述</span><span class="sxs-lookup"><span data-stu-id="8372c-108">Description</span></span>

<span data-ttu-id="8372c-109">此 `dotnet nuget add source` 命令會將新的套件來源新增至您的 NuGet 設定檔。</span><span class="sxs-lookup"><span data-stu-id="8372c-109">The `dotnet nuget add source` command adds a new package source to your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="8372c-110">引數</span><span class="sxs-lookup"><span data-stu-id="8372c-110">Arguments</span></span>

- **`PACKAGE_SOURCE_PATH`**

  <span data-ttu-id="8372c-111">套件來源的路徑。</span><span class="sxs-lookup"><span data-stu-id="8372c-111">Path to the package source.</span></span>

## <a name="options"></a><span data-ttu-id="8372c-112">選項</span><span class="sxs-lookup"><span data-stu-id="8372c-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="8372c-113">NuGet 設定檔案。</span><span class="sxs-lookup"><span data-stu-id="8372c-113">The NuGet configuration file.</span></span> <span data-ttu-id="8372c-114">如果指定，則只會使用來自此檔案的設定。</span><span class="sxs-lookup"><span data-stu-id="8372c-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="8372c-115">如果未指定，將會使用目前目錄中的設定檔階層。</span><span class="sxs-lookup"><span data-stu-id="8372c-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="8372c-116">如需詳細資訊，請參閱 [常見的 NuGet](/nuget/consume-packages/configuring-nuget-behavior)設定。</span><span class="sxs-lookup"><span data-stu-id="8372c-116">For more information, see [Common NuGet Configurations](/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`-n|--name <SOURCE_NAME>`**

  <span data-ttu-id="8372c-117">來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="8372c-117">Name of the source.</span></span>

- **`-p|--password <PASSWORD>`**

  <span data-ttu-id="8372c-118">連接到已驗證的來源時，所要使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="8372c-118">Password to be used when connecting to an authenticated source.</span></span>

- **`--store-password-in-clear-text`**

  <span data-ttu-id="8372c-119">藉由停用密碼加密，啟用儲存便攜套件來源認證。</span><span class="sxs-lookup"><span data-stu-id="8372c-119">Enables storing portable package source credentials by disabling password encryption.</span></span>

- **`-u|--username <USER>`**

  <span data-ttu-id="8372c-120">連接到已驗證的來源時，所要使用的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="8372c-120">Username to be used when connecting to an authenticated source.</span></span>

- **`--valid-authentication-types <TYPES>`**

  <span data-ttu-id="8372c-121">此來源的有效驗證類型清單（以逗號分隔）。</span><span class="sxs-lookup"><span data-stu-id="8372c-121">Comma-separated list of valid authentication types for this source.</span></span> <span data-ttu-id="8372c-122">將此設定為， `basic` 如果伺服器通告 NTLM 或 Negotiate，而且您的認證必須使用基本機制傳送，例如，搭配內部部署 Azure DevOps Server 使用 PAT。</span><span class="sxs-lookup"><span data-stu-id="8372c-122">Set this to `basic` if the server advertises NTLM or Negotiate and your credentials must be sent using the Basic mechanism, for instance when using a PAT with on-premises Azure DevOps Server.</span></span> <span data-ttu-id="8372c-123">其他有效的值包括 `negotiate` 、 `kerberos` 、 `ntlm` 和 `digest` ，但這些值不太可能很有用。</span><span class="sxs-lookup"><span data-stu-id="8372c-123">Other valid values include `negotiate`, `kerberos`, `ntlm`, and `digest`, but these values are unlikely to be useful.</span></span>

## <a name="examples"></a><span data-ttu-id="8372c-124">範例</span><span class="sxs-lookup"><span data-stu-id="8372c-124">Examples</span></span>

- <span data-ttu-id="8372c-125">新增 `nuget.org` 為來源：</span><span class="sxs-lookup"><span data-stu-id="8372c-125">Add `nuget.org` as a source:</span></span>

  ```dotnetcli
  dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org
  ```

- <span data-ttu-id="8372c-126">新增 `c:\packages` 為本機來源：</span><span class="sxs-lookup"><span data-stu-id="8372c-126">Add `c:\packages` as a local source:</span></span>

  ```dotnetcli
  dotnet nuget add source c:\packages
  ```

- <span data-ttu-id="8372c-127">新增需要驗證的來源：</span><span class="sxs-lookup"><span data-stu-id="8372c-127">Add a source that needs authentication:</span></span>

  ```dotnetcli
  dotnet nuget add source https://someServer/myTeam -n myTeam -u myUsername -p myPassword --store-password-in-clear-text
  ```

- <span data-ttu-id="8372c-128">新增需要驗證的來源 (然後 go 安裝認證提供者) ：</span><span class="sxs-lookup"><span data-stu-id="8372c-128">Add a source that needs authentication (then go install credential provider):</span></span>

  ```dotnetcli
  dotnet nuget add source https://azureartifacts.microsoft.com/myTeam -n myTeam
  ```

## <a name="see-also"></a><span data-ttu-id="8372c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8372c-129">See also</span></span>

- [<span data-ttu-id="8372c-130">NuGet.config 檔案中的套件來源區段</span><span class="sxs-lookup"><span data-stu-id="8372c-130">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="8372c-131">來源命令 ( # A0) </span><span class="sxs-lookup"><span data-stu-id="8372c-131">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
