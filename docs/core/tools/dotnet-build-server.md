---
title: dotnet build-server 命令
description: dotnet build-server 命令會與組建所啟動的伺服器互動。
ms.date: 02/14/2020
ms.openlocfilehash: 882b697c07aac0e20266f3ad4e6c11888a0b7acc
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463729"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="4c372-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="4c372-103">dotnet build-server</span></span>

<span data-ttu-id="4c372-104">**本文適用於:✔️** .NET 核心 2.1 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="4c372-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="4c372-105">名稱</span><span class="sxs-lookup"><span data-stu-id="4c372-105">Name</span></span>

<span data-ttu-id="4c372-106">`dotnet build-server` - 與組建所啟動的伺服器互動。</span><span class="sxs-lookup"><span data-stu-id="4c372-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4c372-107">概要</span><span class="sxs-lookup"><span data-stu-id="4c372-107">Synopsis</span></span>

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]

dotnet build-server shutdown -h|--help

dotnet build-server -h|--help
```

## <a name="commands"></a><span data-ttu-id="4c372-108">命令</span><span class="sxs-lookup"><span data-stu-id="4c372-108">Commands</span></span>

- **`shutdown`**

  <span data-ttu-id="4c372-109">將透過 dotnet 啟動的組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="4c372-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="4c372-110">根據預設，所有伺服器都會關機。</span><span class="sxs-lookup"><span data-stu-id="4c372-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="4c372-111">選項。</span><span class="sxs-lookup"><span data-stu-id="4c372-111">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="4c372-112">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="4c372-112">Prints out a short help for the command.</span></span>

- **`--msbuild`**

  <span data-ttu-id="4c372-113">將 MSBuild 組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="4c372-113">Shuts down the MSBuild build server.</span></span>

- **`--razor`**

  <span data-ttu-id="4c372-114">將 Razor 組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="4c372-114">Shuts down the Razor build server.</span></span>

- **`--vbcscompiler`**

  <span data-ttu-id="4c372-115">將 VB/C# 編譯器組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="4c372-115">Shuts down the VB/C# compiler build server.</span></span>
