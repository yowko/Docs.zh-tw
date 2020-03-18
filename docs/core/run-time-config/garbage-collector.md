---
title: 垃圾回收器配置設置
description: 瞭解用於配置垃圾回收器如何管理 .NET Core 應用記憶體的運行時設置。
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: 044083d69601f5092724a46d358b2ee5673d428d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76733526"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="8b3ba-103">垃圾回收的運行時配置選項</span><span class="sxs-lookup"><span data-stu-id="8b3ba-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="8b3ba-104">此頁包含有關可在運行時更改的垃圾回收器 （GC） 設置的資訊。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="8b3ba-105">如果您嘗試實現正在運行的應用的峰值性能，請考慮使用這些設置。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="8b3ba-106">但是，預設值為大多數應用程式在典型情況下提供了最佳性能。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="8b3ba-107">設置在此頁上按組排列。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="8b3ba-108">每個組中的設置通常相互結合使用，以實現特定結果。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="8b3ba-109">這些設置也可以由應用在運行時動態更改，因此您設置的任何運行時設置都可能被覆蓋。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="8b3ba-110">某些設置（如[延遲級別](../../standard/garbage-collection/latency.md)）通常僅在設計時通過 API 設置。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="8b3ba-111">此頁省略了此類設置。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="8b3ba-112">對於數位值，對*運行時 config.json*檔中的設置使用十進位標記法，對環境變數設置使用十進位標記法。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="8b3ba-113">對於十六進位值，可以使用或沒有"0x"首碼來指定它們。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="8b3ba-114">垃圾回收的味道</span><span class="sxs-lookup"><span data-stu-id="8b3ba-114">Flavors of garbage collection</span></span>

<span data-ttu-id="8b3ba-115">垃圾回收的兩個主要類型是工作站 GC 和伺服器 GC。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="8b3ba-116">有關兩者之間的差異的詳細資訊，請參閱[垃圾回收的基礎知識](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection)。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-116">For more information about differences between the two, see [Fundamentals of garbage collection](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span></span>

<span data-ttu-id="8b3ba-117">垃圾回收的子口味是背景和非併發的。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="8b3ba-118">使用以下設置選擇垃圾回收的味道：</span><span class="sxs-lookup"><span data-stu-id="8b3ba-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="8b3ba-119">系統.GC.伺服器/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="8b3ba-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="8b3ba-120">配置應用程式是使用工作站垃圾回收還是伺服器垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="8b3ba-121">預設值：工作站垃圾回收 （）。`false`</span><span class="sxs-lookup"><span data-stu-id="8b3ba-121">Default: Workstation garbage collection (`false`).</span></span>

| | <span data-ttu-id="8b3ba-122">設定名稱</span><span class="sxs-lookup"><span data-stu-id="8b3ba-122">Setting name</span></span> | <span data-ttu-id="8b3ba-123">值</span><span class="sxs-lookup"><span data-stu-id="8b3ba-123">Values</span></span> | <span data-ttu-id="8b3ba-124">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="8b3ba-124">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8b3ba-125">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-125">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="8b3ba-126">`false`- 工作站</span><span class="sxs-lookup"><span data-stu-id="8b3ba-126">`false` - workstation</span></span><br/><span data-ttu-id="8b3ba-127">`true`- 伺服器</span><span class="sxs-lookup"><span data-stu-id="8b3ba-127">`true` - server</span></span> | <span data-ttu-id="8b3ba-128">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="8b3ba-128">.NET Core 1.0</span></span> |
| <span data-ttu-id="8b3ba-129">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-129">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="8b3ba-130">`false`- 工作站</span><span class="sxs-lookup"><span data-stu-id="8b3ba-130">`false` - workstation</span></span><br/><span data-ttu-id="8b3ba-131">`true`- 伺服器</span><span class="sxs-lookup"><span data-stu-id="8b3ba-131">`true` - server</span></span> | <span data-ttu-id="8b3ba-132">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="8b3ba-132">.NET Core 1.0</span></span> |
| <span data-ttu-id="8b3ba-133">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-133">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="8b3ba-134">`0`- 工作站</span><span class="sxs-lookup"><span data-stu-id="8b3ba-134">`0` - workstation</span></span><br/><span data-ttu-id="8b3ba-135">`1`- 伺服器</span><span class="sxs-lookup"><span data-stu-id="8b3ba-135">`1` - server</span></span> | <span data-ttu-id="8b3ba-136">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="8b3ba-136">.NET Core 1.0</span></span> |
| <span data-ttu-id="8b3ba-137">**.NET 框架的應用程式佈建**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-137">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="8b3ba-138">GCServer</span><span class="sxs-lookup"><span data-stu-id="8b3ba-138">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="8b3ba-139">`false`- 工作站</span><span class="sxs-lookup"><span data-stu-id="8b3ba-139">`false` - workstation</span></span><br/><span data-ttu-id="8b3ba-140">`true`- 伺服器</span><span class="sxs-lookup"><span data-stu-id="8b3ba-140">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="8b3ba-141">範例</span><span class="sxs-lookup"><span data-stu-id="8b3ba-141">Examples</span></span>

