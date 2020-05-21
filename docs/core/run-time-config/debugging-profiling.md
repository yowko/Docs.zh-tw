---
title: 分析設定檔設定
description: 瞭解設定 .NET Core 應用程式之偵測和分析的執行時間設定。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 5efd0f776da4b7ce6ff7f3bdfda24feec6e00f79
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761989"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a><span data-ttu-id="1d988-103">用於進行偵錯工具和分析的執行時間設定選項</span><span class="sxs-lookup"><span data-stu-id="1d988-103">Run-time configuration options for debugging and profiling</span></span>

## <a name="enable-diagnostics"></a><span data-ttu-id="1d988-104">啟用診斷</span><span class="sxs-lookup"><span data-stu-id="1d988-104">Enable diagnostics</span></span>

- <span data-ttu-id="1d988-105">設定是否啟用或停用偵錯工具、分析工具和 EventPipe 診斷。</span><span class="sxs-lookup"><span data-stu-id="1d988-105">Configures whether the debugger, the profiler, and EventPipe diagnostics are enabled or disabled.</span></span>
- <span data-ttu-id="1d988-106">如果您省略此設定，就會啟用診斷。</span><span class="sxs-lookup"><span data-stu-id="1d988-106">If you omit this setting, diagnostics are enabled.</span></span> <span data-ttu-id="1d988-107">這相當於將值設定為 `1` 。</span><span class="sxs-lookup"><span data-stu-id="1d988-107">This is equivalent to setting the value to `1`.</span></span>

| | <span data-ttu-id="1d988-108">設定名稱</span><span class="sxs-lookup"><span data-stu-id="1d988-108">Setting name</span></span> | <span data-ttu-id="1d988-109">值</span><span class="sxs-lookup"><span data-stu-id="1d988-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="1d988-110">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="1d988-110">**runtimeconfig.json**</span></span> | <span data-ttu-id="1d988-111">N/A</span><span class="sxs-lookup"><span data-stu-id="1d988-111">N/A</span></span> | <span data-ttu-id="1d988-112">N/A</span><span class="sxs-lookup"><span data-stu-id="1d988-112">N/A</span></span> |
| <span data-ttu-id="1d988-113">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="1d988-113">**Environment variable**</span></span> | `COMPlus_EnableDiagnostics` | <span data-ttu-id="1d988-114">`1`-已啟用</span><span class="sxs-lookup"><span data-stu-id="1d988-114">`1` - enabled</span></span><br/><span data-ttu-id="1d988-115">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="1d988-115">`0` - disabled</span></span> |

## <a name="enable-profiling"></a><span data-ttu-id="1d988-116">啟用分析</span><span class="sxs-lookup"><span data-stu-id="1d988-116">Enable profiling</span></span>

- <span data-ttu-id="1d988-117">設定是否針對目前正在執行的進程啟用分析。</span><span class="sxs-lookup"><span data-stu-id="1d988-117">Configures whether profiling is enabled for the currently running process.</span></span>
- <span data-ttu-id="1d988-118">如果您省略此設定，就會停用分析。</span><span class="sxs-lookup"><span data-stu-id="1d988-118">If you omit this setting, profiling is disabled.</span></span> <span data-ttu-id="1d988-119">這相當於將值設定為 `0` 。</span><span class="sxs-lookup"><span data-stu-id="1d988-119">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="1d988-120">設定名稱</span><span class="sxs-lookup"><span data-stu-id="1d988-120">Setting name</span></span> | <span data-ttu-id="1d988-121">值</span><span class="sxs-lookup"><span data-stu-id="1d988-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="1d988-122">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="1d988-122">**runtimeconfig.json**</span></span> | <span data-ttu-id="1d988-123">N/A</span><span class="sxs-lookup"><span data-stu-id="1d988-123">N/A</span></span> | <span data-ttu-id="1d988-124">N/A</span><span class="sxs-lookup"><span data-stu-id="1d988-124">N/A</span></span> |
| <span data-ttu-id="1d988-125">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="1d988-125">**Environment variable**</span></span> | `CORECLR_ENABLE_PROFILING` | <span data-ttu-id="1d988-126">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="1d988-126">`0` - disabled</span></span><br/><span data-ttu-id="1d988-127">`1`-已啟用</span><span class="sxs-lookup"><span data-stu-id="1d988-127">`1` - enabled</span></span> |

