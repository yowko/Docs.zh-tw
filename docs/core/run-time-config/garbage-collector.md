---
title: 垃圾收集行程 config 設定
description: 瞭解用來設定垃圾收集行程如何管理 .NET Core 應用程式記憶體的執行時間設定。
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: 044083d69601f5092724a46d358b2ee5673d428d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733526"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="89dc8-103">用於垃圾收集的執行時間設定選項</span><span class="sxs-lookup"><span data-stu-id="89dc8-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="89dc8-104">此頁面包含可在執行時間變更之垃圾收集行程（GC）設定的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="89dc8-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="89dc8-105">如果您正嘗試達到執行中應用程式的尖峰效能，請考慮使用這些設定。</span><span class="sxs-lookup"><span data-stu-id="89dc8-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="89dc8-106">不過，在一般情況下，預設值可為大部分的應用程式提供最佳效能。</span><span class="sxs-lookup"><span data-stu-id="89dc8-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="89dc8-107">這些設定會依此頁面的群組排列。</span><span class="sxs-lookup"><span data-stu-id="89dc8-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="89dc8-108">每個群組內的設定通常會彼此搭配使用，以達成特定結果。</span><span class="sxs-lookup"><span data-stu-id="89dc8-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="89dc8-109">這些設定也可以在應用程式執行時動態變更，因此您設定的任何執行時間設定可能會遭到覆寫。</span><span class="sxs-lookup"><span data-stu-id="89dc8-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="89dc8-110">某些設定（例如[延遲層級](../../standard/garbage-collection/latency.md)）通常只會在設計階段透過 API 進行設定。</span><span class="sxs-lookup"><span data-stu-id="89dc8-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="89dc8-111">此頁面會省略這類設定。</span><span class="sxs-lookup"><span data-stu-id="89dc8-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="89dc8-112">針對 [數值]，使用十進位標記法做為 *.runtimeconfig.json*檔案中的設定，並針對環境變數設定使用十六進位標記法。</span><span class="sxs-lookup"><span data-stu-id="89dc8-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="89dc8-113">若為十六進位值，您可以使用或不搭配 "0x" 前置詞來指定它們。</span><span class="sxs-lookup"><span data-stu-id="89dc8-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="89dc8-114">垃圾收集的種類</span><span class="sxs-lookup"><span data-stu-id="89dc8-114">Flavors of garbage collection</span></span>

<span data-ttu-id="89dc8-115">垃圾收集的兩個主要類別是工作站 GC 和伺服器 GC。</span><span class="sxs-lookup"><span data-stu-id="89dc8-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="89dc8-116">如需兩者之間差異的詳細資訊，請參閱[垃圾收集的基本](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection)概念。</span><span class="sxs-lookup"><span data-stu-id="89dc8-116">For more information about differences between the two, see [Fundamentals of garbage collection](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span></span>

<span data-ttu-id="89dc8-117">垃圾收集的 subflavors 是背景和非並行的。</span><span class="sxs-lookup"><span data-stu-id="89dc8-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="89dc8-118">使用下列設定來選取垃圾收集的種類：</span><span class="sxs-lookup"><span data-stu-id="89dc8-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="89dc8-119">System.web/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="89dc8-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="89dc8-120">設定應用程式是否使用工作站垃圾收集或伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="89dc8-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="89dc8-121">預設值：工作站垃圾收集（`false`）。</span><span class="sxs-lookup"><span data-stu-id="89dc8-121">Default: Workstation garbage collection (`false`).</span></span>

| | <span data-ttu-id="89dc8-122">設定名稱</span><span class="sxs-lookup"><span data-stu-id="89dc8-122">Setting name</span></span> | <span data-ttu-id="89dc8-123">值</span><span class="sxs-lookup"><span data-stu-id="89dc8-123">Values</span></span> | <span data-ttu-id="89dc8-124">引進的版本</span><span class="sxs-lookup"><span data-stu-id="89dc8-124">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="89dc8-125">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="89dc8-125">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="89dc8-126">`false`-工作站</span><span class="sxs-lookup"><span data-stu-id="89dc8-126">`false` - workstation</span></span><br/><span data-ttu-id="89dc8-127">`true`-伺服器</span><span class="sxs-lookup"><span data-stu-id="89dc8-127">`true` - server</span></span> | <span data-ttu-id="89dc8-128">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="89dc8-128">.NET Core 1.0</span></span> |
| <span data-ttu-id="89dc8-129">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="89dc8-129">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="89dc8-130">`false`-工作站</span><span class="sxs-lookup"><span data-stu-id="89dc8-130">`false` - workstation</span></span><br/><span data-ttu-id="89dc8-131">`true`-伺服器</span><span class="sxs-lookup"><span data-stu-id="89dc8-131">`true` - server</span></span> | <span data-ttu-id="89dc8-132">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="89dc8-132">.NET Core 1.0</span></span> |
| <span data-ttu-id="89dc8-133">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="89dc8-133">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="89dc8-134">`0`-工作站</span><span class="sxs-lookup"><span data-stu-id="89dc8-134">`0` - workstation</span></span><br/><span data-ttu-id="89dc8-135">`1`-伺服器</span><span class="sxs-lookup"><span data-stu-id="89dc8-135">`1` - server</span></span> | <span data-ttu-id="89dc8-136">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="89dc8-136">.NET Core 1.0</span></span> |
| <span data-ttu-id="89dc8-137">**.NET Framework 的 app.config**</span><span class="sxs-lookup"><span data-stu-id="89dc8-137">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="89dc8-138">GCServer</span><span class="sxs-lookup"><span data-stu-id="89dc8-138">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="89dc8-139">`false`-工作站</span><span class="sxs-lookup"><span data-stu-id="89dc8-139">`false` - workstation</span></span><br/><span data-ttu-id="89dc8-140">`true`-伺服器</span><span class="sxs-lookup"><span data-stu-id="89dc8-140">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="89dc8-141">範例</span><span class="sxs-lookup"><span data-stu-id="89dc8-141">Examples</span></span>

