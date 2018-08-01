---
title: dotnet build-server 命令 - .NET Core CLI
description: dotnet build-server 命令會與組建所啟動的伺服器互動。
author: mairaw
ms.author: mairaw
ms.date: 07/02/2018
ms.openlocfilehash: 1c59c85f246b79c7e2552f704db5b4f076f9b502
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404329"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="74000-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="74000-103">dotnet build-server</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="74000-104">名稱</span><span class="sxs-lookup"><span data-stu-id="74000-104">Name</span></span>

<span data-ttu-id="74000-105">`dotnet build-server` - 與組建所啟動的伺服器互動。</span><span class="sxs-lookup"><span data-stu-id="74000-105">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="74000-106">概要</span><span class="sxs-lookup"><span data-stu-id="74000-106">Synopsis</span></span>

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="74000-107">命令</span><span class="sxs-lookup"><span data-stu-id="74000-107">Commands</span></span>

`shutdown`

<span data-ttu-id="74000-108">將透過 dotnet 啟動的組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="74000-108">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="74000-109">根據預設，所有伺服器都會關機。</span><span class="sxs-lookup"><span data-stu-id="74000-109">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="74000-110">選項</span><span class="sxs-lookup"><span data-stu-id="74000-110">Options</span></span>

`-h|--help`

<span data-ttu-id="74000-111">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="74000-111">Prints out a short help for the command.</span></span>

`--msbuild`

<span data-ttu-id="74000-112">將 MSBuild 組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="74000-112">Shuts down the MSBuild build server.</span></span>

`--razor`

<span data-ttu-id="74000-113">將 Razor 組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="74000-113">Shuts down the Razor build server.</span></span>

`--vbcscompiler`

<span data-ttu-id="74000-114">將 VB/C# 編譯器組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="74000-114">Shuts down the VB/C# compiler build server.</span></span>
