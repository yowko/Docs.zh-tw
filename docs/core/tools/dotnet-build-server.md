---
title: dotnet build-server 命令
description: dotnet build-server 命令會與組建所啟動的伺服器互動。
ms.date: 04/24/2019
ms.openlocfilehash: b2dfd5f317466f18d9246bd1fb281a92c42f6d9d
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168114"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="6d17e-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="6d17e-103">dotnet build-server</span></span>

<span data-ttu-id="6d17e-104">**本文適用於：✓** .NET Core 2.1 SDK 及更新版本</span><span class="sxs-lookup"><span data-stu-id="6d17e-104">**This article applies to: ✓** .NET Core 2.1 SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a><span data-ttu-id="6d17e-105">名稱</span><span class="sxs-lookup"><span data-stu-id="6d17e-105">Name</span></span>

<span data-ttu-id="6d17e-106">`dotnet build-server` - 與組建所啟動的伺服器互動。</span><span class="sxs-lookup"><span data-stu-id="6d17e-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6d17e-107">概要</span><span class="sxs-lookup"><span data-stu-id="6d17e-107">Synopsis</span></span>

```console
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="6d17e-108">命令</span><span class="sxs-lookup"><span data-stu-id="6d17e-108">Commands</span></span>

* **`shutdown`**

  <span data-ttu-id="6d17e-109">將透過 dotnet 啟動的組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="6d17e-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="6d17e-110">根據預設，所有伺服器都會關機。</span><span class="sxs-lookup"><span data-stu-id="6d17e-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="6d17e-111">選項</span><span class="sxs-lookup"><span data-stu-id="6d17e-111">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="6d17e-112">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="6d17e-112">Prints out a short help for the command.</span></span>

* **`--msbuild`**

  <span data-ttu-id="6d17e-113">將 MSBuild 組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="6d17e-113">Shuts down the MSBuild build server.</span></span>

* **`--razor`**

  <span data-ttu-id="6d17e-114">將 Razor 組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="6d17e-114">Shuts down the Razor build server.</span></span>

* **`--vbcscompiler`**

  <span data-ttu-id="6d17e-115">將 VB/C# 編譯器組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="6d17e-115">Shuts down the VB/C# compiler build server.</span></span>
