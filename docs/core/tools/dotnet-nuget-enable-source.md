---
title: 點網 nuget 啟用源命令
description: dotnet nuget 啟用源命令支援 NuGet 設定檔中的現有源。
ms.date: 03/20/2020
ms.openlocfilehash: 1f18e7db6a6c8631bb432676dd97dabfad5b0ab8
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148558"
---
# <a name="dotnet-nuget-enable-source"></a><span data-ttu-id="4b616-103">點網 nuget 啟用源</span><span class="sxs-lookup"><span data-stu-id="4b616-103">dotnet nuget enable source</span></span>

<span data-ttu-id="4b616-104">**本文適用于：✔️** .NET Core 3.1.200 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="4b616-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="4b616-105">名稱</span><span class="sxs-lookup"><span data-stu-id="4b616-105">Name</span></span>

<span data-ttu-id="4b616-106">`dotnet nuget enable source`- 啟用 NuGet 源。</span><span class="sxs-lookup"><span data-stu-id="4b616-106">`dotnet nuget enable source` - Enable a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4b616-107">概要</span><span class="sxs-lookup"><span data-stu-id="4b616-107">Synopsis</span></span>

```dotnetcli
dotnet nuget enable source <NAME> [--configfile]
dotnet nuget enable source [-h|--help]
```

## <a name="description"></a><span data-ttu-id="4b616-108">描述</span><span class="sxs-lookup"><span data-stu-id="4b616-108">Description</span></span>

<span data-ttu-id="4b616-109">該`dotnet nuget enable source`命令啟用 NuGet 設定檔中的現有源。</span><span class="sxs-lookup"><span data-stu-id="4b616-109">The `dotnet nuget enable source` command enables an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="4b616-110">引數</span><span class="sxs-lookup"><span data-stu-id="4b616-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="4b616-111">源的名稱。</span><span class="sxs-lookup"><span data-stu-id="4b616-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="4b616-112">選項。</span><span class="sxs-lookup"><span data-stu-id="4b616-112">Options</span></span>

- **`--configfile`**

  <span data-ttu-id="4b616-113">NuGet 設定檔。</span><span class="sxs-lookup"><span data-stu-id="4b616-113">The NuGet configuration file.</span></span> <span data-ttu-id="4b616-114">如果指定，將僅使用此檔中的設置。</span><span class="sxs-lookup"><span data-stu-id="4b616-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="4b616-115">如果未指定，將使用目前的目錄中的設定檔層次結構。</span><span class="sxs-lookup"><span data-stu-id="4b616-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="4b616-116">有關詳細資訊，請參閱常見[NuGet 配置](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)。</span><span class="sxs-lookup"><span data-stu-id="4b616-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="4b616-117">範例</span><span class="sxs-lookup"><span data-stu-id="4b616-117">Examples</span></span>

- <span data-ttu-id="4b616-118">啟用名稱為 的`mySource`源：</span><span class="sxs-lookup"><span data-stu-id="4b616-118">Enable a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget enable source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="4b616-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b616-119">See also</span></span>

- [<span data-ttu-id="4b616-120">NuGet.config 檔中的包源部分</span><span class="sxs-lookup"><span data-stu-id="4b616-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="4b616-121">源命令 （nuget.exe）</span><span class="sxs-lookup"><span data-stu-id="4b616-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
