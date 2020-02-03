---
title: 編譯 config 設定
description: 瞭解執行時間設定，其可設定 JIT 編譯程式適用于 .NET Core 應用程式的方式。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 0dab3b7b7726a232cf293e338308cf898b370759
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733531"
---
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="ad44b-103">編譯的執行時間設定選項</span><span class="sxs-lookup"><span data-stu-id="ad44b-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="ad44b-104">階層式編譯</span><span class="sxs-lookup"><span data-stu-id="ad44b-104">Tiered compilation</span></span>

- <span data-ttu-id="ad44b-105">設定即時（JIT）編譯器是否使用[分層式編譯](../whats-new/dotnet-core-3-0.md#tiered-compilation)。</span><span class="sxs-lookup"><span data-stu-id="ad44b-105">Configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="ad44b-106">階層式編譯會透過兩個層級轉換方法：</span><span class="sxs-lookup"><span data-stu-id="ad44b-106">Tiered compilation transitions methods through two tiers:</span></span>
  - <span data-ttu-id="ad44b-107">第一層會更快速地產生程式碼（[快速 JIT](#quick-jit)），或載入預先編譯的程式碼（[ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images)）。</span><span class="sxs-lookup"><span data-stu-id="ad44b-107">The first tier generates code more quickly ([quick JIT](#quick-jit)) or loads pre-compiled code ([ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images)).</span></span>
  - <span data-ttu-id="ad44b-108">第二層會在背景產生優化的程式碼（「優化 JIT」）。</span><span class="sxs-lookup"><span data-stu-id="ad44b-108">The second tier generates optimized code in the background ("optimizing JIT").</span></span>
- <span data-ttu-id="ad44b-109">在 .NET Core 3.0 和更新版本中，預設會啟用階層式編譯。</span><span class="sxs-lookup"><span data-stu-id="ad44b-109">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="ad44b-110">在 .NET Core 2.1 和2.2 中，階層式編譯預設為停用。</span><span class="sxs-lookup"><span data-stu-id="ad44b-110">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>
- <span data-ttu-id="ad44b-111">如需詳細資訊，請參閱階層式[編譯指南](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md)。</span><span class="sxs-lookup"><span data-stu-id="ad44b-111">For more information, see the [Tiered compilation guide](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md).</span></span>

| | <span data-ttu-id="ad44b-112">設定名稱</span><span class="sxs-lookup"><span data-stu-id="ad44b-112">Setting name</span></span> | <span data-ttu-id="ad44b-113">值</span><span class="sxs-lookup"><span data-stu-id="ad44b-113">Values</span></span> |
| - | - | - |
| <span data-ttu-id="ad44b-114">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="ad44b-114">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="ad44b-115">已啟用 `true`</span><span class="sxs-lookup"><span data-stu-id="ad44b-115">`true` - enabled</span></span><br/><span data-ttu-id="ad44b-116">`false`-已停用</span><span class="sxs-lookup"><span data-stu-id="ad44b-116">`false` - disabled</span></span> |
| <span data-ttu-id="ad44b-117">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="ad44b-117">**MSBuild property**</span></span> | `TieredCompilation` | <span data-ttu-id="ad44b-118">已啟用 `true`</span><span class="sxs-lookup"><span data-stu-id="ad44b-118">`true` - enabled</span></span><br/><span data-ttu-id="ad44b-119">`false`-已停用</span><span class="sxs-lookup"><span data-stu-id="ad44b-119">`false` - disabled</span></span> |
| <span data-ttu-id="ad44b-120">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="ad44b-120">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="ad44b-121">已啟用 `1`</span><span class="sxs-lookup"><span data-stu-id="ad44b-121">`1` - enabled</span></span><br/><span data-ttu-id="ad44b-122">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="ad44b-122">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="ad44b-123">範例</span><span class="sxs-lookup"><span data-stu-id="ad44b-123">Examples</span></span>

<span data-ttu-id="ad44b-124">*.runtimeconfig.json json*檔案：</span><span class="sxs-lookup"><span data-stu-id="ad44b-124">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

<span data-ttu-id="ad44b-125">專案檔：</span><span class="sxs-lookup"><span data-stu-id="ad44b-125">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a><span data-ttu-id="ad44b-126">快速 JIT</span><span class="sxs-lookup"><span data-stu-id="ad44b-126">Quick JIT</span></span>

- <span data-ttu-id="ad44b-127">設定 JIT 編譯程式是否使用*快速 jit*。</span><span class="sxs-lookup"><span data-stu-id="ad44b-127">Configures whether the JIT compiler uses *quick JIT*.</span></span> <span data-ttu-id="ad44b-128">對於不包含迴圈的方法，以及無法使用預先編譯的程式碼，快速 JIT 會更快速地編譯它們，但不會進行優化。</span><span class="sxs-lookup"><span data-stu-id="ad44b-128">For methods that don't contain loops and for which pre-compiled code is not available, quick JIT compiles them more quickly but without optimizations.</span></span>
- <span data-ttu-id="ad44b-129">啟用快速 JIT 可減少啟動時間，但可能會產生效能特性降低的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ad44b-129">Enabling quick JIT decreases startup time but can produce code with degraded performance characteristics.</span></span> <span data-ttu-id="ad44b-130">例如，程式碼可能會使用更多堆疊空間、配置更多記憶體，且執行速度較慢。</span><span class="sxs-lookup"><span data-stu-id="ad44b-130">For example, the code may use more stack space, allocate more memory, and run slower.</span></span>
- <span data-ttu-id="ad44b-131">如果已停用快速 JIT，但已啟用[分層編譯](#tiered-compilation)，則只有預先編譯的程式碼會參與階層式編譯。</span><span class="sxs-lookup"><span data-stu-id="ad44b-131">If quick JIT is disabled but [tiered compilation](#tiered-compilation) is enabled, only pre-compiled code participates in tiered compilation.</span></span> <span data-ttu-id="ad44b-132">如果未使用[ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images)預先編譯方法，則 JIT 行為會與已停用階層式[編譯](#tiered-compilation)相同。</span><span class="sxs-lookup"><span data-stu-id="ad44b-132">If a method is not pre-compiled with [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images), the JIT behavior is the same as if [tiered compilation](#tiered-compilation) were disabled.</span></span>
- <span data-ttu-id="ad44b-133">在 .NET Core 3.0 和更新版本中，預設會啟用 [快速 JIT]。</span><span class="sxs-lookup"><span data-stu-id="ad44b-133">In .NET Core 3.0 and later, quick JIT is enabled by default.</span></span>
- <span data-ttu-id="ad44b-134">在 .NET Core 2.1 和2.2 中，預設會停用 [快速 JIT]。</span><span class="sxs-lookup"><span data-stu-id="ad44b-134">In .NET Core 2.1 and 2.2, quick JIT is disabled by default.</span></span>

| | <span data-ttu-id="ad44b-135">設定名稱</span><span class="sxs-lookup"><span data-stu-id="ad44b-135">Setting name</span></span> | <span data-ttu-id="ad44b-136">值</span><span class="sxs-lookup"><span data-stu-id="ad44b-136">Values</span></span> |
| - | - | - |
| <span data-ttu-id="ad44b-137">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="ad44b-137">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJit` | <span data-ttu-id="ad44b-138">已啟用 `true`</span><span class="sxs-lookup"><span data-stu-id="ad44b-138">`true` - enabled</span></span><br/><span data-ttu-id="ad44b-139">`false`-已停用</span><span class="sxs-lookup"><span data-stu-id="ad44b-139">`false` - disabled</span></span> |
| <span data-ttu-id="ad44b-140">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="ad44b-140">**MSBuild property**</span></span> | `TieredCompilationQuickJit` | <span data-ttu-id="ad44b-141">已啟用 `true`</span><span class="sxs-lookup"><span data-stu-id="ad44b-141">`true` - enabled</span></span><br/><span data-ttu-id="ad44b-142">`false`-已停用</span><span class="sxs-lookup"><span data-stu-id="ad44b-142">`false` - disabled</span></span> |
| <span data-ttu-id="ad44b-143">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="ad44b-143">**Environment variable**</span></span> | `COMPlus_TC_QuickJit` | <span data-ttu-id="ad44b-144">已啟用 `1`</span><span class="sxs-lookup"><span data-stu-id="ad44b-144">`1` - enabled</span></span><br/><span data-ttu-id="ad44b-145">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="ad44b-145">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="ad44b-146">範例</span><span class="sxs-lookup"><span data-stu-id="ad44b-146">Examples</span></span>

<span data-ttu-id="ad44b-147">*.runtimeconfig.json json*檔案：</span><span class="sxs-lookup"><span data-stu-id="ad44b-147">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

<span data-ttu-id="ad44b-148">專案檔：</span><span class="sxs-lookup"><span data-stu-id="ad44b-148">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a><span data-ttu-id="ad44b-149">快速 JIT for 迴圈</span><span class="sxs-lookup"><span data-stu-id="ad44b-149">Quick JIT for loops</span></span>

- <span data-ttu-id="ad44b-150">設定 JIT 編譯程式是否針對包含迴圈的方法使用快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="ad44b-150">Configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span>
- <span data-ttu-id="ad44b-151">啟用快速 JIT for 迴圈可能會改善啟動效能。</span><span class="sxs-lookup"><span data-stu-id="ad44b-151">Enabling quick JIT for loops may improve startup performance.</span></span> <span data-ttu-id="ad44b-152">不過，長時間執行的迴圈可能會停滯在較不優化的程式碼中。</span><span class="sxs-lookup"><span data-stu-id="ad44b-152">However, long-running loops can get stuck in less-optimized code for long periods.</span></span>
- <span data-ttu-id="ad44b-153">如果已停用[快速 JIT](#quick-jit) ，此設定就不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="ad44b-153">If [quick JIT](#quick-jit) is disabled, this setting has no effect.</span></span>
- <span data-ttu-id="ad44b-154">預設：停用（`false`）。</span><span class="sxs-lookup"><span data-stu-id="ad44b-154">Default: Disabled (`false`).</span></span>

| | <span data-ttu-id="ad44b-155">設定名稱</span><span class="sxs-lookup"><span data-stu-id="ad44b-155">Setting name</span></span> | <span data-ttu-id="ad44b-156">值</span><span class="sxs-lookup"><span data-stu-id="ad44b-156">Values</span></span> |
| - | - | - |
| <span data-ttu-id="ad44b-157">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="ad44b-157">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJitForLoops` | <span data-ttu-id="ad44b-158">`false`-已停用</span><span class="sxs-lookup"><span data-stu-id="ad44b-158">`false` - disabled</span></span><br/><span data-ttu-id="ad44b-159">已啟用 `true`</span><span class="sxs-lookup"><span data-stu-id="ad44b-159">`true` - enabled</span></span> |
| <span data-ttu-id="ad44b-160">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="ad44b-160">**MSBuild property**</span></span> | `TieredCompilationQuickJitForLoops` | <span data-ttu-id="ad44b-161">`false`-已停用</span><span class="sxs-lookup"><span data-stu-id="ad44b-161">`false` - disabled</span></span><br/><span data-ttu-id="ad44b-162">已啟用 `true`</span><span class="sxs-lookup"><span data-stu-id="ad44b-162">`true` - enabled</span></span> |
| <span data-ttu-id="ad44b-163">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="ad44b-163">**Environment variable**</span></span> | `COMPlus_TC_QuickJitForLoops` | <span data-ttu-id="ad44b-164">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="ad44b-164">`0` - disabled</span></span><br/><span data-ttu-id="ad44b-165">已啟用 `1`</span><span class="sxs-lookup"><span data-stu-id="ad44b-165">`1` - enabled</span></span> |

### <a name="examples"></a><span data-ttu-id="ad44b-166">範例</span><span class="sxs-lookup"><span data-stu-id="ad44b-166">Examples</span></span>

<span data-ttu-id="ad44b-167">*.runtimeconfig.json json*檔案：</span><span class="sxs-lookup"><span data-stu-id="ad44b-167">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

<span data-ttu-id="ad44b-168">專案檔：</span><span class="sxs-lookup"><span data-stu-id="ad44b-168">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>false</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```
