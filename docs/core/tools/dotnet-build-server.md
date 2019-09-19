---
title: dotnet build-server 命令
description: dotnet build-server 命令會與組建所啟動的伺服器互動。
ms.date: 04/24/2019
ms.openlocfilehash: 89d1aba104e2cb07b46766a3768eed68d85a7aa7
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117766"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="1271e-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="1271e-103">dotnet build-server</span></span>

<span data-ttu-id="1271e-104">**本文適用於：✓** .NET Core 2.1 SDK 及更新版本</span><span class="sxs-lookup"><span data-stu-id="1271e-104">**This article applies to: ✓** .NET Core 2.1 SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a><span data-ttu-id="1271e-105">名稱</span><span class="sxs-lookup"><span data-stu-id="1271e-105">Name</span></span>

<span data-ttu-id="1271e-106">`dotnet build-server` - 與組建所啟動的伺服器互動。</span><span class="sxs-lookup"><span data-stu-id="1271e-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1271e-107">概要</span><span class="sxs-lookup"><span data-stu-id="1271e-107">Synopsis</span></span>

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="1271e-108">命令</span><span class="sxs-lookup"><span data-stu-id="1271e-108">Commands</span></span>

* **`shutdown`**

  <span data-ttu-id="1271e-109">將透過 dotnet 啟動的組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="1271e-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="1271e-110">根據預設，所有伺服器都會關機。</span><span class="sxs-lookup"><span data-stu-id="1271e-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="1271e-111">選項</span><span class="sxs-lookup"><span data-stu-id="1271e-111">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="1271e-112">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="1271e-112">Prints out a short help for the command.</span></span>

* **`--msbuild`**

  <span data-ttu-id="1271e-113">將 MSBuild 組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="1271e-113">Shuts down the MSBuild build server.</span></span>

* **`--razor`**

  <span data-ttu-id="1271e-114">將 Razor 組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="1271e-114">Shuts down the Razor build server.</span></span>

* **`--vbcscompiler`**

  <span data-ttu-id="1271e-115">將 VB/C# 編譯器組建伺服器關機。</span><span class="sxs-lookup"><span data-stu-id="1271e-115">Shuts down the VB/C# compiler build server.</span></span>
