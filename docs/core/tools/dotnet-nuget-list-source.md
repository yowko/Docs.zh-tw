---
title: 點網 nuget 清單來源指令
description: dotnet nuget 清單來源命令列出了來自 NuGet 設定檔中的所有現有來源。
ms.date: 03/20/2020
ms.openlocfilehash: 8b14413949bd60ddeed977d19eec9bb99982da70
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463545"
---
# <a name="dotnet-nuget-list-source"></a><span data-ttu-id="0c20c-103">dotnet nuget list source</span><span class="sxs-lookup"><span data-stu-id="0c20c-103">dotnet nuget list source</span></span>

<span data-ttu-id="0c20c-104">**本文適用於:✔️** .NET Core 3.1.200 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="0c20c-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="0c20c-105">名稱</span><span class="sxs-lookup"><span data-stu-id="0c20c-105">Name</span></span>

<span data-ttu-id="0c20c-106">`dotnet nuget list source`- 列出所有配置的 NuGet 源。</span><span class="sxs-lookup"><span data-stu-id="0c20c-106">`dotnet nuget list source` - Lists all configured NuGet sources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0c20c-107">概要</span><span class="sxs-lookup"><span data-stu-id="0c20c-107">Synopsis</span></span>

```dotnetcli
dotnet nuget list source [--format [Detailed|Short]] [--configfile <FILE>]

dotnet nuget list source -h|--help
```

## <a name="description"></a><span data-ttu-id="0c20c-108">描述</span><span class="sxs-lookup"><span data-stu-id="0c20c-108">Description</span></span>

<span data-ttu-id="0c20c-109">這個`dotnet nuget list source`指令列出了來自 NuGet 設定檔中的所有現有來源。</span><span class="sxs-lookup"><span data-stu-id="0c20c-109">The `dotnet nuget list source` command lists all existing sources from your NuGet configuration files.</span></span>

## <a name="options"></a><span data-ttu-id="0c20c-110">選項。</span><span class="sxs-lookup"><span data-stu-id="0c20c-110">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="0c20c-111">NuGet 設定檔。</span><span class="sxs-lookup"><span data-stu-id="0c20c-111">The NuGet configuration file.</span></span> <span data-ttu-id="0c20c-112">如果指定,將僅使用此檔中的設置。</span><span class="sxs-lookup"><span data-stu-id="0c20c-112">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="0c20c-113">如果未指定,將使用當前目錄中的設定檔層次結構。</span><span class="sxs-lookup"><span data-stu-id="0c20c-113">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="0c20c-114">有關詳細資訊,請參閱常見[NuGet 設定](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)。</span><span class="sxs-lookup"><span data-stu-id="0c20c-114">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`--format [Detailed|Short]`**

  <span data-ttu-id="0c20c-115">清單指令輸出的格式(`Detailed`預設值)`Short`與 。</span><span class="sxs-lookup"><span data-stu-id="0c20c-115">The format of the list command output: `Detailed` (the default) and `Short`.</span></span>

## <a name="examples"></a><span data-ttu-id="0c20c-116">範例</span><span class="sxs-lookup"><span data-stu-id="0c20c-116">Examples</span></span>

- <span data-ttu-id="0c20c-117">列出目前的目錄中設定的來源:</span><span class="sxs-lookup"><span data-stu-id="0c20c-117">List configured sources from the current directory:</span></span>

  ```dotnetcli
  dotnet nuget list source
  ```

## <a name="see-also"></a><span data-ttu-id="0c20c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c20c-118">See also</span></span>

- [<span data-ttu-id="0c20c-119">NuGet.config 檔案中的套件來源部份</span><span class="sxs-lookup"><span data-stu-id="0c20c-119">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="0c20c-120">來源指令 (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="0c20c-120">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
