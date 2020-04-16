---
title: 點網 nuget 更新來源指令
description: dotnet nuget 更新來源指令更新 NuGet 設定檔中的現有來源。
ms.date: 03/20/2020
ms.openlocfilehash: 42b1aec95cdd57e53f966400f6692a3d0150c16c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463483"
---
# <a name="dotnet-nuget-update-source"></a><span data-ttu-id="b1668-103">dotnet nuget update source</span><span class="sxs-lookup"><span data-stu-id="b1668-103">dotnet nuget update source</span></span>

<span data-ttu-id="b1668-104">**本文適用於:✔️** .NET Core 3.1.200 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="b1668-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="b1668-105">名稱</span><span class="sxs-lookup"><span data-stu-id="b1668-105">Name</span></span>

<span data-ttu-id="b1668-106">`dotnet nuget update source`- 更新 NuGet 源。</span><span class="sxs-lookup"><span data-stu-id="b1668-106">`dotnet nuget update source` - Update a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b1668-107">概要</span><span class="sxs-lookup"><span data-stu-id="b1668-107">Synopsis</span></span>

```dotnetcli
dotnet nuget update source <NAME> [--source <SOURCE>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget update source -h|--help
```

## <a name="description"></a><span data-ttu-id="b1668-108">描述</span><span class="sxs-lookup"><span data-stu-id="b1668-108">Description</span></span>

<span data-ttu-id="b1668-109">該`dotnet nuget update source`指令更新 NuGet 設定檔中的現有來源。</span><span class="sxs-lookup"><span data-stu-id="b1668-109">The `dotnet nuget update source` command updates an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="b1668-110">引數</span><span class="sxs-lookup"><span data-stu-id="b1668-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="b1668-111">源的名稱。</span><span class="sxs-lookup"><span data-stu-id="b1668-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="b1668-112">選項。</span><span class="sxs-lookup"><span data-stu-id="b1668-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="b1668-113">NuGet 設定檔。</span><span class="sxs-lookup"><span data-stu-id="b1668-113">The NuGet configuration file.</span></span> <span data-ttu-id="b1668-114">如果指定,將僅使用此檔中的設置。</span><span class="sxs-lookup"><span data-stu-id="b1668-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="b1668-115">如果未指定,將使用當前目錄中的設定檔層次結構。</span><span class="sxs-lookup"><span data-stu-id="b1668-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="b1668-116">有關詳細資訊,請參閱常見[NuGet 設定](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)。</span><span class="sxs-lookup"><span data-stu-id="b1668-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`-p|--password <PASSWORD>`**

  <span data-ttu-id="b1668-117">連接到經過身份驗證的源時使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="b1668-117">Password to be used when connecting to an authenticated source.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="b1668-118">包源的路徑。</span><span class="sxs-lookup"><span data-stu-id="b1668-118">Path to the package source.</span></span>

- **`--store-password-in-clear-text`**

  <span data-ttu-id="b1668-119">通過禁用密碼加密,支援存儲便攜式包源憑據。</span><span class="sxs-lookup"><span data-stu-id="b1668-119">Enables storing portable package source credentials by disabling password encryption.</span></span>

- **`-u|--username <USER>`**

  <span data-ttu-id="b1668-120">連接到經過身份驗證的源時使用的使用者名。</span><span class="sxs-lookup"><span data-stu-id="b1668-120">Username to be used when connecting to an authenticated source.</span></span>

- **`--valid-authentication-types <TYPES>`**

  <span data-ttu-id="b1668-121">此源的有效身份驗證類型的 Comma 分隔清單。</span><span class="sxs-lookup"><span data-stu-id="b1668-121">Comma-separated list of valid authentication types for this source.</span></span> <span data-ttu-id="b1668-122">`basic`如果伺服器通告 NTLM 或協商,並且必須使用基本機制發送認證,例如將 PAT 與本地 Azure DevOps 伺服器一起使用時,請對此進行設置。</span><span class="sxs-lookup"><span data-stu-id="b1668-122">Set this to `basic` if the server advertises NTLM or Negotiate and your credentials must be sent using the Basic mechanism, for instance when using a PAT with on-premises Azure DevOps Server.</span></span> <span data-ttu-id="b1668-123">其他有效值包括`negotiate``kerberos`、`ntlm``digest`和, 但這些值不太可能有用。</span><span class="sxs-lookup"><span data-stu-id="b1668-123">Other valid values include `negotiate`, `kerberos`, `ntlm`, and `digest`, but these values are unlikely to be useful.</span></span>

## <a name="examples"></a><span data-ttu-id="b1668-124">範例</span><span class="sxs-lookup"><span data-stu-id="b1668-124">Examples</span></span>

- <span data-ttu-id="b1668-125">更新名稱為`mySource`的 來源:</span><span class="sxs-lookup"><span data-stu-id="b1668-125">Update a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget update source mySource --source c:\packages
  ```

## <a name="see-also"></a><span data-ttu-id="b1668-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1668-126">See also</span></span>

- [<span data-ttu-id="b1668-127">NuGet.config 檔案中的套件來源部份</span><span class="sxs-lookup"><span data-stu-id="b1668-127">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="b1668-128">來源指令 (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="b1668-128">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
