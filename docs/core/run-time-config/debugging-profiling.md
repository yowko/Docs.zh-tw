---
title: 分析設定檔設定
description: 瞭解設定 .NET Core 應用程式之偵測和分析的執行時間設定。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: c57cfa7233f48def890ded3c9d589b7f268147df
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802796"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a><span data-ttu-id="4b061-103">用於進行偵錯工具和分析的執行時間設定選項</span><span class="sxs-lookup"><span data-stu-id="4b061-103">Run-time configuration options for debugging and profiling</span></span>

## <a name="enable-diagnostics"></a><span data-ttu-id="4b061-104">啟用診斷</span><span class="sxs-lookup"><span data-stu-id="4b061-104">Enable diagnostics</span></span>

- <span data-ttu-id="4b061-105">設定是否啟用或停用偵錯工具、分析工具和 EventPipe 診斷。</span><span class="sxs-lookup"><span data-stu-id="4b061-105">Configures whether the debugger, the profiler, and EventPipe diagnostics are enabled or disabled.</span></span>
- <span data-ttu-id="4b061-106">預設：啟用（`1`）。</span><span class="sxs-lookup"><span data-stu-id="4b061-106">Default: Enabled (`1`).</span></span>

| | <span data-ttu-id="4b061-107">設定名稱</span><span class="sxs-lookup"><span data-stu-id="4b061-107">Setting name</span></span> | <span data-ttu-id="4b061-108">值</span><span class="sxs-lookup"><span data-stu-id="4b061-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="4b061-109">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="4b061-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="4b061-110">N/A</span><span class="sxs-lookup"><span data-stu-id="4b061-110">N/A</span></span> | <span data-ttu-id="4b061-111">N/A</span><span class="sxs-lookup"><span data-stu-id="4b061-111">N/A</span></span> |
| <span data-ttu-id="4b061-112">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="4b061-112">**Environment variable**</span></span> | `COMPlus_EnableDiagnostics` | <span data-ttu-id="4b061-113">已啟用 `1`</span><span class="sxs-lookup"><span data-stu-id="4b061-113">`1` - enabled</span></span><br/><span data-ttu-id="4b061-114">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="4b061-114">`0` - disabled</span></span> |

## <a name="enable-profiling"></a><span data-ttu-id="4b061-115">啟用分析</span><span class="sxs-lookup"><span data-stu-id="4b061-115">Enable profiling</span></span>

- <span data-ttu-id="4b061-116">設定是否針對目前正在執行的進程啟用分析。</span><span class="sxs-lookup"><span data-stu-id="4b061-116">Configures whether profiling is enabled for the currently running process.</span></span>
- <span data-ttu-id="4b061-117">預設：停用（`0`）。</span><span class="sxs-lookup"><span data-stu-id="4b061-117">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="4b061-118">設定名稱</span><span class="sxs-lookup"><span data-stu-id="4b061-118">Setting name</span></span> | <span data-ttu-id="4b061-119">值</span><span class="sxs-lookup"><span data-stu-id="4b061-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="4b061-120">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="4b061-120">**runtimeconfig.json**</span></span> | <span data-ttu-id="4b061-121">N/A</span><span class="sxs-lookup"><span data-stu-id="4b061-121">N/A</span></span> | <span data-ttu-id="4b061-122">N/A</span><span class="sxs-lookup"><span data-stu-id="4b061-122">N/A</span></span> |
| <span data-ttu-id="4b061-123">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="4b061-123">**Environment variable**</span></span> | `CORECLR_ENABLE_PROFILING` | <span data-ttu-id="4b061-124">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="4b061-124">`0` - disabled</span></span><br/><span data-ttu-id="4b061-125">已啟用 `1`</span><span class="sxs-lookup"><span data-stu-id="4b061-125">`1` - enabled</span></span> |

## <a name="profiler-guid"></a><span data-ttu-id="4b061-126">Profiler GUID</span><span class="sxs-lookup"><span data-stu-id="4b061-126">Profiler GUID</span></span>

- <span data-ttu-id="4b061-127">指定要載入目前正在執行之進程中的分析工具 GUID。</span><span class="sxs-lookup"><span data-stu-id="4b061-127">Specifies the GUID of the profiler to load into the currently running process.</span></span>

| | <span data-ttu-id="4b061-128">設定名稱</span><span class="sxs-lookup"><span data-stu-id="4b061-128">Setting name</span></span> | <span data-ttu-id="4b061-129">值</span><span class="sxs-lookup"><span data-stu-id="4b061-129">Values</span></span> |
| - | - | - |
| <span data-ttu-id="4b061-130">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="4b061-130">**runtimeconfig.json**</span></span> | <span data-ttu-id="4b061-131">N/A</span><span class="sxs-lookup"><span data-stu-id="4b061-131">N/A</span></span> | <span data-ttu-id="4b061-132">N/A</span><span class="sxs-lookup"><span data-stu-id="4b061-132">N/A</span></span> |
| <span data-ttu-id="4b061-133">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="4b061-133">**Environment variable**</span></span> | `CORECLR_PROFILER` | <span data-ttu-id="4b061-134">*字串-guid*</span><span class="sxs-lookup"><span data-stu-id="4b061-134">*string-guid*</span></span> |

## <a name="profiler-location"></a><span data-ttu-id="4b061-135">Profiler 位置</span><span class="sxs-lookup"><span data-stu-id="4b061-135">Profiler location</span></span>