<span data-ttu-id="89dc8-142">*.runtimeconfig.json json*檔案：</span><span class="sxs-lookup"><span data-stu-id="89dc8-142">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="89dc8-143">專案檔：</span><span class="sxs-lookup"><span data-stu-id="89dc8-143">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="89dc8-144">System.web/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="89dc8-144">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="89dc8-145">設定是否啟用背景（並行）垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="89dc8-145">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="89dc8-146">預設：啟用（`true`）。</span><span class="sxs-lookup"><span data-stu-id="89dc8-146">Default: Enabled (`true`).</span></span>
- <span data-ttu-id="89dc8-147">如需詳細資訊，請參閱[背景垃圾收集](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection)和[背景伺服器垃圾收集](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection)。</span><span class="sxs-lookup"><span data-stu-id="89dc8-147">For more information, see [Background garbage collection](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) and [Background server garbage collection](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span></span>

| | <span data-ttu-id="89dc8-148">設定名稱</span><span class="sxs-lookup"><span data-stu-id="89dc8-148">Setting name</span></span> | <span data-ttu-id="89dc8-149">值</span><span class="sxs-lookup"><span data-stu-id="89dc8-149">Values</span></span> | <span data-ttu-id="89dc8-150">引進的版本</span><span class="sxs-lookup"><span data-stu-id="89dc8-150">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="89dc8-151">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="89dc8-151">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="89dc8-152">`true`-背景 GC</span><span class="sxs-lookup"><span data-stu-id="89dc8-152">`true` - background GC</span></span><br/><span data-ttu-id="89dc8-153">`false`-非並行 GC</span><span class="sxs-lookup"><span data-stu-id="89dc8-153">`false` - non-concurrent GC</span></span> | <span data-ttu-id="89dc8-154">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="89dc8-154">.NET Core 1.0</span></span> |
| <span data-ttu-id="89dc8-155">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="89dc8-155">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="89dc8-156">`true`-背景 GC</span><span class="sxs-lookup"><span data-stu-id="89dc8-156">`true` - background GC</span></span><br/><span data-ttu-id="89dc8-157">`false`-非並行 GC</span><span class="sxs-lookup"><span data-stu-id="89dc8-157">`false` - non-concurrent GC</span></span> | <span data-ttu-id="89dc8-158">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="89dc8-158">.NET Core 1.0</span></span> |
| <span data-ttu-id="89dc8-159">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="89dc8-159">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="89dc8-160">`true`-背景 GC</span><span class="sxs-lookup"><span data-stu-id="89dc8-160">`true` - background GC</span></span><br/><span data-ttu-id="89dc8-161">`false`-非並行 GC</span><span class="sxs-lookup"><span data-stu-id="89dc8-161">`false` - non-concurrent GC</span></span> | <span data-ttu-id="89dc8-162">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="89dc8-162">.NET Core 1.0</span></span> |
| <span data-ttu-id="89dc8-163">**.NET Framework 的 app.config**</span><span class="sxs-lookup"><span data-stu-id="89dc8-163">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="89dc8-164">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="89dc8-164">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="89dc8-165">`true`-背景 GC</span><span class="sxs-lookup"><span data-stu-id="89dc8-165">`true` - background GC</span></span><br/><span data-ttu-id="89dc8-166">`false`-非並行 GC</span><span class="sxs-lookup"><span data-stu-id="89dc8-166">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="89dc8-167">範例</span><span class="sxs-lookup"><span data-stu-id="89dc8-167">Examples</span></span>

<span data-ttu-id="89dc8-168">*.runtimeconfig.json json*檔案：</span><span class="sxs-lookup"><span data-stu-id="89dc8-168">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="89dc8-169">專案檔：</span><span class="sxs-lookup"><span data-stu-id="89dc8-169">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="89dc8-170">管理資源使用量</span><span class="sxs-lookup"><span data-stu-id="89dc8-170">Manage resource usage</span></span>

<span data-ttu-id="89dc8-171">使用本節所述的設定來管理垃圾收集行程的記憶體和處理器使用量。</span><span class="sxs-lookup"><span data-stu-id="89dc8-171">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="89dc8-172">如需有關這些設定的詳細資訊，請參閱[工作站與伺服器 GC 之間的中間](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/)專案 blog。</span><span class="sxs-lookup"><span data-stu-id="89dc8-172">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="89dc8-173">HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="89dc8-173">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="89dc8-174">限制垃圾收集行程所建立的堆積數目。</span><span class="sxs-lookup"><span data-stu-id="89dc8-174">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="89dc8-175">僅適用于伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="89dc8-175">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="89dc8-176">如果已啟用 GC 處理器親和性（這是預設值），則堆積計數設定會如何 `n` GC 堆積/執行緒到第一個 `n` 處理器。</span><span class="sxs-lookup"><span data-stu-id="89dc8-176">If GC processor affinity is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="89dc8-177">（使用將相似化為 mask 或將相似化為範圍設定，以確切指定要將相似化為的處理器）。</span><span class="sxs-lookup"><span data-stu-id="89dc8-177">(Use the affinitize mask or affinitize ranges settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="89dc8-178">如果停用 GC 處理器親和性，這項設定會限制 GC 堆積的數目。</span><span class="sxs-lookup"><span data-stu-id="89dc8-178">If GC processor affinity is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="89dc8-179">如需詳細資訊，請參閱[GCHeapCount 備註](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks)。</span><span class="sxs-lookup"><span data-stu-id="89dc8-179">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="89dc8-180">設定名稱</span><span class="sxs-lookup"><span data-stu-id="89dc8-180">Setting name</span></span> | <span data-ttu-id="89dc8-181">值</span><span class="sxs-lookup"><span data-stu-id="89dc8-181">Values</span></span> | <span data-ttu-id="89dc8-182">引進的版本</span><span class="sxs-lookup"><span data-stu-id="89dc8-182">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="89dc8-183">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="89dc8-183">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="89dc8-184">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="89dc8-184">*decimal value*</span></span> | <span data-ttu-id="89dc8-185">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="89dc8-185">.NET Core 3.0</span></span> |
| <span data-ttu-id="89dc8-186">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="89dc8-186">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="89dc8-187">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="89dc8-187">*hexadecimal value*</span></span> | <span data-ttu-id="89dc8-188">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="89dc8-188">.NET Core 3.0</span></span> |
| <span data-ttu-id="89dc8-189">**.NET Framework 的 app.config**</span><span class="sxs-lookup"><span data-stu-id="89dc8-189">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="89dc8-190">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="89dc8-190">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="89dc8-191">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="89dc8-191">*decimal value*</span></span> | <span data-ttu-id="89dc8-192">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="89dc8-192">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="89dc8-193">範例：</span><span class="sxs-lookup"><span data-stu-id="89dc8-193">Example:</span></span>

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
> <span data-ttu-id="89dc8-194">如果您要在 *.runtimeconfig.json*中設定選項，請指定十進位值。</span><span class="sxs-lookup"><span data-stu-id="89dc8-194">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="89dc8-195">如果您要將選項設定為環境變數，請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="89dc8-195">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="89dc8-196">例如，若要將堆積數目限制為16，JSON 檔案的值會是16，而環境變數的值則是0x10 或10。</span><span class="sxs-lookup"><span data-stu-id="89dc8-196">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="89dc8-197">HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="89dc8-197">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="89dc8-198">指定垃圾收集行程執行緒應該使用的確切處理器。</span><span class="sxs-lookup"><span data-stu-id="89dc8-198">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="89dc8-199">如果藉由將 `System.GC.NoAffinitize` 設定為 `true`來停用處理器親和性，則會忽略此設定。</span><span class="sxs-lookup"><span data-stu-id="89dc8-199">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="89dc8-200">僅適用于伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="89dc8-200">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="89dc8-201">值是一個位元遮罩，用來定義進程可用的處理器。</span><span class="sxs-lookup"><span data-stu-id="89dc8-201">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="89dc8-202">例如，十進位值1023（如果您使用環境變數，則為0x3FF 或3FF 的十六進位值）是 0011 1111 1111 （二進位標記法）。</span><span class="sxs-lookup"><span data-stu-id="89dc8-202">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="89dc8-203">這會指定要使用前10個處理器。</span><span class="sxs-lookup"><span data-stu-id="89dc8-203">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="89dc8-204">若要指定接下來的10個處理器（也就是處理器10-19），請指定十進位值1047552（或0xFFC00 或 FFC00 的十六進位值），這相當於二進位值 1111 1111 1100 0000 0000。</span><span class="sxs-lookup"><span data-stu-id="89dc8-204">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="89dc8-205">設定名稱</span><span class="sxs-lookup"><span data-stu-id="89dc8-205">Setting name</span></span> | <span data-ttu-id="89dc8-206">值</span><span class="sxs-lookup"><span data-stu-id="89dc8-206">Values</span></span> | <span data-ttu-id="89dc8-207">引進的版本</span><span class="sxs-lookup"><span data-stu-id="89dc8-207">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="89dc8-208">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="89dc8-208">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="89dc8-209">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="89dc8-209">*decimal value*</span></span> | <span data-ttu-id="89dc8-210">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="89dc8-210">.NET Core 3.0</span></span> |
| <span data-ttu-id="89dc8-211">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="89dc8-211">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="89dc8-212">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="89dc8-212">*hexadecimal value*</span></span> | <span data-ttu-id="89dc8-213">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="89dc8-213">.NET Core 3.0</span></span> |
| <span data-ttu-id="89dc8-214">**.NET Framework 的 app.config**</span><span class="sxs-lookup"><span data-stu-id="89dc8-214">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="89dc8-215">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="89dc8-215">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="89dc8-216">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="89dc8-216">*decimal value*</span></span> | <span data-ttu-id="89dc8-217">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="89dc8-217">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="89dc8-218">範例：</span><span class="sxs-lookup"><span data-stu-id="89dc8-218">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="89dc8-219">GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="89dc8-219">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="89dc8-220">指定要用於垃圾收集行程執行緒的處理器清單。</span><span class="sxs-lookup"><span data-stu-id="89dc8-220">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="89dc8-221">此設定類似于 `System.GC.HeapAffinitizeMask`，但它可讓您指定64個以上的處理器。</span><span class="sxs-lookup"><span data-stu-id="89dc8-221">This setting is similar to `System.GC.HeapAffinitizeMask`, except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="89dc8-222">若是 Windows 作業系統，請在處理器編號或範圍前面加上對應的[CPU 群組](/windows/win32/procthread/processor-groups)，例如 "0： 1-10，0：12，1： 50-52，1： 70"。</span><span class="sxs-lookup"><span data-stu-id="89dc8-222">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="89dc8-223">如果藉由將 `System.GC.NoAffinitize` 設定為 `true`來停用處理器親和性，則會忽略此設定。</span><span class="sxs-lookup"><span data-stu-id="89dc8-223">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="89dc8-224">僅適用于伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="89dc8-224">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="89dc8-225">如需詳細資訊，請參閱 Maoni Stephens 的 blog 上的[針對具有 > 64 cpu 的電腦，讓 CPU 設定更好用於 GC](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) 。</span><span class="sxs-lookup"><span data-stu-id="89dc8-225">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="89dc8-226">設定名稱</span><span class="sxs-lookup"><span data-stu-id="89dc8-226">Setting name</span></span> | <span data-ttu-id="89dc8-227">值</span><span class="sxs-lookup"><span data-stu-id="89dc8-227">Values</span></span> | <span data-ttu-id="89dc8-228">引進的版本</span><span class="sxs-lookup"><span data-stu-id="89dc8-228">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="89dc8-229">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="89dc8-229">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="89dc8-230">以逗號分隔的處理器編號或處理器編號範圍清單。</span><span class="sxs-lookup"><span data-stu-id="89dc8-230">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="89dc8-231">Unix 範例： "1-10，12，50-52，70"</span><span class="sxs-lookup"><span data-stu-id="89dc8-231">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="89dc8-232">Windows 範例： "0： 1-10，0：12，1： 50-52，1： 70"</span><span class="sxs-lookup"><span data-stu-id="89dc8-232">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="89dc8-233">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="89dc8-233">.NET Core 3.0</span></span> |
| <span data-ttu-id="89dc8-234">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="89dc8-234">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="89dc8-235">以逗號分隔的處理器編號或處理器編號範圍清單。</span><span class="sxs-lookup"><span data-stu-id="89dc8-235">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="89dc8-236">Unix 範例： "1-10，12，50-52，70"</span><span class="sxs-lookup"><span data-stu-id="89dc8-236">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="89dc8-237">Windows 範例： "0： 1-10，0：12，1： 50-52，1： 70"</span><span class="sxs-lookup"><span data-stu-id="89dc8-237">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="89dc8-238">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="89dc8-238">.NET Core 3.0</span></span> |

<span data-ttu-id="89dc8-239">範例：</span><span class="sxs-lookup"><span data-stu-id="89dc8-239">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="89dc8-240">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="89dc8-240">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="89dc8-241">設定垃圾收集行程是否使用[CPU 群組](/windows/win32/procthread/processor-groups)。</span><span class="sxs-lookup"><span data-stu-id="89dc8-241">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="89dc8-242">當64位 Windows 電腦具有多個 CPU 群組（也就是，有超過64個處理器）時，啟用這個元素會延伸所有 CPU 群組的垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="89dc8-242">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="89dc8-243">垃圾收集行程會使用所有核心來建立和平衡堆積。</span><span class="sxs-lookup"><span data-stu-id="89dc8-243">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="89dc8-244">僅適用于64位 Windows 作業系統上的伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="89dc8-244">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="89dc8-245">預設：停用（`0`）。</span><span class="sxs-lookup"><span data-stu-id="89dc8-245">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="89dc8-246">如需詳細資訊，請參閱 Maoni Stephens 的 blog 上的[針對具有 > 64 cpu 的電腦，讓 CPU 設定更好用於 GC](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) 。</span><span class="sxs-lookup"><span data-stu-id="89dc8-246">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="89dc8-247">設定名稱</span><span class="sxs-lookup"><span data-stu-id="89dc8-247">Setting name</span></span> | <span data-ttu-id="89dc8-248">值</span><span class="sxs-lookup"><span data-stu-id="89dc8-248">Values</span></span> | <span data-ttu-id="89dc8-249">引進的版本</span><span class="sxs-lookup"><span data-stu-id="89dc8-249">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="89dc8-250">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="89dc8-250">**runtimeconfig.json**</span></span> | <span data-ttu-id="89dc8-251">N/A</span><span class="sxs-lookup"><span data-stu-id="89dc8-251">N/A</span></span> | <span data-ttu-id="89dc8-252">N/A</span><span class="sxs-lookup"><span data-stu-id="89dc8-252">N/A</span></span> | <span data-ttu-id="89dc8-253">N/A</span><span class="sxs-lookup"><span data-stu-id="89dc8-253">N/A</span></span> |
| <span data-ttu-id="89dc8-254">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="89dc8-254">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="89dc8-255">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="89dc8-255">`0` - disabled</span></span><br/><span data-ttu-id="89dc8-256">已啟用 `1`</span><span class="sxs-lookup"><span data-stu-id="89dc8-256">`1` - enabled</span></span> | <span data-ttu-id="89dc8-257">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="89dc8-257">.NET Core 1.0</span></span> |
| <span data-ttu-id="89dc8-258">**.NET Framework 的 app.config**</span><span class="sxs-lookup"><span data-stu-id="89dc8-258">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="89dc8-259">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="89dc8-259">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="89dc8-260">`false`-已停用</span><span class="sxs-lookup"><span data-stu-id="89dc8-260">`false` - disabled</span></span><br/><span data-ttu-id="89dc8-261">已啟用 `true`</span><span class="sxs-lookup"><span data-stu-id="89dc8-261">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="89dc8-262">若要將 common language runtime （CLR）設定為同時將執行緒集區中的執行緒散發到所有 CPU 群組，請啟用 [ [Thread_UseAllCpuGroups 元素](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)] 選項。</span><span class="sxs-lookup"><span data-stu-id="89dc8-262">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="89dc8-263">針對 .NET Core 應用程式，您可以將 `COMPlus_Thread_UseAllCpuGroups` 環境變數的值設定為 `1`來啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="89dc8-263">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="89dc8-264">NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="89dc8-264">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="89dc8-265">指定是否要使用處理器*將相似化為*垃圾收集執行緒。</span><span class="sxs-lookup"><span data-stu-id="89dc8-265">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="89dc8-266">若要將相似化為 GC 執行緒，這表示它只能在其特定的 CPU 上執行。</span><span class="sxs-lookup"><span data-stu-id="89dc8-266">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="89dc8-267">會針對每個 GC 執行緒建立堆積。</span><span class="sxs-lookup"><span data-stu-id="89dc8-267">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="89dc8-268">僅適用于伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="89dc8-268">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="89dc8-269">預設值：使用處理器（`false`）將相似化為垃圾收集執行緒。</span><span class="sxs-lookup"><span data-stu-id="89dc8-269">Default: Affinitize garbage collection threads with processors (`false`).</span></span>

| | <span data-ttu-id="89dc8-270">設定名稱</span><span class="sxs-lookup"><span data-stu-id="89dc8-270">Setting name</span></span> | <span data-ttu-id="89dc8-271">值</span><span class="sxs-lookup"><span data-stu-id="89dc8-271">Values</span></span> | <span data-ttu-id="89dc8-272">引進的版本</span><span class="sxs-lookup"><span data-stu-id="89dc8-272">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="89dc8-273">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="89dc8-273">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="89dc8-274">`false`-將相似化為</span><span class="sxs-lookup"><span data-stu-id="89dc8-274">`false` - affinitize</span></span><br/><span data-ttu-id="89dc8-275">`true`-不將相似化為</span><span class="sxs-lookup"><span data-stu-id="89dc8-275">`true` - don't affinitize</span></span> | <span data-ttu-id="89dc8-276">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="89dc8-276">.NET Core 3.0</span></span> |
| <span data-ttu-id="89dc8-277">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="89dc8-277">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="89dc8-278">`0`-將相似化為</span><span class="sxs-lookup"><span data-stu-id="89dc8-278">`0` - affinitize</span></span><br/><span data-ttu-id="89dc8-279">`1`-不將相似化為</span><span class="sxs-lookup"><span data-stu-id="89dc8-279">`1` - don't affinitize</span></span> | <span data-ttu-id="89dc8-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="89dc8-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="89dc8-281">**.NET Framework 的 app.config**</span><span class="sxs-lookup"><span data-stu-id="89dc8-281">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="89dc8-282">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="89dc8-282">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="89dc8-283">`false`-將相似化為</span><span class="sxs-lookup"><span data-stu-id="89dc8-283">`false` - affinitize</span></span><br/><span data-ttu-id="89dc8-284">`true`-不將相似化為</span><span class="sxs-lookup"><span data-stu-id="89dc8-284">`true` - don't affinitize</span></span> | <span data-ttu-id="89dc8-285">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="89dc8-285">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="89dc8-286">範例：</span><span class="sxs-lookup"><span data-stu-id="89dc8-286">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="89dc8-287">HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="89dc8-287">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="89dc8-288">指定 GC 堆積和 GC 簿記的認可大小上限（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="89dc8-288">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>

| | <span data-ttu-id="89dc8-289">設定名稱</span><span class="sxs-lookup"><span data-stu-id="89dc8-289">Setting name</span></span> | <span data-ttu-id="89dc8-290">值</span><span class="sxs-lookup"><span data-stu-id="89dc8-290">Values</span></span> | <span data-ttu-id="89dc8-291">引進的版本</span><span class="sxs-lookup"><span data-stu-id="89dc8-291">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="89dc8-292">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="89dc8-292">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="89dc8-293">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="89dc8-293">*decimal value*</span></span> | <span data-ttu-id="89dc8-294">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="89dc8-294">.NET Core 3.0</span></span> |
| <span data-ttu-id="89dc8-295">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="89dc8-295">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="89dc8-296">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="89dc8-296">*hexadecimal value*</span></span> | <span data-ttu-id="89dc8-297">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="89dc8-297">.NET Core 3.0</span></span> |

<span data-ttu-id="89dc8-298">範例：</span><span class="sxs-lookup"><span data-stu-id="89dc8-298">Example:</span></span>

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
> <span data-ttu-id="89dc8-299">如果您要在 *.runtimeconfig.json*中設定選項，請指定十進位值。</span><span class="sxs-lookup"><span data-stu-id="89dc8-299">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="89dc8-300">如果您要將選項設定為環境變數，請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="89dc8-300">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="89dc8-301">例如，若要指定200數量（MiB）的堆積固定限制，其值會是209715200（針對 JSON 檔案）和0xC800000 或 C800000 （適用于環境變數）。</span><span class="sxs-lookup"><span data-stu-id="89dc8-301">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="89dc8-302">HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="89dc8-302">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="89dc8-303">將 GC 堆積使用量指定為總記憶體的百分比。</span><span class="sxs-lookup"><span data-stu-id="89dc8-303">Specifies the GC heap usage as a percentage of the total memory.</span></span>

| | <span data-ttu-id="89dc8-304">設定名稱</span><span class="sxs-lookup"><span data-stu-id="89dc8-304">Setting name</span></span> | <span data-ttu-id="89dc8-305">值</span><span class="sxs-lookup"><span data-stu-id="89dc8-305">Values</span></span> | <span data-ttu-id="89dc8-306">引進的版本</span><span class="sxs-lookup"><span data-stu-id="89dc8-306">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="89dc8-307">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="89dc8-307">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="89dc8-308">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="89dc8-308">*decimal value*</span></span> | <span data-ttu-id="89dc8-309">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="89dc8-309">.NET Core 3.0</span></span> |
| <span data-ttu-id="89dc8-310">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="89dc8-310">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="89dc8-311">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="89dc8-311">*hexadecimal value*</span></span> | <span data-ttu-id="89dc8-312">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="89dc8-312">.NET Core 3.0</span></span> |

<span data-ttu-id="89dc8-313">範例：</span><span class="sxs-lookup"><span data-stu-id="89dc8-313">Example:</span></span>

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
> <span data-ttu-id="89dc8-314">如果您要在 *.runtimeconfig.json*中設定選項，請指定十進位值。</span><span class="sxs-lookup"><span data-stu-id="89dc8-314">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="89dc8-315">如果您要將選項設定為環境變數，請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="89dc8-315">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="89dc8-316">例如，若要將堆積使用量限制為30%，JSON 檔案的值會是30，而0x1E 或1E 則適用于環境變數。</span><span class="sxs-lookup"><span data-stu-id="89dc8-316">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="89dc8-317">RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="89dc8-317">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="89dc8-318">設定是否要將應該刪除的區段放在待命清單上以供日後使用，或發行回作業系統（OS）。</span><span class="sxs-lookup"><span data-stu-id="89dc8-318">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="89dc8-319">預設值：將區段釋放回作業系統（`false`）。</span><span class="sxs-lookup"><span data-stu-id="89dc8-319">Default: Release segments back to the operating system (`false`).</span></span>

| | <span data-ttu-id="89dc8-320">設定名稱</span><span class="sxs-lookup"><span data-stu-id="89dc8-320">Setting name</span></span> | <span data-ttu-id="89dc8-321">值</span><span class="sxs-lookup"><span data-stu-id="89dc8-321">Values</span></span> | <span data-ttu-id="89dc8-322">引進的版本</span><span class="sxs-lookup"><span data-stu-id="89dc8-322">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="89dc8-323">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="89dc8-323">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="89dc8-324">`false`-發行至 OS</span><span class="sxs-lookup"><span data-stu-id="89dc8-324">`false` - release to OS</span></span><br/><span data-ttu-id="89dc8-325">`true`-put 待命</span><span class="sxs-lookup"><span data-stu-id="89dc8-325">`true` - put on standby</span></span> | <span data-ttu-id="89dc8-326">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="89dc8-326">.NET Core 1.0</span></span> |
| <span data-ttu-id="89dc8-327">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="89dc8-327">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="89dc8-328">`false`-發行至 OS</span><span class="sxs-lookup"><span data-stu-id="89dc8-328">`false` - release to OS</span></span><br/><span data-ttu-id="89dc8-329">`true`-put 待命</span><span class="sxs-lookup"><span data-stu-id="89dc8-329">`true` - put on standby</span></span> | <span data-ttu-id="89dc8-330">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="89dc8-330">.NET Core 1.0</span></span> |
| <span data-ttu-id="89dc8-331">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="89dc8-331">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="89dc8-332">`0`-發行至 OS</span><span class="sxs-lookup"><span data-stu-id="89dc8-332">`0` - release to OS</span></span><br/><span data-ttu-id="89dc8-333">`1`-put 待命</span><span class="sxs-lookup"><span data-stu-id="89dc8-333">`1` - put on standby</span></span> | <span data-ttu-id="89dc8-334">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="89dc8-334">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="89dc8-335">範例</span><span class="sxs-lookup"><span data-stu-id="89dc8-335">Examples</span></span>

<span data-ttu-id="89dc8-336">*.runtimeconfig.json json*檔案：</span><span class="sxs-lookup"><span data-stu-id="89dc8-336">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="89dc8-337">專案檔：</span><span class="sxs-lookup"><span data-stu-id="89dc8-337">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="89dc8-338">大型頁面</span><span class="sxs-lookup"><span data-stu-id="89dc8-338">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="89dc8-339">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="89dc8-339">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="89dc8-340">指定在設定堆積固定限制時是否應該使用大型分頁。</span><span class="sxs-lookup"><span data-stu-id="89dc8-340">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="89dc8-341">預設：停用（`0`）。</span><span class="sxs-lookup"><span data-stu-id="89dc8-341">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="89dc8-342">這是實驗性設定。</span><span class="sxs-lookup"><span data-stu-id="89dc8-342">This is an experimental setting.</span></span>

| | <span data-ttu-id="89dc8-343">設定名稱</span><span class="sxs-lookup"><span data-stu-id="89dc8-343">Setting name</span></span> | <span data-ttu-id="89dc8-344">值</span><span class="sxs-lookup"><span data-stu-id="89dc8-344">Values</span></span> | <span data-ttu-id="89dc8-345">引進的版本</span><span class="sxs-lookup"><span data-stu-id="89dc8-345">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="89dc8-346">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="89dc8-346">**runtimeconfig.json**</span></span> | <span data-ttu-id="89dc8-347">N/A</span><span class="sxs-lookup"><span data-stu-id="89dc8-347">N/A</span></span> | <span data-ttu-id="89dc8-348">N/A</span><span class="sxs-lookup"><span data-stu-id="89dc8-348">N/A</span></span> | <span data-ttu-id="89dc8-349">N/A</span><span class="sxs-lookup"><span data-stu-id="89dc8-349">N/A</span></span> |
| <span data-ttu-id="89dc8-350">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="89dc8-350">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="89dc8-351">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="89dc8-351">`0` - disabled</span></span><br/><span data-ttu-id="89dc8-352">已啟用 `1`</span><span class="sxs-lookup"><span data-stu-id="89dc8-352">`1` - enabled</span></span> | <span data-ttu-id="89dc8-353">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="89dc8-353">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="89dc8-354">大型物件</span><span class="sxs-lookup"><span data-stu-id="89dc8-354">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="89dc8-355">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="89dc8-355">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="89dc8-356">針對大小總計大於 2 gb 的陣列，設定64位平臺上的垃圾收集行程支援。</span><span class="sxs-lookup"><span data-stu-id="89dc8-356">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="89dc8-357">預設：啟用（`1`）。</span><span class="sxs-lookup"><span data-stu-id="89dc8-357">Default: Enabled (`1`).</span></span>
- <span data-ttu-id="89dc8-358">在未來的 .NET 版本中，此選項可能會過時。</span><span class="sxs-lookup"><span data-stu-id="89dc8-358">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="89dc8-359">設定名稱</span><span class="sxs-lookup"><span data-stu-id="89dc8-359">Setting name</span></span> | <span data-ttu-id="89dc8-360">值</span><span class="sxs-lookup"><span data-stu-id="89dc8-360">Values</span></span> | <span data-ttu-id="89dc8-361">引進的版本</span><span class="sxs-lookup"><span data-stu-id="89dc8-361">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="89dc8-362">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="89dc8-362">**runtimeconfig.json**</span></span> | <span data-ttu-id="89dc8-363">N/A</span><span class="sxs-lookup"><span data-stu-id="89dc8-363">N/A</span></span> | <span data-ttu-id="89dc8-364">N/A</span><span class="sxs-lookup"><span data-stu-id="89dc8-364">N/A</span></span> | <span data-ttu-id="89dc8-365">N/A</span><span class="sxs-lookup"><span data-stu-id="89dc8-365">N/A</span></span> |
| <span data-ttu-id="89dc8-366">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="89dc8-366">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="89dc8-367">已啟用 `1`</span><span class="sxs-lookup"><span data-stu-id="89dc8-367">`1` - enabled</span></span><br/> <span data-ttu-id="89dc8-368">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="89dc8-368">`0` - disabled</span></span> | <span data-ttu-id="89dc8-369">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="89dc8-369">.NET Core 1.0</span></span> |
| <span data-ttu-id="89dc8-370">**.NET Framework 的 app.config**</span><span class="sxs-lookup"><span data-stu-id="89dc8-370">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="89dc8-371">Gcallowverylargeobjects></span><span class="sxs-lookup"><span data-stu-id="89dc8-371">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="89dc8-372">已啟用 `1`</span><span class="sxs-lookup"><span data-stu-id="89dc8-372">`1` - enabled</span></span><br/> <span data-ttu-id="89dc8-373">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="89dc8-373">`0` - disabled</span></span> | <span data-ttu-id="89dc8-374">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="89dc8-374">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="89dc8-375">大型物件堆積閾值</span><span class="sxs-lookup"><span data-stu-id="89dc8-375">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="89dc8-376">LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="89dc8-376">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="89dc8-377">指定導致物件在大型物件堆積（LOH）上執行的閾值大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="89dc8-377">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="89dc8-378">預設閾值為85000個位元組。</span><span class="sxs-lookup"><span data-stu-id="89dc8-378">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="89dc8-379">您指定的值必須大於預設閾值。</span><span class="sxs-lookup"><span data-stu-id="89dc8-379">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="89dc8-380">設定名稱</span><span class="sxs-lookup"><span data-stu-id="89dc8-380">Setting name</span></span> | <span data-ttu-id="89dc8-381">值</span><span class="sxs-lookup"><span data-stu-id="89dc8-381">Values</span></span> | <span data-ttu-id="89dc8-382">引進的版本</span><span class="sxs-lookup"><span data-stu-id="89dc8-382">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="89dc8-383">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="89dc8-383">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="89dc8-384">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="89dc8-384">*decimal value*</span></span> | <span data-ttu-id="89dc8-385">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="89dc8-385">.NET Core 1.0</span></span> |
| <span data-ttu-id="89dc8-386">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="89dc8-386">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="89dc8-387">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="89dc8-387">*hexadecimal value*</span></span> | <span data-ttu-id="89dc8-388">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="89dc8-388">.NET Core 1.0</span></span> |
| <span data-ttu-id="89dc8-389">**.NET Framework 的 app.config**</span><span class="sxs-lookup"><span data-stu-id="89dc8-389">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="89dc8-390">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="89dc8-390">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="89dc8-391">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="89dc8-391">*decimal value*</span></span> | <span data-ttu-id="89dc8-392">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="89dc8-392">.NET Framework 4.8</span></span> |

<span data-ttu-id="89dc8-393">範例：</span><span class="sxs-lookup"><span data-stu-id="89dc8-393">Example:</span></span>

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
> <span data-ttu-id="89dc8-394">如果您要在 *.runtimeconfig.json*中設定選項，請指定十進位值。</span><span class="sxs-lookup"><span data-stu-id="89dc8-394">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="89dc8-395">如果您要將選項設定為環境變數，請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="89dc8-395">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="89dc8-396">例如，若要設定120000個位元組的閾值大小，JSON 檔案的值會是120000，而環境變數的值則是0x1D4C0 或1D4C0。</span><span class="sxs-lookup"><span data-stu-id="89dc8-396">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="89dc8-397">獨立 GC</span><span class="sxs-lookup"><span data-stu-id="89dc8-397">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="89dc8-398">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="89dc8-398">COMPlus_GCName</span></span>

- <span data-ttu-id="89dc8-399">指定包含執行時間打算載入之垃圾收集行程的程式庫路徑。</span><span class="sxs-lookup"><span data-stu-id="89dc8-399">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="89dc8-400">如需詳細資訊，請參閱[獨立 GC 載入器設計](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md)。</span><span class="sxs-lookup"><span data-stu-id="89dc8-400">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="89dc8-401">設定名稱</span><span class="sxs-lookup"><span data-stu-id="89dc8-401">Setting name</span></span> | <span data-ttu-id="89dc8-402">值</span><span class="sxs-lookup"><span data-stu-id="89dc8-402">Values</span></span> | <span data-ttu-id="89dc8-403">引進的版本</span><span class="sxs-lookup"><span data-stu-id="89dc8-403">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="89dc8-404">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="89dc8-404">**runtimeconfig.json**</span></span> | <span data-ttu-id="89dc8-405">N/A</span><span class="sxs-lookup"><span data-stu-id="89dc8-405">N/A</span></span> | <span data-ttu-id="89dc8-406">N/A</span><span class="sxs-lookup"><span data-stu-id="89dc8-406">N/A</span></span> | <span data-ttu-id="89dc8-407">N/A</span><span class="sxs-lookup"><span data-stu-id="89dc8-407">N/A</span></span> |
| <span data-ttu-id="89dc8-408">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="89dc8-408">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="89dc8-409">*string_path*</span><span class="sxs-lookup"><span data-stu-id="89dc8-409">*string_path*</span></span> | <span data-ttu-id="89dc8-410">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="89dc8-410">.NET Core 2.0</span></span> |
