---
title: 執行緒配置設定
description: 瞭解設定 .NET Core 應用程式之執行緒的執行時間設定。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 1c7c16993a07ef95223481791153b75ab2f61533
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761924"
---
# <a name="run-time-configuration-options-for-threading"></a><span data-ttu-id="2d77e-103">執行緒的執行時間設定選項</span><span class="sxs-lookup"><span data-stu-id="2d77e-103">Run-time configuration options for threading</span></span>

## <a name="cpu-groups"></a><span data-ttu-id="2d77e-104">CPU 群組</span><span class="sxs-lookup"><span data-stu-id="2d77e-104">CPU groups</span></span>

- <span data-ttu-id="2d77e-105">設定是否要在 CPU 群組之間自動散發執行緒。</span><span class="sxs-lookup"><span data-stu-id="2d77e-105">Configures whether threads are automatically distributed across CPU groups.</span></span>
- <span data-ttu-id="2d77e-106">如果您省略此設定，則不會在 CPU 群組之間散發執行緒。</span><span class="sxs-lookup"><span data-stu-id="2d77e-106">If you omit this setting, threads are not distributed across CPU groups.</span></span> <span data-ttu-id="2d77e-107">這相當於將值設定為 `0` 。</span><span class="sxs-lookup"><span data-stu-id="2d77e-107">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="2d77e-108">設定名稱</span><span class="sxs-lookup"><span data-stu-id="2d77e-108">Setting name</span></span> | <span data-ttu-id="2d77e-109">值</span><span class="sxs-lookup"><span data-stu-id="2d77e-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="2d77e-110">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="2d77e-110">**runtimeconfig.json**</span></span> | <span data-ttu-id="2d77e-111">N/A</span><span class="sxs-lookup"><span data-stu-id="2d77e-111">N/A</span></span> | <span data-ttu-id="2d77e-112">N/A</span><span class="sxs-lookup"><span data-stu-id="2d77e-112">N/A</span></span> |
| <span data-ttu-id="2d77e-113">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="2d77e-113">**Environment variable**</span></span> | `COMPlus_Thread_UseAllCpuGroups` | <span data-ttu-id="2d77e-114">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="2d77e-114">`0` - disabled</span></span><br/><span data-ttu-id="2d77e-115">`1`-已啟用</span><span class="sxs-lookup"><span data-stu-id="2d77e-115">`1` - enabled</span></span> |

## <a name="minimum-threads"></a><span data-ttu-id="2d77e-116">執行緒數下限</span><span class="sxs-lookup"><span data-stu-id="2d77e-116">Minimum threads</span></span>

- <span data-ttu-id="2d77e-117">指定背景工作執行緒集區的執行緒數目下限。</span><span class="sxs-lookup"><span data-stu-id="2d77e-117">Specifies the minimum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="2d77e-118">對應至 <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="2d77e-118">Corresponds to the <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="2d77e-119">設定名稱</span><span class="sxs-lookup"><span data-stu-id="2d77e-119">Setting name</span></span> | <span data-ttu-id="2d77e-120">值</span><span class="sxs-lookup"><span data-stu-id="2d77e-120">Values</span></span> |
| - | - | - |
| <span data-ttu-id="2d77e-121">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="2d77e-121">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MinThreads` | <span data-ttu-id="2d77e-122">整數，表示執行緒的最小數目</span><span class="sxs-lookup"><span data-stu-id="2d77e-122">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="2d77e-123">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="2d77e-123">**MSBuild property**</span></span> | `ThreadPoolMinThreads` | <span data-ttu-id="2d77e-124">整數，表示執行緒的最小數目</span><span class="sxs-lookup"><span data-stu-id="2d77e-124">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="2d77e-125">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="2d77e-125">**Environment variable**</span></span> | <span data-ttu-id="2d77e-126">N/A</span><span class="sxs-lookup"><span data-stu-id="2d77e-126">N/A</span></span> | <span data-ttu-id="2d77e-127">N/A</span><span class="sxs-lookup"><span data-stu-id="2d77e-127">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="2d77e-128">範例</span><span class="sxs-lookup"><span data-stu-id="2d77e-128">Examples</span></span>

<span data-ttu-id="2d77e-129">*.runtimeconfig.json json*檔案：</span><span class="sxs-lookup"><span data-stu-id="2d77e-129">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MinThreads": 4
      }
   }
}
```

<span data-ttu-id="2d77e-130">專案檔：</span><span class="sxs-lookup"><span data-stu-id="2d77e-130">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>

</Project>
```

## <a name="maximum-threads"></a><span data-ttu-id="2d77e-131">最大執行緒數</span><span class="sxs-lookup"><span data-stu-id="2d77e-131">Maximum threads</span></span>

- <span data-ttu-id="2d77e-132">指定背景工作執行緒集區的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="2d77e-132">Specifies the maximum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="2d77e-133">對應至 <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="2d77e-133">Corresponds to the <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="2d77e-134">設定名稱</span><span class="sxs-lookup"><span data-stu-id="2d77e-134">Setting name</span></span> | <span data-ttu-id="2d77e-135">值</span><span class="sxs-lookup"><span data-stu-id="2d77e-135">Values</span></span> |
| - | - | - |
| <span data-ttu-id="2d77e-136">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="2d77e-136">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MaxThreads` | <span data-ttu-id="2d77e-137">表示執行緒數目上限的整數。</span><span class="sxs-lookup"><span data-stu-id="2d77e-137">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="2d77e-138">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="2d77e-138">**MSBuild property**</span></span> | `ThreadPoolMaxThreads` | <span data-ttu-id="2d77e-139">表示執行緒數目上限的整數。</span><span class="sxs-lookup"><span data-stu-id="2d77e-139">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="2d77e-140">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="2d77e-140">**Environment variable**</span></span> | <span data-ttu-id="2d77e-141">N/A</span><span class="sxs-lookup"><span data-stu-id="2d77e-141">N/A</span></span> | <span data-ttu-id="2d77e-142">N/A</span><span class="sxs-lookup"><span data-stu-id="2d77e-142">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="2d77e-143">範例</span><span class="sxs-lookup"><span data-stu-id="2d77e-143">Examples</span></span>

<span data-ttu-id="2d77e-144">*.runtimeconfig.json json*檔案：</span><span class="sxs-lookup"><span data-stu-id="2d77e-144">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MaxThreads": 20
      }
   }
}
```

<span data-ttu-id="2d77e-145">專案檔：</span><span class="sxs-lookup"><span data-stu-id="2d77e-145">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```
