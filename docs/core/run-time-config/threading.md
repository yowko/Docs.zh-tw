---
title: 執行緒配置設定
description: 瞭解設定 .NET Core 應用程式之執行緒的執行時間設定。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 6a920dbc301830e3f4c95bf637ff3de6d4f464ff
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802761"
---
# <a name="run-time-configuration-options-for-threading"></a><span data-ttu-id="bf406-103">執行緒的執行時間設定選項</span><span class="sxs-lookup"><span data-stu-id="bf406-103">Run-time configuration options for threading</span></span>

## <a name="cpu-groups"></a><span data-ttu-id="bf406-104">CPU 群組</span><span class="sxs-lookup"><span data-stu-id="bf406-104">CPU groups</span></span>

- <span data-ttu-id="bf406-105">設定是否要在 CPU 群組之間自動散發執行緒。</span><span class="sxs-lookup"><span data-stu-id="bf406-105">Configures whether threads are automatically distributed across CPU groups.</span></span>
- <span data-ttu-id="bf406-106">預設：停用（`0`）。</span><span class="sxs-lookup"><span data-stu-id="bf406-106">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="bf406-107">設定名稱</span><span class="sxs-lookup"><span data-stu-id="bf406-107">Setting name</span></span> | <span data-ttu-id="bf406-108">值</span><span class="sxs-lookup"><span data-stu-id="bf406-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="bf406-109">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="bf406-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="bf406-110">N/A</span><span class="sxs-lookup"><span data-stu-id="bf406-110">N/A</span></span> | <span data-ttu-id="bf406-111">N/A</span><span class="sxs-lookup"><span data-stu-id="bf406-111">N/A</span></span> |
| <span data-ttu-id="bf406-112">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="bf406-112">**Environment variable**</span></span> | `COMPlus_Thread_UseAllCpuGroups` | <span data-ttu-id="bf406-113">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="bf406-113">`0` - disabled</span></span><br/><span data-ttu-id="bf406-114">已啟用 `1`</span><span class="sxs-lookup"><span data-stu-id="bf406-114">`1` - enabled</span></span> |

## <a name="minimum-threads"></a><span data-ttu-id="bf406-115">執行緒數下限</span><span class="sxs-lookup"><span data-stu-id="bf406-115">Minimum threads</span></span>

- <span data-ttu-id="bf406-116">指定背景工作執行緒集區的執行緒數目下限。</span><span class="sxs-lookup"><span data-stu-id="bf406-116">Specifies the minimum number of threads for the worker threadpool.</span></span>
- <span data-ttu-id="bf406-117">對應至 <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="bf406-117">Corresponds to the <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="bf406-118">設定名稱</span><span class="sxs-lookup"><span data-stu-id="bf406-118">Setting name</span></span> | <span data-ttu-id="bf406-119">值</span><span class="sxs-lookup"><span data-stu-id="bf406-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="bf406-120">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="bf406-120">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MinThreads` | <span data-ttu-id="bf406-121">整數，表示執行緒的最小數目</span><span class="sxs-lookup"><span data-stu-id="bf406-121">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="bf406-122">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="bf406-122">**Environment variable**</span></span> | <span data-ttu-id="bf406-123">N/A</span><span class="sxs-lookup"><span data-stu-id="bf406-123">N/A</span></span> | <span data-ttu-id="bf406-124">N/A</span><span class="sxs-lookup"><span data-stu-id="bf406-124">N/A</span></span> |

## <a name="maximum-threads"></a><span data-ttu-id="bf406-125">最大執行緒數</span><span class="sxs-lookup"><span data-stu-id="bf406-125">Maximum threads</span></span>

- <span data-ttu-id="bf406-126">指定背景工作執行緒集區的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="bf406-126">Specifies the maximum number of threads for the worker threadpool.</span></span>
- <span data-ttu-id="bf406-127">對應至 <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="bf406-127">Corresponds to the <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="bf406-128">設定名稱</span><span class="sxs-lookup"><span data-stu-id="bf406-128">Setting name</span></span> | <span data-ttu-id="bf406-129">值</span><span class="sxs-lookup"><span data-stu-id="bf406-129">Values</span></span> |
| - | - | - |
| <span data-ttu-id="bf406-130">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="bf406-130">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MaxThreads` | <span data-ttu-id="bf406-131">表示執行緒數目上限的整數。</span><span class="sxs-lookup"><span data-stu-id="bf406-131">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="bf406-132">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="bf406-132">**Environment variable**</span></span> | <span data-ttu-id="bf406-133">N/A</span><span class="sxs-lookup"><span data-stu-id="bf406-133">N/A</span></span> | <span data-ttu-id="bf406-134">N/A</span><span class="sxs-lookup"><span data-stu-id="bf406-134">N/A</span></span> |
