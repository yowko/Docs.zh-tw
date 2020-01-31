---
title: 執行緒配置設定
description: 瞭解設定 .NET Core 應用程式之執行緒的執行時間設定。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 68b8e93ca6ec3f708a7a627307655ada1955500a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789858"
---
# <a name="run-time-configuration-options-for-threading"></a><span data-ttu-id="7b67d-103">執行緒的執行時間設定選項</span><span class="sxs-lookup"><span data-stu-id="7b67d-103">Run-time configuration options for threading</span></span>

## <a name="cpu-groups"></a><span data-ttu-id="7b67d-104">CPU 群組</span><span class="sxs-lookup"><span data-stu-id="7b67d-104">CPU groups</span></span>

- <span data-ttu-id="7b67d-105">設定是否要在 CPU 群組之間自動散發執行緒。</span><span class="sxs-lookup"><span data-stu-id="7b67d-105">Configures whether threads are automatically distributed across CPU groups.</span></span>
- <span data-ttu-id="7b67d-106">預設：停用（`0`）。</span><span class="sxs-lookup"><span data-stu-id="7b67d-106">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="7b67d-107">設定名稱</span><span class="sxs-lookup"><span data-stu-id="7b67d-107">Setting name</span></span> | <span data-ttu-id="7b67d-108">值</span><span class="sxs-lookup"><span data-stu-id="7b67d-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="7b67d-109">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="7b67d-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="7b67d-110">N/A</span><span class="sxs-lookup"><span data-stu-id="7b67d-110">N/A</span></span> | <span data-ttu-id="7b67d-111">N/A</span><span class="sxs-lookup"><span data-stu-id="7b67d-111">N/A</span></span> |
| <span data-ttu-id="7b67d-112">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="7b67d-112">**Environment variable**</span></span> | `COMPlus_Thread_UseAllCpuGroups` | <span data-ttu-id="7b67d-113">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="7b67d-113">`0` - disabled</span></span><br/><span data-ttu-id="7b67d-114">已啟用 `1`</span><span class="sxs-lookup"><span data-stu-id="7b67d-114">`1` - enabled</span></span> |

## <a name="minimum-threads"></a><span data-ttu-id="7b67d-115">執行緒數下限</span><span class="sxs-lookup"><span data-stu-id="7b67d-115">Minimum threads</span></span>

- <span data-ttu-id="7b67d-116">指定背景工作執行緒集區的執行緒數目下限。</span><span class="sxs-lookup"><span data-stu-id="7b67d-116">Specifies the minimum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="7b67d-117">對應至 <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="7b67d-117">Corresponds to the <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="7b67d-118">設定名稱</span><span class="sxs-lookup"><span data-stu-id="7b67d-118">Setting name</span></span> | <span data-ttu-id="7b67d-119">值</span><span class="sxs-lookup"><span data-stu-id="7b67d-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="7b67d-120">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="7b67d-120">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MinThreads` | <span data-ttu-id="7b67d-121">整數，表示執行緒的最小數目</span><span class="sxs-lookup"><span data-stu-id="7b67d-121">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="7b67d-122">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="7b67d-122">**MSBuild property**</span></span> | `ThreadPoolMinThreads` | <span data-ttu-id="7b67d-123">整數，表示執行緒的最小數目</span><span class="sxs-lookup"><span data-stu-id="7b67d-123">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="7b67d-124">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="7b67d-124">**Environment variable**</span></span> | <span data-ttu-id="7b67d-125">N/A</span><span class="sxs-lookup"><span data-stu-id="7b67d-125">N/A</span></span> | <span data-ttu-id="7b67d-126">N/A</span><span class="sxs-lookup"><span data-stu-id="7b67d-126">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="7b67d-127">範例</span><span class="sxs-lookup"><span data-stu-id="7b67d-127">Examples</span></span>

<span data-ttu-id="7b67d-128">*.runtimeconfig.json json*檔案：</span><span class="sxs-lookup"><span data-stu-id="7b67d-128">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MinThreads": 4
      }
   }
}
```

<span data-ttu-id="7b67d-129">專案檔：</span><span class="sxs-lookup"><span data-stu-id="7b67d-129">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>

</Project>
```

## <a name="maximum-threads"></a><span data-ttu-id="7b67d-130">最大執行緒數</span><span class="sxs-lookup"><span data-stu-id="7b67d-130">Maximum threads</span></span>

- <span data-ttu-id="7b67d-131">指定背景工作執行緒集區的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="7b67d-131">Specifies the maximum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="7b67d-132">對應至 <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="7b67d-132">Corresponds to the <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="7b67d-133">設定名稱</span><span class="sxs-lookup"><span data-stu-id="7b67d-133">Setting name</span></span> | <span data-ttu-id="7b67d-134">值</span><span class="sxs-lookup"><span data-stu-id="7b67d-134">Values</span></span> |
| - | - | - |
| <span data-ttu-id="7b67d-135">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="7b67d-135">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MaxThreads` | <span data-ttu-id="7b67d-136">表示執行緒數目上限的整數。</span><span class="sxs-lookup"><span data-stu-id="7b67d-136">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="7b67d-137">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="7b67d-137">**MSBuild property**</span></span> | `ThreadPoolMaxThreads` | <span data-ttu-id="7b67d-138">表示執行緒數目上限的整數。</span><span class="sxs-lookup"><span data-stu-id="7b67d-138">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="7b67d-139">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="7b67d-139">**Environment variable**</span></span> | <span data-ttu-id="7b67d-140">N/A</span><span class="sxs-lookup"><span data-stu-id="7b67d-140">N/A</span></span> | <span data-ttu-id="7b67d-141">N/A</span><span class="sxs-lookup"><span data-stu-id="7b67d-141">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="7b67d-142">範例</span><span class="sxs-lookup"><span data-stu-id="7b67d-142">Examples</span></span>

<span data-ttu-id="7b67d-143">*.runtimeconfig.json json*檔案：</span><span class="sxs-lookup"><span data-stu-id="7b67d-143">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MaxThreads": 20
      }
   }
}
```

<span data-ttu-id="7b67d-144">專案檔：</span><span class="sxs-lookup"><span data-stu-id="7b67d-144">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```
