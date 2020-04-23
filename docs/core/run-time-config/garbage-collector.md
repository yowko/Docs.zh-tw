---
title: 垃圾資源配置設定
description: 瞭解用於配置垃圾回收器如何管理 .NET Core 應用記憶體的運行時設置。
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: ec575bdd17c8a7c290673b7085074bbba94cedef
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102862"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="f68af-103">垃圾資源回收的執行時設定選項</span><span class="sxs-lookup"><span data-stu-id="f68af-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="f68af-104">此頁包含有關可在運行時更改的垃圾回收器 (GC) 設置的資訊。</span><span class="sxs-lookup"><span data-stu-id="f68af-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="f68af-105">如果您嘗試實現正在運行的應用的峰值性能,請考慮使用這些設置。</span><span class="sxs-lookup"><span data-stu-id="f68af-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="f68af-106">但是,預設值為大多數應用程式在典型情況下提供了最佳性能。</span><span class="sxs-lookup"><span data-stu-id="f68af-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="f68af-107">設定在此頁上按組排列。</span><span class="sxs-lookup"><span data-stu-id="f68af-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="f68af-108">每個組中的設置通常相互結合使用,以實現特定結果。</span><span class="sxs-lookup"><span data-stu-id="f68af-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="f68af-109">這些設置也可以由應用在運行時動態更改,因此您設置的任何運行時設置都可能被覆蓋。</span><span class="sxs-lookup"><span data-stu-id="f68af-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="f68af-110">某些設置(如[延遲級別](../../standard/garbage-collection/latency.md))通常僅在設計時通過 API 設置。</span><span class="sxs-lookup"><span data-stu-id="f68af-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="f68af-111">此頁省略了此類設置。</span><span class="sxs-lookup"><span data-stu-id="f68af-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="f68af-112">對於數位值,對*運行時 config.json*檔中的設置使用十進位表示法,對環境變數設置使用十進位表示法。</span><span class="sxs-lookup"><span data-stu-id="f68af-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="f68af-113">對於十六進位值,可以使用或沒有"0x"首碼來指定它們。</span><span class="sxs-lookup"><span data-stu-id="f68af-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="f68af-114">垃圾回收的味道</span><span class="sxs-lookup"><span data-stu-id="f68af-114">Flavors of garbage collection</span></span>

<span data-ttu-id="f68af-115">垃圾回收的兩個主要類型是工作站 GC 和伺服器 GC。</span><span class="sxs-lookup"><span data-stu-id="f68af-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="f68af-116">有關兩者之間的差異的詳細資訊,請參閱[工作站和伺服器垃圾回收](../../standard/garbage-collection/workstation-server-gc.md)。</span><span class="sxs-lookup"><span data-stu-id="f68af-116">For more information about differences between the two, see [Workstation and server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span>

<span data-ttu-id="f68af-117">垃圾回收的子口味是背景和非併發的。</span><span class="sxs-lookup"><span data-stu-id="f68af-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="f68af-118">使用以下設定選擇垃圾回收的味道:</span><span class="sxs-lookup"><span data-stu-id="f68af-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="f68af-119">系統.GC.伺服器/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="f68af-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="f68af-120">配置應用程式是使用工作站垃圾回收還是伺服器垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="f68af-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="f68af-121">默認值:工作站垃圾回收 ()。`false`</span><span class="sxs-lookup"><span data-stu-id="f68af-121">Default: Workstation garbage collection (`false`).</span></span>

| | <span data-ttu-id="f68af-122">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f68af-122">Setting name</span></span> | <span data-ttu-id="f68af-123">值</span><span class="sxs-lookup"><span data-stu-id="f68af-123">Values</span></span> | <span data-ttu-id="f68af-124">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="f68af-124">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f68af-125">**執行時設定.json**</span><span class="sxs-lookup"><span data-stu-id="f68af-125">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="f68af-126">`false`- 工作站</span><span class="sxs-lookup"><span data-stu-id="f68af-126">`false` - workstation</span></span><br/><span data-ttu-id="f68af-127">`true`- 伺服器</span><span class="sxs-lookup"><span data-stu-id="f68af-127">`true` - server</span></span> | <span data-ttu-id="f68af-128">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f68af-128">.NET Core 1.0</span></span> |
| <span data-ttu-id="f68af-129">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="f68af-129">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="f68af-130">`false`- 工作站</span><span class="sxs-lookup"><span data-stu-id="f68af-130">`false` - workstation</span></span><br/><span data-ttu-id="f68af-131">`true`- 伺服器</span><span class="sxs-lookup"><span data-stu-id="f68af-131">`true` - server</span></span> | <span data-ttu-id="f68af-132">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f68af-132">.NET Core 1.0</span></span> |
| <span data-ttu-id="f68af-133">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f68af-133">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="f68af-134">`0`- 工作站</span><span class="sxs-lookup"><span data-stu-id="f68af-134">`0` - workstation</span></span><br/><span data-ttu-id="f68af-135">`1`- 伺服器</span><span class="sxs-lookup"><span data-stu-id="f68af-135">`1` - server</span></span> | <span data-ttu-id="f68af-136">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f68af-136">.NET Core 1.0</span></span> |
| <span data-ttu-id="f68af-137">**.NET 框架的應用程式設定**</span><span class="sxs-lookup"><span data-stu-id="f68af-137">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f68af-138">GCServer</span><span class="sxs-lookup"><span data-stu-id="f68af-138">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="f68af-139">`false`- 工作站</span><span class="sxs-lookup"><span data-stu-id="f68af-139">`false` - workstation</span></span><br/><span data-ttu-id="f68af-140">`true`- 伺服器</span><span class="sxs-lookup"><span data-stu-id="f68af-140">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="f68af-141">範例</span><span class="sxs-lookup"><span data-stu-id="f68af-141">Examples</span></span>