<span data-ttu-id="8b3ba-142">*運行時配置.json*檔：</span><span class="sxs-lookup"><span data-stu-id="8b3ba-142">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="8b3ba-143">專案檔：</span><span class="sxs-lookup"><span data-stu-id="8b3ba-143">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="8b3ba-144">系統.GC.併發/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="8b3ba-144">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="8b3ba-145">配置是否啟用後臺（併發）垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-145">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="8b3ba-146">預設值： 已`true`啟用 （ 。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-146">Default: Enabled (`true`).</span></span>
- <span data-ttu-id="8b3ba-147">有關詳細資訊，請參閱[後臺垃圾回收](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection)和[後臺伺服器垃圾回收](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection)。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-147">For more information, see [Background garbage collection](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) and [Background server garbage collection](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span></span>

| | <span data-ttu-id="8b3ba-148">設定名稱</span><span class="sxs-lookup"><span data-stu-id="8b3ba-148">Setting name</span></span> | <span data-ttu-id="8b3ba-149">值</span><span class="sxs-lookup"><span data-stu-id="8b3ba-149">Values</span></span> | <span data-ttu-id="8b3ba-150">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="8b3ba-150">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8b3ba-151">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-151">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="8b3ba-152">`true`- 背景 GC</span><span class="sxs-lookup"><span data-stu-id="8b3ba-152">`true` - background GC</span></span><br/><span data-ttu-id="8b3ba-153">`false`- 非併發 GC</span><span class="sxs-lookup"><span data-stu-id="8b3ba-153">`false` - non-concurrent GC</span></span> | <span data-ttu-id="8b3ba-154">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="8b3ba-154">.NET Core 1.0</span></span> |
| <span data-ttu-id="8b3ba-155">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-155">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="8b3ba-156">`true`- 背景 GC</span><span class="sxs-lookup"><span data-stu-id="8b3ba-156">`true` - background GC</span></span><br/><span data-ttu-id="8b3ba-157">`false`- 非併發 GC</span><span class="sxs-lookup"><span data-stu-id="8b3ba-157">`false` - non-concurrent GC</span></span> | <span data-ttu-id="8b3ba-158">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="8b3ba-158">.NET Core 1.0</span></span> |
| <span data-ttu-id="8b3ba-159">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-159">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="8b3ba-160">`true`- 背景 GC</span><span class="sxs-lookup"><span data-stu-id="8b3ba-160">`true` - background GC</span></span><br/><span data-ttu-id="8b3ba-161">`false`- 非併發 GC</span><span class="sxs-lookup"><span data-stu-id="8b3ba-161">`false` - non-concurrent GC</span></span> | <span data-ttu-id="8b3ba-162">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="8b3ba-162">.NET Core 1.0</span></span> |
| <span data-ttu-id="8b3ba-163">**.NET 框架的應用程式佈建**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-163">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="8b3ba-164">gc 併發</span><span class="sxs-lookup"><span data-stu-id="8b3ba-164">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="8b3ba-165">`true`- 背景 GC</span><span class="sxs-lookup"><span data-stu-id="8b3ba-165">`true` - background GC</span></span><br/><span data-ttu-id="8b3ba-166">`false`- 非併發 GC</span><span class="sxs-lookup"><span data-stu-id="8b3ba-166">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="8b3ba-167">範例</span><span class="sxs-lookup"><span data-stu-id="8b3ba-167">Examples</span></span>

<span data-ttu-id="8b3ba-168">*運行時配置.json*檔：</span><span class="sxs-lookup"><span data-stu-id="8b3ba-168">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="8b3ba-169">專案檔：</span><span class="sxs-lookup"><span data-stu-id="8b3ba-169">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="8b3ba-170">管理資源使用方式</span><span class="sxs-lookup"><span data-stu-id="8b3ba-170">Manage resource usage</span></span>

