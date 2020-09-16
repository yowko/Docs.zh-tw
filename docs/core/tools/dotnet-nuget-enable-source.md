---
title: dotnet nuget enable source 命令
description: Dotnet nuget enable source 命令會在您的 NuGet 設定檔中啟用現有的來源。
ms.date: 03/20/2020
ms.openlocfilehash: b727844dd7d7cc82476e94a3f0ec4ecc6559d5ed
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537930"
---
# <a name="dotnet-nuget-enable-source"></a><span data-ttu-id="d0f0c-103">dotnet nuget enable source</span><span class="sxs-lookup"><span data-stu-id="d0f0c-103">dotnet nuget enable source</span></span>

<span data-ttu-id="d0f0c-104">本文**適用于：** ✔️ .net CORE 3.1.200 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="d0f0c-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="d0f0c-105">名稱</span><span class="sxs-lookup"><span data-stu-id="d0f0c-105">Name</span></span>

<span data-ttu-id="d0f0c-106">`dotnet nuget enable source` -啟用 NuGet 來源。</span><span class="sxs-lookup"><span data-stu-id="d0f0c-106">`dotnet nuget enable source` - Enable a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d0f0c-107">概要</span><span class="sxs-lookup"><span data-stu-id="d0f0c-107">Synopsis</span></span>

```dotnetcli
dotnet nuget enable source <NAME> [--configfile <FILE>]

dotnet nuget enable source -h|--help
```

## <a name="description"></a><span data-ttu-id="d0f0c-108">描述</span><span class="sxs-lookup"><span data-stu-id="d0f0c-108">Description</span></span>

<span data-ttu-id="d0f0c-109">此 `dotnet nuget enable source` 命令會在您的 NuGet 設定檔中啟用現有的來源。</span><span class="sxs-lookup"><span data-stu-id="d0f0c-109">The `dotnet nuget enable source` command enables an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="d0f0c-110">引數</span><span class="sxs-lookup"><span data-stu-id="d0f0c-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="d0f0c-111">來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="d0f0c-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="d0f0c-112">選項</span><span class="sxs-lookup"><span data-stu-id="d0f0c-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="d0f0c-113">NuGet 設定檔案。</span><span class="sxs-lookup"><span data-stu-id="d0f0c-113">The NuGet configuration file.</span></span> <span data-ttu-id="d0f0c-114">如果指定，則只會使用來自此檔案的設定。</span><span class="sxs-lookup"><span data-stu-id="d0f0c-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="d0f0c-115">如果未指定，將會使用目前目錄中的設定檔階層。</span><span class="sxs-lookup"><span data-stu-id="d0f0c-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="d0f0c-116">如需詳細資訊，請參閱 [常見的 NuGet](/nuget/consume-packages/configuring-nuget-behavior)設定。</span><span class="sxs-lookup"><span data-stu-id="d0f0c-116">For more information, see [Common NuGet Configurations](/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="d0f0c-117">範例</span><span class="sxs-lookup"><span data-stu-id="d0f0c-117">Examples</span></span>

- <span data-ttu-id="d0f0c-118">以下列名稱啟用來源 `mySource` ：</span><span class="sxs-lookup"><span data-stu-id="d0f0c-118">Enable a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget enable source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="d0f0c-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0f0c-119">See also</span></span>

- [<span data-ttu-id="d0f0c-120">NuGet.config 檔案中的套件來源區段</span><span class="sxs-lookup"><span data-stu-id="d0f0c-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="d0f0c-121">來源命令 ( # A0) </span><span class="sxs-lookup"><span data-stu-id="d0f0c-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
