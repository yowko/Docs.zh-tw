---
title: 在容器中收集診斷
description: 在本文中，您將瞭解如何在 Docker 容器中使用 .NET Core 診斷工具。
ms.date: 09/01/2020
ms.openlocfilehash: cf4bbdf75e943f093a2202f91303a2eea7125487
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94916205"
---
# <a name="collect-diagnostics-in-containers"></a><span data-ttu-id="a6c98-103">在容器中收集診斷</span><span class="sxs-lookup"><span data-stu-id="a6c98-103">Collect diagnostics in containers</span></span>

<span data-ttu-id="a6c98-104">相同的診斷工具對於診斷其他案例中的 .NET Core 問題也適用于 Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="a6c98-104">The same diagnostics tools that are useful for diagnosing .NET Core issues in other scenarios also work in Docker containers.</span></span> <span data-ttu-id="a6c98-105">不過，有些工具需要特殊的步驟才能在容器中工作。</span><span class="sxs-lookup"><span data-stu-id="a6c98-105">However, some of the tools require special steps to work in a container.</span></span> <span data-ttu-id="a6c98-106">本文涵蓋收集效能追蹤和收集傾印的工具，可用於 Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="a6c98-106">This article covers how tools for gathering performance traces and collecting dumps can be used in Docker containers.</span></span>

## <a name="using-net-core-cli-tools-in-a-container"></a><span data-ttu-id="a6c98-107">在容器中使用 .NET Core CLI 工具</span><span class="sxs-lookup"><span data-stu-id="a6c98-107">Using .NET Core CLI tools in a container</span></span>

