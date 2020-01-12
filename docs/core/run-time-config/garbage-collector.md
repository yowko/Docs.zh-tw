---
title: 垃圾收集行程 config 設定
description: 瞭解用來設定垃圾收集行程如何管理 .NET Core 應用程式記憶體的執行時間設定。
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: 24e5c47de781e7eed5f76d2c551cac2dce1e8f05
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900101"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="99ed9-103">用於垃圾收集的執行時間設定選項</span><span class="sxs-lookup"><span data-stu-id="99ed9-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="99ed9-104">此頁面包含可在執行時間變更之垃圾收集行程（GC）設定的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="99ed9-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="99ed9-105">如果您正嘗試達到執行中應用程式的尖峰效能，請考慮使用這些設定。</span><span class="sxs-lookup"><span data-stu-id="99ed9-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="99ed9-106">不過，在一般情況下，預設值可為大部分的應用程式提供最佳效能。</span><span class="sxs-lookup"><span data-stu-id="99ed9-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="99ed9-107">這些設定會依此頁面的群組排列。</span><span class="sxs-lookup"><span data-stu-id="99ed9-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="99ed9-108">每個群組內的設定通常會彼此搭配使用，以達成特定結果。</span><span class="sxs-lookup"><span data-stu-id="99ed9-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="99ed9-109">這些設定也可以在應用程式執行時動態變更，因此您設定的任何執行時間設定可能會遭到覆寫。</span><span class="sxs-lookup"><span data-stu-id="99ed9-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="99ed9-110">某些設定（例如[延遲層級](../../standard/garbage-collection/latency.md)）通常只會在設計階段透過 API 進行設定。</span><span class="sxs-lookup"><span data-stu-id="99ed9-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="99ed9-111">此頁面會省略這類設定。</span><span class="sxs-lookup"><span data-stu-id="99ed9-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="99ed9-112">針對 [數值]，使用十進位標記法做為 *.runtimeconfig.json*檔案中的設定，並針對環境變數設定使用十六進位標記法。</span><span class="sxs-lookup"><span data-stu-id="99ed9-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="99ed9-113">若為十六進位值，您可以使用或不搭配 "0x" 前置詞來指定它們。</span><span class="sxs-lookup"><span data-stu-id="99ed9-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="99ed9-114">垃圾收集的種類</span><span class="sxs-lookup"><span data-stu-id="99ed9-114">Flavors of garbage collection</span></span>

<span data-ttu-id="99ed9-115">垃圾收集的兩個主要類別是工作站 GC 和伺服器 GC。</span><span class="sxs-lookup"><span data-stu-id="99ed9-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="99ed9-116">如需兩者之間差異的詳細資訊，請參閱[垃圾收集的基本](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection)概念。</span><span class="sxs-lookup"><span data-stu-id="99ed9-116">For more information about differences between the two, see [Fundamentals of garbage collection](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span></span>

<span data-ttu-id="99ed9-117">垃圾收集的 subflavors 是背景和非並行的。</span><span class="sxs-lookup"><span data-stu-id="99ed9-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="99ed9-118">使用下列設定來選取垃圾收集的種類：</span><span class="sxs-lookup"><span data-stu-id="99ed9-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="99ed9-119">System.web/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="99ed9-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="99ed9-120">設定應用程式是否使用工作站垃圾收集或伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="99ed9-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="99ed9-121">預設值：工作站垃圾收集（`false`）。</span><span class="sxs-lookup"><span data-stu-id="99ed9-121">Default: Workstation garbage collection (`false`).</span></span>

| | <span data-ttu-id="99ed9-122">設定名稱</span><span class="sxs-lookup"><span data-stu-id="99ed9-122">Setting name</span></span> | <span data-ttu-id="99ed9-123">值</span><span class="sxs-lookup"><span data-stu-id="99ed9-123">Values</span></span> | <span data-ttu-id="99ed9-124">引進的版本</span><span class="sxs-lookup"><span data-stu-id="99ed9-124">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="99ed9-125">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="99ed9-125">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="99ed9-126">`false`-工作站</span><span class="sxs-lookup"><span data-stu-id="99ed9-126">`false` - workstation</span></span><br/><span data-ttu-id="99ed9-127">`true`-伺服器</span><span class="sxs-lookup"><span data-stu-id="99ed9-127">`true` - server</span></span> | <span data-ttu-id="99ed9-128">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="99ed9-128">.NET Core 1.0</span></span> |
| <span data-ttu-id="99ed9-129">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="99ed9-129">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="99ed9-130">`0`-工作站</span><span class="sxs-lookup"><span data-stu-id="99ed9-130">`0` - workstation</span></span><br/><span data-ttu-id="99ed9-131">`1`-伺服器</span><span class="sxs-lookup"><span data-stu-id="99ed9-131">`1` - server</span></span> | <span data-ttu-id="99ed9-132">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="99ed9-132">.NET Core 1.0</span></span> |
| <span data-ttu-id="99ed9-133">**.NET Framework 的 app.config**</span><span class="sxs-lookup"><span data-stu-id="99ed9-133">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="99ed9-134">GCServer</span><span class="sxs-lookup"><span data-stu-id="99ed9-134">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="99ed9-135">`false`-工作站</span><span class="sxs-lookup"><span data-stu-id="99ed9-135">`false` - workstation</span></span><br/><span data-ttu-id="99ed9-136">`true`-伺服器</span><span class="sxs-lookup"><span data-stu-id="99ed9-136">`true` - server</span></span> |  |

