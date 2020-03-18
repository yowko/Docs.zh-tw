---
title: 執行緒配置設置
description: 瞭解為 .NET Core 應用配置執行緒的運行時設置。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 68b8e93ca6ec3f708a7a627307655ada1955500a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789858"
---
# <a name="run-time-configuration-options-for-threading"></a><span data-ttu-id="ce10c-103">用於執行緒的運行時配置選項</span><span class="sxs-lookup"><span data-stu-id="ce10c-103">Run-time configuration options for threading</span></span>

## <a name="cpu-groups"></a><span data-ttu-id="ce10c-104">CPU 組</span><span class="sxs-lookup"><span data-stu-id="ce10c-104">CPU groups</span></span>

- <span data-ttu-id="ce10c-105">配置執行緒是否自動分佈在 CPU 組中。</span><span class="sxs-lookup"><span data-stu-id="ce10c-105">Configures whether threads are automatically distributed across CPU groups.</span></span>
- <span data-ttu-id="ce10c-106">預設值： 已`0`禁用 （ 。</span><span class="sxs-lookup"><span data-stu-id="ce10c-106">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="ce10c-107">設定名稱</span><span class="sxs-lookup"><span data-stu-id="ce10c-107">Setting name</span></span> | <span data-ttu-id="ce10c-108">值</span><span class="sxs-lookup"><span data-stu-id="ce10c-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="ce10c-109">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="ce10c-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="ce10c-110">N/A</span><span class="sxs-lookup"><span data-stu-id="ce10c-110">N/A</span></span> | <span data-ttu-id="ce10c-111">N/A</span><span class="sxs-lookup"><span data-stu-id="ce10c-111">N/A</span></span> |
| <span data-ttu-id="ce10c-112">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="ce10c-112">**Environment variable**</span></span> | `COMPlus_Thread_UseAllCpuGroups` | <span data-ttu-id="ce10c-113">`0`- 禁用</span><span class="sxs-lookup"><span data-stu-id="ce10c-113">`0` - disabled</span></span><br/><span data-ttu-id="ce10c-114">`1`- 已啟用</span><span class="sxs-lookup"><span data-stu-id="ce10c-114">`1` - enabled</span></span> |

## <a name="minimum-threads"></a><span data-ttu-id="ce10c-115">最小線程</span><span class="sxs-lookup"><span data-stu-id="ce10c-115">Minimum threads</span></span>

- <span data-ttu-id="ce10c-116">指定輔助執行緒池的最小線程數。</span><span class="sxs-lookup"><span data-stu-id="ce10c-116">Specifies the minimum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="ce10c-117">對應于 方法<xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="ce10c-117">Corresponds to the <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="ce10c-118">設定名稱</span><span class="sxs-lookup"><span data-stu-id="ce10c-118">Setting name</span></span> | <span data-ttu-id="ce10c-119">值</span><span class="sxs-lookup"><span data-stu-id="ce10c-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="ce10c-120">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="ce10c-120">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MinThreads` | <span data-ttu-id="ce10c-121">表示最小線程數的整數</span><span class="sxs-lookup"><span data-stu-id="ce10c-121">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="ce10c-122">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="ce10c-122">**MSBuild property**</span></span> | `ThreadPoolMinThreads` | <span data-ttu-id="ce10c-123">表示最小線程數的整數</span><span class="sxs-lookup"><span data-stu-id="ce10c-123">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="ce10c-124">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="ce10c-124">**Environment variable**</span></span> | <span data-ttu-id="ce10c-125">N/A</span><span class="sxs-lookup"><span data-stu-id="ce10c-125">N/A</span></span> | <span data-ttu-id="ce10c-126">N/A</span><span class="sxs-lookup"><span data-stu-id="ce10c-126">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="ce10c-127">範例</span><span class="sxs-lookup"><span data-stu-id="ce10c-127">Examples</span></span>

<span data-ttu-id="ce10c-128">*運行時配置.json*檔：</span><span class="sxs-lookup"><span data-stu-id="ce10c-128">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MinThreads": 4
      }
   }
}
```

<span data-ttu-id="ce10c-129">專案檔：</span><span class="sxs-lookup"><span data-stu-id="ce10c-129">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>

</Project>
```

## <a name="maximum-threads"></a><span data-ttu-id="ce10c-130">最大執行緒數</span><span class="sxs-lookup"><span data-stu-id="ce10c-130">Maximum threads</span></span>

- <span data-ttu-id="ce10c-131">指定輔助執行緒池的最大執行緒數。</span><span class="sxs-lookup"><span data-stu-id="ce10c-131">Specifies the maximum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="ce10c-132">對應于 方法<xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="ce10c-132">Corresponds to the <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="ce10c-133">設定名稱</span><span class="sxs-lookup"><span data-stu-id="ce10c-133">Setting name</span></span> | <span data-ttu-id="ce10c-134">值</span><span class="sxs-lookup"><span data-stu-id="ce10c-134">Values</span></span> |
| - | - | - |
| <span data-ttu-id="ce10c-135">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="ce10c-135">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MaxThreads` | <span data-ttu-id="ce10c-136">表示最大執行緒數的整數</span><span class="sxs-lookup"><span data-stu-id="ce10c-136">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="ce10c-137">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="ce10c-137">**MSBuild property**</span></span> | `ThreadPoolMaxThreads` | <span data-ttu-id="ce10c-138">表示最大執行緒數的整數</span><span class="sxs-lookup"><span data-stu-id="ce10c-138">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="ce10c-139">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="ce10c-139">**Environment variable**</span></span> | <span data-ttu-id="ce10c-140">N/A</span><span class="sxs-lookup"><span data-stu-id="ce10c-140">N/A</span></span> | <span data-ttu-id="ce10c-141">N/A</span><span class="sxs-lookup"><span data-stu-id="ce10c-141">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="ce10c-142">範例</span><span class="sxs-lookup"><span data-stu-id="ce10c-142">Examples</span></span>

<span data-ttu-id="ce10c-143">*運行時配置.json*檔：</span><span class="sxs-lookup"><span data-stu-id="ce10c-143">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MaxThreads": 20
      }
   }
}
```

<span data-ttu-id="ce10c-144">專案檔：</span><span class="sxs-lookup"><span data-stu-id="ce10c-144">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```