<span data-ttu-id="a6c98-108">**這些工具適用于：✔️** .net CORE 3.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="a6c98-108">**These tools apply to: ✔️** .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="a6c98-109">.Net Core 全域 CLI 診斷工具 ([`dotnet-counters`](dotnet-counters.md) 、、 [`dotnet-dump`](dotnet-dump.md) [`dotnet-gcdump`](dotnet-gcdump.md) 和 [`dotnet-trace`](dotnet-trace.md)) 設計成可在各種不同的環境中運作，而且應該全都直接在 Docker 容器中工作。</span><span class="sxs-lookup"><span data-stu-id="a6c98-109">The .NET Core global CLI diagnostic tools ([`dotnet-counters`](dotnet-counters.md), [`dotnet-dump`](dotnet-dump.md), [`dotnet-gcdump`](dotnet-gcdump.md), and [`dotnet-trace`](dotnet-trace.md)) are designed to work in a wide variety of environments and should all work directly in Docker containers.</span></span> <span data-ttu-id="a6c98-110">因此，在容器中) 的情況下，這些工具是收集以 .NET Core 3.0 或更新版本為目標之 .NET Core 案例的診斷資訊的慣用方法 (或3.1 或更新版本 `dotnet-gcdump` 。</span><span class="sxs-lookup"><span data-stu-id="a6c98-110">Because of this, these tools are the preferred method of collecting diagnostic information for .NET Core scenarios targeting .NET Core 3.0 or above (or 3.1 or above in the case of `dotnet-gcdump`) in containers.</span></span>

<span data-ttu-id="a6c98-111">在容器中使用這些工具時，唯一的最複雜的因素是它們會隨 .NET Core SDK 一起安裝，而許多 Docker 容器則會在沒有 .NET Core SDK 存在的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="a6c98-111">The only complicating factor of using these tools in a container is that they are installed with the .NET Core SDK and many Docker containers run without the .NET Core SDK present.</span></span> <span data-ttu-id="a6c98-112">解決此問題的一個簡單解決方案是在初始 Docker 映射中安裝這些工具。</span><span class="sxs-lookup"><span data-stu-id="a6c98-112">One easy solution to this problem is to install the tools in the initial Docker image.</span></span> <span data-ttu-id="a6c98-113">這些工具不需要執行 .NET Core SDK，只能進行安裝。</span><span class="sxs-lookup"><span data-stu-id="a6c98-113">The tools don't need the .NET Core SDK to run, only to be installed.</span></span> <span data-ttu-id="a6c98-114">因此，您可以建立具有 [多階段組建](https://docs.docker.com/develop/develop-images/multistage-build/) 的 Dockerfile，以將工具安裝在組建階段 (其中 .NET Core SDK 存在) 然後將二進位檔複製到最後的映射。</span><span class="sxs-lookup"><span data-stu-id="a6c98-114">Therefore, it's possible to create a Dockerfile with a [multi-stage build](https://docs.docker.com/develop/develop-images/multistage-build/) that installs the tools in a build stage (where the .NET Core SDK is present) and then copies the binaries into the final image.</span></span> <span data-ttu-id="a6c98-115">這種方法的唯一缺點是 Docker 映射大小的增加。</span><span class="sxs-lookup"><span data-stu-id="a6c98-115">The only downside to this approach is increased Docker image size.</span></span>

```dockerfile
# In build stage
# Install desired .NET CLI diagnostics tools
RUN dotnet tool install --tool-path /tools dotnet-trace
RUN dotnet tool install --tool-path /tools dotnet-counters
RUN dotnet tool install --tool-path /tools dotnet-dump

...

# In final stage
# Copy diagnostics tools
WORKDIR /tools
COPY --from=build /tools .
```

<span data-ttu-id="a6c98-116">或者，您也可以視需要在容器中安裝 .NET Core SDK，以便安裝 CLI 工具。</span><span class="sxs-lookup"><span data-stu-id="a6c98-116">Alternatively, the .NET Core SDK can be installed in a container when needed in order to install the CLI tools.</span></span> <span data-ttu-id="a6c98-117">請注意，安裝 .NET Core SDK 將會影響重新安裝 .NET Core 執行時間的副作用。</span><span class="sxs-lookup"><span data-stu-id="a6c98-117">Be aware that installing the .NET Core SDK will have the side-effect of reinstalling the .NET Core runtime.</span></span> <span data-ttu-id="a6c98-118">因此，請務必安裝符合容器中存在之執行時間的 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="a6c98-118">So be sure to install the version of the SDK that matches the runtime present in the container.</span></span>

### <a name="using-net-core-global-cli-tools-in-a-sidecar-container"></a><span data-ttu-id="a6c98-119">在側車容器中使用 .NET Core 全域 CLI 工具</span><span class="sxs-lookup"><span data-stu-id="a6c98-119">Using .NET Core global CLI tools in a sidecar container</span></span>

<span data-ttu-id="a6c98-120">如果您想要使用 .NET Core 全域 CLI 診斷工具來診斷不同容器中的進程，請記住下列其他需求：</span><span class="sxs-lookup"><span data-stu-id="a6c98-120">If you would like to use .NET Core global CLI diagnostic tools to diagnose processes in a different container, bear the following additional requirements in mind:</span></span>

1. <span data-ttu-id="a6c98-121">容器必須 [共用進程命名空間](https://docs.docker.com/engine/reference/run/#pid-settings---pid) (以便側車容器中的工具可以存取目標容器) 中的進程。</span><span class="sxs-lookup"><span data-stu-id="a6c98-121">The containers must [share a process namespace](https://docs.docker.com/engine/reference/run/#pid-settings---pid) (so that tools in the sidecar container can access processes in the target container).</span></span>
2. <span data-ttu-id="a6c98-122">.NET Core 全域 CLI 診斷工具需要存取 .NET Core 執行時間寫入/tmp 目錄的檔案，因此必須透過磁片區掛接，在目標和側車容器之間共用/tmp 目錄。</span><span class="sxs-lookup"><span data-stu-id="a6c98-122">The .NET Core global CLI diagnostic tools need access to files the .NET Core runtime writes to the /tmp directory, so the /tmp directory must be shared between the target and sidecar container via a volume mount.</span></span> <span data-ttu-id="a6c98-123">例如，藉由讓容器共用一般 [磁片](https://docs.docker.com/storage/volumes/#create-and-manage-volumes) 區或 Kubernetes [emptyDir](https://kubernetes.io/docs/concepts/storage/volumes/#emptydir) 磁片區，即可完成這項操作。</span><span class="sxs-lookup"><span data-stu-id="a6c98-123">This could be done, for example, by having the containers share a common [volume](https://docs.docker.com/storage/volumes/#create-and-manage-volumes) or a Kubernetes [emptyDir](https://kubernetes.io/docs/concepts/storage/volumes/#emptydir) volume.</span></span> <span data-ttu-id="a6c98-124">如果您嘗試在不共用/tmp 目錄的情況下，從側車容器使用診斷工具，您將會收到有關「未執行相容的 .NET 執行時間」處理常式的錯誤。</span><span class="sxs-lookup"><span data-stu-id="a6c98-124">If you attempt to use the diagnostic tools from a sidecar container without sharing the /tmp directory, you will get an error about the process "not running compatible .NET runtime."</span></span>

## <a name="using-perfcollect-in-a-container"></a><span data-ttu-id="a6c98-125">`PerfCollect`在容器中使用</span><span class="sxs-lookup"><span data-stu-id="a6c98-125">Using `PerfCollect` in a container</span></span>

<span data-ttu-id="a6c98-126">**此工具適用于：✔️** .net Core 2.1 和更新版本</span><span class="sxs-lookup"><span data-stu-id="a6c98-126">**This tool applies to: ✔️** .NET Core 2.1 and later versions</span></span>

<span data-ttu-id="a6c98-127">[`PerfCollect`](./trace-perfcollect-lttng.md)腳本有助於收集效能追蹤，而且是建議用來在 .Net Core 3.0 之前收集追蹤的工具。</span><span class="sxs-lookup"><span data-stu-id="a6c98-127">The [`PerfCollect`](./trace-perfcollect-lttng.md) script is useful for collecting performance traces and is the recommended tool for collecting traces prior to .NET Core 3.0.</span></span> <span data-ttu-id="a6c98-128">如果 `PerfCollect` 在容器中使用，請記住下列需求：</span><span class="sxs-lookup"><span data-stu-id="a6c98-128">If using `PerfCollect` in a container, keep the following requirements in mind:</span></span>

1. <span data-ttu-id="a6c98-129">`PerfCollect`需要 ([ `SYS_ADMIN` 功能](https://man7.org/linux/man-pages/man7/capabilities.7.html)才能執行 `perf` 工具) ，因此請確定容器是[以該功能啟動](https://docs.docker.com/engine/reference/run/#runtime-privilege-and-linux-capabilities)。</span><span class="sxs-lookup"><span data-stu-id="a6c98-129">`PerfCollect` requires the [`SYS_ADMIN` capability](https://man7.org/linux/man-pages/man7/capabilities.7.html) (in order to run the `perf` tool), so be sure the container is [started with that capability](https://docs.docker.com/engine/reference/run/#runtime-privilege-and-linux-capabilities).</span></span>
2. <span data-ttu-id="a6c98-130">`PerfCollect` 需要先設定某些環境變數，才能開始進行程式碼剖析。</span><span class="sxs-lookup"><span data-stu-id="a6c98-130">`PerfCollect` requires some environment variables be set prior to the app it is profiling starting.</span></span> <span data-ttu-id="a6c98-131">這些可以在 [Dockerfile](https://docs.docker.com/engine/reference/builder/#env) 中或在 [啟動容器](https://docs.docker.com/engine/reference/run/#env-environment-variables)時設定。</span><span class="sxs-lookup"><span data-stu-id="a6c98-131">These can be set either in a [Dockerfile](https://docs.docker.com/engine/reference/builder/#env) or when [starting the container](https://docs.docker.com/engine/reference/run/#env-environment-variables).</span></span> <span data-ttu-id="a6c98-132">因為這些變數不應該在一般生產環境中設定，所以在啟動將會進行分析的容器時，通常只需新增這些變數。</span><span class="sxs-lookup"><span data-stu-id="a6c98-132">Because these variables shouldn't be set in normal production environments, it's common to just add them when starting a container that will be profiled.</span></span> <span data-ttu-id="a6c98-133">PerfCollect 所需的兩個變數如下：</span><span class="sxs-lookup"><span data-stu-id="a6c98-133">The two variables which PerfCollect requires are:</span></span>
    1. <span data-ttu-id="a6c98-134">COMPlus_PerfMapEnabled = 1</span><span class="sxs-lookup"><span data-stu-id="a6c98-134">COMPlus_PerfMapEnabled=1</span></span>
    1. <span data-ttu-id="a6c98-135">COMPlus_EnableEventLog = 1</span><span class="sxs-lookup"><span data-stu-id="a6c98-135">COMPlus_EnableEventLog=1</span></span>

### <a name="using-perfcollect-in-a-sidecar-container"></a><span data-ttu-id="a6c98-136">`PerfCollect`在側車容器中使用</span><span class="sxs-lookup"><span data-stu-id="a6c98-136">Using `PerfCollect` in a sidecar container</span></span>

<span data-ttu-id="a6c98-137">如果您想要 `PerfCollect` 在一個容器中執行，以分析不同容器中的 .Net Core 進程，除了這些差異之外，此體驗幾乎相同：</span><span class="sxs-lookup"><span data-stu-id="a6c98-137">If you would like to run `PerfCollect` in one container to profile a .NET Core process in a different container, the experience is almost the same except for these differences:</span></span>

1. <span data-ttu-id="a6c98-138">先前所述的環境變數 (COMPlus_PerfMapEnabled 和 COMPlus_EnableEventLog) 必須針對目標容器設定， (不是執行中 `PerfCollect`) 的容器。</span><span class="sxs-lookup"><span data-stu-id="a6c98-138">The environment variables mentioned previously (COMPlus_PerfMapEnabled and COMPlus_EnableEventLog) must be set for the target container (not the one running `PerfCollect`).</span></span>
2. <span data-ttu-id="a6c98-139">執行的容器 `PerfCollect` 必須有 `SYS_ADMIN` (並非目標容器) 的功能。</span><span class="sxs-lookup"><span data-stu-id="a6c98-139">The container running `PerfCollect` must have the `SYS_ADMIN` capability (not the target container).</span></span>
3. <span data-ttu-id="a6c98-140">這兩個容器必須 [共用進程命名空間](https://docs.docker.com/engine/reference/run/#pid-settings---pid)。</span><span class="sxs-lookup"><span data-stu-id="a6c98-140">The two containers must [share a process namespace](https://docs.docker.com/engine/reference/run/#pid-settings---pid).</span></span>

## <a name="using-createdump-in-a-container"></a><span data-ttu-id="a6c98-141">`createdump`在容器中使用</span><span class="sxs-lookup"><span data-stu-id="a6c98-141">Using `createdump` in a container</span></span>

<span data-ttu-id="a6c98-142">**此工具適用于：✔️** .net Core 2.1 和更新版本</span><span class="sxs-lookup"><span data-stu-id="a6c98-142">**This tool applies to: ✔️** .NET Core 2.1 and later versions</span></span>

<span data-ttu-id="a6c98-143">的替代方案 `dotnet-dump` [`createdump`](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) 可以用來在 Linux 上建立核心傾印，同時包含原生和受控資訊。</span><span class="sxs-lookup"><span data-stu-id="a6c98-143">An alternative to `dotnet-dump`, [`createdump`](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) can be used for creating core dumps on Linux containing both native and managed information.</span></span> <span data-ttu-id="a6c98-144">此 `createdump` 工具會與 .Net Core 執行時間一起安裝，並可在 libcoreclr.so 的旁邊找到， (通常位於 "/usr/share/dotnet/shared/Microsoft.NETCore.App/[version]" ) 。</span><span class="sxs-lookup"><span data-stu-id="a6c98-144">The `createdump` tool is installed with the .NET Core runtime and can be found next to libcoreclr.so (typically in "/usr/share/dotnet/shared/Microsoft.NETCore.App/[version]").</span></span> <span data-ttu-id="a6c98-145">此工具在容器中的運作方式與在非容器化 Linux 環境中的運作方式相同，唯一的例外是工具需要此[ `SYS_PTRACE` 功能](https://man7.org/linux/man-pages/man7/capabilities.7.html)，因此必須以[該功能啟動](https://docs.docker.com/engine/reference/run/#runtime-privilege-and-linux-capabilities)Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="a6c98-145">The tool works the same in a container as it does in non-containerized Linux environments with the single exception that the tool requires the [`SYS_PTRACE` capability](https://man7.org/linux/man-pages/man7/capabilities.7.html), so the Docker container must be [started with that capability](https://docs.docker.com/engine/reference/run/#runtime-privilege-and-linux-capabilities).</span></span>

### <a name="using-createdump-in-a-sidecar-container"></a><span data-ttu-id="a6c98-146">`createdump`在側車容器中使用</span><span class="sxs-lookup"><span data-stu-id="a6c98-146">Using `createdump` in a sidecar container</span></span>

<span data-ttu-id="a6c98-147">如果您想要使用 `createdump` 從不同容器的進程建立傾印，除了下列差異之外，此體驗幾乎相同：</span><span class="sxs-lookup"><span data-stu-id="a6c98-147">If you would like to use `createdump` to create a dump from a process in a different container, the experience is almost the same except for these differences:</span></span>

1. <span data-ttu-id="a6c98-148">執行的容器 `createdump` 必須有 `SYS_PTRACE` (並非目標容器) 的功能。</span><span class="sxs-lookup"><span data-stu-id="a6c98-148">The container running `createdump` must have the `SYS_PTRACE` capability (not the target container).</span></span>
2. <span data-ttu-id="a6c98-149">這兩個容器必須 [共用進程命名空間](https://docs.docker.com/engine/reference/run/#pid-settings---pid)。</span><span class="sxs-lookup"><span data-stu-id="a6c98-149">The two containers must [share a process namespace](https://docs.docker.com/engine/reference/run/#pid-settings---pid).</span></span>
