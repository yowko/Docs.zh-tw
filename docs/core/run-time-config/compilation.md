---
title: 編譯 config 設定
description: 瞭解執行時間設定，其可設定 JIT 編譯程式適用于 .NET Core 應用程式的方式。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: cfcf9b5fc8d11a4ae35ab9b152f32133cd6930bf
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762002"
---
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="83758-103">編譯的執行時間設定選項</span><span class="sxs-lookup"><span data-stu-id="83758-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="83758-104">階層式編譯</span><span class="sxs-lookup"><span data-stu-id="83758-104">Tiered compilation</span></span>

- <span data-ttu-id="83758-105">設定即時（JIT）編譯器是否使用[分層式編譯](../whats-new/dotnet-core-3-0.md#tiered-compilation)。</span><span class="sxs-lookup"><span data-stu-id="83758-105">Configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="83758-106">階層式編譯會透過兩個層級轉換方法：</span><span class="sxs-lookup"><span data-stu-id="83758-106">Tiered compilation transitions methods through two tiers:</span></span>
  - <span data-ttu-id="83758-107">第一層會更快速地產生程式碼（[快速 JIT](#quick-jit)），或載入預先編譯的程式碼（[ReadyToRun](#readytorun)）。</span><span class="sxs-lookup"><span data-stu-id="83758-107">The first tier generates code more quickly ([quick JIT](#quick-jit)) or loads pre-compiled code ([ReadyToRun](#readytorun)).</span></span>
  - <span data-ttu-id="83758-108">第二層會在背景產生優化的程式碼（「優化 JIT」）。</span><span class="sxs-lookup"><span data-stu-id="83758-108">The second tier generates optimized code in the background ("optimizing JIT").</span></span>
- <span data-ttu-id="83758-109">在 .NET Core 3.0 和更新版本中，預設會啟用階層式編譯。</span><span class="sxs-lookup"><span data-stu-id="83758-109">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="83758-110">在 .NET Core 2.1 和2.2 中，階層式編譯預設為停用。</span><span class="sxs-lookup"><span data-stu-id="83758-110">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>
- <span data-ttu-id="83758-111">如需詳細資訊，請參閱階層式[編譯指南](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md)。</span><span class="sxs-lookup"><span data-stu-id="83758-111">For more information, see the [Tiered compilation guide](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md).</span></span>

| | <span data-ttu-id="83758-112">設定名稱</span><span class="sxs-lookup"><span data-stu-id="83758-112">Setting name</span></span> | <span data-ttu-id="83758-113">值</span><span class="sxs-lookup"><span data-stu-id="83758-113">Values</span></span> |
| - | - | - |
| <span data-ttu-id="83758-114">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="83758-114">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="83758-115">`true`-已啟用</span><span class="sxs-lookup"><span data-stu-id="83758-115">`true` - enabled</span></span><br/><span data-ttu-id="83758-116">`false`-已停用</span><span class="sxs-lookup"><span data-stu-id="83758-116">`false` - disabled</span></span> |
| <span data-ttu-id="83758-117">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="83758-117">**MSBuild property**</span></span> | `TieredCompilation` | <span data-ttu-id="83758-118">`true`-已啟用</span><span class="sxs-lookup"><span data-stu-id="83758-118">`true` - enabled</span></span><br/><span data-ttu-id="83758-119">`false`-已停用</span><span class="sxs-lookup"><span data-stu-id="83758-119">`false` - disabled</span></span> |
| <span data-ttu-id="83758-120">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="83758-120">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="83758-121">`1`-已啟用</span><span class="sxs-lookup"><span data-stu-id="83758-121">`1` - enabled</span></span><br/><span data-ttu-id="83758-122">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="83758-122">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="83758-123">範例</span><span class="sxs-lookup"><span data-stu-id="83758-123">Examples</span></span>

<span data-ttu-id="83758-124">*.runtimeconfig.json json*檔案：</span><span class="sxs-lookup"><span data-stu-id="83758-124">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

<span data-ttu-id="83758-125">專案檔：</span><span class="sxs-lookup"><span data-stu-id="83758-125">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a><span data-ttu-id="83758-126">快速 JIT</span><span class="sxs-lookup"><span data-stu-id="83758-126">Quick JIT</span></span>

- <span data-ttu-id="83758-127">設定 JIT 編譯程式是否使用*快速 jit*。</span><span class="sxs-lookup"><span data-stu-id="83758-127">Configures whether the JIT compiler uses *quick JIT*.</span></span> <span data-ttu-id="83758-128">對於不包含迴圈的方法，以及無法使用預先編譯的程式碼，快速 JIT 會更快速地編譯它們，但不會進行優化。</span><span class="sxs-lookup"><span data-stu-id="83758-128">For methods that don't contain loops and for which pre-compiled code is not available, quick JIT compiles them more quickly but without optimizations.</span></span>
- <span data-ttu-id="83758-129">啟用快速 JIT 可減少啟動時間，但可能會產生效能特性降低的程式碼。</span><span class="sxs-lookup"><span data-stu-id="83758-129">Enabling quick JIT decreases startup time but can produce code with degraded performance characteristics.</span></span> <span data-ttu-id="83758-130">例如，程式碼可能會使用更多堆疊空間、配置更多記憶體，且執行速度較慢。</span><span class="sxs-lookup"><span data-stu-id="83758-130">For example, the code may use more stack space, allocate more memory, and run slower.</span></span>
- <span data-ttu-id="83758-131">如果已停用快速 JIT，但已啟用[分層編譯](#tiered-compilation)，則只有預先編譯的程式碼會參與階層式編譯。</span><span class="sxs-lookup"><span data-stu-id="83758-131">If quick JIT is disabled but [tiered compilation](#tiered-compilation) is enabled, only pre-compiled code participates in tiered compilation.</span></span> <span data-ttu-id="83758-132">如果未使用[ReadyToRun](#readytorun)預先編譯方法，則 JIT 行為會與已停用階層式[編譯](#tiered-compilation)相同。</span><span class="sxs-lookup"><span data-stu-id="83758-132">If a method is not pre-compiled with [ReadyToRun](#readytorun), the JIT behavior is the same as if [tiered compilation](#tiered-compilation) were disabled.</span></span>
- <span data-ttu-id="83758-133">在 .NET Core 3.0 和更新版本中，預設會啟用 [快速 JIT]。</span><span class="sxs-lookup"><span data-stu-id="83758-133">In .NET Core 3.0 and later, quick JIT is enabled by default.</span></span>
- <span data-ttu-id="83758-134">在 .NET Core 2.1 和2.2 中，預設會停用 [快速 JIT]。</span><span class="sxs-lookup"><span data-stu-id="83758-134">In .NET Core 2.1 and 2.2, quick JIT is disabled by default.</span></span>

| | <span data-ttu-id="83758-135">設定名稱</span><span class="sxs-lookup"><span data-stu-id="83758-135">Setting name</span></span> | <span data-ttu-id="83758-136">值</span><span class="sxs-lookup"><span data-stu-id="83758-136">Values</span></span> |
| - | - | - |
| <span data-ttu-id="83758-137">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="83758-137">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJit` | <span data-ttu-id="83758-138">`true`-已啟用</span><span class="sxs-lookup"><span data-stu-id="83758-138">`true` - enabled</span></span><br/><span data-ttu-id="83758-139">`false`-已停用</span><span class="sxs-lookup"><span data-stu-id="83758-139">`false` - disabled</span></span> |
| <span data-ttu-id="83758-140">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="83758-140">**MSBuild property**</span></span> | `TieredCompilationQuickJit` | <span data-ttu-id="83758-141">`true`-已啟用</span><span class="sxs-lookup"><span data-stu-id="83758-141">`true` - enabled</span></span><br/><span data-ttu-id="83758-142">`false`-已停用</span><span class="sxs-lookup"><span data-stu-id="83758-142">`false` - disabled</span></span> |
| <span data-ttu-id="83758-143">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="83758-143">**Environment variable**</span></span> | `COMPlus_TC_QuickJit` | <span data-ttu-id="83758-144">`1`-已啟用</span><span class="sxs-lookup"><span data-stu-id="83758-144">`1` - enabled</span></span><br/><span data-ttu-id="83758-145">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="83758-145">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="83758-146">範例</span><span class="sxs-lookup"><span data-stu-id="83758-146">Examples</span></span>

<span data-ttu-id="83758-147">*.runtimeconfig.json json*檔案：</span><span class="sxs-lookup"><span data-stu-id="83758-147">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

<span data-ttu-id="83758-148">專案檔：</span><span class="sxs-lookup"><span data-stu-id="83758-148">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a><span data-ttu-id="83758-149">快速 JIT for 迴圈</span><span class="sxs-lookup"><span data-stu-id="83758-149">Quick JIT for loops</span></span>

- <span data-ttu-id="83758-150">設定 JIT 編譯程式是否針對包含迴圈的方法使用快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="83758-150">Configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span>
- <span data-ttu-id="83758-151">啟用快速 JIT for 迴圈可能會改善啟動效能。</span><span class="sxs-lookup"><span data-stu-id="83758-151">Enabling quick JIT for loops may improve startup performance.</span></span> <span data-ttu-id="83758-152">不過，長時間執行的迴圈可能會停滯在較不優化的程式碼中。</span><span class="sxs-lookup"><span data-stu-id="83758-152">However, long-running loops can get stuck in less-optimized code for long periods.</span></span>
- <span data-ttu-id="83758-153">如果已停用[快速 JIT](#quick-jit) ，此設定就不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="83758-153">If [quick JIT](#quick-jit) is disabled, this setting has no effect.</span></span>
- <span data-ttu-id="83758-154">如果您省略此設定，則不會針對包含迴圈的方法使用快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="83758-154">If you omit this setting, quick JIT is not used for methods that contain loops.</span></span> <span data-ttu-id="83758-155">這相當於將值設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="83758-155">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="83758-156">設定名稱</span><span class="sxs-lookup"><span data-stu-id="83758-156">Setting name</span></span> | <span data-ttu-id="83758-157">值</span><span class="sxs-lookup"><span data-stu-id="83758-157">Values</span></span> |
| - | - | - |
| <span data-ttu-id="83758-158">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="83758-158">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJitForLoops` | <span data-ttu-id="83758-159">`false`-已停用</span><span class="sxs-lookup"><span data-stu-id="83758-159">`false` - disabled</span></span><br/><span data-ttu-id="83758-160">`true`-已啟用</span><span class="sxs-lookup"><span data-stu-id="83758-160">`true` - enabled</span></span> |
| <span data-ttu-id="83758-161">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="83758-161">**MSBuild property**</span></span> | `TieredCompilationQuickJitForLoops` | <span data-ttu-id="83758-162">`false`-已停用</span><span class="sxs-lookup"><span data-stu-id="83758-162">`false` - disabled</span></span><br/><span data-ttu-id="83758-163">`true`-已啟用</span><span class="sxs-lookup"><span data-stu-id="83758-163">`true` - enabled</span></span> |
| <span data-ttu-id="83758-164">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="83758-164">**Environment variable**</span></span> | `COMPlus_TC_QuickJitForLoops` | <span data-ttu-id="83758-165">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="83758-165">`0` - disabled</span></span><br/><span data-ttu-id="83758-166">`1`-已啟用</span><span class="sxs-lookup"><span data-stu-id="83758-166">`1` - enabled</span></span> |

### <a name="examples"></a><span data-ttu-id="83758-167">範例</span><span class="sxs-lookup"><span data-stu-id="83758-167">Examples</span></span>

<span data-ttu-id="83758-168">*.runtimeconfig.json json*檔案：</span><span class="sxs-lookup"><span data-stu-id="83758-168">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

<span data-ttu-id="83758-169">專案檔：</span><span class="sxs-lookup"><span data-stu-id="83758-169">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```

## <a name="readytorun"></a><span data-ttu-id="83758-170">ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="83758-170">ReadyToRun</span></span>

- <span data-ttu-id="83758-171">設定 .NET Core 執行時間是否針對具有可用 ReadyToRun 資料的影像使用預先編譯的程式碼。</span><span class="sxs-lookup"><span data-stu-id="83758-171">Configures whether the .NET Core runtime uses pre-compiled code for images with available ReadyToRun data.</span></span> <span data-ttu-id="83758-172">停用這個選項會強制執行時間執行 JIT 編譯架構程式碼。</span><span class="sxs-lookup"><span data-stu-id="83758-172">Disabling this option forces the runtime to JIT-compile framework code.</span></span>
- <span data-ttu-id="83758-173">如需詳細資訊，請參閱[ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images)。</span><span class="sxs-lookup"><span data-stu-id="83758-173">For more information, see [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span></span>
- <span data-ttu-id="83758-174">如果您省略此設定，.NET 會使用 ReadyToRun 資料（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="83758-174">If you omit this setting, .NET uses ReadyToRun data when it's available.</span></span> <span data-ttu-id="83758-175">這相當於將值設定為 `1` 。</span><span class="sxs-lookup"><span data-stu-id="83758-175">This is equivalent to setting the value to `1`.</span></span>

| | <span data-ttu-id="83758-176">設定名稱</span><span class="sxs-lookup"><span data-stu-id="83758-176">Setting name</span></span> | <span data-ttu-id="83758-177">值</span><span class="sxs-lookup"><span data-stu-id="83758-177">Values</span></span> |
| - | - | - |
| <span data-ttu-id="83758-178">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="83758-178">**Environment variable**</span></span> | `COMPlus_ReadyToRun` | <span data-ttu-id="83758-179">`1`-已啟用</span><span class="sxs-lookup"><span data-stu-id="83758-179">`1` - enabled</span></span><br/><span data-ttu-id="83758-180">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="83758-180">`0` - disabled</span></span> |
