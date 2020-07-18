---
title: 垃圾收集行程 config 設定
description: 瞭解用來設定垃圾收集行程如何管理 .NET Core 應用程式記憶體的執行時間設定。
ms.date: 07/10/2020
ms.topic: reference
ms.openlocfilehash: 6ae5b7447fb0df4978ea9dcaa5e76fcc7a6cc4ca
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441399"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="f4f2c-103">用於垃圾收集的執行時間設定選項</span><span class="sxs-lookup"><span data-stu-id="f4f2c-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="f4f2c-104">此頁面包含可在執行時間變更之垃圾收集行程（GC）設定的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="f4f2c-105">如果您正嘗試達到執行中應用程式的尖峰效能，請考慮使用這些設定。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="f4f2c-106">不過，在一般情況下，預設值可為大部分的應用程式提供最佳效能。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="f4f2c-107">這些設定會依此頁面的群組排列。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="f4f2c-108">每個群組內的設定通常會彼此搭配使用，以達成特定結果。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="f4f2c-109">這些設定也可以在應用程式執行時動態變更，因此您設定的任何執行時間設定可能會遭到覆寫。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="f4f2c-110">某些設定（例如[延遲層級](../../standard/garbage-collection/latency.md)）通常只會在設計階段透過 API 進行設定。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="f4f2c-111">此頁面會省略這類設定。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="f4f2c-112">針對 [數值]，在 [檔案中的*runtimeconfig.js* ] 和 [用於環境變數的十六進位標記法] 設定中，使用十進位標記來進行設定。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="f4f2c-113">若為十六進位值，您可以使用或不搭配 "0x" 前置詞來指定它們。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="f4f2c-114">垃圾收集的種類</span><span class="sxs-lookup"><span data-stu-id="f4f2c-114">Flavors of garbage collection</span></span>

<span data-ttu-id="f4f2c-115">垃圾收集的兩個主要類別是工作站 GC 和伺服器 GC。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="f4f2c-116">如需兩者之間差異的詳細資訊，請參閱[工作站和伺服器垃圾收集](../../standard/garbage-collection/workstation-server-gc.md)。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-116">For more information about differences between the two, see [Workstation and server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span>

<span data-ttu-id="f4f2c-117">垃圾收集的 subflavors 是背景和非並行的。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="f4f2c-118">使用下列設定來選取垃圾收集的種類：</span><span class="sxs-lookup"><span data-stu-id="f4f2c-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="f4f2c-119">System.web/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="f4f2c-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="f4f2c-120">設定應用程式是否使用工作站垃圾收集或伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="f4f2c-121">預設值：工作站垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-121">Default: Workstation garbage collection.</span></span> <span data-ttu-id="f4f2c-122">這相當於將值設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-122">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="f4f2c-123">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f4f2c-123">Setting name</span></span> | <span data-ttu-id="f4f2c-124">值</span><span class="sxs-lookup"><span data-stu-id="f4f2c-124">Values</span></span> | <span data-ttu-id="f4f2c-125">引進的版本</span><span class="sxs-lookup"><span data-stu-id="f4f2c-125">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f4f2c-126">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-126">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="f4f2c-127">`false`-工作站</span><span class="sxs-lookup"><span data-stu-id="f4f2c-127">`false` - workstation</span></span><br/><span data-ttu-id="f4f2c-128">`true`-伺服器</span><span class="sxs-lookup"><span data-stu-id="f4f2c-128">`true` - server</span></span> | <span data-ttu-id="f4f2c-129">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-129">.NET Core 1.0</span></span> |
| <span data-ttu-id="f4f2c-130">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-130">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="f4f2c-131">`false`-工作站</span><span class="sxs-lookup"><span data-stu-id="f4f2c-131">`false` - workstation</span></span><br/><span data-ttu-id="f4f2c-132">`true`-伺服器</span><span class="sxs-lookup"><span data-stu-id="f4f2c-132">`true` - server</span></span> | <span data-ttu-id="f4f2c-133">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-133">.NET Core 1.0</span></span> |
| <span data-ttu-id="f4f2c-134">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-134">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="f4f2c-135">`0`-工作站</span><span class="sxs-lookup"><span data-stu-id="f4f2c-135">`0` - workstation</span></span><br/><span data-ttu-id="f4f2c-136">`1`-伺服器</span><span class="sxs-lookup"><span data-stu-id="f4f2c-136">`1` - server</span></span> | <span data-ttu-id="f4f2c-137">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-137">.NET Core 1.0</span></span> |
| <span data-ttu-id="f4f2c-138">**.NET Framework 的app.config**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-138">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f4f2c-139">GCServer</span><span class="sxs-lookup"><span data-stu-id="f4f2c-139">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="f4f2c-140">`false`-工作站</span><span class="sxs-lookup"><span data-stu-id="f4f2c-140">`false` - workstation</span></span><br/><span data-ttu-id="f4f2c-141">`true`-伺服器</span><span class="sxs-lookup"><span data-stu-id="f4f2c-141">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="f4f2c-142">範例</span><span class="sxs-lookup"><span data-stu-id="f4f2c-142">Examples</span></span>

<span data-ttu-id="f4f2c-143">檔案*上的runtimeconfig.js* ：</span><span class="sxs-lookup"><span data-stu-id="f4f2c-143">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="f4f2c-144">專案檔：</span><span class="sxs-lookup"><span data-stu-id="f4f2c-144">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="f4f2c-145">System.web/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="f4f2c-145">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="f4f2c-146">設定是否啟用背景（並行）垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-146">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="f4f2c-147">預設值：使用背景 GC。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-147">Default: Use background GC.</span></span> <span data-ttu-id="f4f2c-148">這相當於將值設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-148">This is equivalent to setting the value to `true`.</span></span>
- <span data-ttu-id="f4f2c-149">如需詳細資訊，請參閱[背景垃圾收集](../../standard/garbage-collection/background-gc.md)。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-149">For more information, see [Background garbage collection](../../standard/garbage-collection/background-gc.md).</span></span>

