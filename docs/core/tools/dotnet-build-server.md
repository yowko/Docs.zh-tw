---
title: dotnet build-server 命令 - .NET Core CLI
description: dotnet build-server 會與組建所啟動的伺服器互動。
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 929b8d74aa5f3f0ad73b108be8a5bf22f86e30d6
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696250"
---
# <a name="dotnet-build"></a><span data-ttu-id="3966a-103">dotnet-build</span><span class="sxs-lookup"><span data-stu-id="3966a-103">dotnet-build</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="3966a-104">名稱</span><span class="sxs-lookup"><span data-stu-id="3966a-104">Name</span></span>

<span data-ttu-id="3966a-105">`dotnet build-server` - 與組建所啟動的伺服器互動。</span><span class="sxs-lookup"><span data-stu-id="3966a-105">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3966a-106">概要</span><span class="sxs-lookup"><span data-stu-id="3966a-106">Synopsis</span></span>

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="3966a-107">命令</span><span class="sxs-lookup"><span data-stu-id="3966a-107">Commands</span></span>

`shutdown`

<span data-ttu-id="3966a-108">將透過 dotnet 啟動的組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="3966a-108">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="3966a-109">根據預設，所有伺服器都會關機。</span><span class="sxs-lookup"><span data-stu-id="3966a-109">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="3966a-110">選項</span><span class="sxs-lookup"><span data-stu-id="3966a-110">Options</span></span>

`-h|--help`

<span data-ttu-id="3966a-111">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="3966a-111">Prints out a short help for the command.</span></span>

`--msbuild`

<span data-ttu-id="3966a-112">將 MSBuild 組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="3966a-112">Shuts down the MSBuild build server.</span></span>

`--razor`

<span data-ttu-id="3966a-113">將 Razor 組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="3966a-113">Shuts down the Razor build server.</span></span>

`--vbcscompiler`

<span data-ttu-id="3966a-114">將 VB/C# 編譯器組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="3966a-114">Shuts down the VB/C# compiler build server.</span></span>
