---
title: 垃圾收集行程 config 設定
description: 瞭解用來設定垃圾收集行程如何管理 .NET Core 應用程式記憶體的執行時間設定。
ms.date: 07/10/2020
ms.topic: reference
ms.openlocfilehash: 91d155b638c7e69b3d2c0216266a7c0c0410db4c
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915994"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="3a0db-103">用於垃圾收集的執行時間設定選項</span><span class="sxs-lookup"><span data-stu-id="3a0db-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="3a0db-104">此頁面包含垃圾收集行程 (GC) 設定的相關資訊，可在執行時間變更。</span><span class="sxs-lookup"><span data-stu-id="3a0db-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="3a0db-105">如果您正嘗試達到執行中應用程式的尖峰效能，請考慮使用這些設定。</span><span class="sxs-lookup"><span data-stu-id="3a0db-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="3a0db-106">不過，在一般情況下，預設值可為大部分的應用程式提供最佳效能。</span><span class="sxs-lookup"><span data-stu-id="3a0db-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="3a0db-107">這些設定會依此頁面的群組排列。</span><span class="sxs-lookup"><span data-stu-id="3a0db-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="3a0db-108">每個群組內的設定通常會彼此搭配使用，以達成特定結果。</span><span class="sxs-lookup"><span data-stu-id="3a0db-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="3a0db-109">這些設定也可以在應用程式執行時動態變更，因此您設定的任何執行時間設定可能會遭到覆寫。</span><span class="sxs-lookup"><span data-stu-id="3a0db-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="3a0db-110">某些設定（例如[延遲層級](../../standard/garbage-collection/latency.md)）通常只會在設計階段透過 API 進行設定。</span><span class="sxs-lookup"><span data-stu-id="3a0db-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="3a0db-111">此頁面會省略這類設定。</span><span class="sxs-lookup"><span data-stu-id="3a0db-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="3a0db-112">針對 [數值]，在 [檔案中的*runtimeconfig.js* ] 和 [用於環境變數的十六進位標記法] 設定中，使用十進位標記來進行設定。</span><span class="sxs-lookup"><span data-stu-id="3a0db-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="3a0db-113">若為十六進位值，您可以使用或不搭配 "0x" 前置詞來指定它們。</span><span class="sxs-lookup"><span data-stu-id="3a0db-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="3a0db-114">垃圾收集的種類</span><span class="sxs-lookup"><span data-stu-id="3a0db-114">Flavors of garbage collection</span></span>

<span data-ttu-id="3a0db-115">垃圾收集的兩個主要類別是工作站 GC 和伺服器 GC。</span><span class="sxs-lookup"><span data-stu-id="3a0db-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="3a0db-116">如需兩者之間差異的詳細資訊，請參閱[工作站和伺服器垃圾收集](../../standard/garbage-collection/workstation-server-gc.md)。</span><span class="sxs-lookup"><span data-stu-id="3a0db-116">For more information about differences between the two, see [Workstation and server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span>

<span data-ttu-id="3a0db-117">垃圾收集的 subflavors 是背景和非並行的。</span><span class="sxs-lookup"><span data-stu-id="3a0db-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="3a0db-118">使用下列設定來選取垃圾收集的種類：</span><span class="sxs-lookup"><span data-stu-id="3a0db-118">Use the following settings to select flavors of garbage collection:</span></span>

