---
title: Debug Linux 傾印
description: 在本文中，您將瞭解如何收集和分析來自 Linux 環境的傾印。
ms.date: 08/27/2020
ms.openlocfilehash: d62295e165f56e32ef73ab628ca9ebd77a4435d1
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598332"
---
# <a name="debug-linux-dumps"></a><span data-ttu-id="57731-103">Debug Linux 傾印</span><span class="sxs-lookup"><span data-stu-id="57731-103">Debug Linux dumps</span></span>

<span data-ttu-id="57731-104">本文**適用于：✔️** .net CORE 3.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="57731-104">**This article applies to: ✔️** .NET Core 3.0 SDK and later versions</span></span>

## <a name="collect-dumps-on-linux"></a><span data-ttu-id="57731-105">在 Linux 上收集傾印</span><span class="sxs-lookup"><span data-stu-id="57731-105">Collect dumps on Linux</span></span>

<span data-ttu-id="57731-106">在 Linux 上收集傾印的兩個建議方法是 [`dotnet-dump`](dotnet-dump.md) 或 [`createdump`](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) 工具。</span><span class="sxs-lookup"><span data-stu-id="57731-106">The two recommended ways of collecting dumps on Linux are the [`dotnet-dump`](dotnet-dump.md) or [`createdump`](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) tools.</span></span>

### <a name="managed-dumps-with-dotnet-dump"></a><span data-ttu-id="57731-107">受控傾印 `dotnet-dump`</span><span class="sxs-lookup"><span data-stu-id="57731-107">Managed dumps with `dotnet-dump`</span></span>

<span data-ttu-id="57731-108">此 [`dotnet-dump`](dotnet-dump.md) 工具很容易使用，而且沒有任何原生偵錯工具的相依性。</span><span class="sxs-lookup"><span data-stu-id="57731-108">The [`dotnet-dump`](dotnet-dump.md) tool is simple to use, and does not have a dependency on any native debuggers.</span></span> <span data-ttu-id="57731-109">`dotnet-dump` 適用于各種不同的 Linux 平臺 (例如 Alpine 或 ARM32/ARM64) 可能無法使用傳統的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="57731-109">`dotnet-dump` works on a wide variety of Linux platforms (like Alpine or ARM32/ARM64) where traditional debugging tools may not be available.</span></span> <span data-ttu-id="57731-110">不過， `dotnet-dump` 只會取得受管理的狀態，使其無法用於偵測機器碼中的問題。</span><span class="sxs-lookup"><span data-stu-id="57731-110">However, `dotnet-dump` only captures managed state so it can't be used for debugging issues in native code.</span></span> <span data-ttu-id="57731-111">收集的傾印 `dotnet-dump` 會在具有建立傾印之相同作業系統和架構的環境中進行分析。</span><span class="sxs-lookup"><span data-stu-id="57731-111">Dumps collected by `dotnet-dump` are analyzed in an environment with the the same OS and architecture the dump was created on.</span></span> <span data-ttu-id="57731-112">此 [`dotnet-gcdump`](dotnet-gcdump.md) 工具可用來做為替代方案，只會捕捉 GC 堆積資訊，但會產生可在 Windows 上分析的傾印。</span><span class="sxs-lookup"><span data-stu-id="57731-112">The [`dotnet-gcdump`](dotnet-gcdump.md) tool can be used as an alternative that only captures GC heap information but produces dumps that can be analyzed on Windows.</span></span>

### <a name="core-dumps-with-createdump"></a><span data-ttu-id="57731-113">核心傾印 `createdump`</span><span class="sxs-lookup"><span data-stu-id="57731-113">Core dumps with `createdump`</span></span>

