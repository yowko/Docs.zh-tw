---
title: 編譯配置設置
description: 瞭解配置 JIT 編譯器如何為 .NET Core 應用工作的運行時設置。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: adf1f01dba7387b89ee56784e33653d6a132c0e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77092885"
---
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="3c365-103">用於編譯的運行時配置選項</span><span class="sxs-lookup"><span data-stu-id="3c365-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="3c365-104">階層式編譯</span><span class="sxs-lookup"><span data-stu-id="3c365-104">Tiered compilation</span></span>

- <span data-ttu-id="3c365-105">配置即時 （JIT） 編譯器是否使用[分層編譯](../whats-new/dotnet-core-3-0.md#tiered-compilation)。</span><span class="sxs-lookup"><span data-stu-id="3c365-105">Configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="3c365-106">分層編譯通過兩層轉換方法：</span><span class="sxs-lookup"><span data-stu-id="3c365-106">Tiered compilation transitions methods through two tiers:</span></span>
  - <span data-ttu-id="3c365-107">第一層生成代碼更快 （[快速 JIT）](#quick-jit)或載入預編譯代碼 （[ReadyToRun](#readytorun)）。</span><span class="sxs-lookup"><span data-stu-id="3c365-107">The first tier generates code more quickly ([quick JIT](#quick-jit)) or loads pre-compiled code ([ReadyToRun](#readytorun)).</span></span>
  - <span data-ttu-id="3c365-108">第二層在後臺生成優化的代碼（"優化 JIT"）。</span><span class="sxs-lookup"><span data-stu-id="3c365-108">The second tier generates optimized code in the background ("optimizing JIT").</span></span>
- <span data-ttu-id="3c365-109">在 .NET Core 3.0 及更高版本中，預設情況下啟用分層編譯。</span><span class="sxs-lookup"><span data-stu-id="3c365-109">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="3c365-110">在 .NET Core 2.1 和 2.2 中，預設情況下禁用分層編譯。</span><span class="sxs-lookup"><span data-stu-id="3c365-110">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>
- <span data-ttu-id="3c365-111">有關詳細資訊，請參閱[分層編譯指南](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md)。</span><span class="sxs-lookup"><span data-stu-id="3c365-111">For more information, see the [Tiered compilation guide](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md).</span></span>

| | <span data-ttu-id="3c365-112">設定名稱</span><span class="sxs-lookup"><span data-stu-id="3c365-112">Setting name</span></span> | <span data-ttu-id="3c365-113">值</span><span class="sxs-lookup"><span data-stu-id="3c365-113">Values</span></span> |
| - | - | - |
| <span data-ttu-id="3c365-114">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="3c365-114">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="3c365-115">`true`- 已啟用</span><span class="sxs-lookup"><span data-stu-id="3c365-115">`true` - enabled</span></span><br/><span data-ttu-id="3c365-116">`false`- 禁用</span><span class="sxs-lookup"><span data-stu-id="3c365-116">`false` - disabled</span></span> |
| <span data-ttu-id="3c365-117">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="3c365-117">**MSBuild property**</span></span> | `TieredCompilation` | <span data-ttu-id="3c365-118">`true`- 已啟用</span><span class="sxs-lookup"><span data-stu-id="3c365-118">`true` - enabled</span></span><br/><span data-ttu-id="3c365-119">`false`- 禁用</span><span class="sxs-lookup"><span data-stu-id="3c365-119">`false` - disabled</span></span> |
| <span data-ttu-id="3c365-120">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="3c365-120">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="3c365-121">`1`- 已啟用</span><span class="sxs-lookup"><span data-stu-id="3c365-121">`1` - enabled</span></span><br/><span data-ttu-id="3c365-122">`0`- 禁用</span><span class="sxs-lookup"><span data-stu-id="3c365-122">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="3c365-123">範例</span><span class="sxs-lookup"><span data-stu-id="3c365-123">Examples</span></span>

<span data-ttu-id="3c365-124">*運行時配置.json*檔：</span><span class="sxs-lookup"><span data-stu-id="3c365-124">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

<span data-ttu-id="3c365-125">專案檔：</span><span class="sxs-lookup"><span data-stu-id="3c365-125">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a><span data-ttu-id="3c365-126">快速 JIT</span><span class="sxs-lookup"><span data-stu-id="3c365-126">Quick JIT</span></span>

- <span data-ttu-id="3c365-127">配置 JIT 編譯器是否使用*快速 JIT*。</span><span class="sxs-lookup"><span data-stu-id="3c365-127">Configures whether the JIT compiler uses *quick JIT*.</span></span> <span data-ttu-id="3c365-128">對於不包含迴圈且預編譯代碼不可用的方法，快速 JIT 可以更快地編譯它們，但無需優化。</span><span class="sxs-lookup"><span data-stu-id="3c365-128">For methods that don't contain loops and for which pre-compiled code is not available, quick JIT compiles them more quickly but without optimizations.</span></span>
- <span data-ttu-id="3c365-129">啟用快速 JIT 可縮短啟動時間，但可以生成性能降低的代碼。</span><span class="sxs-lookup"><span data-stu-id="3c365-129">Enabling quick JIT decreases startup time but can produce code with degraded performance characteristics.</span></span> <span data-ttu-id="3c365-130">例如，代碼可能使用更多的堆疊空間、分配更多記憶體和運行速度較慢。</span><span class="sxs-lookup"><span data-stu-id="3c365-130">For example, the code may use more stack space, allocate more memory, and run slower.</span></span>
- <span data-ttu-id="3c365-131">如果禁用快速 JIT，但啟用[分層編譯](#tiered-compilation)，則只有預編譯代碼參與分層編譯。</span><span class="sxs-lookup"><span data-stu-id="3c365-131">If quick JIT is disabled but [tiered compilation](#tiered-compilation) is enabled, only pre-compiled code participates in tiered compilation.</span></span> <span data-ttu-id="3c365-132">如果未使用[ReadyToRun](#readytorun)預編譯方法，則 JIT 行為與禁用[分層編譯](#tiered-compilation)相同。</span><span class="sxs-lookup"><span data-stu-id="3c365-132">If a method is not pre-compiled with [ReadyToRun](#readytorun), the JIT behavior is the same as if [tiered compilation](#tiered-compilation) were disabled.</span></span>
- <span data-ttu-id="3c365-133">在 .NET 核心 3.0 及更高版本中，預設情況下啟用快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="3c365-133">In .NET Core 3.0 and later, quick JIT is enabled by default.</span></span>
- <span data-ttu-id="3c365-134">在 .NET 核心 2.1 和 2.2 中，預設情況下禁用快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="3c365-134">In .NET Core 2.1 and 2.2, quick JIT is disabled by default.</span></span>

| | <span data-ttu-id="3c365-135">設定名稱</span><span class="sxs-lookup"><span data-stu-id="3c365-135">Setting name</span></span> | <span data-ttu-id="3c365-136">值</span><span class="sxs-lookup"><span data-stu-id="3c365-136">Values</span></span> |
| - | - | - |
| <span data-ttu-id="3c365-137">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="3c365-137">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJit` | <span data-ttu-id="3c365-138">`true`- 已啟用</span><span class="sxs-lookup"><span data-stu-id="3c365-138">`true` - enabled</span></span><br/><span data-ttu-id="3c365-139">`false`- 禁用</span><span class="sxs-lookup"><span data-stu-id="3c365-139">`false` - disabled</span></span> |
| <span data-ttu-id="3c365-140">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="3c365-140">**MSBuild property**</span></span> | `TieredCompilationQuickJit` | <span data-ttu-id="3c365-141">`true`- 已啟用</span><span class="sxs-lookup"><span data-stu-id="3c365-141">`true` - enabled</span></span><br/><span data-ttu-id="3c365-142">`false`- 禁用</span><span class="sxs-lookup"><span data-stu-id="3c365-142">`false` - disabled</span></span> |
| <span data-ttu-id="3c365-143">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="3c365-143">**Environment variable**</span></span> | `COMPlus_TC_QuickJit` | <span data-ttu-id="3c365-144">`1`- 已啟用</span><span class="sxs-lookup"><span data-stu-id="3c365-144">`1` - enabled</span></span><br/><span data-ttu-id="3c365-145">`0`- 禁用</span><span class="sxs-lookup"><span data-stu-id="3c365-145">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="3c365-146">範例</span><span class="sxs-lookup"><span data-stu-id="3c365-146">Examples</span></span>

<span data-ttu-id="3c365-147">*運行時配置.json*檔：</span><span class="sxs-lookup"><span data-stu-id="3c365-147">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

<span data-ttu-id="3c365-148">專案檔：</span><span class="sxs-lookup"><span data-stu-id="3c365-148">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a><span data-ttu-id="3c365-149">用於迴圈的快速 JIT</span><span class="sxs-lookup"><span data-stu-id="3c365-149">Quick JIT for loops</span></span>

- <span data-ttu-id="3c365-150">配置 JIT 編譯器是否對包含迴圈的方法使用快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="3c365-150">Configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span>
- <span data-ttu-id="3c365-151">為迴圈啟用快速 JIT 可以提高啟動性能。</span><span class="sxs-lookup"><span data-stu-id="3c365-151">Enabling quick JIT for loops may improve startup performance.</span></span> <span data-ttu-id="3c365-152">但是，長時間運行的迴圈可能會長時間卡在不太優化的代碼中。</span><span class="sxs-lookup"><span data-stu-id="3c365-152">However, long-running loops can get stuck in less-optimized code for long periods.</span></span>
- <span data-ttu-id="3c365-153">如果禁用[快速 JIT，](#quick-jit)則此設置不起作用。</span><span class="sxs-lookup"><span data-stu-id="3c365-153">If [quick JIT](#quick-jit) is disabled, this setting has no effect.</span></span>
- <span data-ttu-id="3c365-154">預設值： 已`false`禁用 （ 。</span><span class="sxs-lookup"><span data-stu-id="3c365-154">Default: Disabled (`false`).</span></span>

| | <span data-ttu-id="3c365-155">設定名稱</span><span class="sxs-lookup"><span data-stu-id="3c365-155">Setting name</span></span> | <span data-ttu-id="3c365-156">值</span><span class="sxs-lookup"><span data-stu-id="3c365-156">Values</span></span> |
| - | - | - |
| <span data-ttu-id="3c365-157">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="3c365-157">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJitForLoops` | <span data-ttu-id="3c365-158">`false`- 禁用</span><span class="sxs-lookup"><span data-stu-id="3c365-158">`false` - disabled</span></span><br/><span data-ttu-id="3c365-159">`true`- 已啟用</span><span class="sxs-lookup"><span data-stu-id="3c365-159">`true` - enabled</span></span> |
| <span data-ttu-id="3c365-160">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="3c365-160">**MSBuild property**</span></span> | `TieredCompilationQuickJitForLoops` | <span data-ttu-id="3c365-161">`false`- 禁用</span><span class="sxs-lookup"><span data-stu-id="3c365-161">`false` - disabled</span></span><br/><span data-ttu-id="3c365-162">`true`- 已啟用</span><span class="sxs-lookup"><span data-stu-id="3c365-162">`true` - enabled</span></span> |
| <span data-ttu-id="3c365-163">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="3c365-163">**Environment variable**</span></span> | `COMPlus_TC_QuickJitForLoops` | <span data-ttu-id="3c365-164">`0`- 禁用</span><span class="sxs-lookup"><span data-stu-id="3c365-164">`0` - disabled</span></span><br/><span data-ttu-id="3c365-165">`1`- 已啟用</span><span class="sxs-lookup"><span data-stu-id="3c365-165">`1` - enabled</span></span> |

### <a name="examples"></a><span data-ttu-id="3c365-166">範例</span><span class="sxs-lookup"><span data-stu-id="3c365-166">Examples</span></span>

<span data-ttu-id="3c365-167">*運行時配置.json*檔：</span><span class="sxs-lookup"><span data-stu-id="3c365-167">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

<span data-ttu-id="3c365-168">專案檔：</span><span class="sxs-lookup"><span data-stu-id="3c365-168">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>false</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```

## <a name="readytorun"></a><span data-ttu-id="3c365-169">準備運行</span><span class="sxs-lookup"><span data-stu-id="3c365-169">ReadyToRun</span></span>

- <span data-ttu-id="3c365-170">配置 .NET Core 運行時是否對具有可用 ReadyToRun 資料的圖像使用預編譯代碼。</span><span class="sxs-lookup"><span data-stu-id="3c365-170">Configures whether the .NET Core runtime uses pre-compiled code for images with available ReadyToRun data.</span></span> <span data-ttu-id="3c365-171">禁用此選項將強制運行時為 JIT 編譯框架代碼。</span><span class="sxs-lookup"><span data-stu-id="3c365-171">Disabling this option forces the runtime to JIT-compile framework code.</span></span>
- <span data-ttu-id="3c365-172">有關詳細資訊，請參閱["準備運行](../whats-new/dotnet-core-3-0.md#readytorun-images)"。</span><span class="sxs-lookup"><span data-stu-id="3c365-172">For more information, see [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span></span>
- <span data-ttu-id="3c365-173">預設值： 已`1`啟用 （ 。</span><span class="sxs-lookup"><span data-stu-id="3c365-173">Default: Enabled (`1`).</span></span>

| | <span data-ttu-id="3c365-174">設定名稱</span><span class="sxs-lookup"><span data-stu-id="3c365-174">Setting name</span></span> | <span data-ttu-id="3c365-175">值</span><span class="sxs-lookup"><span data-stu-id="3c365-175">Values</span></span> |
| - | - | - |
| <span data-ttu-id="3c365-176">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="3c365-176">**Environment variable**</span></span> | `COMPlus_ReadyToRun` | <span data-ttu-id="3c365-177">`1`- 已啟用</span><span class="sxs-lookup"><span data-stu-id="3c365-177">`1` - enabled</span></span><br/><span data-ttu-id="3c365-178">`0`- 禁用</span><span class="sxs-lookup"><span data-stu-id="3c365-178">`0` - disabled</span></span> |
