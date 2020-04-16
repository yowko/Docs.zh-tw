---
title: 點網 nuget 刪除來源指令
description: dotnet nuget 刪除來源命令從 NuGet 設定檔中刪除現有來源。
ms.date: 03/20/2020
ms.openlocfilehash: b259873e1885644b272136fa31414410bdfd9f27
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463499"
---
# <a name="dotnet-nuget-remove-source"></a><span data-ttu-id="e1d05-103">dotnet nuget remove source</span><span class="sxs-lookup"><span data-stu-id="e1d05-103">dotnet nuget remove source</span></span>

<span data-ttu-id="e1d05-104">**本文適用於:✔️** .NET Core 3.1.200 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="e1d05-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="e1d05-105">名稱</span><span class="sxs-lookup"><span data-stu-id="e1d05-105">Name</span></span>

<span data-ttu-id="e1d05-106">`dotnet nuget remove source`- 刪除 NuGet 源。</span><span class="sxs-lookup"><span data-stu-id="e1d05-106">`dotnet nuget remove source` - Remove a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e1d05-107">概要</span><span class="sxs-lookup"><span data-stu-id="e1d05-107">Synopsis</span></span>

```dotnetcli
dotnet nuget remove source <NAME> [--configfile <FILE>]

dotnet nuget remove source -h|--help
```

## <a name="description"></a><span data-ttu-id="e1d05-108">描述</span><span class="sxs-lookup"><span data-stu-id="e1d05-108">Description</span></span>

<span data-ttu-id="e1d05-109">這個`dotnet nuget remove source`指令從 NuGet 設定檔中移除現有來源。</span><span class="sxs-lookup"><span data-stu-id="e1d05-109">The `dotnet nuget remove source` command removes an existing source from your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="e1d05-110">引數</span><span class="sxs-lookup"><span data-stu-id="e1d05-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="e1d05-111">源的名稱。</span><span class="sxs-lookup"><span data-stu-id="e1d05-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="e1d05-112">選項。</span><span class="sxs-lookup"><span data-stu-id="e1d05-112">Options</span></span>

- **`--configfile`**

  <span data-ttu-id="e1d05-113">NuGet 設定檔。</span><span class="sxs-lookup"><span data-stu-id="e1d05-113">The NuGet configuration file.</span></span> <span data-ttu-id="e1d05-114">如果指定,將僅使用此檔中的設置。</span><span class="sxs-lookup"><span data-stu-id="e1d05-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="e1d05-115">如果未指定,將使用當前目錄中的設定檔層次結構。</span><span class="sxs-lookup"><span data-stu-id="e1d05-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="e1d05-116">有關詳細資訊,請參閱常見[NuGet 設定](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)。</span><span class="sxs-lookup"><span data-stu-id="e1d05-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="e1d05-117">範例</span><span class="sxs-lookup"><span data-stu-id="e1d05-117">Examples</span></span>

- <span data-ttu-id="e1d05-118">刪除名為的`mySource`來源:</span><span class="sxs-lookup"><span data-stu-id="e1d05-118">Remove a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget remove source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="e1d05-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1d05-119">See also</span></span>

- [<span data-ttu-id="e1d05-120">NuGet.config 檔案中的套件來源部份</span><span class="sxs-lookup"><span data-stu-id="e1d05-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="e1d05-121">來源指令 (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="e1d05-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