<span data-ttu-id="57731-114">建立僅限受控傾印的替代方案 `dotnet-dump` [`createdump`](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) 是在 Linux 上建立核心傾印的建議工具，其中包含原生和受管理的資訊。</span><span class="sxs-lookup"><span data-stu-id="57731-114">Alternative to `dotnet-dump` which creates managed-only dumps, [`createdump`](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) is the recommended tool for creating core dumps on Linux containing both native and managed information.</span></span> <span data-ttu-id="57731-115">其他工具（例如 gdb 或 gcore）也可以用來建立核心傾印，但可能會遺失 managed 偵錯工具所需的狀態，在分析期間導致「未知」類型或函式名稱。</span><span class="sxs-lookup"><span data-stu-id="57731-115">Other tools like gdb or gcore can also be used to create core dumps but may miss state needed for managed debugging, resulting in "UNKNOWN" type or function names during analysis.</span></span>

<span data-ttu-id="57731-116">這些 `createdump` 工具會與 .Net Core 執行時間一起安裝，並可在 libcoreclr.so 的旁邊找到， (通常位於 "/usr/share/dotnet/shared/Microsoft.NETCore.App/[version]" ) 。</span><span class="sxs-lookup"><span data-stu-id="57731-116">The `createdump` tools is installed with the .NET Core runtime and can be found next to libcoreclr.so (typically in "/usr/share/dotnet/shared/Microsoft.NETCore.App/[version]").</span></span> <span data-ttu-id="57731-117">此工具會採用處理序識別碼來收集傾印作為其主要引數，也可以使用選擇性參數來指定要收集的傾印類型 (使用堆積的小型傾印是預設) 。</span><span class="sxs-lookup"><span data-stu-id="57731-117">The tool takes a process ID to collect a dump from as its primary argument and can also take optional parameters specifying what kind of dump to collect (a minidump with heap is the default).</span></span> <span data-ttu-id="57731-118">選項包括：</span><span class="sxs-lookup"><span data-stu-id="57731-118">Options include:</span></span>

- **`<input-filename>`**

  <span data-ttu-id="57731-119">要轉換的輸入追蹤檔案。</span><span class="sxs-lookup"><span data-stu-id="57731-119">Input trace file to be converted.</span></span> <span data-ttu-id="57731-120">預設值為 *nettrace*。</span><span class="sxs-lookup"><span data-stu-id="57731-120">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="57731-121">選項。</span><span class="sxs-lookup"><span data-stu-id="57731-121">Options</span></span>

- **`-f|--name <output-filename>`**

  <span data-ttu-id="57731-122">要寫入傾印的檔案。</span><span class="sxs-lookup"><span data-stu-id="57731-122">The file to write the dump to.</span></span> <span data-ttu-id="57731-123">預設值為 '/tmp/coredump.%p '，其中% p 是目標進程的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="57731-123">Default is '/tmp/coredump.%p' where %p is the process ID of the target process.</span></span>

- **`-n|--normal`**

  <span data-ttu-id="57731-124">建立小型傾印。</span><span class="sxs-lookup"><span data-stu-id="57731-124">Create a minidump.</span></span>

- **`-h|--withheap`**

  <span data-ttu-id="57731-125">使用堆積 (預設) 建立小型傾印。</span><span class="sxs-lookup"><span data-stu-id="57731-125">Create a minidump with heap (default).</span></span>

- **`-t|--triage`**

  <span data-ttu-id="57731-126">建立分級小型傾印。</span><span class="sxs-lookup"><span data-stu-id="57731-126">Create a triage minidump.</span></span>

- **`-u|--full`**

  <span data-ttu-id="57731-127">建立完整的核心轉儲。</span><span class="sxs-lookup"><span data-stu-id="57731-127">Create a full core dump.</span></span>

- **`-d|--diag`**

  <span data-ttu-id="57731-128">啟用診斷訊息。</span><span class="sxs-lookup"><span data-stu-id="57731-128">Enable diagnostic messages.</span></span>

<span data-ttu-id="57731-129">請注意，收集核心傾印需要 `SYS_PTRACE` 功能或 `createdump` 使用 sudo 或 su 來執行。</span><span class="sxs-lookup"><span data-stu-id="57731-129">Note that collecting core dumps requires either the `SYS_PTRACE` capability or that `createdump` be run with sudo or su.</span></span>

