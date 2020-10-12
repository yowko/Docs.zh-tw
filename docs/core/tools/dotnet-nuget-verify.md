---
title: dotnet nuget 驗證命令
description: Dotnet nuget verify 命令會驗證已簽署的套件。
author: kartheekp-ms
ms.date: 10/08/2020
ms.openlocfilehash: 6cb368e2b6c203f3774b4450c0831c5d6b2dc0e8
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2020
ms.locfileid: "91957139"
---
# <a name="dotnet-nuget-verify"></a><span data-ttu-id="5f982-103">dotnet nuget 驗證</span><span class="sxs-lookup"><span data-stu-id="5f982-103">dotnet nuget verify</span></span>

<span data-ttu-id="5f982-104">本文**適用于：** ✔️ .net 5.0.100-rc. x SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="5f982-104">**This article applies to:** ✔️ .NET 5.0.100-rc.2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="5f982-105">Name</span><span class="sxs-lookup"><span data-stu-id="5f982-105">Name</span></span>

<span data-ttu-id="5f982-106">`dotnet nuget verify` -驗證已簽署的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="5f982-106">`dotnet nuget verify` - Verifies a signed NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5f982-107">概要</span><span class="sxs-lookup"><span data-stu-id="5f982-107">Synopsis</span></span>

```dotnetcli
dotnet nuget verify [<package-path(s)>]
    [--all]
    [--certificate-fingerprint <FINGERPRINT>]
    [-v|--verbosity <LEVEL>]

dotnet nuget verify -h|--help
```

## <a name="description"></a><span data-ttu-id="5f982-108">描述</span><span class="sxs-lookup"><span data-stu-id="5f982-108">Description</span></span>

<span data-ttu-id="5f982-109">此 `dotnet nuget verify` 命令會驗證已簽署的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="5f982-109">The `dotnet nuget verify` command verifies a signed NuGet package.</span></span>

## <a name="arguments"></a><span data-ttu-id="5f982-110">引數</span><span class="sxs-lookup"><span data-stu-id="5f982-110">Arguments</span></span>

- **`package-path(s)`**

  <span data-ttu-id="5f982-111">指定要驗證的封裝 (的檔案路徑) 。</span><span class="sxs-lookup"><span data-stu-id="5f982-111">Specifies the file path to the package(s) to be verified.</span></span> <span data-ttu-id="5f982-112">您可以傳入多個位置引數來驗證多個封裝。</span><span class="sxs-lookup"><span data-stu-id="5f982-112">Multiple position arguments can be passed in to verify multiple packages.</span></span>

## <a name="options"></a><span data-ttu-id="5f982-113">選項</span><span class="sxs-lookup"><span data-stu-id="5f982-113">Options</span></span>

- **`--all`**

  <span data-ttu-id="5f982-114">指定所有可能的驗證都應該在封裝 (s) 上執行。</span><span class="sxs-lookup"><span data-stu-id="5f982-114">Specifies that all verifications possible should be performed on the package(s).</span></span> <span data-ttu-id="5f982-115">依預設，只 `signatures` 會驗證。</span><span class="sxs-lookup"><span data-stu-id="5f982-115">By default, only `signatures` are verified.</span></span>

> [!NOTE]
> <span data-ttu-id="5f982-116">此命令目前僅支援 `signature` 驗證。</span><span class="sxs-lookup"><span data-stu-id="5f982-116">This command currently supports only `signature` verification.</span></span>

- **`--certificate-fingerprint <FINGERPRINT>`**

  <span data-ttu-id="5f982-117">確認簽署者憑證符合其中一個指定的 `SHA256` 指紋。</span><span class="sxs-lookup"><span data-stu-id="5f982-117">Verify that the signer certificate matches with one of the specified `SHA256` fingerprints.</span></span> <span data-ttu-id="5f982-118">您可以多次提供這個選項來提供多個指紋。</span><span class="sxs-lookup"><span data-stu-id="5f982-118">This option can be supplied multiple times to provide multiple fingerprints.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="5f982-119">設定 MSBuild 詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="5f982-119">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="5f982-120">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="5f982-120">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="5f982-121">預設為 `normal`。</span><span class="sxs-lookup"><span data-stu-id="5f982-121">The default is `normal`.</span></span>

* **`-h|--help`**

  <span data-ttu-id="5f982-122">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="5f982-122">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="5f982-123">範例</span><span class="sxs-lookup"><span data-stu-id="5f982-123">Examples</span></span>

- <span data-ttu-id="5f982-124">確認 *foo. nupkg*：</span><span class="sxs-lookup"><span data-stu-id="5f982-124">Verify *foo.nupkg*:</span></span>

  ```dotnetcli
  dotnet nuget verify foo.nupkg
  ```

- <span data-ttu-id="5f982-125">確認已*指定目錄中的*多個 NuGet 套件- *foo. nupkg*和 nupkg 檔案：</span><span class="sxs-lookup"><span data-stu-id="5f982-125">Verify multiple NuGet packages - *foo.nupkg* and *all .nupkg files in the directory specified*:</span></span>

  ```dotnetcli
  dotnet nuget verify foo.nupkg c:\mydir\*.nupkg
  ```

- <span data-ttu-id="5f982-126">使用指定的憑證指紋確認 *foo. nupkg* 簽章相符：</span><span class="sxs-lookup"><span data-stu-id="5f982-126">Verify *foo.nupkg* signature matches with the specified certificate fingerprint:</span></span>

  ```dotnetcli
  dotnet nuget verify foo.nupkg --certificate-fingerprint CE40881FF5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E039
  ```

- <span data-ttu-id="5f982-127">確認 *foo. nupkg* 簽章與其中一個指定的憑證指紋相符：</span><span class="sxs-lookup"><span data-stu-id="5f982-127">Verify *foo.nupkg* signature matches with one of the specified certificate fingerprints:</span></span>

  ```dotnetcli
  dotnet nuget verify foo.nupkg --certificate-fingerprint CE40881FF5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E039 --certificate-fingerprint EC10992GG5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E027
  ```