- [<span data-ttu-id="3a0db-119">工作站與伺服器 GC 的比較</span><span class="sxs-lookup"><span data-stu-id="3a0db-119">Workstation vs. server GC</span></span>](#workstation-vs-server)
- [<span data-ttu-id="3a0db-120">背景 GC</span><span class="sxs-lookup"><span data-stu-id="3a0db-120">Background GC</span></span>](#background-gc)

### <a name="workstation-vs-server"></a><span data-ttu-id="3a0db-121">工作站與伺服器的比較</span><span class="sxs-lookup"><span data-stu-id="3a0db-121">Workstation vs. server</span></span>

- <span data-ttu-id="3a0db-122">設定應用程式是否使用工作站垃圾收集或伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="3a0db-122">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="3a0db-123">預設值：工作站垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="3a0db-123">Default: Workstation garbage collection.</span></span> <span data-ttu-id="3a0db-124">這相當於將值設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="3a0db-124">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="3a0db-125">設定名稱</span><span class="sxs-lookup"><span data-stu-id="3a0db-125">Setting name</span></span> | <span data-ttu-id="3a0db-126">值</span><span class="sxs-lookup"><span data-stu-id="3a0db-126">Values</span></span> | <span data-ttu-id="3a0db-127">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3a0db-127">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="3a0db-128">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="3a0db-128">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="3a0db-129">`false`-工作站</span><span class="sxs-lookup"><span data-stu-id="3a0db-129">`false` - workstation</span></span><br/><span data-ttu-id="3a0db-130">`true`-伺服器</span><span class="sxs-lookup"><span data-stu-id="3a0db-130">`true` - server</span></span> | <span data-ttu-id="3a0db-131">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="3a0db-131">.NET Core 1.0</span></span> |
| <span data-ttu-id="3a0db-132">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="3a0db-132">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="3a0db-133">`false`-工作站</span><span class="sxs-lookup"><span data-stu-id="3a0db-133">`false` - workstation</span></span><br/><span data-ttu-id="3a0db-134">`true`-伺服器</span><span class="sxs-lookup"><span data-stu-id="3a0db-134">`true` - server</span></span> | <span data-ttu-id="3a0db-135">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="3a0db-135">.NET Core 1.0</span></span> |
| <span data-ttu-id="3a0db-136">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="3a0db-136">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="3a0db-137">`0`-工作站</span><span class="sxs-lookup"><span data-stu-id="3a0db-137">`0` - workstation</span></span><br/><span data-ttu-id="3a0db-138">`1`-伺服器</span><span class="sxs-lookup"><span data-stu-id="3a0db-138">`1` - server</span></span> | <span data-ttu-id="3a0db-139">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="3a0db-139">.NET Core 1.0</span></span> |
| <span data-ttu-id="3a0db-140">**.NET Framework 的app.config**</span><span class="sxs-lookup"><span data-stu-id="3a0db-140">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="3a0db-141">GCServer</span><span class="sxs-lookup"><span data-stu-id="3a0db-141">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="3a0db-142">`false`-工作站</span><span class="sxs-lookup"><span data-stu-id="3a0db-142">`false` - workstation</span></span><br/><span data-ttu-id="3a0db-143">`true`-伺服器</span><span class="sxs-lookup"><span data-stu-id="3a0db-143">`true` - server</span></span> |  |

#### <a name="examples"></a><span data-ttu-id="3a0db-144">範例</span><span class="sxs-lookup"><span data-stu-id="3a0db-144">Examples</span></span>

<span data-ttu-id="3a0db-145">檔案*上的runtimeconfig.js* ：</span><span class="sxs-lookup"><span data-stu-id="3a0db-145">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="3a0db-146">專案檔：</span><span class="sxs-lookup"><span data-stu-id="3a0db-146">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="background-gc"></a><span data-ttu-id="3a0db-147">背景 GC</span><span class="sxs-lookup"><span data-stu-id="3a0db-147">Background GC</span></span>

- <span data-ttu-id="3a0db-148">設定是否啟用背景 (並行) 垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="3a0db-148">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="3a0db-149">預設值：使用背景 GC。</span><span class="sxs-lookup"><span data-stu-id="3a0db-149">Default: Use background GC.</span></span> <span data-ttu-id="3a0db-150">這相當於將值設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="3a0db-150">This is equivalent to setting the value to `true`.</span></span>
- <span data-ttu-id="3a0db-151">如需詳細資訊，請參閱[背景垃圾收集](../../standard/garbage-collection/background-gc.md)。</span><span class="sxs-lookup"><span data-stu-id="3a0db-151">For more information, see [Background garbage collection](../../standard/garbage-collection/background-gc.md).</span></span>

| | <span data-ttu-id="3a0db-152">設定名稱</span><span class="sxs-lookup"><span data-stu-id="3a0db-152">Setting name</span></span> | <span data-ttu-id="3a0db-153">值</span><span class="sxs-lookup"><span data-stu-id="3a0db-153">Values</span></span> | <span data-ttu-id="3a0db-154">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3a0db-154">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="3a0db-155">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="3a0db-155">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="3a0db-156">`true`-背景 GC</span><span class="sxs-lookup"><span data-stu-id="3a0db-156">`true` - background GC</span></span><br/><span data-ttu-id="3a0db-157">`false`-非並行 GC</span><span class="sxs-lookup"><span data-stu-id="3a0db-157">`false` - non-concurrent GC</span></span> | <span data-ttu-id="3a0db-158">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="3a0db-158">.NET Core 1.0</span></span> |
| <span data-ttu-id="3a0db-159">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="3a0db-159">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="3a0db-160">`true`-背景 GC</span><span class="sxs-lookup"><span data-stu-id="3a0db-160">`true` - background GC</span></span><br/><span data-ttu-id="3a0db-161">`false`-非並行 GC</span><span class="sxs-lookup"><span data-stu-id="3a0db-161">`false` - non-concurrent GC</span></span> | <span data-ttu-id="3a0db-162">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="3a0db-162">.NET Core 1.0</span></span> |
| <span data-ttu-id="3a0db-163">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="3a0db-163">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="3a0db-164">`1`-背景 GC</span><span class="sxs-lookup"><span data-stu-id="3a0db-164">`1` - background GC</span></span><br/><span data-ttu-id="3a0db-165">`0`-非並行 GC</span><span class="sxs-lookup"><span data-stu-id="3a0db-165">`0` - non-concurrent GC</span></span> | <span data-ttu-id="3a0db-166">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="3a0db-166">.NET Core 1.0</span></span> |
| <span data-ttu-id="3a0db-167">**.NET Framework 的app.config**</span><span class="sxs-lookup"><span data-stu-id="3a0db-167">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="3a0db-168">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="3a0db-168">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="3a0db-169">`true`-背景 GC</span><span class="sxs-lookup"><span data-stu-id="3a0db-169">`true` - background GC</span></span><br/><span data-ttu-id="3a0db-170">`false`-非並行 GC</span><span class="sxs-lookup"><span data-stu-id="3a0db-170">`false` - non-concurrent GC</span></span> |  |

#### <a name="examples"></a><span data-ttu-id="3a0db-171">範例</span><span class="sxs-lookup"><span data-stu-id="3a0db-171">Examples</span></span>

<span data-ttu-id="3a0db-172">檔案*上的runtimeconfig.js* ：</span><span class="sxs-lookup"><span data-stu-id="3a0db-172">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="3a0db-173">專案檔：</span><span class="sxs-lookup"><span data-stu-id="3a0db-173">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="3a0db-174">管理資源使用量</span><span class="sxs-lookup"><span data-stu-id="3a0db-174">Manage resource usage</span></span>

<span data-ttu-id="3a0db-175">使用下列設定來管理垃圾收集行程的記憶體和處理器使用量：</span><span class="sxs-lookup"><span data-stu-id="3a0db-175">Use the following settings to manage the garbage collector's memory and processor usage:</span></span>

- [<span data-ttu-id="3a0db-176">將相似化為</span><span class="sxs-lookup"><span data-stu-id="3a0db-176">Affinitize</span></span>](#affinitize)
- [<span data-ttu-id="3a0db-177">將相似化為 mask</span><span class="sxs-lookup"><span data-stu-id="3a0db-177">Affinitize mask</span></span>](#affinitize-mask)
- [<span data-ttu-id="3a0db-178">將相似化為範圍</span><span class="sxs-lookup"><span data-stu-id="3a0db-178">Affinitize ranges</span></span>](#affinitize-ranges)
- [<span data-ttu-id="3a0db-179">CPU 群組</span><span class="sxs-lookup"><span data-stu-id="3a0db-179">CPU groups</span></span>](#cpu-groups)
- [<span data-ttu-id="3a0db-180">堆積計數</span><span class="sxs-lookup"><span data-stu-id="3a0db-180">Heap count</span></span>](#heap-count)
- [<span data-ttu-id="3a0db-181">堆積限制</span><span class="sxs-lookup"><span data-stu-id="3a0db-181">Heap limit</span></span>](#heap-limit)
- [<span data-ttu-id="3a0db-182">堆積限制百分比</span><span class="sxs-lookup"><span data-stu-id="3a0db-182">Heap limit percent</span></span>](#heap-limit-percent)
- [<span data-ttu-id="3a0db-183">高記憶體百分比</span><span class="sxs-lookup"><span data-stu-id="3a0db-183">High memory percent</span></span>](#high-memory-percent)
- [<span data-ttu-id="3a0db-184">每個物件的堆積限制</span><span class="sxs-lookup"><span data-stu-id="3a0db-184">Per-object-heap limits</span></span>](#per-object-heap-limits)
- [<span data-ttu-id="3a0db-185">每個物件堆積限制百分比</span><span class="sxs-lookup"><span data-stu-id="3a0db-185">Per-object-heap limit percents</span></span>](#per-object-heap-limit-percents)
- [<span data-ttu-id="3a0db-186">保留 VM</span><span class="sxs-lookup"><span data-stu-id="3a0db-186">Retain VM</span></span>](#retain-vm)

<span data-ttu-id="3a0db-187">如需有關這些設定的詳細資訊，請參閱[工作站與伺服器 GC 之間的中間](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/)專案 blog。</span><span class="sxs-lookup"><span data-stu-id="3a0db-187">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="heap-count"></a><span data-ttu-id="3a0db-188">堆積計數</span><span class="sxs-lookup"><span data-stu-id="3a0db-188">Heap count</span></span>

- <span data-ttu-id="3a0db-189">限制垃圾收集行程所建立的堆積數目。</span><span class="sxs-lookup"><span data-stu-id="3a0db-189">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="3a0db-190">僅適用于伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="3a0db-190">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="3a0db-191">如果已啟用[GC 處理器親和性](#affinitize)（這是預設值），則堆積計數會將如何 `n` GC 堆積/執行緒設定為第一個 `n` 處理器。</span><span class="sxs-lookup"><span data-stu-id="3a0db-191">If [GC processor affinity](#affinitize) is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="3a0db-192"> (使用[將相似化為 mask](#affinitize-mask)或[將相似化為範圍](#affinitize-ranges)設定，以確切指定要將相似化為的處理器。 ) </span><span class="sxs-lookup"><span data-stu-id="3a0db-192">(Use the [affinitize mask](#affinitize-mask) or [affinitize ranges](#affinitize-ranges) settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="3a0db-193">如果停用[gc 處理器親和性](#affinitize)，這項設定會限制 gc 堆積的數目。</span><span class="sxs-lookup"><span data-stu-id="3a0db-193">If [GC processor affinity](#affinitize) is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="3a0db-194">如需詳細資訊，請參閱[GCHeapCount 備註](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks)。</span><span class="sxs-lookup"><span data-stu-id="3a0db-194">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="3a0db-195">設定名稱</span><span class="sxs-lookup"><span data-stu-id="3a0db-195">Setting name</span></span> | <span data-ttu-id="3a0db-196">值</span><span class="sxs-lookup"><span data-stu-id="3a0db-196">Values</span></span> | <span data-ttu-id="3a0db-197">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3a0db-197">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="3a0db-198">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="3a0db-198">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="3a0db-199">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="3a0db-199">*decimal value*</span></span> | <span data-ttu-id="3a0db-200">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="3a0db-200">.NET Core 3.0</span></span> |
| <span data-ttu-id="3a0db-201">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="3a0db-201">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="3a0db-202">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="3a0db-202">*hexadecimal value*</span></span> | <span data-ttu-id="3a0db-203">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="3a0db-203">.NET Core 3.0</span></span> |
| <span data-ttu-id="3a0db-204">**.NET Framework 的app.config**</span><span class="sxs-lookup"><span data-stu-id="3a0db-204">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="3a0db-205">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="3a0db-205">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="3a0db-206">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="3a0db-206">*decimal value*</span></span> | <span data-ttu-id="3a0db-207">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="3a0db-207">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="3a0db-208">範例：</span><span class="sxs-lookup"><span data-stu-id="3a0db-208">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapCount": 16
      }
   }
}
```

> [!TIP]
> <span data-ttu-id="3a0db-209">如果您要在*runtimeconfig.js*中設定選項，請指定十進位值。</span><span class="sxs-lookup"><span data-stu-id="3a0db-209">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="3a0db-210">如果您要將選項設定為環境變數，請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="3a0db-210">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="3a0db-211">例如，若要將堆積數目限制為16，JSON 檔案的值會是16，而環境變數的值則是0x10 或10。</span><span class="sxs-lookup"><span data-stu-id="3a0db-211">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="affinitize-mask"></a><span data-ttu-id="3a0db-212">將相似化為 mask</span><span class="sxs-lookup"><span data-stu-id="3a0db-212">Affinitize mask</span></span>

- <span data-ttu-id="3a0db-213">指定垃圾收集行程執行緒應該使用的確切處理器。</span><span class="sxs-lookup"><span data-stu-id="3a0db-213">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="3a0db-214">如果停用[GC 處理器親和性](#affinitize)，則會忽略此設定。</span><span class="sxs-lookup"><span data-stu-id="3a0db-214">If [GC processor affinity](#affinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="3a0db-215">僅適用于伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="3a0db-215">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="3a0db-216">值是一個位元遮罩，用來定義進程可用的處理器。</span><span class="sxs-lookup"><span data-stu-id="3a0db-216">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="3a0db-217">例如，如果您要使用環境) 變數，則十進位值 1023 (或十六進位值為0x3FF 或3FF，如果是二進位標記法，則為 0011 1111 1111。</span><span class="sxs-lookup"><span data-stu-id="3a0db-217">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="3a0db-218">這會指定要使用前10個處理器。</span><span class="sxs-lookup"><span data-stu-id="3a0db-218">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="3a0db-219">若要指定接下來的10個處理器（也就是處理器10-19），請指定十進位值 1047552 (或0xFFC00 或 FFC00) 的十六進位值，這相當於二進位值 1111 1111 1100 0000 0000。</span><span class="sxs-lookup"><span data-stu-id="3a0db-219">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="3a0db-220">設定名稱</span><span class="sxs-lookup"><span data-stu-id="3a0db-220">Setting name</span></span> | <span data-ttu-id="3a0db-221">值</span><span class="sxs-lookup"><span data-stu-id="3a0db-221">Values</span></span> | <span data-ttu-id="3a0db-222">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3a0db-222">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="3a0db-223">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="3a0db-223">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="3a0db-224">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="3a0db-224">*decimal value*</span></span> | <span data-ttu-id="3a0db-225">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="3a0db-225">.NET Core 3.0</span></span> |
| <span data-ttu-id="3a0db-226">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="3a0db-226">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="3a0db-227">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="3a0db-227">*hexadecimal value*</span></span> | <span data-ttu-id="3a0db-228">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="3a0db-228">.NET Core 3.0</span></span> |
| <span data-ttu-id="3a0db-229">**.NET Framework 的app.config**</span><span class="sxs-lookup"><span data-stu-id="3a0db-229">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="3a0db-230">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="3a0db-230">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="3a0db-231">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="3a0db-231">*decimal value*</span></span> | <span data-ttu-id="3a0db-232">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="3a0db-232">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="3a0db-233">範例：</span><span class="sxs-lookup"><span data-stu-id="3a0db-233">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="affinitize-ranges"></a><span data-ttu-id="3a0db-234">將相似化為範圍</span><span class="sxs-lookup"><span data-stu-id="3a0db-234">Affinitize ranges</span></span>

- <span data-ttu-id="3a0db-235">指定要用於垃圾收集行程執行緒的處理器清單。</span><span class="sxs-lookup"><span data-stu-id="3a0db-235">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="3a0db-236">此設定類似[HeapAffinitizeMask](#affinitize-mask)，不同之處在于它可讓您指定64個以上的處理器。</span><span class="sxs-lookup"><span data-stu-id="3a0db-236">This setting is similar to [System.GC.HeapAffinitizeMask](#affinitize-mask), except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="3a0db-237">若是 Windows 作業系統，請在處理器編號或範圍前面加上對應的[CPU 群組](/windows/win32/procthread/processor-groups)，例如 "0： 1-10，0：12，1： 50-52，1： 70"。</span><span class="sxs-lookup"><span data-stu-id="3a0db-237">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="3a0db-238">如果停用[GC 處理器親和性](#affinitize)，則會忽略此設定。</span><span class="sxs-lookup"><span data-stu-id="3a0db-238">If [GC processor affinity](#affinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="3a0db-239">僅適用于伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="3a0db-239">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="3a0db-240">如需詳細資訊，請參閱 Maoni Stephens 的 blog 上的[針對具有 > 64 cpu 的電腦，讓 CPU 設定更好用於 GC](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) 。</span><span class="sxs-lookup"><span data-stu-id="3a0db-240">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="3a0db-241">設定名稱</span><span class="sxs-lookup"><span data-stu-id="3a0db-241">Setting name</span></span> | <span data-ttu-id="3a0db-242">值</span><span class="sxs-lookup"><span data-stu-id="3a0db-242">Values</span></span> | <span data-ttu-id="3a0db-243">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3a0db-243">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="3a0db-244">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="3a0db-244">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="3a0db-245">以逗號分隔的處理器編號或處理器編號範圍清單。</span><span class="sxs-lookup"><span data-stu-id="3a0db-245">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="3a0db-246">Unix 範例： "1-10，12，50-52，70"</span><span class="sxs-lookup"><span data-stu-id="3a0db-246">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="3a0db-247">Windows 範例： "0： 1-10，0：12，1： 50-52，1： 70"</span><span class="sxs-lookup"><span data-stu-id="3a0db-247">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="3a0db-248">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="3a0db-248">.NET Core 3.0</span></span> |
| <span data-ttu-id="3a0db-249">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="3a0db-249">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="3a0db-250">以逗號分隔的處理器編號或處理器編號範圍清單。</span><span class="sxs-lookup"><span data-stu-id="3a0db-250">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="3a0db-251">Unix 範例： "1-10，12，50-52，70"</span><span class="sxs-lookup"><span data-stu-id="3a0db-251">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="3a0db-252">Windows 範例： "0： 1-10，0：12，1： 50-52，1： 70"</span><span class="sxs-lookup"><span data-stu-id="3a0db-252">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="3a0db-253">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="3a0db-253">.NET Core 3.0</span></span> |

<span data-ttu-id="3a0db-254">範例：</span><span class="sxs-lookup"><span data-stu-id="3a0db-254">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="cpu-groups"></a><span data-ttu-id="3a0db-255">CPU 群組</span><span class="sxs-lookup"><span data-stu-id="3a0db-255">CPU groups</span></span>

- <span data-ttu-id="3a0db-256">設定垃圾收集行程是否使用[CPU 群組](/windows/win32/procthread/processor-groups)。</span><span class="sxs-lookup"><span data-stu-id="3a0db-256">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="3a0db-257">當64位 Windows 電腦具有多個 CPU 群組（也就是，有超過64個處理器）時，啟用這個元素會延伸所有 CPU 群組的垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="3a0db-257">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="3a0db-258">垃圾收集行程會使用所有核心來建立和平衡堆積。</span><span class="sxs-lookup"><span data-stu-id="3a0db-258">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="3a0db-259">僅適用于64位 Windows 作業系統上的伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="3a0db-259">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="3a0db-260">預設值： GC 不會跨越 CPU 群組延伸。</span><span class="sxs-lookup"><span data-stu-id="3a0db-260">Default: GC does not extend across CPU groups.</span></span> <span data-ttu-id="3a0db-261">這相當於將值設定為 `0` 。</span><span class="sxs-lookup"><span data-stu-id="3a0db-261">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="3a0db-262">如需詳細資訊，請參閱 Maoni Stephens 的 blog 上的[針對具有 > 64 cpu 的電腦，讓 CPU 設定更好用於 GC](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) 。</span><span class="sxs-lookup"><span data-stu-id="3a0db-262">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="3a0db-263">設定名稱</span><span class="sxs-lookup"><span data-stu-id="3a0db-263">Setting name</span></span> | <span data-ttu-id="3a0db-264">值</span><span class="sxs-lookup"><span data-stu-id="3a0db-264">Values</span></span> | <span data-ttu-id="3a0db-265">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3a0db-265">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="3a0db-266">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="3a0db-266">**runtimeconfig.json**</span></span> | `System.GC.CpuGroup` | <span data-ttu-id="3a0db-267">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="3a0db-267">`0` - disabled</span></span><br/><span data-ttu-id="3a0db-268">`1`-已啟用</span><span class="sxs-lookup"><span data-stu-id="3a0db-268">`1` - enabled</span></span> | <span data-ttu-id="3a0db-269">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="3a0db-269">.NET 5.0</span></span> |
| <span data-ttu-id="3a0db-270">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="3a0db-270">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="3a0db-271">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="3a0db-271">`0` - disabled</span></span><br/><span data-ttu-id="3a0db-272">`1`-已啟用</span><span class="sxs-lookup"><span data-stu-id="3a0db-272">`1` - enabled</span></span> | <span data-ttu-id="3a0db-273">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="3a0db-273">.NET Core 1.0</span></span> |
| <span data-ttu-id="3a0db-274">**.NET Framework 的app.config**</span><span class="sxs-lookup"><span data-stu-id="3a0db-274">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="3a0db-275">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="3a0db-275">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="3a0db-276">`false`-已停用</span><span class="sxs-lookup"><span data-stu-id="3a0db-276">`false` - disabled</span></span><br/><span data-ttu-id="3a0db-277">`true`-已啟用</span><span class="sxs-lookup"><span data-stu-id="3a0db-277">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="3a0db-278">若要設定 common language runtime (CLR) 也將執行緒集區中的執行緒分散到所有 CPU 群組，請啟用[Thread_UseAllCpuGroups 元素](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)選項。</span><span class="sxs-lookup"><span data-stu-id="3a0db-278">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="3a0db-279">針對 .NET Core 應用程式，您可以將環境變數的值設定為，以啟用此選項 `COMPlus_Thread_UseAllCpuGroups` `1` 。</span><span class="sxs-lookup"><span data-stu-id="3a0db-279">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="affinitize"></a><span data-ttu-id="3a0db-280">將相似化為</span><span class="sxs-lookup"><span data-stu-id="3a0db-280">Affinitize</span></span>

- <span data-ttu-id="3a0db-281">指定是否要使用處理器*將相似化為*垃圾收集執行緒。</span><span class="sxs-lookup"><span data-stu-id="3a0db-281">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="3a0db-282">若要將相似化為 GC 執行緒，這表示它只能在其特定的 CPU 上執行。</span><span class="sxs-lookup"><span data-stu-id="3a0db-282">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="3a0db-283">會針對每個 GC 執行緒建立堆積。</span><span class="sxs-lookup"><span data-stu-id="3a0db-283">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="3a0db-284">僅適用于伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="3a0db-284">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="3a0db-285">預設值：使用處理器將相似化為垃圾收集執行緒。</span><span class="sxs-lookup"><span data-stu-id="3a0db-285">Default: Affinitize garbage collection threads with processors.</span></span> <span data-ttu-id="3a0db-286">這相當於將值設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="3a0db-286">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="3a0db-287">設定名稱</span><span class="sxs-lookup"><span data-stu-id="3a0db-287">Setting name</span></span> | <span data-ttu-id="3a0db-288">值</span><span class="sxs-lookup"><span data-stu-id="3a0db-288">Values</span></span> | <span data-ttu-id="3a0db-289">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3a0db-289">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="3a0db-290">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="3a0db-290">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="3a0db-291">`false`-將相似化為</span><span class="sxs-lookup"><span data-stu-id="3a0db-291">`false` - affinitize</span></span><br/><span data-ttu-id="3a0db-292">`true`-不將相似化為</span><span class="sxs-lookup"><span data-stu-id="3a0db-292">`true` - don't affinitize</span></span> | <span data-ttu-id="3a0db-293">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="3a0db-293">.NET Core 3.0</span></span> |
| <span data-ttu-id="3a0db-294">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="3a0db-294">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="3a0db-295">`0`-將相似化為</span><span class="sxs-lookup"><span data-stu-id="3a0db-295">`0` - affinitize</span></span><br/><span data-ttu-id="3a0db-296">`1`-不將相似化為</span><span class="sxs-lookup"><span data-stu-id="3a0db-296">`1` - don't affinitize</span></span> | <span data-ttu-id="3a0db-297">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="3a0db-297">.NET Core 3.0</span></span> |
| <span data-ttu-id="3a0db-298">**.NET Framework 的app.config**</span><span class="sxs-lookup"><span data-stu-id="3a0db-298">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="3a0db-299">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="3a0db-299">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="3a0db-300">`false`-將相似化為</span><span class="sxs-lookup"><span data-stu-id="3a0db-300">`false` - affinitize</span></span><br/><span data-ttu-id="3a0db-301">`true`-不將相似化為</span><span class="sxs-lookup"><span data-stu-id="3a0db-301">`true` - don't affinitize</span></span> | <span data-ttu-id="3a0db-302">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="3a0db-302">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="3a0db-303">範例：</span><span class="sxs-lookup"><span data-stu-id="3a0db-303">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="heap-limit"></a><span data-ttu-id="3a0db-304">堆積限制</span><span class="sxs-lookup"><span data-stu-id="3a0db-304">Heap limit</span></span>

- <span data-ttu-id="3a0db-305">指定 GC 堆積和 GC 簿記的認可大小上限（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="3a0db-305">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>
- <span data-ttu-id="3a0db-306">此設定僅適用于64位電腦。</span><span class="sxs-lookup"><span data-stu-id="3a0db-306">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="3a0db-307">如果設定了[每個物件堆積的限制](#per-object-heap-limits)，則會忽略此設定。</span><span class="sxs-lookup"><span data-stu-id="3a0db-307">This setting is ignored if the [Per-object-heap limits](#per-object-heap-limits) are configured.</span></span>
- <span data-ttu-id="3a0db-308">只有在特定情況下才適用的預設值是容器的 20 MB 或75% 的記憶體限制。</span><span class="sxs-lookup"><span data-stu-id="3a0db-308">The default value, which only applies in certain cases, is the greater of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="3a0db-309">預設值適用于下列情況：</span><span class="sxs-lookup"><span data-stu-id="3a0db-309">The default value applies if:</span></span>

  - <span data-ttu-id="3a0db-310">進程在具有指定記憶體限制的容器內執行。</span><span class="sxs-lookup"><span data-stu-id="3a0db-310">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="3a0db-311">未設定[HeapHardLimitPercent](#heap-limit-percent) 。</span><span class="sxs-lookup"><span data-stu-id="3a0db-311">[System.GC.HeapHardLimitPercent](#heap-limit-percent) is not set.</span></span>

| | <span data-ttu-id="3a0db-312">設定名稱</span><span class="sxs-lookup"><span data-stu-id="3a0db-312">Setting name</span></span> | <span data-ttu-id="3a0db-313">值</span><span class="sxs-lookup"><span data-stu-id="3a0db-313">Values</span></span> | <span data-ttu-id="3a0db-314">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3a0db-314">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="3a0db-315">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="3a0db-315">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="3a0db-316">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="3a0db-316">*decimal value*</span></span> | <span data-ttu-id="3a0db-317">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="3a0db-317">.NET Core 3.0</span></span> |
| <span data-ttu-id="3a0db-318">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="3a0db-318">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="3a0db-319">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="3a0db-319">*hexadecimal value*</span></span> | <span data-ttu-id="3a0db-320">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="3a0db-320">.NET Core 3.0</span></span> |

<span data-ttu-id="3a0db-321">範例：</span><span class="sxs-lookup"><span data-stu-id="3a0db-321">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimit": 209715200
      }
   }
}
```

> [!TIP]
> <span data-ttu-id="3a0db-322">如果您要在*runtimeconfig.js*中設定選項，請指定十進位值。</span><span class="sxs-lookup"><span data-stu-id="3a0db-322">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="3a0db-323">如果您要將選項設定為環境變數，請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="3a0db-323">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="3a0db-324">例如，若要指定200數量 (MiB) 的堆積固定限制，此值會是209715200，適用于 JSON 檔案，而0xC800000 或 C800000 則適用于環境變數。</span><span class="sxs-lookup"><span data-stu-id="3a0db-324">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="heap-limit-percent"></a><span data-ttu-id="3a0db-325">堆積限制百分比</span><span class="sxs-lookup"><span data-stu-id="3a0db-325">Heap limit percent</span></span>

- <span data-ttu-id="3a0db-326">指定允許的 GC 堆積使用量，以總實體記憶體的百分比表示。</span><span class="sxs-lookup"><span data-stu-id="3a0db-326">Specifies the allowable GC heap usage as a percentage of the total physical memory.</span></span>
- <span data-ttu-id="3a0db-327">如果也設定了[HeapHardLimit](#heap-limit) ，則會忽略此設定。</span><span class="sxs-lookup"><span data-stu-id="3a0db-327">If [System.GC.HeapHardLimit](#heap-limit) is also set, this setting is ignored.</span></span>
- <span data-ttu-id="3a0db-328">此設定僅適用于64位電腦。</span><span class="sxs-lookup"><span data-stu-id="3a0db-328">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="3a0db-329">如果處理常式是在具有指定記憶體限制的容器內執行，則會以該記憶體限制的百分比來計算百分比。</span><span class="sxs-lookup"><span data-stu-id="3a0db-329">If the process is running inside a container that has a specified memory limit, the percentage is calculated as a percentage of that memory limit.</span></span>
- <span data-ttu-id="3a0db-330">如果設定了[每個物件堆積的限制](#per-object-heap-limits)，則會忽略此設定。</span><span class="sxs-lookup"><span data-stu-id="3a0db-330">This setting is ignored if the [Per-object-heap limits](#per-object-heap-limits) are configured.</span></span>
- <span data-ttu-id="3a0db-331">只有在特定情況下才適用的預設值是容器上 20 MB 或75% 記憶體限制的較小者。</span><span class="sxs-lookup"><span data-stu-id="3a0db-331">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="3a0db-332">預設值適用于下列情況：</span><span class="sxs-lookup"><span data-stu-id="3a0db-332">The default value applies if:</span></span>

  - <span data-ttu-id="3a0db-333">進程在具有指定記憶體限制的容器內執行。</span><span class="sxs-lookup"><span data-stu-id="3a0db-333">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="3a0db-334">未設定[HeapHardLimit](#heap-limit) 。</span><span class="sxs-lookup"><span data-stu-id="3a0db-334">[System.GC.HeapHardLimit](#heap-limit) is not set.</span></span>

| | <span data-ttu-id="3a0db-335">設定名稱</span><span class="sxs-lookup"><span data-stu-id="3a0db-335">Setting name</span></span> | <span data-ttu-id="3a0db-336">值</span><span class="sxs-lookup"><span data-stu-id="3a0db-336">Values</span></span> | <span data-ttu-id="3a0db-337">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3a0db-337">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="3a0db-338">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="3a0db-338">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="3a0db-339">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="3a0db-339">*decimal value*</span></span> | <span data-ttu-id="3a0db-340">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="3a0db-340">.NET Core 3.0</span></span> |
| <span data-ttu-id="3a0db-341">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="3a0db-341">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="3a0db-342">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="3a0db-342">*hexadecimal value*</span></span> | <span data-ttu-id="3a0db-343">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="3a0db-343">.NET Core 3.0</span></span> |

<span data-ttu-id="3a0db-344">範例：</span><span class="sxs-lookup"><span data-stu-id="3a0db-344">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimitPercent": 30
      }
   }
}
```

> [!TIP]
> <span data-ttu-id="3a0db-345">如果您要在*runtimeconfig.js*中設定選項，請指定十進位值。</span><span class="sxs-lookup"><span data-stu-id="3a0db-345">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="3a0db-346">如果您要將選項設定為環境變數，請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="3a0db-346">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="3a0db-347">例如，若要將堆積使用量限制為30%，JSON 檔案的值會是30，而0x1E 或1E 則適用于環境變數。</span><span class="sxs-lookup"><span data-stu-id="3a0db-347">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="per-object-heap-limits"></a><span data-ttu-id="3a0db-348">每個物件的堆積限制</span><span class="sxs-lookup"><span data-stu-id="3a0db-348">Per-object-heap limits</span></span>

<span data-ttu-id="3a0db-349">您可以針對每個物件堆積指定 GC 的允許堆積使用方式。</span><span class="sxs-lookup"><span data-stu-id="3a0db-349">You can specify the GC's allowable heap usage on a per-object-heap basis.</span></span> <span data-ttu-id="3a0db-350">不同的堆積是大型物件堆積 (LOH) 、小型物件堆積 (SOH) ，以及釘選的物件堆積 (POH) 。</span><span class="sxs-lookup"><span data-stu-id="3a0db-350">The different heaps are the large object heap (LOH), small object heap (SOH), and pinned object heap (POH).</span></span>

- <span data-ttu-id="3a0db-351">如果您指定任何 `COMPLUS_GCHeapHardLimitSOH` 、 `COMPLUS_GCHeapHardLimitLOH` 或設定的值 `COMPLUS_GCHeapHardLimitPOH` ，您也必須指定和的值 `COMPLUS_GCHeapHardLimitSOH` `COMPLUS_GCHeapHardLimitLOH` 。</span><span class="sxs-lookup"><span data-stu-id="3a0db-351">If you specify a value for any of the `COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH`, or `COMPLUS_GCHeapHardLimitPOH` settings, you must also specify a value for `COMPLUS_GCHeapHardLimitSOH` and `COMPLUS_GCHeapHardLimitLOH`.</span></span> <span data-ttu-id="3a0db-352">如果您沒有這麼做，執行時間將無法初始化。</span><span class="sxs-lookup"><span data-stu-id="3a0db-352">If you don't, the runtime will fail to initialize.</span></span>
- <span data-ttu-id="3a0db-353">`COMPLUS_GCHeapHardLimitPOH` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="3a0db-353">The default value for `COMPLUS_GCHeapHardLimitPOH` is 0.</span></span> <span data-ttu-id="3a0db-354">`COMPLUS_GCHeapHardLimitSOH`和 `COMPLUS_GCHeapHardLimitLOH` 沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="3a0db-354">`COMPLUS_GCHeapHardLimitSOH` and `COMPLUS_GCHeapHardLimitLOH` don't have default values.</span></span>

| | <span data-ttu-id="3a0db-355">設定名稱</span><span class="sxs-lookup"><span data-stu-id="3a0db-355">Setting name</span></span> | <span data-ttu-id="3a0db-356">值</span><span class="sxs-lookup"><span data-stu-id="3a0db-356">Values</span></span> | <span data-ttu-id="3a0db-357">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3a0db-357">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="3a0db-358">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="3a0db-358">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitSOH` | <span data-ttu-id="3a0db-359">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="3a0db-359">*decimal value*</span></span> | <span data-ttu-id="3a0db-360">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="3a0db-360">.NET 5.0</span></span> |
| <span data-ttu-id="3a0db-361">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="3a0db-361">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitSOH` | <span data-ttu-id="3a0db-362">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="3a0db-362">*hexadecimal value*</span></span> | <span data-ttu-id="3a0db-363">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="3a0db-363">.NET 5.0</span></span> |

| | <span data-ttu-id="3a0db-364">設定名稱</span><span class="sxs-lookup"><span data-stu-id="3a0db-364">Setting name</span></span> | <span data-ttu-id="3a0db-365">值</span><span class="sxs-lookup"><span data-stu-id="3a0db-365">Values</span></span> | <span data-ttu-id="3a0db-366">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3a0db-366">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="3a0db-367">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="3a0db-367">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitLOH` | <span data-ttu-id="3a0db-368">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="3a0db-368">*decimal value*</span></span> | <span data-ttu-id="3a0db-369">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="3a0db-369">.NET 5.0</span></span> |
| <span data-ttu-id="3a0db-370">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="3a0db-370">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitLOH` | <span data-ttu-id="3a0db-371">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="3a0db-371">*hexadecimal value*</span></span> | <span data-ttu-id="3a0db-372">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="3a0db-372">.NET 5.0</span></span> |

| | <span data-ttu-id="3a0db-373">設定名稱</span><span class="sxs-lookup"><span data-stu-id="3a0db-373">Setting name</span></span> | <span data-ttu-id="3a0db-374">值</span><span class="sxs-lookup"><span data-stu-id="3a0db-374">Values</span></span> | <span data-ttu-id="3a0db-375">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3a0db-375">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="3a0db-376">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="3a0db-376">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPOH` | <span data-ttu-id="3a0db-377">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="3a0db-377">*decimal value*</span></span> | <span data-ttu-id="3a0db-378">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="3a0db-378">.NET 5.0</span></span> |
| <span data-ttu-id="3a0db-379">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="3a0db-379">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitPOH` | <span data-ttu-id="3a0db-380">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="3a0db-380">*hexadecimal value*</span></span> | <span data-ttu-id="3a0db-381">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="3a0db-381">.NET 5.0</span></span> |

> [!TIP]
> <span data-ttu-id="3a0db-382">如果您要在*runtimeconfig.js*中設定選項，請指定十進位值。</span><span class="sxs-lookup"><span data-stu-id="3a0db-382">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="3a0db-383">如果您要將選項設定為環境變數，請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="3a0db-383">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="3a0db-384">例如，若要指定200數量 (MiB) 的堆積固定限制，此值會是209715200，適用于 JSON 檔案，而0xC800000 或 C800000 則適用于環境變數。</span><span class="sxs-lookup"><span data-stu-id="3a0db-384">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="per-object-heap-limit-percents"></a><span data-ttu-id="3a0db-385">每個物件堆積限制百分比</span><span class="sxs-lookup"><span data-stu-id="3a0db-385">Per-object-heap limit percents</span></span>

<span data-ttu-id="3a0db-386">您可以針對每個物件堆積指定 GC 的允許堆積使用方式。</span><span class="sxs-lookup"><span data-stu-id="3a0db-386">You can specify the GC's allowable heap usage on a per-object-heap basis.</span></span> <span data-ttu-id="3a0db-387">不同的堆積是大型物件堆積 (LOH) 、小型物件堆積 (SOH) ，以及釘選的物件堆積 (POH) 。</span><span class="sxs-lookup"><span data-stu-id="3a0db-387">The different heaps are the large object heap (LOH), small object heap (SOH), and pinned object heap (POH).</span></span>

- <span data-ttu-id="3a0db-388">如果您指定任何 `COMPLUS_GCHeapHardLimitSOHPercent` 、 `COMPLUS_GCHeapHardLimitLOHPercent` 或設定的值 `COMPLUS_GCHeapHardLimitPOHPercent` ，您也必須指定和的值 `COMPLUS_GCHeapHardLimitSOHPercent` `COMPLUS_GCHeapHardLimitLOHPercent` 。</span><span class="sxs-lookup"><span data-stu-id="3a0db-388">If you specify a value for any of the `COMPLUS_GCHeapHardLimitSOHPercent`, `COMPLUS_GCHeapHardLimitLOHPercent`, or `COMPLUS_GCHeapHardLimitPOHPercent` settings, you must also specify a value for `COMPLUS_GCHeapHardLimitSOHPercent` and `COMPLUS_GCHeapHardLimitLOHPercent`.</span></span> <span data-ttu-id="3a0db-389">如果您沒有這麼做，執行時間將無法初始化。</span><span class="sxs-lookup"><span data-stu-id="3a0db-389">If you don't, the runtime will fail to initialize.</span></span>
- <span data-ttu-id="3a0db-390">如果 `COMPLUS_GCHeapHardLimitSOH` 指定、和，則會忽略這些設定 `COMPLUS_GCHeapHardLimitLOH` `COMPLUS_GCHeapHardLimitPOH` 。</span><span class="sxs-lookup"><span data-stu-id="3a0db-390">These settings are ignored if `COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH`, and `COMPLUS_GCHeapHardLimitPOH` are specified.</span></span>
- <span data-ttu-id="3a0db-391">值為1表示 GC 使用該物件堆積的總實體記憶體的1%。</span><span class="sxs-lookup"><span data-stu-id="3a0db-391">A value of 1 means that GC uses 1% of total physical memory for that object heap.</span></span>
- <span data-ttu-id="3a0db-392">每個值都必須大於零且小於100。</span><span class="sxs-lookup"><span data-stu-id="3a0db-392">Each value must be greater than zero and less than 100.</span></span> <span data-ttu-id="3a0db-393">此外，這三個百分比值的總和必須小於100。</span><span class="sxs-lookup"><span data-stu-id="3a0db-393">Additionally, the sum of the three percentage values must be less than 100.</span></span> <span data-ttu-id="3a0db-394">否則，執行時間將無法初始化。</span><span class="sxs-lookup"><span data-stu-id="3a0db-394">Otherwise, the runtime will fail to initialize.</span></span>

| | <span data-ttu-id="3a0db-395">設定名稱</span><span class="sxs-lookup"><span data-stu-id="3a0db-395">Setting name</span></span> | <span data-ttu-id="3a0db-396">值</span><span class="sxs-lookup"><span data-stu-id="3a0db-396">Values</span></span> | <span data-ttu-id="3a0db-397">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3a0db-397">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="3a0db-398">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="3a0db-398">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitSOHPercent` | <span data-ttu-id="3a0db-399">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="3a0db-399">*decimal value*</span></span> | <span data-ttu-id="3a0db-400">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="3a0db-400">.NET 5.0</span></span> |
| <span data-ttu-id="3a0db-401">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="3a0db-401">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitSOHPercent` | <span data-ttu-id="3a0db-402">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="3a0db-402">*hexadecimal value*</span></span> | <span data-ttu-id="3a0db-403">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="3a0db-403">.NET 5.0</span></span> |

| | <span data-ttu-id="3a0db-404">設定名稱</span><span class="sxs-lookup"><span data-stu-id="3a0db-404">Setting name</span></span> | <span data-ttu-id="3a0db-405">值</span><span class="sxs-lookup"><span data-stu-id="3a0db-405">Values</span></span> | <span data-ttu-id="3a0db-406">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3a0db-406">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="3a0db-407">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="3a0db-407">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitLOHPercent` | <span data-ttu-id="3a0db-408">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="3a0db-408">*decimal value*</span></span> | <span data-ttu-id="3a0db-409">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="3a0db-409">.NET 5.0</span></span> |
| <span data-ttu-id="3a0db-410">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="3a0db-410">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitLOHPercent` | <span data-ttu-id="3a0db-411">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="3a0db-411">*hexadecimal value*</span></span> | <span data-ttu-id="3a0db-412">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="3a0db-412">.NET 5.0</span></span> |

| | <span data-ttu-id="3a0db-413">設定名稱</span><span class="sxs-lookup"><span data-stu-id="3a0db-413">Setting name</span></span> | <span data-ttu-id="3a0db-414">值</span><span class="sxs-lookup"><span data-stu-id="3a0db-414">Values</span></span> | <span data-ttu-id="3a0db-415">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3a0db-415">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="3a0db-416">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="3a0db-416">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPOHPercent` | <span data-ttu-id="3a0db-417">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="3a0db-417">*decimal value*</span></span> | <span data-ttu-id="3a0db-418">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="3a0db-418">.NET 5.0</span></span> |
| <span data-ttu-id="3a0db-419">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="3a0db-419">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitPOHPercent` | <span data-ttu-id="3a0db-420">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="3a0db-420">*hexadecimal value*</span></span> | <span data-ttu-id="3a0db-421">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="3a0db-421">.NET 5.0</span></span> |

> [!TIP]
> <span data-ttu-id="3a0db-422">如果您要在*runtimeconfig.js*中設定選項，請指定十進位值。</span><span class="sxs-lookup"><span data-stu-id="3a0db-422">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="3a0db-423">如果您要將選項設定為環境變數，請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="3a0db-423">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="3a0db-424">例如，若要將堆積使用量限制為30%，JSON 檔案的值會是30，而0x1E 或1E 則適用于環境變數。</span><span class="sxs-lookup"><span data-stu-id="3a0db-424">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="high-memory-percent"></a><span data-ttu-id="3a0db-425">高記憶體百分比</span><span class="sxs-lookup"><span data-stu-id="3a0db-425">High memory percent</span></span>

<span data-ttu-id="3a0db-426">記憶體負載會以使用中的實體記憶體百分比表示。</span><span class="sxs-lookup"><span data-stu-id="3a0db-426">Memory load is indicated by the percentage of physical memory in use.</span></span> <span data-ttu-id="3a0db-427">根據預設，當實體記憶體負載達到**90%** 時，垃圾收集會更積極地執行完整、壓縮垃圾收集，以避免分頁。</span><span class="sxs-lookup"><span data-stu-id="3a0db-427">By default, when the physical memory load reaches **90%**, garbage collection becomes more aggressive about doing full, compacting garbage collections to avoid paging.</span></span> <span data-ttu-id="3a0db-428">當記憶體負載低於90% 時，GC 會優先使用完整垃圾收集的背景集合，其暫停時間較短，但不會減少總堆積大小。</span><span class="sxs-lookup"><span data-stu-id="3a0db-428">When memory load is below 90%, GC favors background collections for full garbage collections, which have shorter pauses but don't reduce the total heap size by much.</span></span> <span data-ttu-id="3a0db-429">在具有大量記憶體 (80 GB 或更) 的電腦上，預設負載閾值介於90% 到97% 之間。</span><span class="sxs-lookup"><span data-stu-id="3a0db-429">On machines with a significant amount of memory (80GB or more), the default load threshold is between 90% and 97%.</span></span>

<span data-ttu-id="3a0db-430">高記憶體負載閾值可以透過 `COMPlus_GCHighMemPercent` 環境變數或 JSON 設定來調整 `System.GC.HighMemoryPercent` 。</span><span class="sxs-lookup"><span data-stu-id="3a0db-430">The high memory load threshold can be adjusted by the `COMPlus_GCHighMemPercent` environment variable or `System.GC.HighMemoryPercent` JSON configuration setting.</span></span> <span data-ttu-id="3a0db-431">如果您想要控制堆積大小，請考慮調整閾值。</span><span class="sxs-lookup"><span data-stu-id="3a0db-431">Consider adjusting the threshold if you want to control heap size.</span></span> <span data-ttu-id="3a0db-432">例如，針對具有64GB 記憶體的電腦上的主要進程，當有10% 的可用記憶體時，GC 就可以開始做出反應。</span><span class="sxs-lookup"><span data-stu-id="3a0db-432">For example, for the dominant process on a machine with 64GB of memory, it's reasonable for GC to start reacting when there's 10% of memory available.</span></span> <span data-ttu-id="3a0db-433">但是對於較小的進程（例如，只耗用1GB 記憶體的處理常式），GC 很容易就能在沒有10% 的記憶體可用的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="3a0db-433">But for smaller processes, for example, a process that only consumes 1GB of memory, GC can comfortably run with less than 10% of memory available.</span></span> <span data-ttu-id="3a0db-434">針對這些較小的進程，請考慮設定較高的閾值。</span><span class="sxs-lookup"><span data-stu-id="3a0db-434">For these smaller processes, consider setting the threshold higher.</span></span> <span data-ttu-id="3a0db-435">另一方面，如果您想要讓較大的進程具有較小的堆積大小 (即使有足夠的實體記憶體可用) ，也能降低此臨界值，這是一個有效的方法，讓 GC 能夠更快地將堆積壓縮。</span><span class="sxs-lookup"><span data-stu-id="3a0db-435">On the other hand, if you want larger processes to have smaller heap sizes (even when there's plenty of physical memory available), lowering this threshold is an effective way for GC to react sooner to compact the heap down.</span></span>

> [!NOTE]
> <span data-ttu-id="3a0db-436">針對在容器中執行的進程，GC 會根據容器限制來考慮實體記憶體。</span><span class="sxs-lookup"><span data-stu-id="3a0db-436">For processes running in a container, GC considers the physical memory based on the container limit.</span></span>

| | <span data-ttu-id="3a0db-437">設定名稱</span><span class="sxs-lookup"><span data-stu-id="3a0db-437">Setting name</span></span> | <span data-ttu-id="3a0db-438">值</span><span class="sxs-lookup"><span data-stu-id="3a0db-438">Values</span></span> | <span data-ttu-id="3a0db-439">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3a0db-439">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="3a0db-440">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="3a0db-440">**runtimeconfig.json**</span></span> | `System.GC.HighMemoryPercent` | <span data-ttu-id="3a0db-441">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="3a0db-441">*decimal value*</span></span> | <span data-ttu-id="3a0db-442">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="3a0db-442">.NET 5.0</span></span> |
| <span data-ttu-id="3a0db-443">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="3a0db-443">**Environment variable**</span></span> | `COMPlus_GCHighMemPercent` | <span data-ttu-id="3a0db-444">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="3a0db-444">*hexadecimal value*</span></span> | |

> [!TIP]
> <span data-ttu-id="3a0db-445">如果您要在*runtimeconfig.js*中設定選項，請指定十進位值。</span><span class="sxs-lookup"><span data-stu-id="3a0db-445">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="3a0db-446">如果您要將選項設定為環境變數，請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="3a0db-446">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="3a0db-447">例如，若要將高記憶體閾值設定為75%，JSON 檔案的值會是75，而0x4B 或4B 則適用于環境變數。</span><span class="sxs-lookup"><span data-stu-id="3a0db-447">For example, to set the high memory threshold to 75%, the values would be 75 for the JSON file and 0x4B or 4B for the environment variable.</span></span>

### <a name="retain-vm"></a><span data-ttu-id="3a0db-448">保留 VM</span><span class="sxs-lookup"><span data-stu-id="3a0db-448">Retain VM</span></span>

- <span data-ttu-id="3a0db-449">設定是否要將應該刪除的區段放在待命清單上以供日後使用，或是釋放給作業系統 (作業系統) 。</span><span class="sxs-lookup"><span data-stu-id="3a0db-449">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="3a0db-450">預設值：將區段釋放回作業系統。</span><span class="sxs-lookup"><span data-stu-id="3a0db-450">Default: Release segments back to the operating system.</span></span> <span data-ttu-id="3a0db-451">這相當於將值設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="3a0db-451">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="3a0db-452">設定名稱</span><span class="sxs-lookup"><span data-stu-id="3a0db-452">Setting name</span></span> | <span data-ttu-id="3a0db-453">值</span><span class="sxs-lookup"><span data-stu-id="3a0db-453">Values</span></span> | <span data-ttu-id="3a0db-454">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3a0db-454">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="3a0db-455">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="3a0db-455">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="3a0db-456">`false`-發行至 OS</span><span class="sxs-lookup"><span data-stu-id="3a0db-456">`false` - release to OS</span></span><br/><span data-ttu-id="3a0db-457">`true`-put 待命</span><span class="sxs-lookup"><span data-stu-id="3a0db-457">`true` - put on standby</span></span> | <span data-ttu-id="3a0db-458">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="3a0db-458">.NET Core 1.0</span></span> |
| <span data-ttu-id="3a0db-459">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="3a0db-459">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="3a0db-460">`false`-發行至 OS</span><span class="sxs-lookup"><span data-stu-id="3a0db-460">`false` - release to OS</span></span><br/><span data-ttu-id="3a0db-461">`true`-put 待命</span><span class="sxs-lookup"><span data-stu-id="3a0db-461">`true` - put on standby</span></span> | <span data-ttu-id="3a0db-462">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="3a0db-462">.NET Core 1.0</span></span> |
| <span data-ttu-id="3a0db-463">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="3a0db-463">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="3a0db-464">`0`-發行至 OS</span><span class="sxs-lookup"><span data-stu-id="3a0db-464">`0` - release to OS</span></span><br/><span data-ttu-id="3a0db-465">`1`-put 待命</span><span class="sxs-lookup"><span data-stu-id="3a0db-465">`1` - put on standby</span></span> | <span data-ttu-id="3a0db-466">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="3a0db-466">.NET Core 1.0</span></span> |

#### <a name="examples"></a><span data-ttu-id="3a0db-467">範例</span><span class="sxs-lookup"><span data-stu-id="3a0db-467">Examples</span></span>

<span data-ttu-id="3a0db-468">檔案*上的runtimeconfig.js* ：</span><span class="sxs-lookup"><span data-stu-id="3a0db-468">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="3a0db-469">專案檔：</span><span class="sxs-lookup"><span data-stu-id="3a0db-469">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="3a0db-470">大型頁面</span><span class="sxs-lookup"><span data-stu-id="3a0db-470">Large pages</span></span>

- <span data-ttu-id="3a0db-471">指定在設定堆積固定限制時是否應該使用大型分頁。</span><span class="sxs-lookup"><span data-stu-id="3a0db-471">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="3a0db-472">預設值：設定堆積固定限制時，請勿使用大型頁面。</span><span class="sxs-lookup"><span data-stu-id="3a0db-472">Default: Don't use large pages when a heap hard limit is set.</span></span> <span data-ttu-id="3a0db-473">這相當於將值設定為 `0` 。</span><span class="sxs-lookup"><span data-stu-id="3a0db-473">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="3a0db-474">這是實驗性設定。</span><span class="sxs-lookup"><span data-stu-id="3a0db-474">This is an experimental setting.</span></span>

| | <span data-ttu-id="3a0db-475">設定名稱</span><span class="sxs-lookup"><span data-stu-id="3a0db-475">Setting name</span></span> | <span data-ttu-id="3a0db-476">值</span><span class="sxs-lookup"><span data-stu-id="3a0db-476">Values</span></span> | <span data-ttu-id="3a0db-477">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3a0db-477">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="3a0db-478">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="3a0db-478">**runtimeconfig.json**</span></span> | <span data-ttu-id="3a0db-479">N/A</span><span class="sxs-lookup"><span data-stu-id="3a0db-479">N/A</span></span> | <span data-ttu-id="3a0db-480">N/A</span><span class="sxs-lookup"><span data-stu-id="3a0db-480">N/A</span></span> | <span data-ttu-id="3a0db-481">N/A</span><span class="sxs-lookup"><span data-stu-id="3a0db-481">N/A</span></span> |
| <span data-ttu-id="3a0db-482">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="3a0db-482">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="3a0db-483">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="3a0db-483">`0` - disabled</span></span><br/><span data-ttu-id="3a0db-484">`1`-已啟用</span><span class="sxs-lookup"><span data-stu-id="3a0db-484">`1` - enabled</span></span> | <span data-ttu-id="3a0db-485">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="3a0db-485">.NET Core 3.0</span></span> |

## <a name="allow-large-objects"></a><span data-ttu-id="3a0db-486">允許大型物件</span><span class="sxs-lookup"><span data-stu-id="3a0db-486">Allow large objects</span></span>

- <span data-ttu-id="3a0db-487">針對大於 2 gb (GB) 大小的陣列，設定64位平臺上的垃圾收集行程支援。</span><span class="sxs-lookup"><span data-stu-id="3a0db-487">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="3a0db-488">預設值： GC 支援大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="3a0db-488">Default: GC supports arrays greater than 2-GB.</span></span> <span data-ttu-id="3a0db-489">這相當於將值設定為 `1` 。</span><span class="sxs-lookup"><span data-stu-id="3a0db-489">This is equivalent to setting the value to `1`.</span></span>
- <span data-ttu-id="3a0db-490">在未來的 .NET 版本中，此選項可能會過時。</span><span class="sxs-lookup"><span data-stu-id="3a0db-490">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="3a0db-491">設定名稱</span><span class="sxs-lookup"><span data-stu-id="3a0db-491">Setting name</span></span> | <span data-ttu-id="3a0db-492">值</span><span class="sxs-lookup"><span data-stu-id="3a0db-492">Values</span></span> | <span data-ttu-id="3a0db-493">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3a0db-493">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="3a0db-494">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="3a0db-494">**runtimeconfig.json**</span></span> | <span data-ttu-id="3a0db-495">N/A</span><span class="sxs-lookup"><span data-stu-id="3a0db-495">N/A</span></span> | <span data-ttu-id="3a0db-496">N/A</span><span class="sxs-lookup"><span data-stu-id="3a0db-496">N/A</span></span> | <span data-ttu-id="3a0db-497">N/A</span><span class="sxs-lookup"><span data-stu-id="3a0db-497">N/A</span></span> |
| <span data-ttu-id="3a0db-498">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="3a0db-498">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="3a0db-499">`1`-已啟用</span><span class="sxs-lookup"><span data-stu-id="3a0db-499">`1` - enabled</span></span><br/> <span data-ttu-id="3a0db-500">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="3a0db-500">`0` - disabled</span></span> | <span data-ttu-id="3a0db-501">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="3a0db-501">.NET Core 1.0</span></span> |
| <span data-ttu-id="3a0db-502">**.NET Framework 的app.config**</span><span class="sxs-lookup"><span data-stu-id="3a0db-502">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="3a0db-503">Gcallowverylargeobjects></span><span class="sxs-lookup"><span data-stu-id="3a0db-503">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="3a0db-504">`1`-已啟用</span><span class="sxs-lookup"><span data-stu-id="3a0db-504">`1` - enabled</span></span><br/> <span data-ttu-id="3a0db-505">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="3a0db-505">`0` - disabled</span></span> | <span data-ttu-id="3a0db-506">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="3a0db-506">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="3a0db-507">大型物件堆積閾值</span><span class="sxs-lookup"><span data-stu-id="3a0db-507">Large object heap threshold</span></span>

- <span data-ttu-id="3a0db-508">指定導致物件在大型物件堆積上執行的臨界值大小（以位元組為單位） (LOH) 。</span><span class="sxs-lookup"><span data-stu-id="3a0db-508">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="3a0db-509">預設閾值為85000個位元組。</span><span class="sxs-lookup"><span data-stu-id="3a0db-509">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="3a0db-510">您指定的值必須大於預設閾值。</span><span class="sxs-lookup"><span data-stu-id="3a0db-510">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="3a0db-511">設定名稱</span><span class="sxs-lookup"><span data-stu-id="3a0db-511">Setting name</span></span> | <span data-ttu-id="3a0db-512">值</span><span class="sxs-lookup"><span data-stu-id="3a0db-512">Values</span></span> | <span data-ttu-id="3a0db-513">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3a0db-513">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="3a0db-514">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="3a0db-514">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="3a0db-515">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="3a0db-515">*decimal value*</span></span> | <span data-ttu-id="3a0db-516">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="3a0db-516">.NET Core 1.0</span></span> |
| <span data-ttu-id="3a0db-517">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="3a0db-517">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="3a0db-518">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="3a0db-518">*hexadecimal value*</span></span> | <span data-ttu-id="3a0db-519">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="3a0db-519">.NET Core 1.0</span></span> |
| <span data-ttu-id="3a0db-520">**.NET Framework 的app.config**</span><span class="sxs-lookup"><span data-stu-id="3a0db-520">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="3a0db-521">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="3a0db-521">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="3a0db-522">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="3a0db-522">*decimal value*</span></span> | <span data-ttu-id="3a0db-523">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="3a0db-523">.NET Framework 4.8</span></span> |

<span data-ttu-id="3a0db-524">範例：</span><span class="sxs-lookup"><span data-stu-id="3a0db-524">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.LOHThreshold": 120000
      }
   }
}
```

> [!TIP]
> <span data-ttu-id="3a0db-525">如果您要在*runtimeconfig.js*中設定選項，請指定十進位值。</span><span class="sxs-lookup"><span data-stu-id="3a0db-525">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="3a0db-526">如果您要將選項設定為環境變數，請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="3a0db-526">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="3a0db-527">例如，若要設定120000個位元組的閾值大小，JSON 檔案的值會是120000，而環境變數的值則是0x1D4C0 或1D4C0。</span><span class="sxs-lookup"><span data-stu-id="3a0db-527">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="3a0db-528">獨立 GC</span><span class="sxs-lookup"><span data-stu-id="3a0db-528">Standalone GC</span></span>

- <span data-ttu-id="3a0db-529">指定包含執行時間打算載入之垃圾收集行程的程式庫路徑。</span><span class="sxs-lookup"><span data-stu-id="3a0db-529">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="3a0db-530">如需詳細資訊，請參閱[獨立 GC 載入器設計](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md)。</span><span class="sxs-lookup"><span data-stu-id="3a0db-530">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="3a0db-531">設定名稱</span><span class="sxs-lookup"><span data-stu-id="3a0db-531">Setting name</span></span> | <span data-ttu-id="3a0db-532">值</span><span class="sxs-lookup"><span data-stu-id="3a0db-532">Values</span></span> | <span data-ttu-id="3a0db-533">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3a0db-533">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="3a0db-534">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="3a0db-534">**runtimeconfig.json**</span></span> | <span data-ttu-id="3a0db-535">N/A</span><span class="sxs-lookup"><span data-stu-id="3a0db-535">N/A</span></span> | <span data-ttu-id="3a0db-536">N/A</span><span class="sxs-lookup"><span data-stu-id="3a0db-536">N/A</span></span> | <span data-ttu-id="3a0db-537">N/A</span><span class="sxs-lookup"><span data-stu-id="3a0db-537">N/A</span></span> |
| <span data-ttu-id="3a0db-538">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="3a0db-538">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="3a0db-539">*string_path*</span><span class="sxs-lookup"><span data-stu-id="3a0db-539">*string_path*</span></span> | <span data-ttu-id="3a0db-540">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="3a0db-540">.NET Core 2.0</span></span> |
