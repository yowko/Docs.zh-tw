---
title: dotnet build-server 命令 - .NET Core CLI
description: dotnet build-server 命令會與組建所啟動的伺服器互動。
ms.date: 12/04/2018
ms.openlocfilehash: 2746ade12cc819089258483e84a8c0f02a64c755
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53125674"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="3bafc-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="3bafc-103">dotnet build-server</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="3bafc-104">名稱</span><span class="sxs-lookup"><span data-stu-id="3bafc-104">Name</span></span>

<span data-ttu-id="3bafc-105">`dotnet build-server` - 與組建所啟動的伺服器互動。</span><span class="sxs-lookup"><span data-stu-id="3bafc-105">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3bafc-106">概要</span><span class="sxs-lookup"><span data-stu-id="3bafc-106">Synopsis</span></span>

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="3bafc-107">命令</span><span class="sxs-lookup"><span data-stu-id="3bafc-107">Commands</span></span>

* **`shutdown`**

  <span data-ttu-id="3bafc-108">將透過 dotnet 啟動的組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="3bafc-108">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="3bafc-109">根據預設，所有伺服器都會關機。</span><span class="sxs-lookup"><span data-stu-id="3bafc-109">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="3bafc-110">選項</span><span class="sxs-lookup"><span data-stu-id="3bafc-110">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="3bafc-111">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="3bafc-111">Prints out a short help for the command.</span></span>

* **`--msbuild`**

  <span data-ttu-id="3bafc-112">將 MSBuild 組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="3bafc-112">Shuts down the MSBuild build server.</span></span>

* **`--razor`**

  <span data-ttu-id="3bafc-113">將 Razor 組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="3bafc-113">Shuts down the Razor build server.</span></span>

* **`--vbcscompiler`**

  <span data-ttu-id="3bafc-114">將 VB/C# 編譯器組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="3bafc-114">Shuts down the VB/C# compiler build server.</span></span>