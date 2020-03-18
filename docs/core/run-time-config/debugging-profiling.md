---
title: 調試分析配置設置
description: 瞭解配置 .NET Core 應用的調試和分析的運行時設置。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: c57cfa7233f48def890ded3c9d589b7f268147df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74802796"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a><span data-ttu-id="7c089-103">用於調試和分析的運行時配置選項</span><span class="sxs-lookup"><span data-stu-id="7c089-103">Run-time configuration options for debugging and profiling</span></span>

## <a name="enable-diagnostics"></a><span data-ttu-id="7c089-104">啟用診斷</span><span class="sxs-lookup"><span data-stu-id="7c089-104">Enable diagnostics</span></span>

- <span data-ttu-id="7c089-105">配置調試器、探測器和事件管道診斷是啟用還是禁用。</span><span class="sxs-lookup"><span data-stu-id="7c089-105">Configures whether the debugger, the profiler, and EventPipe diagnostics are enabled or disabled.</span></span>
- <span data-ttu-id="7c089-106">預設值： 已`1`啟用 （ 。</span><span class="sxs-lookup"><span data-stu-id="7c089-106">Default: Enabled (`1`).</span></span>

| | <span data-ttu-id="7c089-107">設定名稱</span><span class="sxs-lookup"><span data-stu-id="7c089-107">Setting name</span></span> | <span data-ttu-id="7c089-108">值</span><span class="sxs-lookup"><span data-stu-id="7c089-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="7c089-109">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="7c089-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="7c089-110">N/A</span><span class="sxs-lookup"><span data-stu-id="7c089-110">N/A</span></span> | <span data-ttu-id="7c089-111">N/A</span><span class="sxs-lookup"><span data-stu-id="7c089-111">N/A</span></span> |
| <span data-ttu-id="7c089-112">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="7c089-112">**Environment variable**</span></span> | `COMPlus_EnableDiagnostics` | <span data-ttu-id="7c089-113">`1`- 已啟用</span><span class="sxs-lookup"><span data-stu-id="7c089-113">`1` - enabled</span></span><br/><span data-ttu-id="7c089-114">`0`- 禁用</span><span class="sxs-lookup"><span data-stu-id="7c089-114">`0` - disabled</span></span> |

## <a name="enable-profiling"></a><span data-ttu-id="7c089-115">啟用分析</span><span class="sxs-lookup"><span data-stu-id="7c089-115">Enable profiling</span></span>

- <span data-ttu-id="7c089-116">配置是否為當前正在運行的進程啟用了分析。</span><span class="sxs-lookup"><span data-stu-id="7c089-116">Configures whether profiling is enabled for the currently running process.</span></span>
- <span data-ttu-id="7c089-117">預設值： 已`0`禁用 （ 。</span><span class="sxs-lookup"><span data-stu-id="7c089-117">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="7c089-118">設定名稱</span><span class="sxs-lookup"><span data-stu-id="7c089-118">Setting name</span></span> | <span data-ttu-id="7c089-119">值</span><span class="sxs-lookup"><span data-stu-id="7c089-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="7c089-120">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="7c089-120">**runtimeconfig.json**</span></span> | <span data-ttu-id="7c089-121">N/A</span><span class="sxs-lookup"><span data-stu-id="7c089-121">N/A</span></span> | <span data-ttu-id="7c089-122">N/A</span><span class="sxs-lookup"><span data-stu-id="7c089-122">N/A</span></span> |
| <span data-ttu-id="7c089-123">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="7c089-123">**Environment variable**</span></span> | `CORECLR_ENABLE_PROFILING` | <span data-ttu-id="7c089-124">`0`- 禁用</span><span class="sxs-lookup"><span data-stu-id="7c089-124">`0` - disabled</span></span><br/><span data-ttu-id="7c089-125">`1`- 已啟用</span><span class="sxs-lookup"><span data-stu-id="7c089-125">`1` - enabled</span></span> |

## <a name="profiler-guid"></a><span data-ttu-id="7c089-126">探測器 GUID</span><span class="sxs-lookup"><span data-stu-id="7c089-126">Profiler GUID</span></span>

- <span data-ttu-id="7c089-127">指定要載入到當前正在運行的進程中的探測器的 GUID。</span><span class="sxs-lookup"><span data-stu-id="7c089-127">Specifies the GUID of the profiler to load into the currently running process.</span></span>

| | <span data-ttu-id="7c089-128">設定名稱</span><span class="sxs-lookup"><span data-stu-id="7c089-128">Setting name</span></span> | <span data-ttu-id="7c089-129">值</span><span class="sxs-lookup"><span data-stu-id="7c089-129">Values</span></span> |
| - | - | - |
| <span data-ttu-id="7c089-130">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="7c089-130">**runtimeconfig.json**</span></span> | <span data-ttu-id="7c089-131">N/A</span><span class="sxs-lookup"><span data-stu-id="7c089-131">N/A</span></span> | <span data-ttu-id="7c089-132">N/A</span><span class="sxs-lookup"><span data-stu-id="7c089-132">N/A</span></span> |
| <span data-ttu-id="7c089-133">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="7c089-133">**Environment variable**</span></span> | `CORECLR_PROFILER` | <span data-ttu-id="7c089-134">*字串吉德*</span><span class="sxs-lookup"><span data-stu-id="7c089-134">*string-guid*</span></span> |

## <a name="profiler-location"></a><span data-ttu-id="7c089-135">探測器位置</span><span class="sxs-lookup"><span data-stu-id="7c089-135">Profiler location</span></span>