<span data-ttu-id="f68af-142">*執行時設定.json*檔:</span><span class="sxs-lookup"><span data-stu-id="f68af-142">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="f68af-143">專案檔：</span><span class="sxs-lookup"><span data-stu-id="f68af-143">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="f68af-144">系統.GC.併發/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="f68af-144">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="f68af-145">配置是否啟用後台(併發)垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="f68af-145">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="f68af-146">預設值:`true`已開啟 ( 。</span><span class="sxs-lookup"><span data-stu-id="f68af-146">Default: Enabled (`true`).</span></span>
- <span data-ttu-id="f68af-147">有關詳細資訊,請參閱[後臺垃圾回收](../../standard/garbage-collection/background-gc.md)。</span><span class="sxs-lookup"><span data-stu-id="f68af-147">For more information, see [Background garbage collection](../../standard/garbage-collection/background-gc.md).</span></span>

| | <span data-ttu-id="f68af-148">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f68af-148">Setting name</span></span> | <span data-ttu-id="f68af-149">值</span><span class="sxs-lookup"><span data-stu-id="f68af-149">Values</span></span> | <span data-ttu-id="f68af-150">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="f68af-150">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f68af-151">**執行時設定.json**</span><span class="sxs-lookup"><span data-stu-id="f68af-151">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="f68af-152">`true`- 背景 GC</span><span class="sxs-lookup"><span data-stu-id="f68af-152">`true` - background GC</span></span><br/><span data-ttu-id="f68af-153">`false`- 非併發 GC</span><span class="sxs-lookup"><span data-stu-id="f68af-153">`false` - non-concurrent GC</span></span> | <span data-ttu-id="f68af-154">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f68af-154">.NET Core 1.0</span></span> |
| <span data-ttu-id="f68af-155">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="f68af-155">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="f68af-156">`true`- 背景 GC</span><span class="sxs-lookup"><span data-stu-id="f68af-156">`true` - background GC</span></span><br/><span data-ttu-id="f68af-157">`false`- 非併發 GC</span><span class="sxs-lookup"><span data-stu-id="f68af-157">`false` - non-concurrent GC</span></span> | <span data-ttu-id="f68af-158">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f68af-158">.NET Core 1.0</span></span> |
| <span data-ttu-id="f68af-159">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f68af-159">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="f68af-160">`true`- 背景 GC</span><span class="sxs-lookup"><span data-stu-id="f68af-160">`true` - background GC</span></span><br/><span data-ttu-id="f68af-161">`false`- 非併發 GC</span><span class="sxs-lookup"><span data-stu-id="f68af-161">`false` - non-concurrent GC</span></span> | <span data-ttu-id="f68af-162">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f68af-162">.NET Core 1.0</span></span> |
| <span data-ttu-id="f68af-163">**.NET 框架的應用程式設定**</span><span class="sxs-lookup"><span data-stu-id="f68af-163">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f68af-164">gc 併發</span><span class="sxs-lookup"><span data-stu-id="f68af-164">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="f68af-165">`true`- 背景 GC</span><span class="sxs-lookup"><span data-stu-id="f68af-165">`true` - background GC</span></span><br/><span data-ttu-id="f68af-166">`false`- 非併發 GC</span><span class="sxs-lookup"><span data-stu-id="f68af-166">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="f68af-167">範例</span><span class="sxs-lookup"><span data-stu-id="f68af-167">Examples</span></span>

<span data-ttu-id="f68af-168">*執行時設定.json*檔:</span><span class="sxs-lookup"><span data-stu-id="f68af-168">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="f68af-169">專案檔：</span><span class="sxs-lookup"><span data-stu-id="f68af-169">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="f68af-170">管理資源使用方式</span><span class="sxs-lookup"><span data-stu-id="f68af-170">Manage resource usage</span></span>

<span data-ttu-id="f68af-171">使用本節中描述的設置來管理垃圾回收器的記憶體和處理器使用方式。</span><span class="sxs-lookup"><span data-stu-id="f68af-171">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="f68af-172">有關其中一些設定的詳細資訊,請參閱[工作站和伺服器 GC 部落格項目之間的中間地帶](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/)。</span><span class="sxs-lookup"><span data-stu-id="f68af-172">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="f68af-173">系統.GC.堆計數/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="f68af-173">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="f68af-174">限制垃圾回收器創建的堆數。</span><span class="sxs-lookup"><span data-stu-id="f68af-174">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="f68af-175">僅適用於伺服器垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="f68af-175">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="f68af-176">如果[啟用了 GC 處理器關聯](#systemgcnoaffinitizecomplus_gcnoaffinitize)(這是預設值,則堆`n`計數設置將 GC 堆/ 線`n`程關聯化為第一個 處理器)。</span><span class="sxs-lookup"><span data-stu-id="f68af-176">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="f68af-177">(使用[關聯掩碼](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask)或[關聯範圍](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges)設置來準確指定要關聯處理器的處理器。</span><span class="sxs-lookup"><span data-stu-id="f68af-177">(Use the [affinitize mask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) or [affinitize ranges](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="f68af-178">如果[禁用 GC 處理器關聯](#systemgcnoaffinitizecomplus_gcnoaffinitize),此設置將限制 GC 堆的數量。</span><span class="sxs-lookup"><span data-stu-id="f68af-178">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="f68af-179">有關詳細資訊,請參閱[GCHeapCount 註釋](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks)。</span><span class="sxs-lookup"><span data-stu-id="f68af-179">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="f68af-180">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f68af-180">Setting name</span></span> | <span data-ttu-id="f68af-181">值</span><span class="sxs-lookup"><span data-stu-id="f68af-181">Values</span></span> | <span data-ttu-id="f68af-182">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="f68af-182">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f68af-183">**執行時設定.json**</span><span class="sxs-lookup"><span data-stu-id="f68af-183">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="f68af-184">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="f68af-184">*decimal value*</span></span> | <span data-ttu-id="f68af-185">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f68af-185">.NET Core 3.0</span></span> |
| <span data-ttu-id="f68af-186">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f68af-186">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="f68af-187">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="f68af-187">*hexadecimal value*</span></span> | <span data-ttu-id="f68af-188">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f68af-188">.NET Core 3.0</span></span> |
| <span data-ttu-id="f68af-189">**.NET 框架的應用程式設定**</span><span class="sxs-lookup"><span data-stu-id="f68af-189">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f68af-190">GCHeap( Gc) Count</span><span class="sxs-lookup"><span data-stu-id="f68af-190">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="f68af-191">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="f68af-191">*decimal value*</span></span> | <span data-ttu-id="f68af-192">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="f68af-192">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="f68af-193">範例：</span><span class="sxs-lookup"><span data-stu-id="f68af-193">Example:</span></span>

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
> <span data-ttu-id="f68af-194">如果要在*運行時 config.json*中設置該選項,請指定一個小數值。</span><span class="sxs-lookup"><span data-stu-id="f68af-194">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="f68af-195">如果要將該選項設置為環境變數,請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="f68af-195">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="f68af-196">例如,要將堆數限制為 16,JSON 檔的值將為 16,環境變數的值為 0x10 或 10。</span><span class="sxs-lookup"><span data-stu-id="f68af-196">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="f68af-197">系統.GC.Heapaffinitize 掩碼/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="f68af-197">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="f68af-198">指定垃圾回收器線程應使用的確切處理器。</span><span class="sxs-lookup"><span data-stu-id="f68af-198">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="f68af-199">如果[禁用 GC 處理器關聯](#systemgcnoaffinitizecomplus_gcnoaffinitize),則忽略此設置。</span><span class="sxs-lookup"><span data-stu-id="f68af-199">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="f68af-200">僅適用於伺服器垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="f68af-200">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="f68af-201">該值是定義進程可用的處理器的位掩碼。</span><span class="sxs-lookup"><span data-stu-id="f68af-201">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="f68af-202">例如,十進位值 1023(或十六進位值 0x3FF或 3FF,如果您正在使用環境變數)是 0011 1111 1111 在二進位表示法中。</span><span class="sxs-lookup"><span data-stu-id="f68af-202">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="f68af-203">這指定將使用前 10 個處理器。</span><span class="sxs-lookup"><span data-stu-id="f68af-203">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="f68af-204">要指定接下來的 10 個處理器,即處理器 10-19,請指定 1047552(或十六進位值 0xFFC00 或 FFC00),這相當於二進位值 1111 1111 1100 00000000000。</span><span class="sxs-lookup"><span data-stu-id="f68af-204">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="f68af-205">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f68af-205">Setting name</span></span> | <span data-ttu-id="f68af-206">值</span><span class="sxs-lookup"><span data-stu-id="f68af-206">Values</span></span> | <span data-ttu-id="f68af-207">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="f68af-207">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f68af-208">**執行時設定.json**</span><span class="sxs-lookup"><span data-stu-id="f68af-208">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="f68af-209">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="f68af-209">*decimal value*</span></span> | <span data-ttu-id="f68af-210">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f68af-210">.NET Core 3.0</span></span> |
| <span data-ttu-id="f68af-211">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f68af-211">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="f68af-212">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="f68af-212">*hexadecimal value*</span></span> | <span data-ttu-id="f68af-213">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f68af-213">.NET Core 3.0</span></span> |
| <span data-ttu-id="f68af-214">**.NET 框架的應用程式設定**</span><span class="sxs-lookup"><span data-stu-id="f68af-214">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f68af-215">GCHeapaffinitize 遮罩</span><span class="sxs-lookup"><span data-stu-id="f68af-215">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="f68af-216">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="f68af-216">*decimal value*</span></span> | <span data-ttu-id="f68af-217">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="f68af-217">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="f68af-218">範例：</span><span class="sxs-lookup"><span data-stu-id="f68af-218">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="f68af-219">系統.GC.GCHeapaffinitize 範圍/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="f68af-219">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="f68af-220">指定用於垃圾回收器線程的處理器清單。</span><span class="sxs-lookup"><span data-stu-id="f68af-220">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="f68af-221">此設定類似於[System.GC.Heapaffinitize Mask,](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask)只不過它允許您指定超過 64 個處理器。</span><span class="sxs-lookup"><span data-stu-id="f68af-221">This setting is similar to [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="f68af-222">對於 Windows 作業系統,使用相應的[CPU 組](/windows/win32/procthread/processor-groups)對處理器編號或範圍進行前綴,例如,「0:1-10,0:12,1:50-52,1:70」。。</span><span class="sxs-lookup"><span data-stu-id="f68af-222">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="f68af-223">如果[禁用 GC 處理器關聯](#systemgcnoaffinitizecomplus_gcnoaffinitize),則忽略此設置。</span><span class="sxs-lookup"><span data-stu-id="f68af-223">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="f68af-224">僅適用於伺服器垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="f68af-224">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="f68af-225">有關詳細資訊,請參閱在 Maoni Stephens 部落格上[具有 > 64 個 CPU 的電腦上為 GC 提供更好的 CPU 配置](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/)。</span><span class="sxs-lookup"><span data-stu-id="f68af-225">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="f68af-226">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f68af-226">Setting name</span></span> | <span data-ttu-id="f68af-227">值</span><span class="sxs-lookup"><span data-stu-id="f68af-227">Values</span></span> | <span data-ttu-id="f68af-228">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="f68af-228">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f68af-229">**執行時設定.json**</span><span class="sxs-lookup"><span data-stu-id="f68af-229">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="f68af-230">處理器編號或處理器編號範圍的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="f68af-230">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="f68af-231">Unix 示例:"1-10,12,50-52,70"</span><span class="sxs-lookup"><span data-stu-id="f68af-231">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="f68af-232">視窗示例:"0:1-10,0:12,1:50-52,1:70"</span><span class="sxs-lookup"><span data-stu-id="f68af-232">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="f68af-233">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f68af-233">.NET Core 3.0</span></span> |
| <span data-ttu-id="f68af-234">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f68af-234">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="f68af-235">處理器編號或處理器編號範圍的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="f68af-235">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="f68af-236">Unix 示例:"1-10,12,50-52,70"</span><span class="sxs-lookup"><span data-stu-id="f68af-236">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="f68af-237">視窗示例:"0:1-10,0:12,1:50-52,1:70"</span><span class="sxs-lookup"><span data-stu-id="f68af-237">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="f68af-238">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f68af-238">.NET Core 3.0</span></span> |

<span data-ttu-id="f68af-239">範例：</span><span class="sxs-lookup"><span data-stu-id="f68af-239">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="f68af-240">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="f68af-240">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="f68af-241">設定垃圾資源回收器是否使用[CPU 群組](/windows/win32/procthread/processor-groups)。</span><span class="sxs-lookup"><span data-stu-id="f68af-241">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="f68af-242">當 64 位 Windows 電腦具有多個 CPU 組(即,超過 64 個處理器)時,啟用此元素會跨所有 CPU 組擴展垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="f68af-242">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="f68af-243">垃圾回收器使用所有內核創建和平衡堆。</span><span class="sxs-lookup"><span data-stu-id="f68af-243">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="f68af-244">僅適用於 64 位 Windows 作業系統上的伺服器垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="f68af-244">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="f68af-245">預設值:`0`已關閉 ( 。</span><span class="sxs-lookup"><span data-stu-id="f68af-245">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="f68af-246">有關詳細資訊,請參閱在 Maoni Stephens 部落格上[具有 > 64 個 CPU 的電腦上為 GC 提供更好的 CPU 配置](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/)。</span><span class="sxs-lookup"><span data-stu-id="f68af-246">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="f68af-247">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f68af-247">Setting name</span></span> | <span data-ttu-id="f68af-248">值</span><span class="sxs-lookup"><span data-stu-id="f68af-248">Values</span></span> | <span data-ttu-id="f68af-249">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="f68af-249">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f68af-250">**執行時設定.json**</span><span class="sxs-lookup"><span data-stu-id="f68af-250">**runtimeconfig.json**</span></span> | <span data-ttu-id="f68af-251">N/A</span><span class="sxs-lookup"><span data-stu-id="f68af-251">N/A</span></span> | <span data-ttu-id="f68af-252">N/A</span><span class="sxs-lookup"><span data-stu-id="f68af-252">N/A</span></span> | <span data-ttu-id="f68af-253">N/A</span><span class="sxs-lookup"><span data-stu-id="f68af-253">N/A</span></span> |
| <span data-ttu-id="f68af-254">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f68af-254">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="f68af-255">`0`- 停用</span><span class="sxs-lookup"><span data-stu-id="f68af-255">`0` - disabled</span></span><br/><span data-ttu-id="f68af-256">`1`- 已開啟</span><span class="sxs-lookup"><span data-stu-id="f68af-256">`1` - enabled</span></span> | <span data-ttu-id="f68af-257">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f68af-257">.NET Core 1.0</span></span> |
| <span data-ttu-id="f68af-258">**.NET 框架的應用程式設定**</span><span class="sxs-lookup"><span data-stu-id="f68af-258">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f68af-259">GCCpu集團</span><span class="sxs-lookup"><span data-stu-id="f68af-259">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="f68af-260">`false`- 停用</span><span class="sxs-lookup"><span data-stu-id="f68af-260">`false` - disabled</span></span><br/><span data-ttu-id="f68af-261">`true`- 已開啟</span><span class="sxs-lookup"><span data-stu-id="f68af-261">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="f68af-262">要將通用語言執行時 (CLR) 設定為將線程池中的線程分配到所有 CPU 組,請啟用[Thread_UseAllCpuGroups元素](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)選項。</span><span class="sxs-lookup"><span data-stu-id="f68af-262">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="f68af-263">對於 .NET Core 應用`COMPlus_Thread_UseAllCpuGroups`,可以通過將 環境變數`1`的值設置為 來啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="f68af-263">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="f68af-264">系統.GC.無資訊化/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="f68af-264">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="f68af-265">指定是否將垃圾回收線程與處理器*關聯*化。</span><span class="sxs-lookup"><span data-stu-id="f68af-265">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="f68af-266">關聯 GC 線程意味著它只能在其特定 CPU 上運行。</span><span class="sxs-lookup"><span data-stu-id="f68af-266">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="f68af-267">為每個 GC 執行緒創建一個堆。</span><span class="sxs-lookup"><span data-stu-id="f68af-267">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="f68af-268">僅適用於伺服器垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="f68af-268">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="f68af-269">默認值:使用處理器 () 對垃圾回收`false`線程 進行 affinitit 化。</span><span class="sxs-lookup"><span data-stu-id="f68af-269">Default: Affinitize garbage collection threads with processors (`false`).</span></span>

| | <span data-ttu-id="f68af-270">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f68af-270">Setting name</span></span> | <span data-ttu-id="f68af-271">值</span><span class="sxs-lookup"><span data-stu-id="f68af-271">Values</span></span> | <span data-ttu-id="f68af-272">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="f68af-272">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f68af-273">**執行時設定.json**</span><span class="sxs-lookup"><span data-stu-id="f68af-273">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="f68af-274">`false`- 親緣關係</span><span class="sxs-lookup"><span data-stu-id="f68af-274">`false` - affinitize</span></span><br/><span data-ttu-id="f68af-275">`true`-不要親和</span><span class="sxs-lookup"><span data-stu-id="f68af-275">`true` - don't affinitize</span></span> | <span data-ttu-id="f68af-276">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f68af-276">.NET Core 3.0</span></span> |
| <span data-ttu-id="f68af-277">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f68af-277">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="f68af-278">`0`- 親緣關係</span><span class="sxs-lookup"><span data-stu-id="f68af-278">`0` - affinitize</span></span><br/><span data-ttu-id="f68af-279">`1`-不要親和</span><span class="sxs-lookup"><span data-stu-id="f68af-279">`1` - don't affinitize</span></span> | <span data-ttu-id="f68af-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f68af-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="f68af-281">**.NET 框架的應用程式設定**</span><span class="sxs-lookup"><span data-stu-id="f68af-281">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f68af-282">GCNoaffinitize</span><span class="sxs-lookup"><span data-stu-id="f68af-282">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="f68af-283">`false`- 親緣關係</span><span class="sxs-lookup"><span data-stu-id="f68af-283">`false` - affinitize</span></span><br/><span data-ttu-id="f68af-284">`true`-不要親和</span><span class="sxs-lookup"><span data-stu-id="f68af-284">`true` - don't affinitize</span></span> | <span data-ttu-id="f68af-285">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="f68af-285">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="f68af-286">範例：</span><span class="sxs-lookup"><span data-stu-id="f68af-286">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="f68af-287">系統.GC.HeapHard 限制/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="f68af-287">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="f68af-288">為 GC 堆和 GC 簿記指定最大提交大小(以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="f68af-288">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>
- <span data-ttu-id="f68af-289">此設定僅適用於 64 位元電腦。</span><span class="sxs-lookup"><span data-stu-id="f68af-289">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="f68af-290">默認值僅在某些情況下適用,是容器上記憶體限制的 20 MB 或 75%。</span><span class="sxs-lookup"><span data-stu-id="f68af-290">The default value, which only applies in certain cases, is the greater of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="f68af-291">預設值適用於:</span><span class="sxs-lookup"><span data-stu-id="f68af-291">The default value applies if:</span></span>

  - <span data-ttu-id="f68af-292">進程在具有指定記憶體限制的容器內運行。</span><span class="sxs-lookup"><span data-stu-id="f68af-292">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="f68af-293">[系統.GC.HeapHard 限制百分比](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent)未設置。</span><span class="sxs-lookup"><span data-stu-id="f68af-293">[System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) is not set.</span></span>

| | <span data-ttu-id="f68af-294">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f68af-294">Setting name</span></span> | <span data-ttu-id="f68af-295">值</span><span class="sxs-lookup"><span data-stu-id="f68af-295">Values</span></span> | <span data-ttu-id="f68af-296">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="f68af-296">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f68af-297">**執行時設定.json**</span><span class="sxs-lookup"><span data-stu-id="f68af-297">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="f68af-298">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="f68af-298">*decimal value*</span></span> | <span data-ttu-id="f68af-299">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f68af-299">.NET Core 3.0</span></span> |
| <span data-ttu-id="f68af-300">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f68af-300">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="f68af-301">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="f68af-301">*hexadecimal value*</span></span> | <span data-ttu-id="f68af-302">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f68af-302">.NET Core 3.0</span></span> |

<span data-ttu-id="f68af-303">範例：</span><span class="sxs-lookup"><span data-stu-id="f68af-303">Example:</span></span>

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
> <span data-ttu-id="f68af-304">如果要在*運行時 config.json*中設置該選項,請指定一個小數值。</span><span class="sxs-lookup"><span data-stu-id="f68af-304">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="f68af-305">如果要將該選項設置為環境變數,請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="f68af-305">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="f68af-306">例如,要指定 200 個乘位元組 (MiB) 的堆硬限制,JSON 檔的值將為 209715200,環境變數的值為 0xC800000 或 C800000。</span><span class="sxs-lookup"><span data-stu-id="f68af-306">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="f68af-307">系統.GC.HeapHard 限制百分比/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="f68af-307">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="f68af-308">指定允許的 GC 堆使用方式,作為總物理記憶體的百分比。</span><span class="sxs-lookup"><span data-stu-id="f68af-308">Specifies the allowable GC heap usage as a percentage of the total physical memory.</span></span>
- <span data-ttu-id="f68af-309">如果還設置了[System.GC.HeapHardLimit,](#systemgcheaphardlimitcomplus_gcheaphardlimit)則忽略此設置。</span><span class="sxs-lookup"><span data-stu-id="f68af-309">If [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is also set, this setting is ignored.</span></span>
- <span data-ttu-id="f68af-310">此設定僅適用於 64 位元電腦。</span><span class="sxs-lookup"><span data-stu-id="f68af-310">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="f68af-311">如果進程在具有指定記憶體限制的容器內運行,則百分比將計算為該記憶體限制的百分比。</span><span class="sxs-lookup"><span data-stu-id="f68af-311">If the process is running inside a container that has a specified memory limit, the percentage is calculated as a percentage of that memory limit.</span></span>
- <span data-ttu-id="f68af-312">默認值僅在某些情況下適用,是容器記憶體限制的 20 MB 或 75% 的較小值。</span><span class="sxs-lookup"><span data-stu-id="f68af-312">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="f68af-313">預設值適用於:</span><span class="sxs-lookup"><span data-stu-id="f68af-313">The default value applies if:</span></span>

  - <span data-ttu-id="f68af-314">進程在具有指定記憶體限制的容器內運行。</span><span class="sxs-lookup"><span data-stu-id="f68af-314">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="f68af-315">[系統.GC.HeapHard 限制](#systemgcheaphardlimitcomplus_gcheaphardlimit)未設置。</span><span class="sxs-lookup"><span data-stu-id="f68af-315">[System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is not set.</span></span>

| | <span data-ttu-id="f68af-316">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f68af-316">Setting name</span></span> | <span data-ttu-id="f68af-317">值</span><span class="sxs-lookup"><span data-stu-id="f68af-317">Values</span></span> | <span data-ttu-id="f68af-318">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="f68af-318">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f68af-319">**執行時設定.json**</span><span class="sxs-lookup"><span data-stu-id="f68af-319">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="f68af-320">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="f68af-320">*decimal value*</span></span> | <span data-ttu-id="f68af-321">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f68af-321">.NET Core 3.0</span></span> |
| <span data-ttu-id="f68af-322">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f68af-322">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="f68af-323">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="f68af-323">*hexadecimal value*</span></span> | <span data-ttu-id="f68af-324">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f68af-324">.NET Core 3.0</span></span> |

<span data-ttu-id="f68af-325">範例：</span><span class="sxs-lookup"><span data-stu-id="f68af-325">Example:</span></span>

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
> <span data-ttu-id="f68af-326">如果要在*運行時 config.json*中設置該選項,請指定一個小數值。</span><span class="sxs-lookup"><span data-stu-id="f68af-326">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="f68af-327">如果要將該選項設置為環境變數,請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="f68af-327">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="f68af-328">例如,要將堆用法限制為 30%,JSON 檔的值為 30,環境變數的值為 0x1E 或 1E。</span><span class="sxs-lookup"><span data-stu-id="f68af-328">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="f68af-329">系統.GC.保留VM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="f68af-329">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="f68af-330">配置應刪除的段是放在備用清單中以備將來使用,還是釋放回作業系統 (OS)。</span><span class="sxs-lookup"><span data-stu-id="f68af-330">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="f68af-331">默認值:釋放段回作業系統 ()。`false`</span><span class="sxs-lookup"><span data-stu-id="f68af-331">Default: Release segments back to the operating system (`false`).</span></span>

| | <span data-ttu-id="f68af-332">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f68af-332">Setting name</span></span> | <span data-ttu-id="f68af-333">值</span><span class="sxs-lookup"><span data-stu-id="f68af-333">Values</span></span> | <span data-ttu-id="f68af-334">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="f68af-334">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f68af-335">**執行時設定.json**</span><span class="sxs-lookup"><span data-stu-id="f68af-335">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="f68af-336">`false`- 向作業系統發佈</span><span class="sxs-lookup"><span data-stu-id="f68af-336">`false` - release to OS</span></span><br/><span data-ttu-id="f68af-337">`true`- 置於待機狀態</span><span class="sxs-lookup"><span data-stu-id="f68af-337">`true` - put on standby</span></span> | <span data-ttu-id="f68af-338">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f68af-338">.NET Core 1.0</span></span> |
| <span data-ttu-id="f68af-339">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="f68af-339">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="f68af-340">`false`- 向作業系統發佈</span><span class="sxs-lookup"><span data-stu-id="f68af-340">`false` - release to OS</span></span><br/><span data-ttu-id="f68af-341">`true`- 置於待機狀態</span><span class="sxs-lookup"><span data-stu-id="f68af-341">`true` - put on standby</span></span> | <span data-ttu-id="f68af-342">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f68af-342">.NET Core 1.0</span></span> |
| <span data-ttu-id="f68af-343">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f68af-343">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="f68af-344">`0`- 向作業系統發佈</span><span class="sxs-lookup"><span data-stu-id="f68af-344">`0` - release to OS</span></span><br/><span data-ttu-id="f68af-345">`1`- 置於待機狀態</span><span class="sxs-lookup"><span data-stu-id="f68af-345">`1` - put on standby</span></span> | <span data-ttu-id="f68af-346">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f68af-346">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="f68af-347">範例</span><span class="sxs-lookup"><span data-stu-id="f68af-347">Examples</span></span>

<span data-ttu-id="f68af-348">*執行時設定.json*檔:</span><span class="sxs-lookup"><span data-stu-id="f68af-348">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="f68af-349">專案檔：</span><span class="sxs-lookup"><span data-stu-id="f68af-349">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="f68af-350">大頁</span><span class="sxs-lookup"><span data-stu-id="f68af-350">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="f68af-351">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="f68af-351">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="f68af-352">指定在設置堆硬限制時是否應使用大頁面。</span><span class="sxs-lookup"><span data-stu-id="f68af-352">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="f68af-353">預設值:`0`已關閉 ( 。</span><span class="sxs-lookup"><span data-stu-id="f68af-353">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="f68af-354">這是一個實驗設置。</span><span class="sxs-lookup"><span data-stu-id="f68af-354">This is an experimental setting.</span></span>

| | <span data-ttu-id="f68af-355">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f68af-355">Setting name</span></span> | <span data-ttu-id="f68af-356">值</span><span class="sxs-lookup"><span data-stu-id="f68af-356">Values</span></span> | <span data-ttu-id="f68af-357">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="f68af-357">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f68af-358">**執行時設定.json**</span><span class="sxs-lookup"><span data-stu-id="f68af-358">**runtimeconfig.json**</span></span> | <span data-ttu-id="f68af-359">N/A</span><span class="sxs-lookup"><span data-stu-id="f68af-359">N/A</span></span> | <span data-ttu-id="f68af-360">N/A</span><span class="sxs-lookup"><span data-stu-id="f68af-360">N/A</span></span> | <span data-ttu-id="f68af-361">N/A</span><span class="sxs-lookup"><span data-stu-id="f68af-361">N/A</span></span> |
| <span data-ttu-id="f68af-362">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f68af-362">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="f68af-363">`0`- 停用</span><span class="sxs-lookup"><span data-stu-id="f68af-363">`0` - disabled</span></span><br/><span data-ttu-id="f68af-364">`1`- 已開啟</span><span class="sxs-lookup"><span data-stu-id="f68af-364">`1` - enabled</span></span> | <span data-ttu-id="f68af-365">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f68af-365">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="f68af-366">大型物件</span><span class="sxs-lookup"><span data-stu-id="f68af-366">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="f68af-367">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="f68af-367">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="f68af-368">為總大小大於 2 GB 的陣列配置 64 位元平臺上的垃圾回收器支援。</span><span class="sxs-lookup"><span data-stu-id="f68af-368">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="f68af-369">預設值:`1`已開啟 ( 。</span><span class="sxs-lookup"><span data-stu-id="f68af-369">Default: Enabled (`1`).</span></span>
- <span data-ttu-id="f68af-370">此選項可能會在 .NET 的未來版本中過時。</span><span class="sxs-lookup"><span data-stu-id="f68af-370">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="f68af-371">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f68af-371">Setting name</span></span> | <span data-ttu-id="f68af-372">值</span><span class="sxs-lookup"><span data-stu-id="f68af-372">Values</span></span> | <span data-ttu-id="f68af-373">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="f68af-373">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f68af-374">**執行時設定.json**</span><span class="sxs-lookup"><span data-stu-id="f68af-374">**runtimeconfig.json**</span></span> | <span data-ttu-id="f68af-375">N/A</span><span class="sxs-lookup"><span data-stu-id="f68af-375">N/A</span></span> | <span data-ttu-id="f68af-376">N/A</span><span class="sxs-lookup"><span data-stu-id="f68af-376">N/A</span></span> | <span data-ttu-id="f68af-377">N/A</span><span class="sxs-lookup"><span data-stu-id="f68af-377">N/A</span></span> |
| <span data-ttu-id="f68af-378">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f68af-378">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="f68af-379">`1`- 已開啟</span><span class="sxs-lookup"><span data-stu-id="f68af-379">`1` - enabled</span></span><br/> <span data-ttu-id="f68af-380">`0`- 停用</span><span class="sxs-lookup"><span data-stu-id="f68af-380">`0` - disabled</span></span> | <span data-ttu-id="f68af-381">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f68af-381">.NET Core 1.0</span></span> |
| <span data-ttu-id="f68af-382">**.NET 框架的應用程式設定**</span><span class="sxs-lookup"><span data-stu-id="f68af-382">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f68af-383">gcAllow非常大的物件</span><span class="sxs-lookup"><span data-stu-id="f68af-383">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="f68af-384">`1`- 已開啟</span><span class="sxs-lookup"><span data-stu-id="f68af-384">`1` - enabled</span></span><br/> <span data-ttu-id="f68af-385">`0`- 停用</span><span class="sxs-lookup"><span data-stu-id="f68af-385">`0` - disabled</span></span> | <span data-ttu-id="f68af-386">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="f68af-386">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="f68af-387">大型物件堆閾值</span><span class="sxs-lookup"><span data-stu-id="f68af-387">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="f68af-388">系統.GC.LOH閾值/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="f68af-388">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="f68af-389">指定導致物件轉到大型物件堆 (LOH) 上的閾值大小(以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="f68af-389">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="f68af-390">默認閾值為 85,000 位元組。</span><span class="sxs-lookup"><span data-stu-id="f68af-390">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="f68af-391">指定的值必須大於預設閾值。</span><span class="sxs-lookup"><span data-stu-id="f68af-391">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="f68af-392">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f68af-392">Setting name</span></span> | <span data-ttu-id="f68af-393">值</span><span class="sxs-lookup"><span data-stu-id="f68af-393">Values</span></span> | <span data-ttu-id="f68af-394">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="f68af-394">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f68af-395">**執行時設定.json**</span><span class="sxs-lookup"><span data-stu-id="f68af-395">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="f68af-396">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="f68af-396">*decimal value*</span></span> | <span data-ttu-id="f68af-397">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f68af-397">.NET Core 1.0</span></span> |
| <span data-ttu-id="f68af-398">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f68af-398">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="f68af-399">*十六進位值*</span><span class="sxs-lookup"><span data-stu-id="f68af-399">*hexadecimal value*</span></span> | <span data-ttu-id="f68af-400">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f68af-400">.NET Core 1.0</span></span> |
| <span data-ttu-id="f68af-401">**.NET 框架的應用程式設定**</span><span class="sxs-lookup"><span data-stu-id="f68af-401">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f68af-402">GCLOH閾值</span><span class="sxs-lookup"><span data-stu-id="f68af-402">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="f68af-403">*十進位值*</span><span class="sxs-lookup"><span data-stu-id="f68af-403">*decimal value*</span></span> | <span data-ttu-id="f68af-404">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="f68af-404">.NET Framework 4.8</span></span> |

<span data-ttu-id="f68af-405">範例：</span><span class="sxs-lookup"><span data-stu-id="f68af-405">Example:</span></span>

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
> <span data-ttu-id="f68af-406">如果要在*運行時 config.json*中設置該選項,請指定一個小數值。</span><span class="sxs-lookup"><span data-stu-id="f68af-406">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="f68af-407">如果要將該選項設置為環境變數,請指定十六進位值。</span><span class="sxs-lookup"><span data-stu-id="f68af-407">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="f68af-408">例如,要設置 120,000 位元組的閾值大小,JSON 檔的值將為 120000,環境變數的值為 0x1D4C0 或 1D4C0。</span><span class="sxs-lookup"><span data-stu-id="f68af-408">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="f68af-409">獨立 GC</span><span class="sxs-lookup"><span data-stu-id="f68af-409">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="f68af-410">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="f68af-410">COMPlus_GCName</span></span>

- <span data-ttu-id="f68af-411">指定包含運行時打算載入的垃圾回收器的庫的路徑。</span><span class="sxs-lookup"><span data-stu-id="f68af-411">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="f68af-412">有關詳細資訊,請參閱獨立[GC 載入程式設計](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md)。</span><span class="sxs-lookup"><span data-stu-id="f68af-412">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="f68af-413">設定名稱</span><span class="sxs-lookup"><span data-stu-id="f68af-413">Setting name</span></span> | <span data-ttu-id="f68af-414">值</span><span class="sxs-lookup"><span data-stu-id="f68af-414">Values</span></span> | <span data-ttu-id="f68af-415">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="f68af-415">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f68af-416">**執行時設定.json**</span><span class="sxs-lookup"><span data-stu-id="f68af-416">**runtimeconfig.json**</span></span> | <span data-ttu-id="f68af-417">N/A</span><span class="sxs-lookup"><span data-stu-id="f68af-417">N/A</span></span> | <span data-ttu-id="f68af-418">N/A</span><span class="sxs-lookup"><span data-stu-id="f68af-418">N/A</span></span> | <span data-ttu-id="f68af-419">N/A</span><span class="sxs-lookup"><span data-stu-id="f68af-419">N/A</span></span> |
| <span data-ttu-id="f68af-420">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="f68af-420">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="f68af-421">*string_path*</span><span class="sxs-lookup"><span data-stu-id="f68af-421">*string_path*</span></span> | <span data-ttu-id="f68af-422">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="f68af-422">.NET Core 2.0</span></span> |