| | <span data-ttu-id="f4f2c-150">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f4f2c-150">Setting name</span></span> | <span data-ttu-id="f4f2c-151">值</span><span class="sxs-lookup"><span data-stu-id="f4f2c-151">Values</span></span> | <span data-ttu-id="f4f2c-152">引進的版本</span><span class="sxs-lookup"><span data-stu-id="f4f2c-152">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f4f2c-153">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-153">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="f4f2c-154">`true`-背景 GC</span><span class="sxs-lookup"><span data-stu-id="f4f2c-154">`true` - background GC</span></span><br/><span data-ttu-id="f4f2c-155">`false`-非並行 GC</span><span class="sxs-lookup"><span data-stu-id="f4f2c-155">`false` - non-concurrent GC</span></span> | <span data-ttu-id="f4f2c-156">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-156">.NET Core 1.0</span></span> |
| <span data-ttu-id="f4f2c-157">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-157">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="f4f2c-158">`true`-背景 GC</span><span class="sxs-lookup"><span data-stu-id="f4f2c-158">`true` - background GC</span></span><br/><span data-ttu-id="f4f2c-159">`false`-非並行 GC</span><span class="sxs-lookup"><span data-stu-id="f4f2c-159">`false` - non-concurrent GC</span></span> | <span data-ttu-id="f4f2c-160">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-160">.NET Core 1.0</span></span> |
| <span data-ttu-id="f4f2c-161">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-161">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="f4f2c-162">`1`-背景 GC</span><span class="sxs-lookup"><span data-stu-id="f4f2c-162">`1` - background GC</span></span><br/><span data-ttu-id="f4f2c-163">`0`-非並行 GC</span><span class="sxs-lookup"><span data-stu-id="f4f2c-163">`0` - non-concurrent GC</span></span> | <span data-ttu-id="f4f2c-164">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-164">.NET Core 1.0</span></span> |
| <span data-ttu-id="f4f2c-165">**.NET Framework 的app.config**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-165">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f4f2c-166">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="f4f2c-166">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="f4f2c-167">`true`-背景 GC</span><span class="sxs-lookup"><span data-stu-id="f4f2c-167">`true` - background GC</span></span><br/><span data-ttu-id="f4f2c-168">`false`-非並行 GC</span><span class="sxs-lookup"><span data-stu-id="f4f2c-168">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="f4f2c-169">範例</span><span class="sxs-lookup"><span data-stu-id="f4f2c-169">Examples</span></span>

<span data-ttu-id="f4f2c-170">檔案*上的runtimeconfig.js* ：</span><span class="sxs-lookup"><span data-stu-id="f4f2c-170">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="f4f2c-171">專案檔：</span><span class="sxs-lookup"><span data-stu-id="f4f2c-171">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="f4f2c-172">管理資源使用量</span><span class="sxs-lookup"><span data-stu-id="f4f2c-172">Manage resource usage</span></span>

