---
title: 編譯 config 設定
description: 瞭解執行時間設定，其可設定 JIT 編譯程式適用于 .NET Core 應用程式的方式。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 4db20ee6d36fe3d3d66f473644b70c02d4e02cb3
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506840"
---
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="86036-103">編譯的執行時間設定選項</span><span class="sxs-lookup"><span data-stu-id="86036-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="86036-104">階層式編譯</span><span class="sxs-lookup"><span data-stu-id="86036-104">Tiered compilation</span></span>

- <span data-ttu-id="86036-105">設定即時（JIT）編譯器是否使用[分層式編譯](../whats-new/dotnet-core-3-0.md#tiered-compilation)。</span><span class="sxs-lookup"><span data-stu-id="86036-105">Configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="86036-106">階層式編譯會透過兩個層級轉換方法：</span><span class="sxs-lookup"><span data-stu-id="86036-106">Tiered compilation transitions methods through two tiers:</span></span>
  - <span data-ttu-id="86036-107">第一層會更快速地產生程式碼（[快速 JIT](#quick-jit)），或載入預先編譯的程式碼（[ReadyToRun](#readytorun)）。</span><span class="sxs-lookup"><span data-stu-id="86036-107">The first tier generates code more quickly ([quick JIT](#quick-jit)) or loads pre-compiled code ([ReadyToRun](#readytorun)).</span></span>
  - <span data-ttu-id="86036-108">第二層會在背景產生優化的程式碼（「優化 JIT」）。</span><span class="sxs-lookup"><span data-stu-id="86036-108">The second tier generates optimized code in the background ("optimizing JIT").</span></span>
- <span data-ttu-id="86036-109">在 .NET Core 3.0 和更新版本中，預設會啟用階層式編譯。</span><span class="sxs-lookup"><span data-stu-id="86036-109">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="86036-110">在 .NET Core 2.1 和2.2 中，階層式編譯預設為停用。</span><span class="sxs-lookup"><span data-stu-id="86036-110">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>
- <span data-ttu-id="86036-111">如需詳細資訊，請參閱階層式[編譯指南](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md)。</span><span class="sxs-lookup"><span data-stu-id="86036-111">For more information, see the [Tiered compilation guide](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md).</span></span>

| | <span data-ttu-id="86036-112">設定名稱</span><span class="sxs-lookup"><span data-stu-id="86036-112">Setting name</span></span> | <span data-ttu-id="86036-113">值</span><span class="sxs-lookup"><span data-stu-id="86036-113">Values</span></span> |
| - | - | - |
| <span data-ttu-id="86036-114">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="86036-114">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="86036-115">`true`-已啟用</span><span class="sxs-lookup"><span data-stu-id="86036-115">`true` - enabled</span></span><br/><span data-ttu-id="86036-116">`false`-已停用</span><span class="sxs-lookup"><span data-stu-id="86036-116">`false` - disabled</span></span> |
| <span data-ttu-id="86036-117">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="86036-117">**MSBuild property**</span></span> | `TieredCompilation` | <span data-ttu-id="86036-118">`true`-已啟用</span><span class="sxs-lookup"><span data-stu-id="86036-118">`true` - enabled</span></span><br/><span data-ttu-id="86036-119">`false`-已停用</span><span class="sxs-lookup"><span data-stu-id="86036-119">`false` - disabled</span></span> |
| <span data-ttu-id="86036-120">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="86036-120">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="86036-121">`1`-已啟用</span><span class="sxs-lookup"><span data-stu-id="86036-121">`1` - enabled</span></span><br/><span data-ttu-id="86036-122">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="86036-122">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="86036-123">範例</span><span class="sxs-lookup"><span data-stu-id="86036-123">Examples</span></span>

<span data-ttu-id="86036-124">*.runtimeconfig.json json*檔案：</span><span class="sxs-lookup"><span data-stu-id="86036-124">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

<span data-ttu-id="86036-125">專案檔：</span><span class="sxs-lookup"><span data-stu-id="86036-125">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a><span data-ttu-id="86036-126">快速 JIT</span><span class="sxs-lookup"><span data-stu-id="86036-126">Quick JIT</span></span>

- <span data-ttu-id="86036-127">設定 JIT 編譯程式是否使用*快速 jit*。</span><span class="sxs-lookup"><span data-stu-id="86036-127">Configures whether the JIT compiler uses *quick JIT*.</span></span> <span data-ttu-id="86036-128">對於不包含迴圈的方法，以及無法使用預先編譯的程式碼，快速 JIT 會更快速地編譯它們，但不會進行優化。</span><span class="sxs-lookup"><span data-stu-id="86036-128">For methods that don't contain loops and for which pre-compiled code is not available, quick JIT compiles them more quickly but without optimizations.</span></span>
- <span data-ttu-id="86036-129">啟用快速 JIT 可減少啟動時間，但可能會產生效能特性降低的程式碼。</span><span class="sxs-lookup"><span data-stu-id="86036-129">Enabling quick JIT decreases startup time but can produce code with degraded performance characteristics.</span></span> <span data-ttu-id="86036-130">例如，程式碼可能會使用更多堆疊空間、配置更多記憶體，且執行速度較慢。</span><span class="sxs-lookup"><span data-stu-id="86036-130">For example, the code may use more stack space, allocate more memory, and run slower.</span></span>
- <span data-ttu-id="86036-131">如果已停用快速 JIT，但已啟用[分層編譯](#tiered-compilation)，則只有預先編譯的程式碼會參與階層式編譯。</span><span class="sxs-lookup"><span data-stu-id="86036-131">If quick JIT is disabled but [tiered compilation](#tiered-compilation) is enabled, only pre-compiled code participates in tiered compilation.</span></span> <span data-ttu-id="86036-132">如果未使用[ReadyToRun](#readytorun)預先編譯方法，則 JIT 行為會與已停用階層式[編譯](#tiered-compilation)相同。</span><span class="sxs-lookup"><span data-stu-id="86036-132">If a method is not pre-compiled with [ReadyToRun](#readytorun), the JIT behavior is the same as if [tiered compilation](#tiered-compilation) were disabled.</span></span>
- <span data-ttu-id="86036-133">在 .NET Core 3.0 和更新版本中，預設會啟用 [快速 JIT]。</span><span class="sxs-lookup"><span data-stu-id="86036-133">In .NET Core 3.0 and later, quick JIT is enabled by default.</span></span>
- <span data-ttu-id="86036-134">在 .NET Core 2.1 和2.2 中，預設會停用 [快速 JIT]。</span><span class="sxs-lookup"><span data-stu-id="86036-134">In .NET Core 2.1 and 2.2, quick JIT is disabled by default.</span></span>

| | <span data-ttu-id="86036-135">設定名稱</span><span class="sxs-lookup"><span data-stu-id="86036-135">Setting name</span></span> | <span data-ttu-id="86036-136">值</span><span class="sxs-lookup"><span data-stu-id="86036-136">Values</span></span> |
| - | - | - |
| <span data-ttu-id="86036-137">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="86036-137">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJit` | <span data-ttu-id="86036-138">`true`-已啟用</span><span class="sxs-lookup"><span data-stu-id="86036-138">`true` - enabled</span></span><br/><span data-ttu-id="86036-139">`false`-已停用</span><span class="sxs-lookup"><span data-stu-id="86036-139">`false` - disabled</span></span> |
| <span data-ttu-id="86036-140">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="86036-140">**MSBuild property**</span></span> | `TieredCompilationQuickJit` | <span data-ttu-id="86036-141">`true`-已啟用</span><span class="sxs-lookup"><span data-stu-id="86036-141">`true` - enabled</span></span><br/><span data-ttu-id="86036-142">`false`-已停用</span><span class="sxs-lookup"><span data-stu-id="86036-142">`false` - disabled</span></span> |
| <span data-ttu-id="86036-143">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="86036-143">**Environment variable**</span></span> | `COMPlus_TC_QuickJit` | <span data-ttu-id="86036-144">`1`-已啟用</span><span class="sxs-lookup"><span data-stu-id="86036-144">`1` - enabled</span></span><br/><span data-ttu-id="86036-145">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="86036-145">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="86036-146">範例</span><span class="sxs-lookup"><span data-stu-id="86036-146">Examples</span></span>

<span data-ttu-id="86036-147">*.runtimeconfig.json json*檔案：</span><span class="sxs-lookup"><span data-stu-id="86036-147">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

<span data-ttu-id="86036-148">專案檔：</span><span class="sxs-lookup"><span data-stu-id="86036-148">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a><span data-ttu-id="86036-149">快速 JIT for 迴圈</span><span class="sxs-lookup"><span data-stu-id="86036-149">Quick JIT for loops</span></span>

- <span data-ttu-id="86036-150">設定 JIT 編譯程式是否針對包含迴圈的方法使用快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="86036-150">Configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span>
- <span data-ttu-id="86036-151">啟用快速 JIT for 迴圈可能會改善啟動效能。</span><span class="sxs-lookup"><span data-stu-id="86036-151">Enabling quick JIT for loops may improve startup performance.</span></span> <span data-ttu-id="86036-152">不過，長時間執行的迴圈可能會停滯在較不優化的程式碼中。</span><span class="sxs-lookup"><span data-stu-id="86036-152">However, long-running loops can get stuck in less-optimized code for long periods.</span></span>
- <span data-ttu-id="86036-153">如果已停用[快速 JIT](#quick-jit) ，此設定就不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="86036-153">If [quick JIT](#quick-jit) is disabled, this setting has no effect.</span></span>
- <span data-ttu-id="86036-154">預設：停用`false`（）。</span><span class="sxs-lookup"><span data-stu-id="86036-154">Default: Disabled (`false`).</span></span>

| | <span data-ttu-id="86036-155">設定名稱</span><span class="sxs-lookup"><span data-stu-id="86036-155">Setting name</span></span> | <span data-ttu-id="86036-156">值</span><span class="sxs-lookup"><span data-stu-id="86036-156">Values</span></span> |
| - | - | - |
| <span data-ttu-id="86036-157">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="86036-157">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJitForLoops` | <span data-ttu-id="86036-158">`false`-已停用</span><span class="sxs-lookup"><span data-stu-id="86036-158">`false` - disabled</span></span><br/><span data-ttu-id="86036-159">`true`-已啟用</span><span class="sxs-lookup"><span data-stu-id="86036-159">`true` - enabled</span></span> |
| <span data-ttu-id="86036-160">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="86036-160">**MSBuild property**</span></span> | `TieredCompilationQuickJitForLoops` | <span data-ttu-id="86036-161">`false`-已停用</span><span class="sxs-lookup"><span data-stu-id="86036-161">`false` - disabled</span></span><br/><span data-ttu-id="86036-162">`true`-已啟用</span><span class="sxs-lookup"><span data-stu-id="86036-162">`true` - enabled</span></span> |
| <span data-ttu-id="86036-163">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="86036-163">**Environment variable**</span></span> | `COMPlus_TC_QuickJitForLoops` | <span data-ttu-id="86036-164">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="86036-164">`0` - disabled</span></span><br/><span data-ttu-id="86036-165">`1`-已啟用</span><span class="sxs-lookup"><span data-stu-id="86036-165">`1` - enabled</span></span> |

### <a name="examples"></a><span data-ttu-id="86036-166">範例</span><span class="sxs-lookup"><span data-stu-id="86036-166">Examples</span></span>

<span data-ttu-id="86036-167">*.runtimeconfig.json json*檔案：</span><span class="sxs-lookup"><span data-stu-id="86036-167">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

<span data-ttu-id="86036-168">專案檔：</span><span class="sxs-lookup"><span data-stu-id="86036-168">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```

## <a name="readytorun"></a><span data-ttu-id="86036-169">ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="86036-169">ReadyToRun</span></span>

- <span data-ttu-id="86036-170">設定 .NET Core 執行時間是否針對具有可用 ReadyToRun 資料的影像使用預先編譯的程式碼。</span><span class="sxs-lookup"><span data-stu-id="86036-170">Configures whether the .NET Core runtime uses pre-compiled code for images with available ReadyToRun data.</span></span> <span data-ttu-id="86036-171">停用這個選項會強制執行時間執行 JIT 編譯架構程式碼。</span><span class="sxs-lookup"><span data-stu-id="86036-171">Disabling this option forces the runtime to JIT-compile framework code.</span></span>
- <span data-ttu-id="86036-172">如需詳細資訊，請參閱[ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images)。</span><span class="sxs-lookup"><span data-stu-id="86036-172">For more information, see [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span></span>
- <span data-ttu-id="86036-173">預設值： Enabled`1`（）。</span><span class="sxs-lookup"><span data-stu-id="86036-173">Default: Enabled (`1`).</span></span>

| | <span data-ttu-id="86036-174">設定名稱</span><span class="sxs-lookup"><span data-stu-id="86036-174">Setting name</span></span> | <span data-ttu-id="86036-175">值</span><span class="sxs-lookup"><span data-stu-id="86036-175">Values</span></span> |
| - | - | - |
| <span data-ttu-id="86036-176">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="86036-176">**Environment variable**</span></span> | `COMPlus_ReadyToRun` | <span data-ttu-id="86036-177">`1`-已啟用</span><span class="sxs-lookup"><span data-stu-id="86036-177">`1` - enabled</span></span><br/><span data-ttu-id="86036-178">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="86036-178">`0` - disabled</span></span> |
