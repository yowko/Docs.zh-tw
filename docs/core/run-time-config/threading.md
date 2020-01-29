---
title: 執行緒配置設定
description: 瞭解設定 .NET Core 應用程式之執行緒的執行時間設定。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: ed7688d4d8f7178440fe59afc6e2f5e0a11b2a5c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733428"
---
# <a name="run-time-configuration-options-for-threading"></a><span data-ttu-id="414a7-103">執行緒的執行時間設定選項</span><span class="sxs-lookup"><span data-stu-id="414a7-103">Run-time configuration options for threading</span></span>

## <a name="cpu-groups"></a><span data-ttu-id="414a7-104">CPU 群組</span><span class="sxs-lookup"><span data-stu-id="414a7-104">CPU groups</span></span>

- <span data-ttu-id="414a7-105">設定是否要在 CPU 群組之間自動散發執行緒。</span><span class="sxs-lookup"><span data-stu-id="414a7-105">Configures whether threads are automatically distributed across CPU groups.</span></span>
- <span data-ttu-id="414a7-106">預設：停用（`0`）。</span><span class="sxs-lookup"><span data-stu-id="414a7-106">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="414a7-107">設定名稱</span><span class="sxs-lookup"><span data-stu-id="414a7-107">Setting name</span></span> | <span data-ttu-id="414a7-108">值</span><span class="sxs-lookup"><span data-stu-id="414a7-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="414a7-109">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="414a7-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="414a7-110">N/A</span><span class="sxs-lookup"><span data-stu-id="414a7-110">N/A</span></span> | <span data-ttu-id="414a7-111">N/A</span><span class="sxs-lookup"><span data-stu-id="414a7-111">N/A</span></span> |
| <span data-ttu-id="414a7-112">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="414a7-112">**Environment variable**</span></span> | `COMPlus_Thread_UseAllCpuGroups` | <span data-ttu-id="414a7-113">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="414a7-113">`0` - disabled</span></span><br/><span data-ttu-id="414a7-114">已啟用 `1`</span><span class="sxs-lookup"><span data-stu-id="414a7-114">`1` - enabled</span></span> |

## <a name="minimum-threads"></a><span data-ttu-id="414a7-115">執行緒數下限</span><span class="sxs-lookup"><span data-stu-id="414a7-115">Minimum threads</span></span>

- <span data-ttu-id="414a7-116">指定背景工作執行緒集區的執行緒數目下限。</span><span class="sxs-lookup"><span data-stu-id="414a7-116">Specifies the minimum number of threads for the worker threadpool.</span></span>
- <span data-ttu-id="414a7-117">對應至 <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="414a7-117">Corresponds to the <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="414a7-118">設定名稱</span><span class="sxs-lookup"><span data-stu-id="414a7-118">Setting name</span></span> | <span data-ttu-id="414a7-119">值</span><span class="sxs-lookup"><span data-stu-id="414a7-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="414a7-120">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="414a7-120">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MinThreads` | <span data-ttu-id="414a7-121">整數，表示執行緒的最小數目</span><span class="sxs-lookup"><span data-stu-id="414a7-121">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="414a7-122">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="414a7-122">**MSBuild property**</span></span> | `ThreadPoolMinThreads` | <span data-ttu-id="414a7-123">整數，表示執行緒的最小數目</span><span class="sxs-lookup"><span data-stu-id="414a7-123">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="414a7-124">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="414a7-124">**Environment variable**</span></span> | <span data-ttu-id="414a7-125">N/A</span><span class="sxs-lookup"><span data-stu-id="414a7-125">N/A</span></span> | <span data-ttu-id="414a7-126">N/A</span><span class="sxs-lookup"><span data-stu-id="414a7-126">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="414a7-127">範例</span><span class="sxs-lookup"><span data-stu-id="414a7-127">Examples</span></span>

<span data-ttu-id="414a7-128">*.runtimeconfig.json json*檔案：</span><span class="sxs-lookup"><span data-stu-id="414a7-128">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MinThreads": 4
      }
   }
}
```

<span data-ttu-id="414a7-129">專案檔：</span><span class="sxs-lookup"><span data-stu-id="414a7-129">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>

</Project>
```

## <a name="maximum-threads"></a><span data-ttu-id="414a7-130">最大執行緒數</span><span class="sxs-lookup"><span data-stu-id="414a7-130">Maximum threads</span></span>

- <span data-ttu-id="414a7-131">指定背景工作執行緒集區的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="414a7-131">Specifies the maximum number of threads for the worker threadpool.</span></span>
- <span data-ttu-id="414a7-132">對應至 <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="414a7-132">Corresponds to the <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="414a7-133">設定名稱</span><span class="sxs-lookup"><span data-stu-id="414a7-133">Setting name</span></span> | <span data-ttu-id="414a7-134">值</span><span class="sxs-lookup"><span data-stu-id="414a7-134">Values</span></span> |
| - | - | - |
| <span data-ttu-id="414a7-135">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="414a7-135">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MaxThreads` | <span data-ttu-id="414a7-136">表示執行緒數目上限的整數。</span><span class="sxs-lookup"><span data-stu-id="414a7-136">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="414a7-137">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="414a7-137">**MSBuild property**</span></span> | `ThreadPoolMaxThreads` | <span data-ttu-id="414a7-138">表示執行緒數目上限的整數。</span><span class="sxs-lookup"><span data-stu-id="414a7-138">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="414a7-139">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="414a7-139">**Environment variable**</span></span> | <span data-ttu-id="414a7-140">N/A</span><span class="sxs-lookup"><span data-stu-id="414a7-140">N/A</span></span> | <span data-ttu-id="414a7-141">N/A</span><span class="sxs-lookup"><span data-stu-id="414a7-141">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="414a7-142">範例</span><span class="sxs-lookup"><span data-stu-id="414a7-142">Examples</span></span>

<span data-ttu-id="414a7-143">*.runtimeconfig.json json*檔案：</span><span class="sxs-lookup"><span data-stu-id="414a7-143">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MaxThreads": 20
      }
   }
}
```

<span data-ttu-id="414a7-144">專案檔：</span><span class="sxs-lookup"><span data-stu-id="414a7-144">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```