## <a name="profiler-guid"></a><span data-ttu-id="1d988-128">Profiler GUID</span><span class="sxs-lookup"><span data-stu-id="1d988-128">Profiler GUID</span></span>

- <span data-ttu-id="1d988-129">指定要載入目前正在執行之進程中的分析工具 GUID。</span><span class="sxs-lookup"><span data-stu-id="1d988-129">Specifies the GUID of the profiler to load into the currently running process.</span></span>

| | <span data-ttu-id="1d988-130">設定名稱</span><span class="sxs-lookup"><span data-stu-id="1d988-130">Setting name</span></span> | <span data-ttu-id="1d988-131">值</span><span class="sxs-lookup"><span data-stu-id="1d988-131">Values</span></span> |
| - | - | - |
| <span data-ttu-id="1d988-132">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="1d988-132">**runtimeconfig.json**</span></span> | <span data-ttu-id="1d988-133">N/A</span><span class="sxs-lookup"><span data-stu-id="1d988-133">N/A</span></span> | <span data-ttu-id="1d988-134">N/A</span><span class="sxs-lookup"><span data-stu-id="1d988-134">N/A</span></span> |
| <span data-ttu-id="1d988-135">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="1d988-135">**Environment variable**</span></span> | `CORECLR_PROFILER` | <span data-ttu-id="1d988-136">*字串-guid*</span><span class="sxs-lookup"><span data-stu-id="1d988-136">*string-guid*</span></span> |

## <a name="profiler-location"></a><span data-ttu-id="1d988-137">Profiler 位置</span><span class="sxs-lookup"><span data-stu-id="1d988-137">Profiler location</span></span>