- <span data-ttu-id="4b061-136">指定要載入目前正在執行之進程（或32位或64位進程）的 profiler DLL 路徑。</span><span class="sxs-lookup"><span data-stu-id="4b061-136">Specifies the path to the profiler DLL to load into the currently running process (or 32-bit or 64-bit process).</span></span>
- <span data-ttu-id="4b061-137">如果設定了一個以上的變數，則會優先使用位特定變數。</span><span class="sxs-lookup"><span data-stu-id="4b061-137">If more than one variable is set, the bitness-specific variables take precedence.</span></span> <span data-ttu-id="4b061-138">它們會指定要載入的 profiler 位。</span><span class="sxs-lookup"><span data-stu-id="4b061-138">They specify which bitness of profiler to load.</span></span>
- <span data-ttu-id="4b061-139">如需詳細資訊，請參閱[尋找 profiler 程式庫](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md)。</span><span class="sxs-lookup"><span data-stu-id="4b061-139">For more information, see [Finding the profiler library](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span></span>

| | <span data-ttu-id="4b061-140">設定名稱</span><span class="sxs-lookup"><span data-stu-id="4b061-140">Setting name</span></span> | <span data-ttu-id="4b061-141">值</span><span class="sxs-lookup"><span data-stu-id="4b061-141">Values</span></span> |
| - | - | - |
| <span data-ttu-id="4b061-142">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="4b061-142">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH` | <span data-ttu-id="4b061-143">*字串-路徑*</span><span class="sxs-lookup"><span data-stu-id="4b061-143">*string-path*</span></span> |
| <span data-ttu-id="4b061-144">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="4b061-144">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_32` | <span data-ttu-id="4b061-145">*字串-路徑*</span><span class="sxs-lookup"><span data-stu-id="4b061-145">*string-path*</span></span> |
| <span data-ttu-id="4b061-146">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="4b061-146">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_64` | <span data-ttu-id="4b061-147">*字串-路徑*</span><span class="sxs-lookup"><span data-stu-id="4b061-147">*string-path*</span></span> |

## <a name="write-perf-map"></a><span data-ttu-id="4b061-148">撰寫 perf map</span><span class="sxs-lookup"><span data-stu-id="4b061-148">Write perf map</span></span>

- <span data-ttu-id="4b061-149">在 Linux 系統上啟用或停用寫入 */tmp/perf-$pid。*</span><span class="sxs-lookup"><span data-stu-id="4b061-149">Enables or disables writing */tmp/perf-$pid.map* on Linux systems.</span></span>
- <span data-ttu-id="4b061-150">預設：停用（`0`）。</span><span class="sxs-lookup"><span data-stu-id="4b061-150">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="4b061-151">設定名稱</span><span class="sxs-lookup"><span data-stu-id="4b061-151">Setting name</span></span> | <span data-ttu-id="4b061-152">值</span><span class="sxs-lookup"><span data-stu-id="4b061-152">Values</span></span> |
| - | - | - |
| <span data-ttu-id="4b061-153">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="4b061-153">**runtimeconfig.json**</span></span> | <span data-ttu-id="4b061-154">N/A</span><span class="sxs-lookup"><span data-stu-id="4b061-154">N/A</span></span> | <span data-ttu-id="4b061-155">N/A</span><span class="sxs-lookup"><span data-stu-id="4b061-155">N/A</span></span> |
| <span data-ttu-id="4b061-156">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="4b061-156">**Environment variable**</span></span> | `COMPlus_PerfMapEnabled` | <span data-ttu-id="4b061-157">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="4b061-157">`0` - disabled</span></span><br/><span data-ttu-id="4b061-158">已啟用 `1`</span><span class="sxs-lookup"><span data-stu-id="4b061-158">`1` - enabled</span></span> |

## <a name="perf-log-markers"></a><span data-ttu-id="4b061-159">效能記錄檔標記</span><span class="sxs-lookup"><span data-stu-id="4b061-159">Perf log markers</span></span>

- <span data-ttu-id="4b061-160">當 `COMPlus_PerfMapEnabled` 設定為 `1`時，會啟用或停用指定的信號，以作為效能記錄檔中的標記接受並予以忽略。</span><span class="sxs-lookup"><span data-stu-id="4b061-160">When `COMPlus_PerfMapEnabled` is set to `1`, enables or disables the specified signal to be accepted and ignored as a marker in the perf logs.</span></span>
- <span data-ttu-id="4b061-161">預設：停用（`0`）。</span><span class="sxs-lookup"><span data-stu-id="4b061-161">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="4b061-162">設定名稱</span><span class="sxs-lookup"><span data-stu-id="4b061-162">Setting name</span></span> | <span data-ttu-id="4b061-163">值</span><span class="sxs-lookup"><span data-stu-id="4b061-163">Values</span></span> |
| - | - | - |
| <span data-ttu-id="4b061-164">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="4b061-164">**runtimeconfig.json**</span></span> | <span data-ttu-id="4b061-165">N/A</span><span class="sxs-lookup"><span data-stu-id="4b061-165">N/A</span></span> | <span data-ttu-id="4b061-166">N/A</span><span class="sxs-lookup"><span data-stu-id="4b061-166">N/A</span></span> |
| <span data-ttu-id="4b061-167">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="4b061-167">**Environment variable**</span></span> | `COMPlus_PerfMapIgnoreSignal` | <span data-ttu-id="4b061-168">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="4b061-168">`0` - disabled</span></span><br/><span data-ttu-id="4b061-169">已啟用 `1`</span><span class="sxs-lookup"><span data-stu-id="4b061-169">`1` - enabled</span></span> |
