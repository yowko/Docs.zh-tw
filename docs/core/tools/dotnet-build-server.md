---
title: dotnet build-server 命令
description: dotnet build-server 命令會與組建所啟動的伺服器互動。
ms.date: 02/14/2020
ms.openlocfilehash: a6a9cd6de66371caef66d1101b3f844dffc771ef
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503773"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="8d01f-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="8d01f-103">dotnet build-server</span></span>

<span data-ttu-id="8d01f-104">**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="8d01f-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="8d01f-105">名稱</span><span class="sxs-lookup"><span data-stu-id="8d01f-105">Name</span></span>

<span data-ttu-id="8d01f-106">`dotnet build-server` - 與組建所啟動的伺服器互動。</span><span class="sxs-lookup"><span data-stu-id="8d01f-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8d01f-107">概要</span><span class="sxs-lookup"><span data-stu-id="8d01f-107">Synopsis</span></span>

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="8d01f-108">命令</span><span class="sxs-lookup"><span data-stu-id="8d01f-108">Commands</span></span>

- **`shutdown`**

  <span data-ttu-id="8d01f-109">將透過 dotnet 啟動的組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="8d01f-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="8d01f-110">根據預設，所有伺服器都會關機。</span><span class="sxs-lookup"><span data-stu-id="8d01f-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="8d01f-111">選項。</span><span class="sxs-lookup"><span data-stu-id="8d01f-111">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="8d01f-112">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="8d01f-112">Prints out a short help for the command.</span></span>

- **`--msbuild`**

  <span data-ttu-id="8d01f-113">將 MSBuild 組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="8d01f-113">Shuts down the MSBuild build server.</span></span>

- **`--razor`**

  <span data-ttu-id="8d01f-114">將 Razor 組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="8d01f-114">Shuts down the Razor build server.</span></span>

- **`--vbcscompiler`**

  <span data-ttu-id="8d01f-115">將 VB/C# 編譯器組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="8d01f-115">Shuts down the VB/C# compiler build server.</span></span>
