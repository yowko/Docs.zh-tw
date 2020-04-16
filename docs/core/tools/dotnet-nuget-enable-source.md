---
title: 點網 nuget 啟用來源指令
description: dotnet nuget 啟用來源指令支援 NuGet 設定檔中的現有來源。
ms.date: 03/20/2020
ms.openlocfilehash: 38fb5917361bd7952fef9c31ed897fb81f005155
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463553"
---
# <a name="dotnet-nuget-enable-source"></a><span data-ttu-id="f6772-103">dotnet nuget enable source</span><span class="sxs-lookup"><span data-stu-id="f6772-103">dotnet nuget enable source</span></span>

<span data-ttu-id="f6772-104">**本文適用於:✔️** .NET Core 3.1.200 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="f6772-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f6772-105">名稱</span><span class="sxs-lookup"><span data-stu-id="f6772-105">Name</span></span>

<span data-ttu-id="f6772-106">`dotnet nuget enable source`- 啟用 NuGet 源。</span><span class="sxs-lookup"><span data-stu-id="f6772-106">`dotnet nuget enable source` - Enable a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f6772-107">概要</span><span class="sxs-lookup"><span data-stu-id="f6772-107">Synopsis</span></span>

```dotnetcli
dotnet nuget enable source <NAME> [--configfile <FILE>]

dotnet nuget enable source -h|--help
```

## <a name="description"></a><span data-ttu-id="f6772-108">描述</span><span class="sxs-lookup"><span data-stu-id="f6772-108">Description</span></span>

<span data-ttu-id="f6772-109">這個`dotnet nuget enable source`指令開啟 NuGet 設定檔中的現有來源。</span><span class="sxs-lookup"><span data-stu-id="f6772-109">The `dotnet nuget enable source` command enables an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="f6772-110">引數</span><span class="sxs-lookup"><span data-stu-id="f6772-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="f6772-111">源的名稱。</span><span class="sxs-lookup"><span data-stu-id="f6772-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="f6772-112">選項。</span><span class="sxs-lookup"><span data-stu-id="f6772-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="f6772-113">NuGet 設定檔。</span><span class="sxs-lookup"><span data-stu-id="f6772-113">The NuGet configuration file.</span></span> <span data-ttu-id="f6772-114">如果指定,將僅使用此檔中的設置。</span><span class="sxs-lookup"><span data-stu-id="f6772-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="f6772-115">如果未指定,將使用當前目錄中的設定檔層次結構。</span><span class="sxs-lookup"><span data-stu-id="f6772-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="f6772-116">有關詳細資訊,請參閱常見[NuGet 設定](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)。</span><span class="sxs-lookup"><span data-stu-id="f6772-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="f6772-117">範例</span><span class="sxs-lookup"><span data-stu-id="f6772-117">Examples</span></span>

- <span data-ttu-id="f6772-118">開啟名為的`mySource`來源:</span><span class="sxs-lookup"><span data-stu-id="f6772-118">Enable a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget enable source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="f6772-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6772-119">See also</span></span>

- [<span data-ttu-id="f6772-120">NuGet.config 檔案中的套件來源部份</span><span class="sxs-lookup"><span data-stu-id="f6772-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="f6772-121">來源指令 (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="f6772-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
