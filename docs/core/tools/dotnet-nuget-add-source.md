---
title: 點網 nuget 添加源命令
description: dotnet nuget 添加源命令向 NuGet 設定檔添加新的包源。
ms.date: 03/20/2020
ms.openlocfilehash: c1e398699c7482a69b750cde718e6f9178b5c4bd
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148565"
---
# <a name="dotnet-nuget-add-source"></a><span data-ttu-id="74dd7-103">點網 nuget 添加源</span><span class="sxs-lookup"><span data-stu-id="74dd7-103">dotnet nuget add source</span></span>

<span data-ttu-id="74dd7-104">**本文適用于：✔️** .NET Core 3.1.200 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="74dd7-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="74dd7-105">名稱</span><span class="sxs-lookup"><span data-stu-id="74dd7-105">Name</span></span>

<span data-ttu-id="74dd7-106">`dotnet nuget add source`- 添加 NuGet 源。</span><span class="sxs-lookup"><span data-stu-id="74dd7-106">`dotnet nuget add source` - Add a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="74dd7-107">概要</span><span class="sxs-lookup"><span data-stu-id="74dd7-107">Synopsis</span></span>

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name] [--username]
    [--password] [--store-password-in-clear-text] [--valid-authentication-types]
    [--configfile]
dotnet nuget add source [-h|--help]
```

## <a name="description"></a><span data-ttu-id="74dd7-108">描述</span><span class="sxs-lookup"><span data-stu-id="74dd7-108">Description</span></span>

<span data-ttu-id="74dd7-109">該`dotnet nuget add source`命令向 NuGet 設定檔添加新的包源。</span><span class="sxs-lookup"><span data-stu-id="74dd7-109">The `dotnet nuget add source` command adds a new package source to your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="74dd7-110">引數</span><span class="sxs-lookup"><span data-stu-id="74dd7-110">Arguments</span></span>

- **`PACKAGE_SOURCE_PATH`**

  <span data-ttu-id="74dd7-111">包源的路徑。</span><span class="sxs-lookup"><span data-stu-id="74dd7-111">Path to the package source.</span></span>

## <a name="options"></a><span data-ttu-id="74dd7-112">選項。</span><span class="sxs-lookup"><span data-stu-id="74dd7-112">Options</span></span>

- **`--configfile`**

  <span data-ttu-id="74dd7-113">NuGet 設定檔。</span><span class="sxs-lookup"><span data-stu-id="74dd7-113">The NuGet configuration file.</span></span> <span data-ttu-id="74dd7-114">如果指定，將僅使用此檔中的設置。</span><span class="sxs-lookup"><span data-stu-id="74dd7-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="74dd7-115">如果未指定，將使用目前的目錄中的設定檔層次結構。</span><span class="sxs-lookup"><span data-stu-id="74dd7-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="74dd7-116">有關詳細資訊，請參閱常見[NuGet 配置](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)。</span><span class="sxs-lookup"><span data-stu-id="74dd7-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`-n|--name`**

  <span data-ttu-id="74dd7-117">源的名稱。</span><span class="sxs-lookup"><span data-stu-id="74dd7-117">Name of the source.</span></span>

- **`-p|--password`**

  <span data-ttu-id="74dd7-118">連接到經過身份驗證的源時使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="74dd7-118">Password to be used when connecting to an authenticated source.</span></span>

- **`--store-password-in-clear-text`**

  <span data-ttu-id="74dd7-119">通過禁用密碼加密，支援存儲可擕式包源憑據。</span><span class="sxs-lookup"><span data-stu-id="74dd7-119">Enables storing portable package source credentials by disabling password encryption.</span></span>

- **`-u|--username`**

  <span data-ttu-id="74dd7-120">連接到經過身份驗證的源時使用的使用者名。</span><span class="sxs-lookup"><span data-stu-id="74dd7-120">Username to be used when connecting to an authenticated source.</span></span>

- **`--valid-authentication-types`**

  <span data-ttu-id="74dd7-121">此源的有效身份驗證類型的 Comma 分隔清單。</span><span class="sxs-lookup"><span data-stu-id="74dd7-121">Comma-separated list of valid authentication types for this source.</span></span> <span data-ttu-id="74dd7-122">`basic`如果伺服器通告 NTLM 或協商，並且必須使用基本機制發送憑據，例如將 PAT 與本地 Azure DevOps 伺服器一起使用時，請對此進行設置。</span><span class="sxs-lookup"><span data-stu-id="74dd7-122">Set this to `basic` if the server advertises NTLM or Negotiate and your credentials must be sent using the Basic mechanism, for instance when using a PAT with on-premises Azure DevOps Server.</span></span> <span data-ttu-id="74dd7-123">其他有效值包括`negotiate` `kerberos`、`ntlm`和`digest`， 但這些值不太可能有用。</span><span class="sxs-lookup"><span data-stu-id="74dd7-123">Other valid values include `negotiate`, `kerberos`, `ntlm`, and `digest`, but these values are unlikely to be useful.</span></span>

## <a name="examples"></a><span data-ttu-id="74dd7-124">範例</span><span class="sxs-lookup"><span data-stu-id="74dd7-124">Examples</span></span>

- <span data-ttu-id="74dd7-125">添加`nuget.org`為源：</span><span class="sxs-lookup"><span data-stu-id="74dd7-125">Add `nuget.org` as a source:</span></span>

  ```dotnetcli
  dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org
  ```

- <span data-ttu-id="74dd7-126">添加`c:\packages`為本地源：</span><span class="sxs-lookup"><span data-stu-id="74dd7-126">Add `c:\packages` as a local source:</span></span>

  ```dotnetcli
  dotnet nuget add source c:\packages
  ```

- <span data-ttu-id="74dd7-127">添加需要身份驗證的源：</span><span class="sxs-lookup"><span data-stu-id="74dd7-127">Add a source that needs authentication:</span></span>

  ```dotnetcli
  dotnet nuget add source https://someServer/myTeam -n myTeam -u myUsername -p myPassword --store-password-in-clear-text
  ```

- <span data-ttu-id="74dd7-128">添加需要身份驗證的源（然後轉到安裝憑據提供程式）：</span><span class="sxs-lookup"><span data-stu-id="74dd7-128">Add a source that needs authentication (then go install credential provider):</span></span>

  ```dotnetcli
  dotnet nuget add source https://azureartifacts.microsoft.com/myTeam -n myTeam
  ```

## <a name="see-also"></a><span data-ttu-id="74dd7-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74dd7-129">See also</span></span>

- [<span data-ttu-id="74dd7-130">NuGet.config 檔中的包源部分</span><span class="sxs-lookup"><span data-stu-id="74dd7-130">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="74dd7-131">源命令 （nuget.exe）</span><span class="sxs-lookup"><span data-stu-id="74dd7-131">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
