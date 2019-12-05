---
title: 編譯 config 設定
description: 瞭解執行時間設定，其可設定 JIT 編譯程式適用于 .NET Core 應用程式的方式。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: bcc445b6edc48d9432ee614b0b19c9c25621f4a0
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802817"
---
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="a3262-103">編譯的執行時間設定選項</span><span class="sxs-lookup"><span data-stu-id="a3262-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="a3262-104">階層式編譯</span><span class="sxs-lookup"><span data-stu-id="a3262-104">Tiered compilation</span></span>

- <span data-ttu-id="a3262-105">設定 JIT 編譯程式是否使用[分層式編譯](../whats-new/dotnet-core-3-0.md#tiered-compilation)。</span><span class="sxs-lookup"><span data-stu-id="a3262-105">Configures whether the JIT compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span>
- <span data-ttu-id="a3262-106">在 .NET Core 3.0 和更新版本中，預設會啟用階層式編譯。</span><span class="sxs-lookup"><span data-stu-id="a3262-106">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="a3262-107">在 .NET Core 2.1 和2.2 中，階層式編譯預設為停用。</span><span class="sxs-lookup"><span data-stu-id="a3262-107">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>

| | <span data-ttu-id="a3262-108">設定名稱</span><span class="sxs-lookup"><span data-stu-id="a3262-108">Setting name</span></span> | <span data-ttu-id="a3262-109">值</span><span class="sxs-lookup"><span data-stu-id="a3262-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a3262-110">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="a3262-110">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="a3262-111">已啟用 `true`</span><span class="sxs-lookup"><span data-stu-id="a3262-111">`true` - enabled</span></span><br/><span data-ttu-id="a3262-112">`false`-已停用</span><span class="sxs-lookup"><span data-stu-id="a3262-112">`false` - disabled</span></span> |
| <span data-ttu-id="a3262-113">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="a3262-113">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="a3262-114">已啟用 `1`</span><span class="sxs-lookup"><span data-stu-id="a3262-114">`1` - enabled</span></span><br/><span data-ttu-id="a3262-115">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="a3262-115">`0` - disabled</span></span> |