<span data-ttu-id="8b3ba-171">使用本節中描述的設置來管理垃圾回收器的記憶體和處理器使用方式。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-171">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="8b3ba-172">有關其中一些設置的詳細資訊，請參閱[工作站和伺服器 GC 博客條目之間的中間地帶](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/)。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-172">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="8b3ba-173">系統.GC.堆計數/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="8b3ba-173">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="8b3ba-174">限制垃圾回收器創建的堆數。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-174">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="8b3ba-175">僅適用于伺服器垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-175">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="8b3ba-176">如果啟用了 GC 處理器關聯（這是預設值，則堆計數設置將`n`GC 堆/執行緒關聯化為第一個`n`處理器）。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-176">If GC processor affinity is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="8b3ba-177">（使用關連遮罩或關聯範圍設置來準確指定要關聯處理器的處理器。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-177">(Use the affinitize mask or affinitize ranges settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="8b3ba-178">如果禁用 GC 處理器關聯，此設置將限制 GC 堆的數量。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-178">If GC processor affinity is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="8b3ba-179">有關詳細資訊，請參閱[GCHeapCount 注釋](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks)。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-179">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="8b3ba-180">設定名稱</span><span class="sxs-lookup"><span data-stu-id="8b3ba-180">Setting name</span></span> | <span data-ttu-id="8b3ba-181">值</span><span class="sxs-lookup"><span data-stu-id="8b3ba-181">Values</span></span> | <span data-ttu-id="8b3ba-182">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="8b3ba-182">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8b3ba-183">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-183">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="8b3ba-184">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="8b3ba-184">*decimal value*</span></span> | <span data-ttu-id="8b3ba-185">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8b3ba-185">.NET Core 3.0</span></span> |
| <span data-ttu-id="8b3ba-186">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-186">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="8b3ba-187">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="8b3ba-187">*hexadecimal value*</span></span> | <span data-ttu-id="8b3ba-188">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8b3ba-188">.NET Core 3.0</span></span> |
| <span data-ttu-id="8b3ba-189">**.NET 框架的應用程式佈建**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-189">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="8b3ba-190">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="8b3ba-190">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="8b3ba-191">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="8b3ba-191">*decimal value*</span></span> | <span data-ttu-id="8b3ba-192">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="8b3ba-192">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="8b3ba-193">範例：</span><span class="sxs-lookup"><span data-stu-id="8b3ba-193">Example:</span></span>

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
> <span data-ttu-id="8b3ba-194">如果要在*運行時 config.json*中設置該選項，請指定一個小數值。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-194">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="8b3ba-195">如果要將該選項設置為環境變數，請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-195">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="8b3ba-196">例如，要將堆數限制為 16，JSON 檔的值將為 16，環境變數的值為 0x10 或 10。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-196">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="8b3ba-197">系統.GC.Heapaffinitize 遮罩/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="8b3ba-197">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="8b3ba-198">指定垃圾回收器執行緒應使用的確切處理器。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-198">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="8b3ba-199">如果通過設置為`System.GC.NoAffinitize``true`禁用處理器關聯，則忽略此設置。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-199">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="8b3ba-200">僅適用于伺服器垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-200">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="8b3ba-201">該值是定義進程可用的處理器的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-201">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="8b3ba-202">例如，十進位值 1023（或十六進位值 0x3FF 或 3FF，如果您正在使用環境變數）是 0011 1111 1111 在二進位標記法中。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-202">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="8b3ba-203">這指定將使用前 10 個處理器。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-203">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="8b3ba-204">要指定接下來的 10 個處理器，即處理器 10-19，請指定 1047552（或十六進位值 0xFFC00 或 FFC00），這相當於二進位值 1111 1111 1100 00000000000。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-204">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="8b3ba-205">設定名稱</span><span class="sxs-lookup"><span data-stu-id="8b3ba-205">Setting name</span></span> | <span data-ttu-id="8b3ba-206">值</span><span class="sxs-lookup"><span data-stu-id="8b3ba-206">Values</span></span> | <span data-ttu-id="8b3ba-207">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="8b3ba-207">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8b3ba-208">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-208">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="8b3ba-209">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="8b3ba-209">*decimal value*</span></span> | <span data-ttu-id="8b3ba-210">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8b3ba-210">.NET Core 3.0</span></span> |
| <span data-ttu-id="8b3ba-211">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-211">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="8b3ba-212">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="8b3ba-212">*hexadecimal value*</span></span> | <span data-ttu-id="8b3ba-213">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8b3ba-213">.NET Core 3.0</span></span> |
| <span data-ttu-id="8b3ba-214">**.NET 框架的應用程式佈建**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-214">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="8b3ba-215">GCHeapaffinitize 遮罩</span><span class="sxs-lookup"><span data-stu-id="8b3ba-215">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="8b3ba-216">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="8b3ba-216">*decimal value*</span></span> | <span data-ttu-id="8b3ba-217">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="8b3ba-217">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="8b3ba-218">範例：</span><span class="sxs-lookup"><span data-stu-id="8b3ba-218">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="8b3ba-219">系統.GC.GCHeapaffinitize 範圍/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="8b3ba-219">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="8b3ba-220">指定用於垃圾回收器執行緒的處理器清單。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-220">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="8b3ba-221">此設置類似于`System.GC.HeapAffinitizeMask`，只不過它允許您指定超過 64 個處理器。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-221">This setting is similar to `System.GC.HeapAffinitizeMask`, except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="8b3ba-222">對於 Windows 作業系統，使用相應的[CPU 組](/windows/win32/procthread/processor-groups)對處理器編號或範圍進行首碼，例如，"0：1-10，0：12，1：50-52，1：70"。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-222">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="8b3ba-223">如果通過設置為`System.GC.NoAffinitize``true`禁用處理器關聯，則忽略此設置。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-223">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="8b3ba-224">僅適用于伺服器垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-224">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="8b3ba-225">有關詳細資訊，請參閱在 Maoni Stephens 博客上[具有 > 64 個 CPU 的電腦上為 GC 提供更好的 CPU 配置](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/)。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-225">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="8b3ba-226">設定名稱</span><span class="sxs-lookup"><span data-stu-id="8b3ba-226">Setting name</span></span> | <span data-ttu-id="8b3ba-227">值</span><span class="sxs-lookup"><span data-stu-id="8b3ba-227">Values</span></span> | <span data-ttu-id="8b3ba-228">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="8b3ba-228">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8b3ba-229">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-229">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="8b3ba-230">處理器編號或處理器編號範圍的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-230">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="8b3ba-231">Unix 示例："1-10，12，50-52，70"</span><span class="sxs-lookup"><span data-stu-id="8b3ba-231">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="8b3ba-232">視窗示例："0：1-10，0：12，1：50-52，1：70"</span><span class="sxs-lookup"><span data-stu-id="8b3ba-232">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="8b3ba-233">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8b3ba-233">.NET Core 3.0</span></span> |
| <span data-ttu-id="8b3ba-234">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-234">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="8b3ba-235">處理器編號或處理器編號範圍的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-235">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="8b3ba-236">Unix 示例："1-10，12，50-52，70"</span><span class="sxs-lookup"><span data-stu-id="8b3ba-236">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="8b3ba-237">視窗示例："0：1-10，0：12，1：50-52，1：70"</span><span class="sxs-lookup"><span data-stu-id="8b3ba-237">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="8b3ba-238">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8b3ba-238">.NET Core 3.0</span></span> |

<span data-ttu-id="8b3ba-239">範例：</span><span class="sxs-lookup"><span data-stu-id="8b3ba-239">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="8b3ba-240">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="8b3ba-240">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="8b3ba-241">配置垃圾回收器是否使用[CPU 組](/windows/win32/procthread/processor-groups)。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-241">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="8b3ba-242">當 64 位 Windows 電腦具有多個 CPU 組（即，超過 64 個處理器）時，啟用此元素會跨所有 CPU 組擴展垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-242">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="8b3ba-243">垃圾回收器使用所有內核創建和平衡堆。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-243">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="8b3ba-244">僅適用于 64 位 Windows 作業系統上的伺服器垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-244">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="8b3ba-245">預設值： 已`0`禁用 （ 。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-245">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="8b3ba-246">有關詳細資訊，請參閱在 Maoni Stephens 博客上[具有 > 64 個 CPU 的電腦上為 GC 提供更好的 CPU 配置](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/)。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-246">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="8b3ba-247">設定名稱</span><span class="sxs-lookup"><span data-stu-id="8b3ba-247">Setting name</span></span> | <span data-ttu-id="8b3ba-248">值</span><span class="sxs-lookup"><span data-stu-id="8b3ba-248">Values</span></span> | <span data-ttu-id="8b3ba-249">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="8b3ba-249">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8b3ba-250">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-250">**runtimeconfig.json**</span></span> | <span data-ttu-id="8b3ba-251">N/A</span><span class="sxs-lookup"><span data-stu-id="8b3ba-251">N/A</span></span> | <span data-ttu-id="8b3ba-252">N/A</span><span class="sxs-lookup"><span data-stu-id="8b3ba-252">N/A</span></span> | <span data-ttu-id="8b3ba-253">N/A</span><span class="sxs-lookup"><span data-stu-id="8b3ba-253">N/A</span></span> |
| <span data-ttu-id="8b3ba-254">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-254">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="8b3ba-255">`0`- 禁用</span><span class="sxs-lookup"><span data-stu-id="8b3ba-255">`0` - disabled</span></span><br/><span data-ttu-id="8b3ba-256">`1`- 已啟用</span><span class="sxs-lookup"><span data-stu-id="8b3ba-256">`1` - enabled</span></span> | <span data-ttu-id="8b3ba-257">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="8b3ba-257">.NET Core 1.0</span></span> |
| <span data-ttu-id="8b3ba-258">**.NET 框架的應用程式佈建**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-258">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="8b3ba-259">GCCpu集團</span><span class="sxs-lookup"><span data-stu-id="8b3ba-259">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="8b3ba-260">`false`- 禁用</span><span class="sxs-lookup"><span data-stu-id="8b3ba-260">`false` - disabled</span></span><br/><span data-ttu-id="8b3ba-261">`true`- 已啟用</span><span class="sxs-lookup"><span data-stu-id="8b3ba-261">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="8b3ba-262">要將通用語言運行時 （CLR） 配置為將執行緒池中的執行緒分配到所有 CPU 組，請啟用[Thread_UseAllCpuGroups元素](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)選項。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-262">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="8b3ba-263">對於 .NET Core 應用，可以通過將`COMPlus_Thread_UseAllCpuGroups`環境變數的值設置為`1`來啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-263">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="8b3ba-264">系統.GC.無資訊化/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="8b3ba-264">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="8b3ba-265">指定是否將垃圾回收執行緒與處理器*關聯*化。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-265">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="8b3ba-266">關聯 GC 執行緒意味著它只能在其特定 CPU 上運行。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-266">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="8b3ba-267">為每個 GC 執行緒創建一個堆。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-267">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="8b3ba-268">僅適用于伺服器垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-268">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="8b3ba-269">預設值：使用處理器 （） 對垃圾回收執行緒`false`進行 affinitit 化。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-269">Default: Affinitize garbage collection threads with processors (`false`).</span></span>

| | <span data-ttu-id="8b3ba-270">設定名稱</span><span class="sxs-lookup"><span data-stu-id="8b3ba-270">Setting name</span></span> | <span data-ttu-id="8b3ba-271">值</span><span class="sxs-lookup"><span data-stu-id="8b3ba-271">Values</span></span> | <span data-ttu-id="8b3ba-272">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="8b3ba-272">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8b3ba-273">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-273">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="8b3ba-274">`false`- 親緣關係</span><span class="sxs-lookup"><span data-stu-id="8b3ba-274">`false` - affinitize</span></span><br/><span data-ttu-id="8b3ba-275">`true`-不要親和</span><span class="sxs-lookup"><span data-stu-id="8b3ba-275">`true` - don't affinitize</span></span> | <span data-ttu-id="8b3ba-276">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8b3ba-276">.NET Core 3.0</span></span> |
| <span data-ttu-id="8b3ba-277">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-277">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="8b3ba-278">`0`- 親緣關係</span><span class="sxs-lookup"><span data-stu-id="8b3ba-278">`0` - affinitize</span></span><br/><span data-ttu-id="8b3ba-279">`1`-不要親和</span><span class="sxs-lookup"><span data-stu-id="8b3ba-279">`1` - don't affinitize</span></span> | <span data-ttu-id="8b3ba-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8b3ba-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="8b3ba-281">**.NET 框架的應用程式佈建**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-281">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="8b3ba-282">GCNoaffinitize</span><span class="sxs-lookup"><span data-stu-id="8b3ba-282">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="8b3ba-283">`false`- 親緣關係</span><span class="sxs-lookup"><span data-stu-id="8b3ba-283">`false` - affinitize</span></span><br/><span data-ttu-id="8b3ba-284">`true`-不要親和</span><span class="sxs-lookup"><span data-stu-id="8b3ba-284">`true` - don't affinitize</span></span> | <span data-ttu-id="8b3ba-285">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="8b3ba-285">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="8b3ba-286">範例：</span><span class="sxs-lookup"><span data-stu-id="8b3ba-286">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="8b3ba-287">系統.GC.HeapHard 限制/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="8b3ba-287">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="8b3ba-288">為 GC 堆和 GC 簿記指定最大提交大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-288">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>

| | <span data-ttu-id="8b3ba-289">設定名稱</span><span class="sxs-lookup"><span data-stu-id="8b3ba-289">Setting name</span></span> | <span data-ttu-id="8b3ba-290">值</span><span class="sxs-lookup"><span data-stu-id="8b3ba-290">Values</span></span> | <span data-ttu-id="8b3ba-291">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="8b3ba-291">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8b3ba-292">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-292">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="8b3ba-293">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="8b3ba-293">*decimal value*</span></span> | <span data-ttu-id="8b3ba-294">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8b3ba-294">.NET Core 3.0</span></span> |
| <span data-ttu-id="8b3ba-295">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-295">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="8b3ba-296">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="8b3ba-296">*hexadecimal value*</span></span> | <span data-ttu-id="8b3ba-297">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8b3ba-297">.NET Core 3.0</span></span> |

<span data-ttu-id="8b3ba-298">範例：</span><span class="sxs-lookup"><span data-stu-id="8b3ba-298">Example:</span></span>

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
> <span data-ttu-id="8b3ba-299">如果要在*運行時 config.json*中設置該選項，請指定一個小數值。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-299">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="8b3ba-300">如果要將該選項設置為環境變數，請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-300">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="8b3ba-301">例如，要指定 200 個乘位元組 （MiB） 的堆硬限制，JSON 檔的值將為 209715200，環境變數的值為 0xC800000 或 C800000。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-301">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="8b3ba-302">系統.GC.HeapHard 限制百分比/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="8b3ba-302">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="8b3ba-303">將 GC 堆使用方式指定為總記憶體的百分比。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-303">Specifies the GC heap usage as a percentage of the total memory.</span></span>

| | <span data-ttu-id="8b3ba-304">設定名稱</span><span class="sxs-lookup"><span data-stu-id="8b3ba-304">Setting name</span></span> | <span data-ttu-id="8b3ba-305">值</span><span class="sxs-lookup"><span data-stu-id="8b3ba-305">Values</span></span> | <span data-ttu-id="8b3ba-306">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="8b3ba-306">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8b3ba-307">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-307">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="8b3ba-308">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="8b3ba-308">*decimal value*</span></span> | <span data-ttu-id="8b3ba-309">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8b3ba-309">.NET Core 3.0</span></span> |
| <span data-ttu-id="8b3ba-310">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-310">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="8b3ba-311">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="8b3ba-311">*hexadecimal value*</span></span> | <span data-ttu-id="8b3ba-312">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8b3ba-312">.NET Core 3.0</span></span> |

<span data-ttu-id="8b3ba-313">範例：</span><span class="sxs-lookup"><span data-stu-id="8b3ba-313">Example:</span></span>

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
> <span data-ttu-id="8b3ba-314">如果要在*運行時 config.json*中設置該選項，請指定一個小數值。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-314">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="8b3ba-315">如果要將該選項設置為環境變數，請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-315">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="8b3ba-316">例如，要將堆用法限制為 30%，JSON 檔的值為 30，環境變數的值為 0x1E 或 1E。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-316">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="8b3ba-317">系統.GC.保留VM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="8b3ba-317">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="8b3ba-318">配置應刪除的段是放在備用清單中以備將來使用，還是釋放回作業系統 （OS）。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-318">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="8b3ba-319">預設值：釋放段回作業系統 （）。`false`</span><span class="sxs-lookup"><span data-stu-id="8b3ba-319">Default: Release segments back to the operating system (`false`).</span></span>

| | <span data-ttu-id="8b3ba-320">設定名稱</span><span class="sxs-lookup"><span data-stu-id="8b3ba-320">Setting name</span></span> | <span data-ttu-id="8b3ba-321">值</span><span class="sxs-lookup"><span data-stu-id="8b3ba-321">Values</span></span> | <span data-ttu-id="8b3ba-322">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="8b3ba-322">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8b3ba-323">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-323">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="8b3ba-324">`false`- 向作業系統發佈</span><span class="sxs-lookup"><span data-stu-id="8b3ba-324">`false` - release to OS</span></span><br/><span data-ttu-id="8b3ba-325">`true`- 置於待機狀態</span><span class="sxs-lookup"><span data-stu-id="8b3ba-325">`true` - put on standby</span></span> | <span data-ttu-id="8b3ba-326">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="8b3ba-326">.NET Core 1.0</span></span> |
| <span data-ttu-id="8b3ba-327">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-327">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="8b3ba-328">`false`- 向作業系統發佈</span><span class="sxs-lookup"><span data-stu-id="8b3ba-328">`false` - release to OS</span></span><br/><span data-ttu-id="8b3ba-329">`true`- 置於待機狀態</span><span class="sxs-lookup"><span data-stu-id="8b3ba-329">`true` - put on standby</span></span> | <span data-ttu-id="8b3ba-330">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="8b3ba-330">.NET Core 1.0</span></span> |
| <span data-ttu-id="8b3ba-331">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-331">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="8b3ba-332">`0`- 向作業系統發佈</span><span class="sxs-lookup"><span data-stu-id="8b3ba-332">`0` - release to OS</span></span><br/><span data-ttu-id="8b3ba-333">`1`- 置於待機狀態</span><span class="sxs-lookup"><span data-stu-id="8b3ba-333">`1` - put on standby</span></span> | <span data-ttu-id="8b3ba-334">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="8b3ba-334">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="8b3ba-335">範例</span><span class="sxs-lookup"><span data-stu-id="8b3ba-335">Examples</span></span>

<span data-ttu-id="8b3ba-336">*運行時配置.json*檔：</span><span class="sxs-lookup"><span data-stu-id="8b3ba-336">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="8b3ba-337">專案檔：</span><span class="sxs-lookup"><span data-stu-id="8b3ba-337">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="8b3ba-338">大頁</span><span class="sxs-lookup"><span data-stu-id="8b3ba-338">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="8b3ba-339">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="8b3ba-339">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="8b3ba-340">指定在設置堆硬限制時是否應使用大頁面。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-340">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="8b3ba-341">預設值： 已`0`禁用 （ 。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-341">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="8b3ba-342">這是一個實驗設置。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-342">This is an experimental setting.</span></span>

| | <span data-ttu-id="8b3ba-343">設定名稱</span><span class="sxs-lookup"><span data-stu-id="8b3ba-343">Setting name</span></span> | <span data-ttu-id="8b3ba-344">值</span><span class="sxs-lookup"><span data-stu-id="8b3ba-344">Values</span></span> | <span data-ttu-id="8b3ba-345">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="8b3ba-345">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8b3ba-346">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-346">**runtimeconfig.json**</span></span> | <span data-ttu-id="8b3ba-347">N/A</span><span class="sxs-lookup"><span data-stu-id="8b3ba-347">N/A</span></span> | <span data-ttu-id="8b3ba-348">N/A</span><span class="sxs-lookup"><span data-stu-id="8b3ba-348">N/A</span></span> | <span data-ttu-id="8b3ba-349">N/A</span><span class="sxs-lookup"><span data-stu-id="8b3ba-349">N/A</span></span> |
| <span data-ttu-id="8b3ba-350">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-350">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="8b3ba-351">`0`- 禁用</span><span class="sxs-lookup"><span data-stu-id="8b3ba-351">`0` - disabled</span></span><br/><span data-ttu-id="8b3ba-352">`1`- 已啟用</span><span class="sxs-lookup"><span data-stu-id="8b3ba-352">`1` - enabled</span></span> | <span data-ttu-id="8b3ba-353">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8b3ba-353">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="8b3ba-354">大型物件</span><span class="sxs-lookup"><span data-stu-id="8b3ba-354">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="8b3ba-355">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="8b3ba-355">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="8b3ba-356">為總大小大於 2 GB 的陣列配置 64 位平臺上的垃圾回收器支援。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-356">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="8b3ba-357">預設值： 已`1`啟用 （ 。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-357">Default: Enabled (`1`).</span></span>
- <span data-ttu-id="8b3ba-358">此選項可能會在 .NET 的未來版本中過時。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-358">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="8b3ba-359">設定名稱</span><span class="sxs-lookup"><span data-stu-id="8b3ba-359">Setting name</span></span> | <span data-ttu-id="8b3ba-360">值</span><span class="sxs-lookup"><span data-stu-id="8b3ba-360">Values</span></span> | <span data-ttu-id="8b3ba-361">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="8b3ba-361">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8b3ba-362">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-362">**runtimeconfig.json**</span></span> | <span data-ttu-id="8b3ba-363">N/A</span><span class="sxs-lookup"><span data-stu-id="8b3ba-363">N/A</span></span> | <span data-ttu-id="8b3ba-364">N/A</span><span class="sxs-lookup"><span data-stu-id="8b3ba-364">N/A</span></span> | <span data-ttu-id="8b3ba-365">N/A</span><span class="sxs-lookup"><span data-stu-id="8b3ba-365">N/A</span></span> |
| <span data-ttu-id="8b3ba-366">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-366">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="8b3ba-367">`1`- 已啟用</span><span class="sxs-lookup"><span data-stu-id="8b3ba-367">`1` - enabled</span></span><br/> <span data-ttu-id="8b3ba-368">`0`- 禁用</span><span class="sxs-lookup"><span data-stu-id="8b3ba-368">`0` - disabled</span></span> | <span data-ttu-id="8b3ba-369">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="8b3ba-369">.NET Core 1.0</span></span> |
| <span data-ttu-id="8b3ba-370">**.NET 框架的應用程式佈建**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-370">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="8b3ba-371">gcAllow非常大的物件</span><span class="sxs-lookup"><span data-stu-id="8b3ba-371">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="8b3ba-372">`1`- 已啟用</span><span class="sxs-lookup"><span data-stu-id="8b3ba-372">`1` - enabled</span></span><br/> <span data-ttu-id="8b3ba-373">`0`- 禁用</span><span class="sxs-lookup"><span data-stu-id="8b3ba-373">`0` - disabled</span></span> | <span data-ttu-id="8b3ba-374">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="8b3ba-374">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="8b3ba-375">大型物件堆閾值</span><span class="sxs-lookup"><span data-stu-id="8b3ba-375">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="8b3ba-376">系統.GC.LOH閾值/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="8b3ba-376">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="8b3ba-377">指定導致物件轉到大型物件堆 （LOH） 上的閾值大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-377">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="8b3ba-378">預設閾值為 85，000 位元組。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-378">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="8b3ba-379">指定的值必須大於預設閾值。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-379">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="8b3ba-380">設定名稱</span><span class="sxs-lookup"><span data-stu-id="8b3ba-380">Setting name</span></span> | <span data-ttu-id="8b3ba-381">值</span><span class="sxs-lookup"><span data-stu-id="8b3ba-381">Values</span></span> | <span data-ttu-id="8b3ba-382">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="8b3ba-382">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8b3ba-383">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-383">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="8b3ba-384">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="8b3ba-384">*decimal value*</span></span> | <span data-ttu-id="8b3ba-385">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="8b3ba-385">.NET Core 1.0</span></span> |
| <span data-ttu-id="8b3ba-386">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-386">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="8b3ba-387">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="8b3ba-387">*hexadecimal value*</span></span> | <span data-ttu-id="8b3ba-388">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="8b3ba-388">.NET Core 1.0</span></span> |
| <span data-ttu-id="8b3ba-389">**.NET 框架的應用程式佈建**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-389">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="8b3ba-390">GCLOH閾值</span><span class="sxs-lookup"><span data-stu-id="8b3ba-390">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="8b3ba-391">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="8b3ba-391">*decimal value*</span></span> | <span data-ttu-id="8b3ba-392">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="8b3ba-392">.NET Framework 4.8</span></span> |

<span data-ttu-id="8b3ba-393">範例：</span><span class="sxs-lookup"><span data-stu-id="8b3ba-393">Example:</span></span>

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
> <span data-ttu-id="8b3ba-394">如果要在*運行時 config.json*中設置該選項，請指定一個小數值。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-394">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="8b3ba-395">如果要將該選項設置為環境變數，請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-395">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="8b3ba-396">例如，要設置 120，000 位元組的閾值大小，JSON 檔的值將為 120000，環境變數的值為 0x1D4C0 或 1D4C0。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-396">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="8b3ba-397">獨立 GC</span><span class="sxs-lookup"><span data-stu-id="8b3ba-397">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="8b3ba-398">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="8b3ba-398">COMPlus_GCName</span></span>

- <span data-ttu-id="8b3ba-399">指定包含運行時打算載入的垃圾回收器的庫的路徑。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-399">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="8b3ba-400">有關詳細資訊，請參閱獨立[GC 載入程式設計](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md)。</span><span class="sxs-lookup"><span data-stu-id="8b3ba-400">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="8b3ba-401">設定名稱</span><span class="sxs-lookup"><span data-stu-id="8b3ba-401">Setting name</span></span> | <span data-ttu-id="8b3ba-402">值</span><span class="sxs-lookup"><span data-stu-id="8b3ba-402">Values</span></span> | <span data-ttu-id="8b3ba-403">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="8b3ba-403">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8b3ba-404">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-404">**runtimeconfig.json**</span></span> | <span data-ttu-id="8b3ba-405">N/A</span><span class="sxs-lookup"><span data-stu-id="8b3ba-405">N/A</span></span> | <span data-ttu-id="8b3ba-406">N/A</span><span class="sxs-lookup"><span data-stu-id="8b3ba-406">N/A</span></span> | <span data-ttu-id="8b3ba-407">N/A</span><span class="sxs-lookup"><span data-stu-id="8b3ba-407">N/A</span></span> |
| <span data-ttu-id="8b3ba-408">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="8b3ba-408">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="8b3ba-409">*string_path*</span><span class="sxs-lookup"><span data-stu-id="8b3ba-409">*string_path*</span></span> | <span data-ttu-id="8b3ba-410">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="8b3ba-410">.NET Core 2.0</span></span> |