## <a name="analyze-dumps-on-linux"></a><span data-ttu-id="57731-130">分析 Linux 上的傾印</span><span class="sxs-lookup"><span data-stu-id="57731-130">Analyze dumps on Linux</span></span>

<span data-ttu-id="57731-131">使用收集的管理傾印和收集的核心傾印，都 `dotnet-dump` `createdump` 可以 `dotnet-dump` 使用命令，利用工具進行分析 `dotnet-dump analyze` 。</span><span class="sxs-lookup"><span data-stu-id="57731-131">Both managed dumps collected with `dotnet-dump` and core dumps collected with `createdump` can be analyzed with the `dotnet-dump` tool using the `dotnet-dump analyze` command.</span></span> <span data-ttu-id="57731-132">需要分析傾印的 `dotnet dump` 環境與用來捕捉傾印的環境具有相同的作業系統和架構。</span><span class="sxs-lookup"><span data-stu-id="57731-132">The `dotnet dump` requires that the environment analyzing the dump has the same OS and architecture as the environment the dump was captured in.</span></span>

<span data-ttu-id="57731-133">或者，您也可以使用 [LLDB](https://lldb.llvm.org/) 來分析 Linux 上的核心傾印，以允許分析 managed 和原生框架。</span><span class="sxs-lookup"><span data-stu-id="57731-133">Alternatively, [LLDB](https://lldb.llvm.org/) can be used to analyze core dumps on Linux, which allows analysis of both managed and native frames.</span></span> <span data-ttu-id="57731-134">LLDB 使用 SOS 擴充功能來進行 managed 程式碼的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="57731-134">LLDB uses the SOS extension to debug managed code.</span></span> <span data-ttu-id="57731-135">您 [`dotnet-sos`](dotnet-sos.md) 可以使用 CLI 工具來安裝包含 [許多實用命令](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) 的 SOS，以進行 managed 程式碼的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="57731-135">The [`dotnet-sos`](dotnet-sos.md) CLI tool can be used to install SOS which has [many useful commands](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) for debugging managed code.</span></span> <span data-ttu-id="57731-136">為了分析 .NET Core 傾印，LLDB 和 SOS 需要下列 .NET Core 二進位檔，其來自于建立傾印的環境：</span><span class="sxs-lookup"><span data-stu-id="57731-136">In order to analyze .NET Core dumps, LLDB and SOS require the following .NET Core binaries from the environment the dump was created in:</span></span>

1. <span data-ttu-id="57731-137">libmscordaccore.so</span><span class="sxs-lookup"><span data-stu-id="57731-137">libmscordaccore.so</span></span>
2. <span data-ttu-id="57731-138">libcoreclr.so</span><span class="sxs-lookup"><span data-stu-id="57731-138">libcoreclr.so</span></span>
3. <span data-ttu-id="57731-139">dotnet (用來啟動應用程式的主機) </span><span class="sxs-lookup"><span data-stu-id="57731-139">dotnet (the host used to launch the app)</span></span>

<span data-ttu-id="57731-140">在大部分的情況下，可以使用工具來下載這些二進位檔 [`dotnet-symbol`](dotnet-symbol.md) 。</span><span class="sxs-lookup"><span data-stu-id="57731-140">In most cases, these binaries can be downloaded using the [`dotnet-symbol`](dotnet-symbol.md) tool.</span></span> <span data-ttu-id="57731-141">如果無法下載所需的二進位檔， `dotnet-symbol` (例如，如果從來源建立的 .Net Core 私用版本是使用中的) ，則可能需要從建立傾印的環境複製上方列出的檔案。</span><span class="sxs-lookup"><span data-stu-id="57731-141">If the necessary binaries can't be downloaded with `dotnet-symbol` (for example, if a private version of .NET Core built from source was in use), it may be necessary to copy the files listed above from the environment the dump was created in.</span></span> <span data-ttu-id="57731-142">如果檔案不在傾印檔案的旁邊，您可以使用 LLDB/SOS 命令設定要 `setclrpath <path>` 從中載入的路徑，以及 `setsymbolserver -directory <path>` 設定要在符號檔中尋找的路徑。</span><span class="sxs-lookup"><span data-stu-id="57731-142">If the files aren't located next to the dump file, you can use the LLDB/SOS command `setclrpath <path>` to set the path they should be loaded from and `setsymbolserver -directory <path>` to set the path to look in for symbol files.</span></span>

<span data-ttu-id="57731-143">一旦有必要的檔案可供使用，就可以藉由將 dotnet 主機指定為要進行偵錯工具的可執行檔，在 LLDB 中載入傾印：</span><span class="sxs-lookup"><span data-stu-id="57731-143">Once the necessary files are available, the dump can be loaded in LLDB by specifying the dotnet host as the executable to debug:</span></span>

```console
lldb --core <dump-file> <host-program>
```

<span data-ttu-id="57731-144">在上述命令列中， `<dump-file>` 是要分析的傾印路徑，而 `<host-program>` 是啟動 .net Core 應用程式的原生程式。</span><span class="sxs-lookup"><span data-stu-id="57731-144">In the above command line, `<dump-file>` is the path of the dump to analyze and `<host-program>` is the native program that started the .NET Core application.</span></span> <span data-ttu-id="57731-145">`dotnet`除非應用程式是獨立的，否則這通常是二進位檔，在此情況下，它是沒有 dll 副檔名的應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="57731-145">This is typically the `dotnet` binary unless the app is self-contained, in which case it is the name of the application without the dll extension.</span></span>

<span data-ttu-id="57731-146">開始 LLDB 之後，您可能必須使用 `setsymbolserver` 命令來指向正確的符號位置， (`setsymbolserver -ms` 使用 Microsoft 的符號伺服器或 `setsymbolserver -directory <path>` 指定本機路徑) 。</span><span class="sxs-lookup"><span data-stu-id="57731-146">Once LLDB starts, it may be necessary to use the `setsymbolserver` command to point at the correct symbol location (`setsymbolserver -ms` to use Microsoft's symbol server or `setsymbolserver -directory <path>` to specify a local path).</span></span> <span data-ttu-id="57731-147">您可以藉由執行來載入原生符號 `loadsymbols` 。</span><span class="sxs-lookup"><span data-stu-id="57731-147">Native symbols can be loaded by running `loadsymbols`.</span></span> <span data-ttu-id="57731-148">此時，可以使用 [SOS 命令](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) 來分析傾印。</span><span class="sxs-lookup"><span data-stu-id="57731-148">At this point, [SOS commands](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) can be used to analyze the dump.</span></span>

## <a name="see-also"></a><span data-ttu-id="57731-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57731-149">See also</span></span>

- <span data-ttu-id="57731-150">[dotnet-sos](dotnet-sos.md) ，以取得安裝 sos 擴充功能的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="57731-150">[dotnet-sos](dotnet-sos.md) for more details on installing the SOS extension.</span></span>
- <span data-ttu-id="57731-151">[dotnet-符號](dotnet-symbol.md) ，以取得安裝和使用符號下載工具的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="57731-151">[dotnet-symbol](dotnet-symbol.md) for more details on installing and using the symbol download tool.</span></span>
- <span data-ttu-id="57731-152">[.Net Core 診斷](https://github.com/dotnet/diagnostics/blob/master/documentation/) 存放庫，以取得更多有關偵錯工具的詳細資料，包括有用的常見問題。</span><span class="sxs-lookup"><span data-stu-id="57731-152">[.NET Core diagnostics repo](https://github.com/dotnet/diagnostics/blob/master/documentation/) for more details on debugging, including a useful FAQ.</span></span>
- <span data-ttu-id="57731-153">[安裝 LLDB](https://github.com/dotnet/diagnostics/blob/master/documentation/sos.md#getting-lldb) 以取得在 Linux 或 Mac 上安裝 LLDB 的指示。</span><span class="sxs-lookup"><span data-stu-id="57731-153">[Installing LLDB](https://github.com/dotnet/diagnostics/blob/master/documentation/sos.md#getting-lldb) for instructions on installing LLDB on Linux or Mac.</span></span>