<span data-ttu-id="99ed9-137">範例：</span><span class="sxs-lookup"><span data-stu-id="99ed9-137">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="99ed9-138">System.web/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="99ed9-138">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="99ed9-139">設定是否啟用背景（並行）垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="99ed9-139">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="99ed9-140">預設：啟用（`true`）。</span><span class="sxs-lookup"><span data-stu-id="99ed9-140">Default: Enabled (`true`).</span></span>
- <span data-ttu-id="99ed9-141">如需詳細資訊，請參閱[背景垃圾收集](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection)和[背景伺服器垃圾收集](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection)。</span><span class="sxs-lookup"><span data-stu-id="99ed9-141">For more information, see [Background garbage collection](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) and [Background server garbage collection](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span></span>

| | <span data-ttu-id="99ed9-142">設定名稱</span><span class="sxs-lookup"><span data-stu-id="99ed9-142">Setting name</span></span> | <span data-ttu-id="99ed9-143">值</span><span class="sxs-lookup"><span data-stu-id="99ed9-143">Values</span></span> | <span data-ttu-id="99ed9-144">引進的版本</span><span class="sxs-lookup"><span data-stu-id="99ed9-144">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="99ed9-145">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="99ed9-145">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="99ed9-146">`true`-背景 GC</span><span class="sxs-lookup"><span data-stu-id="99ed9-146">`true` - background GC</span></span><br/><span data-ttu-id="99ed9-147">`false`-非並行 GC</span><span class="sxs-lookup"><span data-stu-id="99ed9-147">`false` - non-concurrent GC</span></span> | <span data-ttu-id="99ed9-148">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="99ed9-148">.NET Core 1.0</span></span> |
| <span data-ttu-id="99ed9-149">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="99ed9-149">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="99ed9-150">`true`-背景 GC</span><span class="sxs-lookup"><span data-stu-id="99ed9-150">`true` - background GC</span></span><br/><span data-ttu-id="99ed9-151">`false`-非並行 GC</span><span class="sxs-lookup"><span data-stu-id="99ed9-151">`false` - non-concurrent GC</span></span> | <span data-ttu-id="99ed9-152">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="99ed9-152">.NET Core 1.0</span></span> |
| <span data-ttu-id="99ed9-153">**.NET Framework 的 app.config**</span><span class="sxs-lookup"><span data-stu-id="99ed9-153">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="99ed9-154">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="99ed9-154">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="99ed9-155">`true`-背景 GC</span><span class="sxs-lookup"><span data-stu-id="99ed9-155">`true` - background GC</span></span><br/><span data-ttu-id="99ed9-156">`false`-非並行 GC</span><span class="sxs-lookup"><span data-stu-id="99ed9-156">`false` - non-concurrent GC</span></span> |  |

<span data-ttu-id="99ed9-157">範例：</span><span class="sxs-lookup"><span data-stu-id="99ed9-157">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

## <a name="manage-resource-usage"></a><span data-ttu-id="99ed9-158">管理資源使用量</span><span class="sxs-lookup"><span data-stu-id="99ed9-158">Manage resource usage</span></span>

<span data-ttu-id="99ed9-159">使用本節所述的設定來管理垃圾收集行程的記憶體和處理器使用量。</span><span class="sxs-lookup"><span data-stu-id="99ed9-159">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="99ed9-160">如需有關這些設定的詳細資訊，請參閱[工作站與伺服器 GC 之間的中間](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/)專案 blog。</span><span class="sxs-lookup"><span data-stu-id="99ed9-160">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="99ed9-161">HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="99ed9-161">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="99ed9-162">限制垃圾收集行程所建立的堆積數目。</span><span class="sxs-lookup"><span data-stu-id="99ed9-162">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="99ed9-163">僅適用于伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="99ed9-163">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="99ed9-164">如果已啟用 GC 處理器親和性（這是預設值），則堆積計數設定會如何 `n` GC 堆積/執行緒到第一個 `n` 處理器。</span><span class="sxs-lookup"><span data-stu-id="99ed9-164">If GC processor affinity is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="99ed9-165">（使用將相似化為 mask 或將相似化為範圍設定，以確切指定要將相似化為的處理器）。</span><span class="sxs-lookup"><span data-stu-id="99ed9-165">(Use the affinitize mask or affinitize ranges settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="99ed9-166">如果停用 GC 處理器親和性，這項設定會限制 GC 堆積的數目。</span><span class="sxs-lookup"><span data-stu-id="99ed9-166">If GC processor affinity is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="99ed9-167">如需詳細資訊，請參閱[GCHeapCount 備註](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks)。</span><span class="sxs-lookup"><span data-stu-id="99ed9-167">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="99ed9-168">設定名稱</span><span class="sxs-lookup"><span data-stu-id="99ed9-168">Setting name</span></span> | <span data-ttu-id="99ed9-169">值</span><span class="sxs-lookup"><span data-stu-id="99ed9-169">Values</span></span> | <span data-ttu-id="99ed9-170">引進的版本</span><span class="sxs-lookup"><span data-stu-id="99ed9-170">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="99ed9-171">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="99ed9-171">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="99ed9-172">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="99ed9-172">*decimal value*</span></span> | <span data-ttu-id="99ed9-173">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="99ed9-173">.NET Core 3.0</span></span> |
| <span data-ttu-id="99ed9-174">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="99ed9-174">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="99ed9-175">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="99ed9-175">*hexadecimal value*</span></span> | <span data-ttu-id="99ed9-176">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="99ed9-176">.NET Core 3.0</span></span> |
| <span data-ttu-id="99ed9-177">**.NET Framework 的 app.config**</span><span class="sxs-lookup"><span data-stu-id="99ed9-177">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="99ed9-178">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="99ed9-178">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="99ed9-179">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="99ed9-179">*decimal value*</span></span> | <span data-ttu-id="99ed9-180">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="99ed9-180">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="99ed9-181">範例：</span><span class="sxs-lookup"><span data-stu-id="99ed9-181">Example:</span></span>

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
> <span data-ttu-id="99ed9-182">如果您要在 *.runtimeconfig.json*中設定選項，請指定十進位值。</span><span class="sxs-lookup"><span data-stu-id="99ed9-182">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="99ed9-183">如果您要將選項設定為環境變數，請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="99ed9-183">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="99ed9-184">例如，若要將堆積數目限制為16，JSON 檔案的值會是16，而環境變數的值則是0x10 或10。</span><span class="sxs-lookup"><span data-stu-id="99ed9-184">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="99ed9-185">HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="99ed9-185">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="99ed9-186">指定垃圾收集行程執行緒應該使用的確切處理器。</span><span class="sxs-lookup"><span data-stu-id="99ed9-186">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="99ed9-187">如果藉由將 `System.GC.NoAffinitize` 設定為 `true`來停用處理器親和性，則會忽略此設定。</span><span class="sxs-lookup"><span data-stu-id="99ed9-187">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="99ed9-188">僅適用于伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="99ed9-188">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="99ed9-189">值是一個位元遮罩，用來定義進程可用的處理器。</span><span class="sxs-lookup"><span data-stu-id="99ed9-189">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="99ed9-190">例如，十進位值1023（如果您使用環境變數，則為0x3FF 或3FF 的十六進位值）是 0011 1111 1111 （二進位標記法）。</span><span class="sxs-lookup"><span data-stu-id="99ed9-190">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="99ed9-191">這會指定要使用前10個處理器。</span><span class="sxs-lookup"><span data-stu-id="99ed9-191">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="99ed9-192">若要指定接下來的10個處理器（也就是處理器10-19），請指定十進位值1047552（或0xFFC00 或 FFC00 的十六進位值），這相當於二進位值 1111 1111 1100 0000 0000。</span><span class="sxs-lookup"><span data-stu-id="99ed9-192">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="99ed9-193">設定名稱</span><span class="sxs-lookup"><span data-stu-id="99ed9-193">Setting name</span></span> | <span data-ttu-id="99ed9-194">值</span><span class="sxs-lookup"><span data-stu-id="99ed9-194">Values</span></span> | <span data-ttu-id="99ed9-195">引進的版本</span><span class="sxs-lookup"><span data-stu-id="99ed9-195">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="99ed9-196">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="99ed9-196">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="99ed9-197">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="99ed9-197">*decimal value*</span></span> | <span data-ttu-id="99ed9-198">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="99ed9-198">.NET Core 3.0</span></span> |
| <span data-ttu-id="99ed9-199">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="99ed9-199">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="99ed9-200">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="99ed9-200">*hexadecimal value*</span></span> | <span data-ttu-id="99ed9-201">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="99ed9-201">.NET Core 3.0</span></span> |
| <span data-ttu-id="99ed9-202">**.NET Framework 的 app.config**</span><span class="sxs-lookup"><span data-stu-id="99ed9-202">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="99ed9-203">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="99ed9-203">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="99ed9-204">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="99ed9-204">*decimal value*</span></span> | <span data-ttu-id="99ed9-205">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="99ed9-205">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="99ed9-206">範例：</span><span class="sxs-lookup"><span data-stu-id="99ed9-206">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="99ed9-207">GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="99ed9-207">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="99ed9-208">指定要用於垃圾收集行程執行緒的處理器清單。</span><span class="sxs-lookup"><span data-stu-id="99ed9-208">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="99ed9-209">此設定類似于 `System.GC.HeapAffinitizeMask`，但它可讓您指定64個以上的處理器。</span><span class="sxs-lookup"><span data-stu-id="99ed9-209">This setting is similar to `System.GC.HeapAffinitizeMask`, except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="99ed9-210">若是 Windows 作業系統，請在處理器編號或範圍前面加上對應的[CPU 群組](/windows/win32/procthread/processor-groups)，例如 "0： 1-10，0：12，1： 50-52，1： 70"。</span><span class="sxs-lookup"><span data-stu-id="99ed9-210">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="99ed9-211">如果藉由將 `System.GC.NoAffinitize` 設定為 `true`來停用處理器親和性，則會忽略此設定。</span><span class="sxs-lookup"><span data-stu-id="99ed9-211">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="99ed9-212">僅適用于伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="99ed9-212">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="99ed9-213">如需詳細資訊，請參閱 Maoni Stephens 的 blog 上的[針對具有 > 64 cpu 的電腦，讓 CPU 設定更好用於 GC](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) 。</span><span class="sxs-lookup"><span data-stu-id="99ed9-213">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="99ed9-214">設定名稱</span><span class="sxs-lookup"><span data-stu-id="99ed9-214">Setting name</span></span> | <span data-ttu-id="99ed9-215">值</span><span class="sxs-lookup"><span data-stu-id="99ed9-215">Values</span></span> | <span data-ttu-id="99ed9-216">引進的版本</span><span class="sxs-lookup"><span data-stu-id="99ed9-216">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="99ed9-217">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="99ed9-217">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="99ed9-218">以逗號分隔的處理器編號或處理器編號範圍清單。</span><span class="sxs-lookup"><span data-stu-id="99ed9-218">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="99ed9-219">Unix 範例： "1-10，12，50-52，70"</span><span class="sxs-lookup"><span data-stu-id="99ed9-219">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="99ed9-220">Windows 範例： "0： 1-10，0：12，1： 50-52，1： 70"</span><span class="sxs-lookup"><span data-stu-id="99ed9-220">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="99ed9-221">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="99ed9-221">.NET Core 3.0</span></span> |
| <span data-ttu-id="99ed9-222">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="99ed9-222">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="99ed9-223">以逗號分隔的處理器編號或處理器編號範圍清單。</span><span class="sxs-lookup"><span data-stu-id="99ed9-223">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="99ed9-224">Unix 範例： "1-10，12，50-52，70"</span><span class="sxs-lookup"><span data-stu-id="99ed9-224">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="99ed9-225">Windows 範例： "0： 1-10，0：12，1： 50-52，1： 70"</span><span class="sxs-lookup"><span data-stu-id="99ed9-225">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="99ed9-226">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="99ed9-226">.NET Core 3.0</span></span> |

<span data-ttu-id="99ed9-227">範例：</span><span class="sxs-lookup"><span data-stu-id="99ed9-227">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="99ed9-228">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="99ed9-228">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="99ed9-229">設定垃圾收集行程是否使用[CPU 群組](/windows/win32/procthread/processor-groups)。</span><span class="sxs-lookup"><span data-stu-id="99ed9-229">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="99ed9-230">當64位 Windows 電腦具有多個 CPU 群組（也就是，有超過64個處理器）時，啟用這個元素會延伸所有 CPU 群組的垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="99ed9-230">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="99ed9-231">垃圾收集行程會使用所有核心來建立和平衡堆積。</span><span class="sxs-lookup"><span data-stu-id="99ed9-231">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="99ed9-232">僅適用于64位 Windows 作業系統上的伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="99ed9-232">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="99ed9-233">預設：停用（`0`）。</span><span class="sxs-lookup"><span data-stu-id="99ed9-233">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="99ed9-234">如需詳細資訊，請參閱 Maoni Stephens 的 blog 上的[針對具有 > 64 cpu 的電腦，讓 CPU 設定更好用於 GC](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) 。</span><span class="sxs-lookup"><span data-stu-id="99ed9-234">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="99ed9-235">設定名稱</span><span class="sxs-lookup"><span data-stu-id="99ed9-235">Setting name</span></span> | <span data-ttu-id="99ed9-236">值</span><span class="sxs-lookup"><span data-stu-id="99ed9-236">Values</span></span> | <span data-ttu-id="99ed9-237">引進的版本</span><span class="sxs-lookup"><span data-stu-id="99ed9-237">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="99ed9-238">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="99ed9-238">**runtimeconfig.json**</span></span> | <span data-ttu-id="99ed9-239">N/A</span><span class="sxs-lookup"><span data-stu-id="99ed9-239">N/A</span></span> | <span data-ttu-id="99ed9-240">N/A</span><span class="sxs-lookup"><span data-stu-id="99ed9-240">N/A</span></span> | <span data-ttu-id="99ed9-241">N/A</span><span class="sxs-lookup"><span data-stu-id="99ed9-241">N/A</span></span> |
| <span data-ttu-id="99ed9-242">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="99ed9-242">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="99ed9-243">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="99ed9-243">`0` - disabled</span></span><br/><span data-ttu-id="99ed9-244">已啟用 `1`</span><span class="sxs-lookup"><span data-stu-id="99ed9-244">`1` - enabled</span></span> | <span data-ttu-id="99ed9-245">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="99ed9-245">.NET Core 1.0</span></span> |
| <span data-ttu-id="99ed9-246">**.NET Framework 的 app.config**</span><span class="sxs-lookup"><span data-stu-id="99ed9-246">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="99ed9-247">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="99ed9-247">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="99ed9-248">`false`-已停用</span><span class="sxs-lookup"><span data-stu-id="99ed9-248">`false` - disabled</span></span><br/><span data-ttu-id="99ed9-249">已啟用 `true`</span><span class="sxs-lookup"><span data-stu-id="99ed9-249">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="99ed9-250">若要將 common language runtime （CLR）設定為同時將執行緒集區中的執行緒散發到所有 CPU 群組，請啟用 [ [Thread_UseAllCpuGroups 元素](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)] 選項。</span><span class="sxs-lookup"><span data-stu-id="99ed9-250">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="99ed9-251">針對 .NET Core 應用程式，您可以將 `COMPlus_Thread_UseAllCpuGroups` 環境變數的值設定為 `1`來啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="99ed9-251">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="99ed9-252">NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="99ed9-252">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="99ed9-253">指定是否要使用處理器*將相似化為*垃圾收集執行緒。</span><span class="sxs-lookup"><span data-stu-id="99ed9-253">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="99ed9-254">若要將相似化為 GC 執行緒，這表示它只能在其特定的 CPU 上執行。</span><span class="sxs-lookup"><span data-stu-id="99ed9-254">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="99ed9-255">會針對每個 GC 執行緒建立堆積。</span><span class="sxs-lookup"><span data-stu-id="99ed9-255">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="99ed9-256">僅適用于伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="99ed9-256">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="99ed9-257">預設值：使用處理器（`false`）將相似化為垃圾收集執行緒。</span><span class="sxs-lookup"><span data-stu-id="99ed9-257">Default: Affinitize garbage collection threads with processors (`false`).</span></span>

| | <span data-ttu-id="99ed9-258">設定名稱</span><span class="sxs-lookup"><span data-stu-id="99ed9-258">Setting name</span></span> | <span data-ttu-id="99ed9-259">值</span><span class="sxs-lookup"><span data-stu-id="99ed9-259">Values</span></span> | <span data-ttu-id="99ed9-260">引進的版本</span><span class="sxs-lookup"><span data-stu-id="99ed9-260">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="99ed9-261">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="99ed9-261">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="99ed9-262">`false`-將相似化為</span><span class="sxs-lookup"><span data-stu-id="99ed9-262">`false` - affinitize</span></span><br/><span data-ttu-id="99ed9-263">`true`-不將相似化為</span><span class="sxs-lookup"><span data-stu-id="99ed9-263">`true` - don't affinitize</span></span> | <span data-ttu-id="99ed9-264">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="99ed9-264">.NET Core 3.0</span></span> |
| <span data-ttu-id="99ed9-265">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="99ed9-265">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="99ed9-266">`0`-將相似化為</span><span class="sxs-lookup"><span data-stu-id="99ed9-266">`0` - affinitize</span></span><br/><span data-ttu-id="99ed9-267">`1`-不將相似化為</span><span class="sxs-lookup"><span data-stu-id="99ed9-267">`1` - don't affinitize</span></span> | <span data-ttu-id="99ed9-268">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="99ed9-268">.NET Core 3.0</span></span> |
| <span data-ttu-id="99ed9-269">**.NET Framework 的 app.config**</span><span class="sxs-lookup"><span data-stu-id="99ed9-269">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="99ed9-270">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="99ed9-270">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="99ed9-271">`false`-將相似化為</span><span class="sxs-lookup"><span data-stu-id="99ed9-271">`false` - affinitize</span></span><br/><span data-ttu-id="99ed9-272">`true`-不將相似化為</span><span class="sxs-lookup"><span data-stu-id="99ed9-272">`true` - don't affinitize</span></span> | <span data-ttu-id="99ed9-273">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="99ed9-273">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="99ed9-274">範例：</span><span class="sxs-lookup"><span data-stu-id="99ed9-274">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="99ed9-275">HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="99ed9-275">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="99ed9-276">指定 GC 堆積和 GC 簿記的認可大小上限（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="99ed9-276">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>

| | <span data-ttu-id="99ed9-277">設定名稱</span><span class="sxs-lookup"><span data-stu-id="99ed9-277">Setting name</span></span> | <span data-ttu-id="99ed9-278">值</span><span class="sxs-lookup"><span data-stu-id="99ed9-278">Values</span></span> | <span data-ttu-id="99ed9-279">引進的版本</span><span class="sxs-lookup"><span data-stu-id="99ed9-279">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="99ed9-280">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="99ed9-280">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="99ed9-281">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="99ed9-281">*decimal value*</span></span> | <span data-ttu-id="99ed9-282">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="99ed9-282">.NET Core 3.0</span></span> |
| <span data-ttu-id="99ed9-283">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="99ed9-283">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="99ed9-284">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="99ed9-284">*hexadecimal value*</span></span> | <span data-ttu-id="99ed9-285">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="99ed9-285">.NET Core 3.0</span></span> |

<span data-ttu-id="99ed9-286">範例：</span><span class="sxs-lookup"><span data-stu-id="99ed9-286">Example:</span></span>

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
> <span data-ttu-id="99ed9-287">如果您要在 *.runtimeconfig.json*中設定選項，請指定十進位值。</span><span class="sxs-lookup"><span data-stu-id="99ed9-287">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="99ed9-288">如果您要將選項設定為環境變數，請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="99ed9-288">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="99ed9-289">例如，若要指定200數量（MiB）的堆積固定限制，其值會是209715200（針對 JSON 檔案）和0xC800000 或 C800000 （適用于環境變數）。</span><span class="sxs-lookup"><span data-stu-id="99ed9-289">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="99ed9-290">HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="99ed9-290">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="99ed9-291">將 GC 堆積使用量指定為總記憶體的百分比。</span><span class="sxs-lookup"><span data-stu-id="99ed9-291">Specifies the GC heap usage as a percentage of the total memory.</span></span>

| | <span data-ttu-id="99ed9-292">設定名稱</span><span class="sxs-lookup"><span data-stu-id="99ed9-292">Setting name</span></span> | <span data-ttu-id="99ed9-293">值</span><span class="sxs-lookup"><span data-stu-id="99ed9-293">Values</span></span> | <span data-ttu-id="99ed9-294">引進的版本</span><span class="sxs-lookup"><span data-stu-id="99ed9-294">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="99ed9-295">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="99ed9-295">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="99ed9-296">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="99ed9-296">*decimal value*</span></span> | <span data-ttu-id="99ed9-297">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="99ed9-297">.NET Core 3.0</span></span> |
| <span data-ttu-id="99ed9-298">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="99ed9-298">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="99ed9-299">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="99ed9-299">*hexadecimal value*</span></span> | <span data-ttu-id="99ed9-300">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="99ed9-300">.NET Core 3.0</span></span> |

<span data-ttu-id="99ed9-301">範例：</span><span class="sxs-lookup"><span data-stu-id="99ed9-301">Example:</span></span>

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
> <span data-ttu-id="99ed9-302">如果您要在 *.runtimeconfig.json*中設定選項，請指定十進位值。</span><span class="sxs-lookup"><span data-stu-id="99ed9-302">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="99ed9-303">如果您要將選項設定為環境變數，請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="99ed9-303">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="99ed9-304">例如，若要將堆積使用量限制為30%，JSON 檔案的值會是30，而0x1E 或1E 則適用于環境變數。</span><span class="sxs-lookup"><span data-stu-id="99ed9-304">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="99ed9-305">RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="99ed9-305">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="99ed9-306">設定是否要將應該刪除的區段放在待命清單上以供日後使用，或發行回作業系統（OS）。</span><span class="sxs-lookup"><span data-stu-id="99ed9-306">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="99ed9-307">預設值：將區段釋放回作業系統（`false`）。</span><span class="sxs-lookup"><span data-stu-id="99ed9-307">Default: Release segments back to the operating system (`false`).</span></span>

| | <span data-ttu-id="99ed9-308">設定名稱</span><span class="sxs-lookup"><span data-stu-id="99ed9-308">Setting name</span></span> | <span data-ttu-id="99ed9-309">值</span><span class="sxs-lookup"><span data-stu-id="99ed9-309">Values</span></span> | <span data-ttu-id="99ed9-310">引進的版本</span><span class="sxs-lookup"><span data-stu-id="99ed9-310">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="99ed9-311">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="99ed9-311">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="99ed9-312">`false`-發行至 OS</span><span class="sxs-lookup"><span data-stu-id="99ed9-312">`false` - release to OS</span></span><br/><span data-ttu-id="99ed9-313">`true`-put 待命</span><span class="sxs-lookup"><span data-stu-id="99ed9-313">`true` - put on standby</span></span>| <span data-ttu-id="99ed9-314">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="99ed9-314">.NET Core 1.0</span></span> |
| <span data-ttu-id="99ed9-315">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="99ed9-315">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="99ed9-316">`0`-發行至 OS</span><span class="sxs-lookup"><span data-stu-id="99ed9-316">`0` - release to OS</span></span><br/><span data-ttu-id="99ed9-317">`1`-put 待命</span><span class="sxs-lookup"><span data-stu-id="99ed9-317">`1` - put on standby</span></span> | <span data-ttu-id="99ed9-318">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="99ed9-318">.NET Core 1.0</span></span> |

<span data-ttu-id="99ed9-319">範例：</span><span class="sxs-lookup"><span data-stu-id="99ed9-319">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

## <a name="large-pages"></a><span data-ttu-id="99ed9-320">大型頁面</span><span class="sxs-lookup"><span data-stu-id="99ed9-320">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="99ed9-321">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="99ed9-321">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="99ed9-322">指定在設定堆積固定限制時是否應該使用大型分頁。</span><span class="sxs-lookup"><span data-stu-id="99ed9-322">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="99ed9-323">預設：停用（`0`）。</span><span class="sxs-lookup"><span data-stu-id="99ed9-323">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="99ed9-324">這是實驗性設定。</span><span class="sxs-lookup"><span data-stu-id="99ed9-324">This is an experimental setting.</span></span>

| | <span data-ttu-id="99ed9-325">設定名稱</span><span class="sxs-lookup"><span data-stu-id="99ed9-325">Setting name</span></span> | <span data-ttu-id="99ed9-326">值</span><span class="sxs-lookup"><span data-stu-id="99ed9-326">Values</span></span> | <span data-ttu-id="99ed9-327">引進的版本</span><span class="sxs-lookup"><span data-stu-id="99ed9-327">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="99ed9-328">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="99ed9-328">**runtimeconfig.json**</span></span> | <span data-ttu-id="99ed9-329">N/A</span><span class="sxs-lookup"><span data-stu-id="99ed9-329">N/A</span></span> | <span data-ttu-id="99ed9-330">N/A</span><span class="sxs-lookup"><span data-stu-id="99ed9-330">N/A</span></span> | <span data-ttu-id="99ed9-331">N/A</span><span class="sxs-lookup"><span data-stu-id="99ed9-331">N/A</span></span> |
| <span data-ttu-id="99ed9-332">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="99ed9-332">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="99ed9-333">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="99ed9-333">`0` - disabled</span></span><br/><span data-ttu-id="99ed9-334">已啟用 `1`</span><span class="sxs-lookup"><span data-stu-id="99ed9-334">`1` - enabled</span></span> | <span data-ttu-id="99ed9-335">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="99ed9-335">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="99ed9-336">大型物件</span><span class="sxs-lookup"><span data-stu-id="99ed9-336">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="99ed9-337">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="99ed9-337">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="99ed9-338">針對大小總計大於 2 gb 的陣列，設定64位平臺上的垃圾收集行程支援。</span><span class="sxs-lookup"><span data-stu-id="99ed9-338">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="99ed9-339">預設：啟用（`1`）。</span><span class="sxs-lookup"><span data-stu-id="99ed9-339">Default: Enabled (`1`).</span></span>
- <span data-ttu-id="99ed9-340">在未來的 .NET 版本中，此選項可能會過時。</span><span class="sxs-lookup"><span data-stu-id="99ed9-340">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="99ed9-341">設定名稱</span><span class="sxs-lookup"><span data-stu-id="99ed9-341">Setting name</span></span> | <span data-ttu-id="99ed9-342">值</span><span class="sxs-lookup"><span data-stu-id="99ed9-342">Values</span></span> | <span data-ttu-id="99ed9-343">引進的版本</span><span class="sxs-lookup"><span data-stu-id="99ed9-343">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="99ed9-344">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="99ed9-344">**runtimeconfig.json**</span></span> | <span data-ttu-id="99ed9-345">N/A</span><span class="sxs-lookup"><span data-stu-id="99ed9-345">N/A</span></span> | <span data-ttu-id="99ed9-346">N/A</span><span class="sxs-lookup"><span data-stu-id="99ed9-346">N/A</span></span> | <span data-ttu-id="99ed9-347">N/A</span><span class="sxs-lookup"><span data-stu-id="99ed9-347">N/A</span></span> |
| <span data-ttu-id="99ed9-348">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="99ed9-348">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="99ed9-349">已啟用 `1`</span><span class="sxs-lookup"><span data-stu-id="99ed9-349">`1` - enabled</span></span><br/> <span data-ttu-id="99ed9-350">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="99ed9-350">`0` - disabled</span></span> | <span data-ttu-id="99ed9-351">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="99ed9-351">.NET Core 1.0</span></span> |
| <span data-ttu-id="99ed9-352">**.NET Framework 的 app.config**</span><span class="sxs-lookup"><span data-stu-id="99ed9-352">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="99ed9-353">Gcallowverylargeobjects></span><span class="sxs-lookup"><span data-stu-id="99ed9-353">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="99ed9-354">已啟用 `1`</span><span class="sxs-lookup"><span data-stu-id="99ed9-354">`1` - enabled</span></span><br/> <span data-ttu-id="99ed9-355">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="99ed9-355">`0` - disabled</span></span> | <span data-ttu-id="99ed9-356">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="99ed9-356">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="99ed9-357">大型物件堆積閾值</span><span class="sxs-lookup"><span data-stu-id="99ed9-357">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="99ed9-358">LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="99ed9-358">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="99ed9-359">指定導致物件在大型物件堆積（LOH）上執行的閾值大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="99ed9-359">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="99ed9-360">預設閾值為85000個位元組。</span><span class="sxs-lookup"><span data-stu-id="99ed9-360">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="99ed9-361">您指定的值必須大於預設閾值。</span><span class="sxs-lookup"><span data-stu-id="99ed9-361">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="99ed9-362">設定名稱</span><span class="sxs-lookup"><span data-stu-id="99ed9-362">Setting name</span></span> | <span data-ttu-id="99ed9-363">值</span><span class="sxs-lookup"><span data-stu-id="99ed9-363">Values</span></span> | <span data-ttu-id="99ed9-364">引進的版本</span><span class="sxs-lookup"><span data-stu-id="99ed9-364">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="99ed9-365">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="99ed9-365">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="99ed9-366">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="99ed9-366">*decimal value*</span></span> | <span data-ttu-id="99ed9-367">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="99ed9-367">.NET Core 1.0</span></span> |
| <span data-ttu-id="99ed9-368">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="99ed9-368">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="99ed9-369">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="99ed9-369">*hexadecimal value*</span></span> | <span data-ttu-id="99ed9-370">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="99ed9-370">.NET Core 1.0</span></span> |
| <span data-ttu-id="99ed9-371">**.NET Framework 的 app.config**</span><span class="sxs-lookup"><span data-stu-id="99ed9-371">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="99ed9-372">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="99ed9-372">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="99ed9-373">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="99ed9-373">*decimal value*</span></span> | <span data-ttu-id="99ed9-374">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="99ed9-374">.NET Framework 4.8</span></span> |

<span data-ttu-id="99ed9-375">範例：</span><span class="sxs-lookup"><span data-stu-id="99ed9-375">Example:</span></span>

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
> <span data-ttu-id="99ed9-376">如果您要在 *.runtimeconfig.json*中設定選項，請指定十進位值。</span><span class="sxs-lookup"><span data-stu-id="99ed9-376">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="99ed9-377">如果您要將選項設定為環境變數，請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="99ed9-377">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="99ed9-378">例如，若要設定120000個位元組的閾值大小，JSON 檔案的值會是120000，而環境變數的值則是0x1D4C0 或1D4C0。</span><span class="sxs-lookup"><span data-stu-id="99ed9-378">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="99ed9-379">獨立 GC</span><span class="sxs-lookup"><span data-stu-id="99ed9-379">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="99ed9-380">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="99ed9-380">COMPlus_GCName</span></span>

- <span data-ttu-id="99ed9-381">指定包含執行時間打算載入之垃圾收集行程的程式庫路徑。</span><span class="sxs-lookup"><span data-stu-id="99ed9-381">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="99ed9-382">如需詳細資訊，請參閱[獨立 GC 載入器設計](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md)。</span><span class="sxs-lookup"><span data-stu-id="99ed9-382">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="99ed9-383">設定名稱</span><span class="sxs-lookup"><span data-stu-id="99ed9-383">Setting name</span></span> | <span data-ttu-id="99ed9-384">值</span><span class="sxs-lookup"><span data-stu-id="99ed9-384">Values</span></span> | <span data-ttu-id="99ed9-385">引進的版本</span><span class="sxs-lookup"><span data-stu-id="99ed9-385">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="99ed9-386">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="99ed9-386">**runtimeconfig.json**</span></span> | <span data-ttu-id="99ed9-387">N/A</span><span class="sxs-lookup"><span data-stu-id="99ed9-387">N/A</span></span> | <span data-ttu-id="99ed9-388">N/A</span><span class="sxs-lookup"><span data-stu-id="99ed9-388">N/A</span></span> | <span data-ttu-id="99ed9-389">N/A</span><span class="sxs-lookup"><span data-stu-id="99ed9-389">N/A</span></span> |
| <span data-ttu-id="99ed9-390">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="99ed9-390">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="99ed9-391">*string_path*</span><span class="sxs-lookup"><span data-stu-id="99ed9-391">*string_path*</span></span> | <span data-ttu-id="99ed9-392">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="99ed9-392">.NET Core 2.0</span></span> |