- <span data-ttu-id="1d988-138">指定要載入目前正在執行之進程（或32位或64位進程）的 profiler DLL 路徑。</span><span class="sxs-lookup"><span data-stu-id="1d988-138">Specifies the path to the profiler DLL to load into the currently running process (or 32-bit or 64-bit process).</span></span>
- <span data-ttu-id="1d988-139">如果設定了一個以上的變數，則會優先使用位特定變數。</span><span class="sxs-lookup"><span data-stu-id="1d988-139">If more than one variable is set, the bitness-specific variables take precedence.</span></span> <span data-ttu-id="1d988-140">它們會指定要載入的 profiler 位。</span><span class="sxs-lookup"><span data-stu-id="1d988-140">They specify which bitness of profiler to load.</span></span>
- <span data-ttu-id="1d988-141">如需詳細資訊，請參閱[尋找 profiler 程式庫](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md)。</span><span class="sxs-lookup"><span data-stu-id="1d988-141">For more information, see [Finding the profiler library](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span></span>

| | <span data-ttu-id="1d988-142">設定名稱</span><span class="sxs-lookup"><span data-stu-id="1d988-142">Setting name</span></span> | <span data-ttu-id="1d988-143">值</span><span class="sxs-lookup"><span data-stu-id="1d988-143">Values</span></span> |
| - | - | - |
| <span data-ttu-id="1d988-144">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="1d988-144">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH` | <span data-ttu-id="1d988-145">*字串-路徑*</span><span class="sxs-lookup"><span data-stu-id="1d988-145">*string-path*</span></span> |
| <span data-ttu-id="1d988-146">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="1d988-146">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_32` | <span data-ttu-id="1d988-147">*字串-路徑*</span><span class="sxs-lookup"><span data-stu-id="1d988-147">*string-path*</span></span> |
| <span data-ttu-id="1d988-148">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="1d988-148">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_64` | <span data-ttu-id="1d988-149">*字串-路徑*</span><span class="sxs-lookup"><span data-stu-id="1d988-149">*string-path*</span></span> |

## <a name="write-perf-map"></a><span data-ttu-id="1d988-150">撰寫 perf map</span><span class="sxs-lookup"><span data-stu-id="1d988-150">Write perf map</span></span>

- <span data-ttu-id="1d988-151">在 Linux 系統上啟用或停用寫入 */tmp/perf-$pid。*</span><span class="sxs-lookup"><span data-stu-id="1d988-151">Enables or disables writing */tmp/perf-$pid.map* on Linux systems.</span></span>
- <span data-ttu-id="1d988-152">如果您省略此設定，則會停用寫入效能對應。</span><span class="sxs-lookup"><span data-stu-id="1d988-152">If you omit this setting, writing the perf map is disabled.</span></span> <span data-ttu-id="1d988-153">這相當於將值設定為 `0` 。</span><span class="sxs-lookup"><span data-stu-id="1d988-153">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="1d988-154">設定名稱</span><span class="sxs-lookup"><span data-stu-id="1d988-154">Setting name</span></span> | <span data-ttu-id="1d988-155">值</span><span class="sxs-lookup"><span data-stu-id="1d988-155">Values</span></span> |
| - | - | - |
| <span data-ttu-id="1d988-156">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="1d988-156">**runtimeconfig.json**</span></span> | <span data-ttu-id="1d988-157">N/A</span><span class="sxs-lookup"><span data-stu-id="1d988-157">N/A</span></span> | <span data-ttu-id="1d988-158">N/A</span><span class="sxs-lookup"><span data-stu-id="1d988-158">N/A</span></span> |
| <span data-ttu-id="1d988-159">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="1d988-159">**Environment variable**</span></span> | `COMPlus_PerfMapEnabled` | <span data-ttu-id="1d988-160">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="1d988-160">`0` - disabled</span></span><br/><span data-ttu-id="1d988-161">`1`-已啟用</span><span class="sxs-lookup"><span data-stu-id="1d988-161">`1` - enabled</span></span> |

## <a name="perf-log-markers"></a><span data-ttu-id="1d988-162">效能記錄檔標記</span><span class="sxs-lookup"><span data-stu-id="1d988-162">Perf log markers</span></span>

- <span data-ttu-id="1d988-163">啟用或停用指定的信號，以作為效能記錄檔中的標記接受並予以忽略。</span><span class="sxs-lookup"><span data-stu-id="1d988-163">Enables or disables the specified signal to be accepted and ignored as a marker in the perf logs.</span></span>
- <span data-ttu-id="1d988-164">如果您省略此設定，則不會忽略指定的信號。</span><span class="sxs-lookup"><span data-stu-id="1d988-164">If you omit this setting, the specified signal is not ignored.</span></span> <span data-ttu-id="1d988-165">這相當於將值設定為 `0` 。</span><span class="sxs-lookup"><span data-stu-id="1d988-165">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="1d988-166">設定名稱</span><span class="sxs-lookup"><span data-stu-id="1d988-166">Setting name</span></span> | <span data-ttu-id="1d988-167">值</span><span class="sxs-lookup"><span data-stu-id="1d988-167">Values</span></span> |
| - | - | - |
| <span data-ttu-id="1d988-168">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="1d988-168">**runtimeconfig.json**</span></span> | <span data-ttu-id="1d988-169">N/A</span><span class="sxs-lookup"><span data-stu-id="1d988-169">N/A</span></span> | <span data-ttu-id="1d988-170">N/A</span><span class="sxs-lookup"><span data-stu-id="1d988-170">N/A</span></span> |
| <span data-ttu-id="1d988-171">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="1d988-171">**Environment variable**</span></span> | `COMPlus_PerfMapIgnoreSignal` | <span data-ttu-id="1d988-172">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="1d988-172">`0` - disabled</span></span><br/><span data-ttu-id="1d988-173">`1`-已啟用</span><span class="sxs-lookup"><span data-stu-id="1d988-173">`1` - enabled</span></span> |

> [!NOTE]
> <span data-ttu-id="1d988-174">如果[COMPlus_PerfMapEnabled](#write-perf-map)省略或設為 `0` （也就是已停用），則會忽略此設定。</span><span class="sxs-lookup"><span data-stu-id="1d988-174">This setting is ignored if [COMPlus_PerfMapEnabled](#write-perf-map) is omitted or set to `0` (that is, disabled).</span></span>