<span data-ttu-id="f4f2c-173">使用本節所述的設定來管理垃圾收集行程的記憶體和處理器使用量。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-173">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="f4f2c-174">如需有關這些設定的詳細資訊，請參閱[工作站與伺服器 GC 之間的中間](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/)專案 blog。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-174">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="f4f2c-175">HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="f4f2c-175">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="f4f2c-176">限制垃圾收集行程所建立的堆積數目。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-176">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="f4f2c-177">僅適用于伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-177">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="f4f2c-178">如果已啟用[GC 處理器親和性](#systemgcnoaffinitizecomplus_gcnoaffinitize)（這是預設值），則堆積計數會將如何 `n` GC 堆積/執行緒設定為第一個 `n` 處理器。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-178">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="f4f2c-179">（使用[將相似化為 mask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask)或[將相似化為範圍](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges)設定，以確切指定要將相似化為的處理器）。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-179">(Use the [affinitize mask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) or [affinitize ranges](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="f4f2c-180">如果停用[gc 處理器親和性](#systemgcnoaffinitizecomplus_gcnoaffinitize)，這項設定會限制 gc 堆積的數目。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-180">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="f4f2c-181">如需詳細資訊，請參閱[GCHeapCount 備註](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks)。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-181">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="f4f2c-182">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f4f2c-182">Setting name</span></span> | <span data-ttu-id="f4f2c-183">值</span><span class="sxs-lookup"><span data-stu-id="f4f2c-183">Values</span></span> | <span data-ttu-id="f4f2c-184">引進的版本</span><span class="sxs-lookup"><span data-stu-id="f4f2c-184">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f4f2c-185">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-185">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="f4f2c-186">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="f4f2c-186">*decimal value*</span></span> | <span data-ttu-id="f4f2c-187">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-187">.NET Core 3.0</span></span> |
| <span data-ttu-id="f4f2c-188">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-188">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="f4f2c-189">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="f4f2c-189">*hexadecimal value*</span></span> | <span data-ttu-id="f4f2c-190">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-190">.NET Core 3.0</span></span> |
| <span data-ttu-id="f4f2c-191">**.NET Framework 的app.config**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-191">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f4f2c-192">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="f4f2c-192">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="f4f2c-193">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="f4f2c-193">*decimal value*</span></span> | <span data-ttu-id="f4f2c-194">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="f4f2c-194">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="f4f2c-195">範例：</span><span class="sxs-lookup"><span data-stu-id="f4f2c-195">Example:</span></span>

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
> <span data-ttu-id="f4f2c-196">如果您要在*runtimeconfig.js*中設定選項，請指定十進位值。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-196">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="f4f2c-197">如果您要將選項設定為環境變數，請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-197">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="f4f2c-198">例如，若要將堆積數目限制為16，JSON 檔案的值會是16，而環境變數的值則是0x10 或10。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-198">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="f4f2c-199">HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="f4f2c-199">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="f4f2c-200">指定垃圾收集行程執行緒應該使用的確切處理器。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-200">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="f4f2c-201">如果停用[GC 處理器親和性](#systemgcnoaffinitizecomplus_gcnoaffinitize)，則會忽略此設定。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-201">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="f4f2c-202">僅適用于伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-202">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="f4f2c-203">值是一個位元遮罩，用來定義進程可用的處理器。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-203">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="f4f2c-204">例如，十進位值1023（如果您使用環境變數，則為0x3FF 或3FF 的十六進位值）是 0011 1111 1111 （二進位標記法）。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-204">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="f4f2c-205">這會指定要使用前10個處理器。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-205">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="f4f2c-206">若要指定接下來的10個處理器（也就是處理器10-19），請指定十進位值1047552（或0xFFC00 或 FFC00 的十六進位值），這相當於二進位值 1111 1111 1100 0000 0000。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-206">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="f4f2c-207">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f4f2c-207">Setting name</span></span> | <span data-ttu-id="f4f2c-208">值</span><span class="sxs-lookup"><span data-stu-id="f4f2c-208">Values</span></span> | <span data-ttu-id="f4f2c-209">引進的版本</span><span class="sxs-lookup"><span data-stu-id="f4f2c-209">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f4f2c-210">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-210">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="f4f2c-211">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="f4f2c-211">*decimal value*</span></span> | <span data-ttu-id="f4f2c-212">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-212">.NET Core 3.0</span></span> |
| <span data-ttu-id="f4f2c-213">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-213">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="f4f2c-214">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="f4f2c-214">*hexadecimal value*</span></span> | <span data-ttu-id="f4f2c-215">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-215">.NET Core 3.0</span></span> |
| <span data-ttu-id="f4f2c-216">**.NET Framework 的app.config**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-216">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f4f2c-217">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="f4f2c-217">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="f4f2c-218">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="f4f2c-218">*decimal value*</span></span> | <span data-ttu-id="f4f2c-219">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="f4f2c-219">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="f4f2c-220">範例：</span><span class="sxs-lookup"><span data-stu-id="f4f2c-220">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="f4f2c-221">GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="f4f2c-221">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="f4f2c-222">指定要用於垃圾收集行程執行緒的處理器清單。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-222">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="f4f2c-223">此設定類似[HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask)，不同之處在于它可讓您指定64個以上的處理器。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-223">This setting is similar to [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="f4f2c-224">若是 Windows 作業系統，請在處理器編號或範圍前面加上對應的[CPU 群組](/windows/win32/procthread/processor-groups)，例如 "0： 1-10，0：12，1： 50-52，1： 70"。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-224">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="f4f2c-225">如果停用[GC 處理器親和性](#systemgcnoaffinitizecomplus_gcnoaffinitize)，則會忽略此設定。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-225">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="f4f2c-226">僅適用于伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-226">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="f4f2c-227">如需詳細資訊，請參閱 Maoni Stephens 的 blog 上的[針對具有 > 64 cpu 的電腦，讓 CPU 設定更好用於 GC](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) 。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-227">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="f4f2c-228">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f4f2c-228">Setting name</span></span> | <span data-ttu-id="f4f2c-229">值</span><span class="sxs-lookup"><span data-stu-id="f4f2c-229">Values</span></span> | <span data-ttu-id="f4f2c-230">引進的版本</span><span class="sxs-lookup"><span data-stu-id="f4f2c-230">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f4f2c-231">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-231">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="f4f2c-232">以逗號分隔的處理器編號或處理器編號範圍清單。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-232">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="f4f2c-233">Unix 範例： "1-10，12，50-52，70"</span><span class="sxs-lookup"><span data-stu-id="f4f2c-233">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="f4f2c-234">Windows 範例： "0： 1-10，0：12，1： 50-52，1： 70"</span><span class="sxs-lookup"><span data-stu-id="f4f2c-234">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="f4f2c-235">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-235">.NET Core 3.0</span></span> |
| <span data-ttu-id="f4f2c-236">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-236">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="f4f2c-237">以逗號分隔的處理器編號或處理器編號範圍清單。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-237">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="f4f2c-238">Unix 範例： "1-10，12，50-52，70"</span><span class="sxs-lookup"><span data-stu-id="f4f2c-238">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="f4f2c-239">Windows 範例： "0： 1-10，0：12，1： 50-52，1： 70"</span><span class="sxs-lookup"><span data-stu-id="f4f2c-239">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="f4f2c-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-240">.NET Core 3.0</span></span> |

<span data-ttu-id="f4f2c-241">範例：</span><span class="sxs-lookup"><span data-stu-id="f4f2c-241">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="f4f2c-242">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="f4f2c-242">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="f4f2c-243">設定垃圾收集行程是否使用[CPU 群組](/windows/win32/procthread/processor-groups)。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-243">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="f4f2c-244">當64位 Windows 電腦具有多個 CPU 群組（也就是，有超過64個處理器）時，啟用這個元素會延伸所有 CPU 群組的垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-244">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="f4f2c-245">垃圾收集行程會使用所有核心來建立和平衡堆積。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-245">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="f4f2c-246">僅適用于64位 Windows 作業系統上的伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-246">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="f4f2c-247">預設值： GC 不會跨越 CPU 群組延伸。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-247">Default: GC does not extend across CPU groups.</span></span> <span data-ttu-id="f4f2c-248">這相當於將值設定為 `0` 。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-248">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="f4f2c-249">如需詳細資訊，請參閱 Maoni Stephens 的 blog 上的[針對具有 > 64 cpu 的電腦，讓 CPU 設定更好用於 GC](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) 。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-249">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="f4f2c-250">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f4f2c-250">Setting name</span></span> | <span data-ttu-id="f4f2c-251">值</span><span class="sxs-lookup"><span data-stu-id="f4f2c-251">Values</span></span> | <span data-ttu-id="f4f2c-252">引進的版本</span><span class="sxs-lookup"><span data-stu-id="f4f2c-252">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f4f2c-253">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-253">**runtimeconfig.json**</span></span> | <span data-ttu-id="f4f2c-254">N/A</span><span class="sxs-lookup"><span data-stu-id="f4f2c-254">N/A</span></span> | <span data-ttu-id="f4f2c-255">N/A</span><span class="sxs-lookup"><span data-stu-id="f4f2c-255">N/A</span></span> | <span data-ttu-id="f4f2c-256">N/A</span><span class="sxs-lookup"><span data-stu-id="f4f2c-256">N/A</span></span> |
| <span data-ttu-id="f4f2c-257">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-257">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="f4f2c-258">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="f4f2c-258">`0` - disabled</span></span><br/><span data-ttu-id="f4f2c-259">`1`-已啟用</span><span class="sxs-lookup"><span data-stu-id="f4f2c-259">`1` - enabled</span></span> | <span data-ttu-id="f4f2c-260">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-260">.NET Core 1.0</span></span> |
| <span data-ttu-id="f4f2c-261">**.NET Framework 的app.config**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-261">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f4f2c-262">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="f4f2c-262">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="f4f2c-263">`false`-已停用</span><span class="sxs-lookup"><span data-stu-id="f4f2c-263">`false` - disabled</span></span><br/><span data-ttu-id="f4f2c-264">`true`-已啟用</span><span class="sxs-lookup"><span data-stu-id="f4f2c-264">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="f4f2c-265">若要將 common language runtime （CLR）設定為同時將執行緒集區中的執行緒散發到所有 CPU 群組，請啟用 [ [Thread_UseAllCpuGroups 元素](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)] 選項。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-265">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="f4f2c-266">針對 .NET Core 應用程式，您可以將環境變數的值設定為，以啟用此選項 `COMPlus_Thread_UseAllCpuGroups` `1` 。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-266">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="f4f2c-267">NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="f4f2c-267">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="f4f2c-268">指定是否要使用處理器*將相似化為*垃圾收集執行緒。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-268">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="f4f2c-269">若要將相似化為 GC 執行緒，這表示它只能在其特定的 CPU 上執行。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-269">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="f4f2c-270">會針對每個 GC 執行緒建立堆積。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-270">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="f4f2c-271">僅適用于伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-271">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="f4f2c-272">預設值：使用處理器將相似化為垃圾收集執行緒。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-272">Default: Affinitize garbage collection threads with processors.</span></span> <span data-ttu-id="f4f2c-273">這相當於將值設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-273">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="f4f2c-274">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f4f2c-274">Setting name</span></span> | <span data-ttu-id="f4f2c-275">值</span><span class="sxs-lookup"><span data-stu-id="f4f2c-275">Values</span></span> | <span data-ttu-id="f4f2c-276">引進的版本</span><span class="sxs-lookup"><span data-stu-id="f4f2c-276">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f4f2c-277">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-277">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="f4f2c-278">`false`-將相似化為</span><span class="sxs-lookup"><span data-stu-id="f4f2c-278">`false` - affinitize</span></span><br/><span data-ttu-id="f4f2c-279">`true`-不將相似化為</span><span class="sxs-lookup"><span data-stu-id="f4f2c-279">`true` - don't affinitize</span></span> | <span data-ttu-id="f4f2c-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="f4f2c-281">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-281">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="f4f2c-282">`0`-將相似化為</span><span class="sxs-lookup"><span data-stu-id="f4f2c-282">`0` - affinitize</span></span><br/><span data-ttu-id="f4f2c-283">`1`-不將相似化為</span><span class="sxs-lookup"><span data-stu-id="f4f2c-283">`1` - don't affinitize</span></span> | <span data-ttu-id="f4f2c-284">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-284">.NET Core 3.0</span></span> |
| <span data-ttu-id="f4f2c-285">**.NET Framework 的app.config**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-285">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f4f2c-286">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="f4f2c-286">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="f4f2c-287">`false`-將相似化為</span><span class="sxs-lookup"><span data-stu-id="f4f2c-287">`false` - affinitize</span></span><br/><span data-ttu-id="f4f2c-288">`true`-不將相似化為</span><span class="sxs-lookup"><span data-stu-id="f4f2c-288">`true` - don't affinitize</span></span> | <span data-ttu-id="f4f2c-289">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="f4f2c-289">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="f4f2c-290">範例：</span><span class="sxs-lookup"><span data-stu-id="f4f2c-290">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="f4f2c-291">HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="f4f2c-291">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="f4f2c-292">指定 GC 堆積和 GC 簿記的認可大小上限（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-292">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>
- <span data-ttu-id="f4f2c-293">此設定僅適用于64位電腦。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-293">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="f4f2c-294">如果設定了[每個物件堆積的限制](#per-object-heap-limits)，則會忽略此設定。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-294">This setting is ignored if the [Per-object-heap limits](#per-object-heap-limits) are configured.</span></span>
- <span data-ttu-id="f4f2c-295">只有在特定情況下才適用的預設值是容器的 20 MB 或75% 的記憶體限制。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-295">The default value, which only applies in certain cases, is the greater of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="f4f2c-296">預設值適用于下列情況：</span><span class="sxs-lookup"><span data-stu-id="f4f2c-296">The default value applies if:</span></span>

  - <span data-ttu-id="f4f2c-297">進程在具有指定記憶體限制的容器內執行。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-297">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="f4f2c-298">未設定[HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) 。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-298">[System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) is not set.</span></span>

| | <span data-ttu-id="f4f2c-299">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f4f2c-299">Setting name</span></span> | <span data-ttu-id="f4f2c-300">值</span><span class="sxs-lookup"><span data-stu-id="f4f2c-300">Values</span></span> | <span data-ttu-id="f4f2c-301">引進的版本</span><span class="sxs-lookup"><span data-stu-id="f4f2c-301">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f4f2c-302">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-302">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="f4f2c-303">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="f4f2c-303">*decimal value*</span></span> | <span data-ttu-id="f4f2c-304">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-304">.NET Core 3.0</span></span> |
| <span data-ttu-id="f4f2c-305">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-305">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="f4f2c-306">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="f4f2c-306">*hexadecimal value*</span></span> | <span data-ttu-id="f4f2c-307">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-307">.NET Core 3.0</span></span> |

<span data-ttu-id="f4f2c-308">範例：</span><span class="sxs-lookup"><span data-stu-id="f4f2c-308">Example:</span></span>

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
> <span data-ttu-id="f4f2c-309">如果您要在*runtimeconfig.js*中設定選項，請指定十進位值。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-309">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="f4f2c-310">如果您要將選項設定為環境變數，請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-310">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="f4f2c-311">例如，若要指定200數量（MiB）的堆積固定限制，其值會是209715200（針對 JSON 檔案）和0xC800000 或 C800000 （適用于環境變數）。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-311">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="f4f2c-312">HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="f4f2c-312">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="f4f2c-313">指定允許的 GC 堆積使用量，以總實體記憶體的百分比表示。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-313">Specifies the allowable GC heap usage as a percentage of the total physical memory.</span></span>
- <span data-ttu-id="f4f2c-314">如果也設定了[HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) ，則會忽略此設定。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-314">If [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is also set, this setting is ignored.</span></span>
- <span data-ttu-id="f4f2c-315">此設定僅適用于64位電腦。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-315">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="f4f2c-316">如果處理常式是在具有指定記憶體限制的容器內執行，則會以該記憶體限制的百分比來計算百分比。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-316">If the process is running inside a container that has a specified memory limit, the percentage is calculated as a percentage of that memory limit.</span></span>
- <span data-ttu-id="f4f2c-317">如果設定了[每個物件堆積的限制](#per-object-heap-limits)，則會忽略此設定。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-317">This setting is ignored if the [Per-object-heap limits](#per-object-heap-limits) are configured.</span></span>
- <span data-ttu-id="f4f2c-318">只有在特定情況下才適用的預設值是容器上 20 MB 或75% 記憶體限制的較小者。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-318">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="f4f2c-319">預設值適用于下列情況：</span><span class="sxs-lookup"><span data-stu-id="f4f2c-319">The default value applies if:</span></span>

  - <span data-ttu-id="f4f2c-320">進程在具有指定記憶體限制的容器內執行。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-320">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="f4f2c-321">未設定[HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) 。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-321">[System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is not set.</span></span>

| | <span data-ttu-id="f4f2c-322">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f4f2c-322">Setting name</span></span> | <span data-ttu-id="f4f2c-323">值</span><span class="sxs-lookup"><span data-stu-id="f4f2c-323">Values</span></span> | <span data-ttu-id="f4f2c-324">引進的版本</span><span class="sxs-lookup"><span data-stu-id="f4f2c-324">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f4f2c-325">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-325">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="f4f2c-326">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="f4f2c-326">*decimal value*</span></span> | <span data-ttu-id="f4f2c-327">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-327">.NET Core 3.0</span></span> |
| <span data-ttu-id="f4f2c-328">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-328">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="f4f2c-329">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="f4f2c-329">*hexadecimal value*</span></span> | <span data-ttu-id="f4f2c-330">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-330">.NET Core 3.0</span></span> |

<span data-ttu-id="f4f2c-331">範例：</span><span class="sxs-lookup"><span data-stu-id="f4f2c-331">Example:</span></span>

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
> <span data-ttu-id="f4f2c-332">如果您要在*runtimeconfig.js*中設定選項，請指定十進位值。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-332">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="f4f2c-333">如果您要將選項設定為環境變數，請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-333">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="f4f2c-334">例如，若要將堆積使用量限制為30%，JSON 檔案的值會是30，而0x1E 或1E 則適用于環境變數。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-334">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="per-object-heap-limits"></a><span data-ttu-id="f4f2c-335">每個物件的堆積限制</span><span class="sxs-lookup"><span data-stu-id="f4f2c-335">Per-object-heap limits</span></span>

<span data-ttu-id="f4f2c-336">您可以針對每個物件堆積指定 GC 的允許堆積使用方式。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-336">You can specify the GC's allowable heap usage on a per-object-heap basis.</span></span> <span data-ttu-id="f4f2c-337">不同的堆積包括大型物件堆積（LOH）、小型物件堆積（SOH）和釘選的物件堆積（POH）。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-337">The different heaps are the large object heap (LOH), small object heap (SOH), and pinned object heap (POH).</span></span>

#### <a name="complus_gcheaphardlimitsoh-complus_gcheaphardlimitloh-complus_gcheaphardlimitpoh"></a><span data-ttu-id="f4f2c-338">COMPLUS_GCHeapHardLimitSOH、COMPLUS_GCHeapHardLimitLOH、COMPLUS_GCHeapHardLimitPOH</span><span class="sxs-lookup"><span data-stu-id="f4f2c-338">COMPLUS_GCHeapHardLimitSOH, COMPLUS_GCHeapHardLimitLOH, COMPLUS_GCHeapHardLimitPOH</span></span>

- <span data-ttu-id="f4f2c-339">如果您指定任何 `COMPLUS_GCHeapHardLimitSOH` 、 `COMPLUS_GCHeapHardLimitLOH` 或設定的值 `COMPLUS_GCHeapHardLimitPOH` ，您也必須指定和的值 `COMPLUS_GCHeapHardLimitSOH` `COMPLUS_GCHeapHardLimitLOH` 。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-339">If you specify a value for any of the `COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH`, or `COMPLUS_GCHeapHardLimitPOH` settings, you must also specify a value for `COMPLUS_GCHeapHardLimitSOH` and `COMPLUS_GCHeapHardLimitLOH`.</span></span> <span data-ttu-id="f4f2c-340">如果您沒有這麼做，執行時間將無法初始化。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-340">If you don't, the runtime will fail to initialize.</span></span>
- <span data-ttu-id="f4f2c-341">`COMPLUS_GCHeapHardLimitPOH` 的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-341">The default value for `COMPLUS_GCHeapHardLimitPOH` is 0.</span></span> <span data-ttu-id="f4f2c-342">`COMPLUS_GCHeapHardLimitSOH`和 `COMPLUS_GCHeapHardLimitLOH` 沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-342">`COMPLUS_GCHeapHardLimitSOH` and `COMPLUS_GCHeapHardLimitLOH` don't have default values.</span></span>

| | <span data-ttu-id="f4f2c-343">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f4f2c-343">Setting name</span></span> | <span data-ttu-id="f4f2c-344">值</span><span class="sxs-lookup"><span data-stu-id="f4f2c-344">Values</span></span> | <span data-ttu-id="f4f2c-345">引進的版本</span><span class="sxs-lookup"><span data-stu-id="f4f2c-345">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f4f2c-346">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-346">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitSOH` | <span data-ttu-id="f4f2c-347">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="f4f2c-347">*hexadecimal value*</span></span> | <span data-ttu-id="f4f2c-348">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-348">.NET 5.0</span></span> |
| <span data-ttu-id="f4f2c-349">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-349">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitLOH` | <span data-ttu-id="f4f2c-350">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="f4f2c-350">*hexadecimal value*</span></span> | <span data-ttu-id="f4f2c-351">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-351">.NET 5.0</span></span> |
| <span data-ttu-id="f4f2c-352">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-352">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitPOH` | <span data-ttu-id="f4f2c-353">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="f4f2c-353">*hexadecimal value*</span></span> | <span data-ttu-id="f4f2c-354">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-354">.NET 5.0</span></span> |

> [!TIP]
> <span data-ttu-id="f4f2c-355">如果您要將選項設定為環境變數，請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-355">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="f4f2c-356">例如，若要指定200數量（MiB）的堆積固定限制，此值會是0xC800000 或 C800000。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-356">For example, to specify a heap hard limit of 200 mebibytes (MiB), the value would be 0xC800000 or C800000.</span></span>

#### <a name="complus_gcheaphardlimitsohpercent-complus_gcheaphardlimitlohpercent-complus_gcheaphardlimitpohpercent"></a><span data-ttu-id="f4f2c-357">COMPLUS_GCHeapHardLimitSOHPercent、COMPLUS_GCHeapHardLimitLOHPercent、COMPLUS_GCHeapHardLimitPOHPercent</span><span class="sxs-lookup"><span data-stu-id="f4f2c-357">COMPLUS_GCHeapHardLimitSOHPercent, COMPLUS_GCHeapHardLimitLOHPercent, COMPLUS_GCHeapHardLimitPOHPercent</span></span>

- <span data-ttu-id="f4f2c-358">如果您指定任何 `COMPLUS_GCHeapHardLimitSOHPercent` 、 `COMPLUS_GCHeapHardLimitLOHPercent` 或設定的值 `COMPLUS_GCHeapHardLimitPOHPercent` ，您也必須指定和的值 `COMPLUS_GCHeapHardLimitSOHPercent` `COMPLUS_GCHeapHardLimitLOHPercent` 。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-358">If you specify a value for any of the `COMPLUS_GCHeapHardLimitSOHPercent`, `COMPLUS_GCHeapHardLimitLOHPercent`, or `COMPLUS_GCHeapHardLimitPOHPercent` settings, you must also specify a value for `COMPLUS_GCHeapHardLimitSOHPercent` and `COMPLUS_GCHeapHardLimitLOHPercent`.</span></span> <span data-ttu-id="f4f2c-359">如果您沒有這麼做，執行時間將無法初始化。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-359">If you don't, the runtime will fail to initialize.</span></span>
- <span data-ttu-id="f4f2c-360">如果 `COMPLUS_GCHeapHardLimitSOH` 指定、和，則會忽略這些設定 `COMPLUS_GCHeapHardLimitLOH` `COMPLUS_GCHeapHardLimitPOH` 。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-360">These settings are ignored if `COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH`, and `COMPLUS_GCHeapHardLimitPOH` are specified.</span></span>
- <span data-ttu-id="f4f2c-361">值為1表示 GC 使用該物件堆積的總實體記憶體的1%。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-361">A value of 1 means that GC uses 1% of total physical memory for that object heap.</span></span>
- <span data-ttu-id="f4f2c-362">每個值都必須大於零且小於100。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-362">Each value must be greater than zero and less than 100.</span></span> <span data-ttu-id="f4f2c-363">此外，這三個百分比值的總和必須小於100。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-363">Additionally, the sum of the three percentage values must be less than 100.</span></span> <span data-ttu-id="f4f2c-364">否則，執行時間將無法初始化。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-364">Otherwise, the runtime will fail to initialize.</span></span>

| | <span data-ttu-id="f4f2c-365">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f4f2c-365">Setting name</span></span> | <span data-ttu-id="f4f2c-366">值</span><span class="sxs-lookup"><span data-stu-id="f4f2c-366">Values</span></span> | <span data-ttu-id="f4f2c-367">引進的版本</span><span class="sxs-lookup"><span data-stu-id="f4f2c-367">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f4f2c-368">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-368">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitSOHPercent` | <span data-ttu-id="f4f2c-369">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="f4f2c-369">*hexadecimal value*</span></span> | <span data-ttu-id="f4f2c-370">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-370">.NET 5.0</span></span> |
| <span data-ttu-id="f4f2c-371">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-371">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitLOHPercent` | <span data-ttu-id="f4f2c-372">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="f4f2c-372">*hexadecimal value*</span></span> | <span data-ttu-id="f4f2c-373">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-373">.NET 5.0</span></span> |
| <span data-ttu-id="f4f2c-374">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-374">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitPOHPercent` | <span data-ttu-id="f4f2c-375">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="f4f2c-375">*hexadecimal value*</span></span> | <span data-ttu-id="f4f2c-376">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-376">.NET 5.0</span></span> |

> [!TIP]
> <span data-ttu-id="f4f2c-377">如果您要將選項設定為環境變數，請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-377">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="f4f2c-378">例如，若要將堆積使用量限制為30%，此值會是0x1E 或1E。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-378">For example, to limit the heap usage to 30%, the value would be 0x1E or 1E.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="f4f2c-379">RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="f4f2c-379">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="f4f2c-380">設定是否要將應該刪除的區段放在待命清單上以供日後使用，或發行回作業系統（OS）。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-380">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="f4f2c-381">預設值：將區段釋放回作業系統。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-381">Default: Release segments back to the operating system.</span></span> <span data-ttu-id="f4f2c-382">這相當於將值設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-382">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="f4f2c-383">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f4f2c-383">Setting name</span></span> | <span data-ttu-id="f4f2c-384">值</span><span class="sxs-lookup"><span data-stu-id="f4f2c-384">Values</span></span> | <span data-ttu-id="f4f2c-385">引進的版本</span><span class="sxs-lookup"><span data-stu-id="f4f2c-385">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f4f2c-386">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-386">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="f4f2c-387">`false`-發行至 OS</span><span class="sxs-lookup"><span data-stu-id="f4f2c-387">`false` - release to OS</span></span><br/><span data-ttu-id="f4f2c-388">`true`-put 待命</span><span class="sxs-lookup"><span data-stu-id="f4f2c-388">`true` - put on standby</span></span> | <span data-ttu-id="f4f2c-389">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-389">.NET Core 1.0</span></span> |
| <span data-ttu-id="f4f2c-390">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-390">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="f4f2c-391">`false`-發行至 OS</span><span class="sxs-lookup"><span data-stu-id="f4f2c-391">`false` - release to OS</span></span><br/><span data-ttu-id="f4f2c-392">`true`-put 待命</span><span class="sxs-lookup"><span data-stu-id="f4f2c-392">`true` - put on standby</span></span> | <span data-ttu-id="f4f2c-393">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-393">.NET Core 1.0</span></span> |
| <span data-ttu-id="f4f2c-394">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-394">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="f4f2c-395">`0`-發行至 OS</span><span class="sxs-lookup"><span data-stu-id="f4f2c-395">`0` - release to OS</span></span><br/><span data-ttu-id="f4f2c-396">`1`-put 待命</span><span class="sxs-lookup"><span data-stu-id="f4f2c-396">`1` - put on standby</span></span> | <span data-ttu-id="f4f2c-397">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-397">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="f4f2c-398">範例</span><span class="sxs-lookup"><span data-stu-id="f4f2c-398">Examples</span></span>

<span data-ttu-id="f4f2c-399">檔案*上的runtimeconfig.js* ：</span><span class="sxs-lookup"><span data-stu-id="f4f2c-399">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="f4f2c-400">專案檔：</span><span class="sxs-lookup"><span data-stu-id="f4f2c-400">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="f4f2c-401">大型頁面</span><span class="sxs-lookup"><span data-stu-id="f4f2c-401">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="f4f2c-402">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="f4f2c-402">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="f4f2c-403">指定在設定堆積固定限制時是否應該使用大型分頁。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-403">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="f4f2c-404">預設值：設定堆積固定限制時，請勿使用大型頁面。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-404">Default: Don't use large pages when a heap hard limit is set.</span></span> <span data-ttu-id="f4f2c-405">這相當於將值設定為 `0` 。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-405">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="f4f2c-406">這是實驗性設定。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-406">This is an experimental setting.</span></span>

| | <span data-ttu-id="f4f2c-407">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f4f2c-407">Setting name</span></span> | <span data-ttu-id="f4f2c-408">值</span><span class="sxs-lookup"><span data-stu-id="f4f2c-408">Values</span></span> | <span data-ttu-id="f4f2c-409">引進的版本</span><span class="sxs-lookup"><span data-stu-id="f4f2c-409">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f4f2c-410">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-410">**runtimeconfig.json**</span></span> | <span data-ttu-id="f4f2c-411">N/A</span><span class="sxs-lookup"><span data-stu-id="f4f2c-411">N/A</span></span> | <span data-ttu-id="f4f2c-412">N/A</span><span class="sxs-lookup"><span data-stu-id="f4f2c-412">N/A</span></span> | <span data-ttu-id="f4f2c-413">N/A</span><span class="sxs-lookup"><span data-stu-id="f4f2c-413">N/A</span></span> |
| <span data-ttu-id="f4f2c-414">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-414">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="f4f2c-415">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="f4f2c-415">`0` - disabled</span></span><br/><span data-ttu-id="f4f2c-416">`1`-已啟用</span><span class="sxs-lookup"><span data-stu-id="f4f2c-416">`1` - enabled</span></span> | <span data-ttu-id="f4f2c-417">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-417">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="f4f2c-418">大型物件</span><span class="sxs-lookup"><span data-stu-id="f4f2c-418">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="f4f2c-419">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="f4f2c-419">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="f4f2c-420">針對大小總計大於 2 gb 的陣列，設定64位平臺上的垃圾收集行程支援。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-420">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="f4f2c-421">預設值： GC 支援大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-421">Default: GC supports arrays greater than 2-GB.</span></span> <span data-ttu-id="f4f2c-422">這相當於將值設定為 `1` 。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-422">This is equivalent to setting the value to `1`.</span></span>
- <span data-ttu-id="f4f2c-423">在未來的 .NET 版本中，此選項可能會過時。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-423">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="f4f2c-424">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f4f2c-424">Setting name</span></span> | <span data-ttu-id="f4f2c-425">值</span><span class="sxs-lookup"><span data-stu-id="f4f2c-425">Values</span></span> | <span data-ttu-id="f4f2c-426">引進的版本</span><span class="sxs-lookup"><span data-stu-id="f4f2c-426">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f4f2c-427">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-427">**runtimeconfig.json**</span></span> | <span data-ttu-id="f4f2c-428">N/A</span><span class="sxs-lookup"><span data-stu-id="f4f2c-428">N/A</span></span> | <span data-ttu-id="f4f2c-429">N/A</span><span class="sxs-lookup"><span data-stu-id="f4f2c-429">N/A</span></span> | <span data-ttu-id="f4f2c-430">N/A</span><span class="sxs-lookup"><span data-stu-id="f4f2c-430">N/A</span></span> |
| <span data-ttu-id="f4f2c-431">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-431">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="f4f2c-432">`1`-已啟用</span><span class="sxs-lookup"><span data-stu-id="f4f2c-432">`1` - enabled</span></span><br/> <span data-ttu-id="f4f2c-433">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="f4f2c-433">`0` - disabled</span></span> | <span data-ttu-id="f4f2c-434">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-434">.NET Core 1.0</span></span> |
| <span data-ttu-id="f4f2c-435">**.NET Framework 的app.config**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-435">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f4f2c-436">Gcallowverylargeobjects></span><span class="sxs-lookup"><span data-stu-id="f4f2c-436">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="f4f2c-437">`1`-已啟用</span><span class="sxs-lookup"><span data-stu-id="f4f2c-437">`1` - enabled</span></span><br/> <span data-ttu-id="f4f2c-438">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="f4f2c-438">`0` - disabled</span></span> | <span data-ttu-id="f4f2c-439">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="f4f2c-439">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="f4f2c-440">大型物件堆積閾值</span><span class="sxs-lookup"><span data-stu-id="f4f2c-440">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="f4f2c-441">LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="f4f2c-441">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="f4f2c-442">指定導致物件在大型物件堆積（LOH）上執行的閾值大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-442">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="f4f2c-443">預設閾值為85000個位元組。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-443">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="f4f2c-444">您指定的值必須大於預設閾值。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-444">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="f4f2c-445">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f4f2c-445">Setting name</span></span> | <span data-ttu-id="f4f2c-446">值</span><span class="sxs-lookup"><span data-stu-id="f4f2c-446">Values</span></span> | <span data-ttu-id="f4f2c-447">引進的版本</span><span class="sxs-lookup"><span data-stu-id="f4f2c-447">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f4f2c-448">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-448">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="f4f2c-449">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="f4f2c-449">*decimal value*</span></span> | <span data-ttu-id="f4f2c-450">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-450">.NET Core 1.0</span></span> |
| <span data-ttu-id="f4f2c-451">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-451">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="f4f2c-452">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="f4f2c-452">*hexadecimal value*</span></span> | <span data-ttu-id="f4f2c-453">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-453">.NET Core 1.0</span></span> |
| <span data-ttu-id="f4f2c-454">**.NET Framework 的app.config**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-454">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f4f2c-455">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="f4f2c-455">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="f4f2c-456">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="f4f2c-456">*decimal value*</span></span> | <span data-ttu-id="f4f2c-457">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="f4f2c-457">.NET Framework 4.8</span></span> |

<span data-ttu-id="f4f2c-458">範例：</span><span class="sxs-lookup"><span data-stu-id="f4f2c-458">Example:</span></span>

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
> <span data-ttu-id="f4f2c-459">如果您要在*runtimeconfig.js*中設定選項，請指定十進位值。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-459">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="f4f2c-460">如果您要將選項設定為環境變數，請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-460">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="f4f2c-461">例如，若要設定120000個位元組的閾值大小，JSON 檔案的值會是120000，而環境變數的值則是0x1D4C0 或1D4C0。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-461">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="f4f2c-462">獨立 GC</span><span class="sxs-lookup"><span data-stu-id="f4f2c-462">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="f4f2c-463">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="f4f2c-463">COMPlus_GCName</span></span>

- <span data-ttu-id="f4f2c-464">指定包含執行時間打算載入之垃圾收集行程的程式庫路徑。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-464">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="f4f2c-465">如需詳細資訊，請參閱[獨立 GC 載入器設計](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md)。</span><span class="sxs-lookup"><span data-stu-id="f4f2c-465">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="f4f2c-466">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f4f2c-466">Setting name</span></span> | <span data-ttu-id="f4f2c-467">值</span><span class="sxs-lookup"><span data-stu-id="f4f2c-467">Values</span></span> | <span data-ttu-id="f4f2c-468">引進的版本</span><span class="sxs-lookup"><span data-stu-id="f4f2c-468">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f4f2c-469">**runtimeconfig.js于**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-469">**runtimeconfig.json**</span></span> | <span data-ttu-id="f4f2c-470">N/A</span><span class="sxs-lookup"><span data-stu-id="f4f2c-470">N/A</span></span> | <span data-ttu-id="f4f2c-471">N/A</span><span class="sxs-lookup"><span data-stu-id="f4f2c-471">N/A</span></span> | <span data-ttu-id="f4f2c-472">N/A</span><span class="sxs-lookup"><span data-stu-id="f4f2c-472">N/A</span></span> |
| <span data-ttu-id="f4f2c-473">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f4f2c-473">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="f4f2c-474">*string_path*</span><span class="sxs-lookup"><span data-stu-id="f4f2c-474">*string_path*</span></span> | <span data-ttu-id="f4f2c-475">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="f4f2c-475">.NET Core 2.0</span></span> |
