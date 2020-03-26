---
title: 點網 nuget 清單源命令
description: dotnet nuget 清單源命令列出了來自 NuGet 設定檔中的所有現有源。
ms.date: 03/20/2020
ms.openlocfilehash: 4d7bc3dbd3ab5eb14c1ebf592044b685d28355cd
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148572"
---
# <a name="dotnet-nuget-list-source"></a><span data-ttu-id="de10b-103">點網 nuget 清單源</span><span class="sxs-lookup"><span data-stu-id="de10b-103">dotnet nuget list source</span></span>

<span data-ttu-id="de10b-104">**本文適用于：✔️** .NET Core 3.1.200 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="de10b-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="de10b-105">名稱</span><span class="sxs-lookup"><span data-stu-id="de10b-105">Name</span></span>

<span data-ttu-id="de10b-106">`dotnet nuget list source`- 列出所有配置的 NuGet 源。</span><span class="sxs-lookup"><span data-stu-id="de10b-106">`dotnet nuget list source` - Lists all configured NuGet sources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="de10b-107">概要</span><span class="sxs-lookup"><span data-stu-id="de10b-107">Synopsis</span></span>

```dotnetcli
dotnet nuget list source [--format] [--configfile]
dotnet nuget list source [-h|--help]
```

## <a name="description"></a><span data-ttu-id="de10b-108">描述</span><span class="sxs-lookup"><span data-stu-id="de10b-108">Description</span></span>

<span data-ttu-id="de10b-109">該`dotnet nuget list source`命令列出了來自 NuGet 設定檔中的所有現有源。</span><span class="sxs-lookup"><span data-stu-id="de10b-109">The `dotnet nuget list source` command lists all existing sources from your NuGet configuration files.</span></span>

## <a name="options"></a><span data-ttu-id="de10b-110">選項。</span><span class="sxs-lookup"><span data-stu-id="de10b-110">Options</span></span>

- **`--configfile`**

  <span data-ttu-id="de10b-111">NuGet 設定檔。</span><span class="sxs-lookup"><span data-stu-id="de10b-111">The NuGet configuration file.</span></span> <span data-ttu-id="de10b-112">如果指定，將僅使用此檔中的設置。</span><span class="sxs-lookup"><span data-stu-id="de10b-112">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="de10b-113">如果未指定，將使用目前的目錄中的設定檔層次結構。</span><span class="sxs-lookup"><span data-stu-id="de10b-113">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="de10b-114">有關詳細資訊，請參閱常見[NuGet 配置](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)。</span><span class="sxs-lookup"><span data-stu-id="de10b-114">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`--format`**

  <span data-ttu-id="de10b-115">清單命令輸出的格式：（`Detailed`預設值）和`Short`。</span><span class="sxs-lookup"><span data-stu-id="de10b-115">The format of the list command output: `Detailed` (the default) and `Short`.</span></span>

## <a name="examples"></a><span data-ttu-id="de10b-116">範例</span><span class="sxs-lookup"><span data-stu-id="de10b-116">Examples</span></span>

- <span data-ttu-id="de10b-117">列出目前的目錄中配置的源：</span><span class="sxs-lookup"><span data-stu-id="de10b-117">List configured sources from the current directory:</span></span>

  ```dotnetcli
  dotnet nuget list source
  ```

## <a name="see-also"></a><span data-ttu-id="de10b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de10b-118">See also</span></span>

- [<span data-ttu-id="de10b-119">NuGet.config 檔中的包源部分</span><span class="sxs-lookup"><span data-stu-id="de10b-119">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="de10b-120">源命令 （nuget.exe）</span><span class="sxs-lookup"><span data-stu-id="de10b-120">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