- <span data-ttu-id="7c089-136">指定探測器 DLL 的路徑以載入到當前正在運行的進程（或 32 位或 64 位進程）。</span><span class="sxs-lookup"><span data-stu-id="7c089-136">Specifies the path to the profiler DLL to load into the currently running process (or 32-bit or 64-bit process).</span></span>
- <span data-ttu-id="7c089-137">如果設置了多個變數，則位級特定變數優先。</span><span class="sxs-lookup"><span data-stu-id="7c089-137">If more than one variable is set, the bitness-specific variables take precedence.</span></span> <span data-ttu-id="7c089-138">它們指定要載入的探測器的位數。</span><span class="sxs-lookup"><span data-stu-id="7c089-138">They specify which bitness of profiler to load.</span></span>
- <span data-ttu-id="7c089-139">有關詳細資訊，請參閱[查找探測器庫](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md)。</span><span class="sxs-lookup"><span data-stu-id="7c089-139">For more information, see [Finding the profiler library](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span></span>

| | <span data-ttu-id="7c089-140">設定名稱</span><span class="sxs-lookup"><span data-stu-id="7c089-140">Setting name</span></span> | <span data-ttu-id="7c089-141">值</span><span class="sxs-lookup"><span data-stu-id="7c089-141">Values</span></span> |
| - | - | - |
| <span data-ttu-id="7c089-142">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="7c089-142">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH` | <span data-ttu-id="7c089-143">*字串路徑*</span><span class="sxs-lookup"><span data-stu-id="7c089-143">*string-path*</span></span> |
| <span data-ttu-id="7c089-144">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="7c089-144">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_32` | <span data-ttu-id="7c089-145">*字串路徑*</span><span class="sxs-lookup"><span data-stu-id="7c089-145">*string-path*</span></span> |
| <span data-ttu-id="7c089-146">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="7c089-146">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_64` | <span data-ttu-id="7c089-147">*字串路徑*</span><span class="sxs-lookup"><span data-stu-id="7c089-147">*string-path*</span></span> |

## <a name="write-perf-map"></a><span data-ttu-id="7c089-148">寫入 perf 地圖</span><span class="sxs-lookup"><span data-stu-id="7c089-148">Write perf map</span></span>

- <span data-ttu-id="7c089-149">啟用或禁用在 Linux 系統上寫入 */tmp/perf-$pid.map。*</span><span class="sxs-lookup"><span data-stu-id="7c089-149">Enables or disables writing */tmp/perf-$pid.map* on Linux systems.</span></span>
- <span data-ttu-id="7c089-150">預設值： 已`0`禁用 （ 。</span><span class="sxs-lookup"><span data-stu-id="7c089-150">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="7c089-151">設定名稱</span><span class="sxs-lookup"><span data-stu-id="7c089-151">Setting name</span></span> | <span data-ttu-id="7c089-152">值</span><span class="sxs-lookup"><span data-stu-id="7c089-152">Values</span></span> |
| - | - | - |
| <span data-ttu-id="7c089-153">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="7c089-153">**runtimeconfig.json**</span></span> | <span data-ttu-id="7c089-154">N/A</span><span class="sxs-lookup"><span data-stu-id="7c089-154">N/A</span></span> | <span data-ttu-id="7c089-155">N/A</span><span class="sxs-lookup"><span data-stu-id="7c089-155">N/A</span></span> |
| <span data-ttu-id="7c089-156">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="7c089-156">**Environment variable**</span></span> | `COMPlus_PerfMapEnabled` | <span data-ttu-id="7c089-157">`0`- 禁用</span><span class="sxs-lookup"><span data-stu-id="7c089-157">`0` - disabled</span></span><br/><span data-ttu-id="7c089-158">`1`- 已啟用</span><span class="sxs-lookup"><span data-stu-id="7c089-158">`1` - enabled</span></span> |

## <a name="perf-log-markers"></a><span data-ttu-id="7c089-159">Perf 日誌標記</span><span class="sxs-lookup"><span data-stu-id="7c089-159">Perf log markers</span></span>

- <span data-ttu-id="7c089-160">設置為`COMPlus_PerfMapEnabled`時`1`，啟用或禁用指定信號，以在 perf 日誌中作為標記接受和忽略。</span><span class="sxs-lookup"><span data-stu-id="7c089-160">When `COMPlus_PerfMapEnabled` is set to `1`, enables or disables the specified signal to be accepted and ignored as a marker in the perf logs.</span></span>
- <span data-ttu-id="7c089-161">預設值： 已`0`禁用 （ 。</span><span class="sxs-lookup"><span data-stu-id="7c089-161">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="7c089-162">設定名稱</span><span class="sxs-lookup"><span data-stu-id="7c089-162">Setting name</span></span> | <span data-ttu-id="7c089-163">值</span><span class="sxs-lookup"><span data-stu-id="7c089-163">Values</span></span> |
| - | - | - |
| <span data-ttu-id="7c089-164">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="7c089-164">**runtimeconfig.json**</span></span> | <span data-ttu-id="7c089-165">N/A</span><span class="sxs-lookup"><span data-stu-id="7c089-165">N/A</span></span> | <span data-ttu-id="7c089-166">N/A</span><span class="sxs-lookup"><span data-stu-id="7c089-166">N/A</span></span> |
| <span data-ttu-id="7c089-167">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="7c089-167">**Environment variable**</span></span> | `COMPlus_PerfMapIgnoreSignal` | <span data-ttu-id="7c089-168">`0`- 禁用</span><span class="sxs-lookup"><span data-stu-id="7c089-168">`0` - disabled</span></span><br/><span data-ttu-id="7c089-169">`1`- 已啟用</span><span class="sxs-lookup"><span data-stu-id="7c089-169">`1` - enabled</span></span> |
