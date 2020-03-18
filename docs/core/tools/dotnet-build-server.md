---
title: dotnet build-server 命令
description: dotnet build-server 命令會與組建所啟動的伺服器互動。
ms.date: 02/14/2020
ms.openlocfilehash: a6a9cd6de66371caef66d1101b3f844dffc771ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503773"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="7b8af-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="7b8af-103">dotnet build-server</span></span>

<span data-ttu-id="7b8af-104">**本文適用于：✔️** .NET 核心 2.1 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="7b8af-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="7b8af-105">名稱</span><span class="sxs-lookup"><span data-stu-id="7b8af-105">Name</span></span>

<span data-ttu-id="7b8af-106">`dotnet build-server` - 與組建所啟動的伺服器互動。</span><span class="sxs-lookup"><span data-stu-id="7b8af-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7b8af-107">概要</span><span class="sxs-lookup"><span data-stu-id="7b8af-107">Synopsis</span></span>

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="7b8af-108">命令</span><span class="sxs-lookup"><span data-stu-id="7b8af-108">Commands</span></span>

- **`shutdown`**

  <span data-ttu-id="7b8af-109">將透過 dotnet 啟動的組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="7b8af-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="7b8af-110">根據預設，所有伺服器都會關機。</span><span class="sxs-lookup"><span data-stu-id="7b8af-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="7b8af-111">選項。</span><span class="sxs-lookup"><span data-stu-id="7b8af-111">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="7b8af-112">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="7b8af-112">Prints out a short help for the command.</span></span>

- **`--msbuild`**

  <span data-ttu-id="7b8af-113">將 MSBuild 組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="7b8af-113">Shuts down the MSBuild build server.</span></span>

- **`--razor`**

  <span data-ttu-id="7b8af-114">將 Razor 組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="7b8af-114">Shuts down the Razor build server.</span></span>

- **`--vbcscompiler`**

  <span data-ttu-id="7b8af-115">將 VB/C# 編譯器組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="7b8af-115">Shuts down the VB/C# compiler build server.</span></span>
