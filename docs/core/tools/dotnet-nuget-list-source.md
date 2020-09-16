---
title: dotnet nuget list source 命令
description: Dotnet nuget list source 命令會列出您的 NuGet 設定檔中的所有現有來源。
ms.date: 03/20/2020
ms.openlocfilehash: 071061e32aa1bf888e197ec6bf97f4e4f6859f0b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537886"
---
# <a name="dotnet-nuget-list-source"></a><span data-ttu-id="bb015-103">dotnet nuget list source</span><span class="sxs-lookup"><span data-stu-id="bb015-103">dotnet nuget list source</span></span>

<span data-ttu-id="bb015-104">本文**適用于：** ✔️ .net CORE 3.1.200 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="bb015-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="bb015-105">名稱</span><span class="sxs-lookup"><span data-stu-id="bb015-105">Name</span></span>

<span data-ttu-id="bb015-106">`dotnet nuget list source` -列出所有已設定的 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="bb015-106">`dotnet nuget list source` - Lists all configured NuGet sources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="bb015-107">概要</span><span class="sxs-lookup"><span data-stu-id="bb015-107">Synopsis</span></span>

```dotnetcli
dotnet nuget list source [--format [Detailed|Short]] [--configfile <FILE>]

dotnet nuget list source -h|--help
```

## <a name="description"></a><span data-ttu-id="bb015-108">描述</span><span class="sxs-lookup"><span data-stu-id="bb015-108">Description</span></span>

<span data-ttu-id="bb015-109">此 `dotnet nuget list source` 命令會從您的 NuGet 設定檔中列出所有現有的來源。</span><span class="sxs-lookup"><span data-stu-id="bb015-109">The `dotnet nuget list source` command lists all existing sources from your NuGet configuration files.</span></span>

## <a name="options"></a><span data-ttu-id="bb015-110">選項</span><span class="sxs-lookup"><span data-stu-id="bb015-110">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="bb015-111">NuGet 設定檔案。</span><span class="sxs-lookup"><span data-stu-id="bb015-111">The NuGet configuration file.</span></span> <span data-ttu-id="bb015-112">如果指定，則只會使用來自此檔案的設定。</span><span class="sxs-lookup"><span data-stu-id="bb015-112">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="bb015-113">如果未指定，將會使用目前目錄中的設定檔階層。</span><span class="sxs-lookup"><span data-stu-id="bb015-113">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="bb015-114">如需詳細資訊，請參閱 [常見的 NuGet](/nuget/consume-packages/configuring-nuget-behavior)設定。</span><span class="sxs-lookup"><span data-stu-id="bb015-114">For more information, see [Common NuGet Configurations](/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`--format [Detailed|Short]`**

  <span data-ttu-id="bb015-115">清單命令輸出的格式： `Detailed` (預設) 和 `Short` 。</span><span class="sxs-lookup"><span data-stu-id="bb015-115">The format of the list command output: `Detailed` (the default) and `Short`.</span></span>

## <a name="examples"></a><span data-ttu-id="bb015-116">範例</span><span class="sxs-lookup"><span data-stu-id="bb015-116">Examples</span></span>

- <span data-ttu-id="bb015-117">列出來自目前目錄的已設定來源：</span><span class="sxs-lookup"><span data-stu-id="bb015-117">List configured sources from the current directory:</span></span>

  ```dotnetcli
  dotnet nuget list source
  ```

## <a name="see-also"></a><span data-ttu-id="bb015-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb015-118">See also</span></span>

- [<span data-ttu-id="bb015-119">NuGet.config 檔案中的套件來源區段</span><span class="sxs-lookup"><span data-stu-id="bb015-119">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="bb015-120">來源命令 ( # A0) </span><span class="sxs-lookup"><span data-stu-id="bb015-120">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
