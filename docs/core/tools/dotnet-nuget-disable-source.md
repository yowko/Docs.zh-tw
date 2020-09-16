---
title: dotnet nuget disable source 命令
description: Dotnet nuget disable source 命令會停用 NuGet 設定檔中的現有來源。
ms.date: 03/20/2020
ms.openlocfilehash: af37a6589cebaf0501ee5647ebadb83125d0f56e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537947"
---
# <a name="dotnet-nuget-disable-source"></a><span data-ttu-id="2bbec-103">dotnet nuget disable source</span><span class="sxs-lookup"><span data-stu-id="2bbec-103">dotnet nuget disable source</span></span>

<span data-ttu-id="2bbec-104">本文**適用于：** ✔️ .net CORE 3.1.200 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="2bbec-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="2bbec-105">名稱</span><span class="sxs-lookup"><span data-stu-id="2bbec-105">Name</span></span>

<span data-ttu-id="2bbec-106">`dotnet nuget disable source` -停用 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="2bbec-106">`dotnet nuget disable source` - Disable a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2bbec-107">概要</span><span class="sxs-lookup"><span data-stu-id="2bbec-107">Synopsis</span></span>

```dotnetcli
dotnet nuget disable source <NAME> [--configfile <FILE>]

dotnet nuget disable source -h|--help
```

## <a name="description"></a><span data-ttu-id="2bbec-108">描述</span><span class="sxs-lookup"><span data-stu-id="2bbec-108">Description</span></span>

<span data-ttu-id="2bbec-109">此 `dotnet nuget disable source` 命令會停用 NuGet 設定檔中的現有來源。</span><span class="sxs-lookup"><span data-stu-id="2bbec-109">The `dotnet nuget disable source` command disables an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="2bbec-110">引數</span><span class="sxs-lookup"><span data-stu-id="2bbec-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="2bbec-111">來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="2bbec-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="2bbec-112">選項</span><span class="sxs-lookup"><span data-stu-id="2bbec-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="2bbec-113">NuGet 設定檔案。</span><span class="sxs-lookup"><span data-stu-id="2bbec-113">The NuGet configuration file.</span></span> <span data-ttu-id="2bbec-114">如果指定，則只會使用來自此檔案的設定。</span><span class="sxs-lookup"><span data-stu-id="2bbec-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="2bbec-115">如果未指定，將會使用目前目錄中的設定檔階層。</span><span class="sxs-lookup"><span data-stu-id="2bbec-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="2bbec-116">如需詳細資訊，請參閱 [常見的 NuGet](/nuget/consume-packages/configuring-nuget-behavior)設定。</span><span class="sxs-lookup"><span data-stu-id="2bbec-116">For more information, see [Common NuGet Configurations](/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="2bbec-117">範例</span><span class="sxs-lookup"><span data-stu-id="2bbec-117">Examples</span></span>

- <span data-ttu-id="2bbec-118">停用名稱為的來源 `mySource` ：</span><span class="sxs-lookup"><span data-stu-id="2bbec-118">Disable a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget disable source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="2bbec-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2bbec-119">See also</span></span>

- [<span data-ttu-id="2bbec-120">NuGet.config 檔案中的套件來源區段</span><span class="sxs-lookup"><span data-stu-id="2bbec-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="2bbec-121">來源命令 ( # A0) </span><span class="sxs-lookup"><span data-stu-id="2bbec-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
