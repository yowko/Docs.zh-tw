---
title: .NET Core 2.1 的新功能
description: 了解 .NET Core 2.1 所提供的新功能。
author: rpetrusha
ms.author: ronpet
ms.date: 06/06/2018
ms.openlocfilehash: 52fe2d47dbca9bc43c2f1274b0d9e535ba9f9abc
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874568"
---
# <a name="whats-new-in-net-core-21"></a><span data-ttu-id="8c760-103">.NET Core 2.1 的新功能</span><span class="sxs-lookup"><span data-stu-id="8c760-103">What's new in .NET Core 2.1</span></span>

<span data-ttu-id="8c760-104">.NET Core 2.1 包含針對下列區域的增強與新功能：</span><span class="sxs-lookup"><span data-stu-id="8c760-104">.NET Core 2.1 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="8c760-105">工具</span><span class="sxs-lookup"><span data-stu-id="8c760-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="8c760-106">向前復原</span><span class="sxs-lookup"><span data-stu-id="8c760-106">Roll forward</span></span>](#roll-forward)
- [<span data-ttu-id="8c760-107">部署</span><span class="sxs-lookup"><span data-stu-id="8c760-107">Deployment</span></span>](#deployment)
- [<span data-ttu-id="8c760-108">Windows 相容性套件</span><span class="sxs-lookup"><span data-stu-id="8c760-108">Windows Compatibility Pack</span></span>](#windows-compatibility-pack)
- [<span data-ttu-id="8c760-109">JIT 編譯改進功能</span><span class="sxs-lookup"><span data-stu-id="8c760-109">JIT compilation improvements</span></span>](#jit-compiler-improvements)
- [<span data-ttu-id="8c760-110">API 變更</span><span class="sxs-lookup"><span data-stu-id="8c760-110">API changes</span></span>](#api-changes)

## <a name="tooling"></a><span data-ttu-id="8c760-111">Tooling</span><span class="sxs-lookup"><span data-stu-id="8c760-111">Tooling</span></span>

<span data-ttu-id="8c760-112">隨附於 .NET Core 2.1 的工具 .NET Core 2.1 SDK (2.1.300 版) 包含下列變更與增強功能：</span><span class="sxs-lookup"><span data-stu-id="8c760-112">The .NET Core 2.1 SDK (v 2.1.300), the tooling included with .NET Core 2.1, includes the following changes and enhancements:</span></span>

### <a name="build-performance-improvements"></a><span data-ttu-id="8c760-113">建置效能改進</span><span class="sxs-lookup"><span data-stu-id="8c760-113">Build performance improvements</span></span>

<span data-ttu-id="8c760-114">.NET Core 2.1 的主要重點在於改進建置時間效能，特別是針對累加建置。</span><span class="sxs-lookup"><span data-stu-id="8c760-114">A major focus of .NET Core 2.1 is improving build-time performance, particularly for incremental builds.</span></span> <span data-ttu-id="8c760-115">這些效能改進適用於使用 `dotnet build` 的命令列建置和 Visual Studio 中的建置。</span><span class="sxs-lookup"><span data-stu-id="8c760-115">These performance improvements apply to both command-line builds using `dotnet build` and to builds in Visual Studio.</span></span> <span data-ttu-id="8c760-116">改進的一些個別區域包含：</span><span class="sxs-lookup"><span data-stu-id="8c760-116">Some individual areas of improvement include:</span></span>

- <span data-ttu-id="8c760-117">針對套件資產解析，僅解析組建所使用的資產，而非所有資產。</span><span class="sxs-lookup"><span data-stu-id="8c760-117">For package asset resolution, resolving only assets used by a build rather than all assets.</span></span>

- <span data-ttu-id="8c760-118">組件參考的快取。</span><span class="sxs-lookup"><span data-stu-id="8c760-118">Caching of assembly references.</span></span>

- <span data-ttu-id="8c760-119">使用長時間執行的 SDK 組建伺服器，這些是跨越個別 `dotnet build` 引動過程的處理序。</span><span class="sxs-lookup"><span data-stu-id="8c760-119">Use of long-running SDK build servers, which are processes that span across individual `dotnet build` invocations.</span></span> <span data-ttu-id="8c760-120">它們消除了每次執行 `dotnet build` 時，需要以 JIT 編譯大型程式碼區塊的需求。</span><span class="sxs-lookup"><span data-stu-id="8c760-120">They eliminate the need to JIT-compile large blocks of code every time `dotnet build` is run.</span></span> <span data-ttu-id="8c760-121">組建伺服器處理序可使用下列命令自動終止：</span><span class="sxs-lookup"><span data-stu-id="8c760-121">Build server processes can be automatically terminated with the following command:</span></span>

   ```console
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a><span data-ttu-id="8c760-122">新的 CLI 命令</span><span class="sxs-lookup"><span data-stu-id="8c760-122">New CLI commands</span></span>

<span data-ttu-id="8c760-123">先前僅能透過 [`DotnetCliToolReference`](../tools/extensibility.md) 於個別專案上使用的數個工具，現在皆已做為 .NET Core SDK 的一部分提供。</span><span class="sxs-lookup"><span data-stu-id="8c760-123">A number of tools that were available only on a per project basis using [`DotnetCliToolReference`](../tools/extensibility.md) are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="8c760-124">這些工具包括：</span><span class="sxs-lookup"><span data-stu-id="8c760-124">These tools include:</span></span>

- <span data-ttu-id="8c760-125">`dotnet watch` 提供檔案系統監看員，能先等候檔案變更再執行一組指定的命令。</span><span class="sxs-lookup"><span data-stu-id="8c760-125">`dotnet watch` provides a file system watcher that waits for a file to change before executing a designated set of commands.</span></span> <span data-ttu-id="8c760-126">例如，下列命令會自動重建目前的專案，並在其中的檔案發生變更時產生詳細資訊輸出：</span><span class="sxs-lookup"><span data-stu-id="8c760-126">For example, the following command automatically rebuilds the current project and generates verbose output whenever a file in it changes:</span></span>

   ```console
   dotnet watch -- --verbose build
   ```
  
   <span data-ttu-id="8c760-127">請注意到位於 `--verbose` 選項之前的 `--` 選項。</span><span class="sxs-lookup"><span data-stu-id="8c760-127">Note the `--` option that precedes the `--verbose` option.</span></span> <span data-ttu-id="8c760-128">它能將直接傳遞給 `dotnet watch` 命令的選項，與傳遞給子 `dotnet` 處理序的引數分隔開來。</span><span class="sxs-lookup"><span data-stu-id="8c760-128">It delimits the options passed directly to the `dotnet watch` command from the arguments that are passed to the child `dotnet` process.</span></span> <span data-ttu-id="8c760-129">如果沒有它的話，`--verbose` 選項將會套用至 `dotnet watch` 命令，而非 `dotnet build` 命令。</span><span class="sxs-lookup"><span data-stu-id="8c760-129">Without it, the `--verbose` option applies to the `dotnet watch` command, not the `dotnet build` command.</span></span>
  
   <span data-ttu-id="8c760-130">如需詳細資訊，請參閱[使用 dotnet watch 開發 ASP.NET Core 應用程式](/aspnet/core/tutorials/dotnet-watch)</span><span class="sxs-lookup"><span data-stu-id="8c760-130">For more information, see [Develop ASP.NET Core apps using dotnet watch](/aspnet/core/tutorials/dotnet-watch)</span></span>

- <span data-ttu-id="8c760-131">`dotnet dev-certs` 能產生和管理在開發 ASP.NET Core 應用程式期間使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="8c760-131">`dotnet dev-certs` generates and manages certificates used during development in ASP.NET Core applications.</span></span>

- <span data-ttu-id="8c760-132">`dotnet user-secrets` 能管理 ASP.NET Core 中使用者祕密存放區中的祕密。</span><span class="sxs-lookup"><span data-stu-id="8c760-132">`dotnet user-secrets` manages the secrets in a user secret store in ASP.NET Core applications.</span></span>

- <span data-ttu-id="8c760-133">`dotnet sql-cache` 能在 Microsoft SQL Server 資料庫中建立資料表和索引以用於分散式快取。</span><span class="sxs-lookup"><span data-stu-id="8c760-133">`dotnet sql-cache` creates a table and indexes in a Microsoft SQL Server database to be used for distributed caching.</span></span>

- <span data-ttu-id="8c760-134">`dotnet ef` 是用來管理 Entity Framework Core 應用程式中資料庫、<xref:Microsoft.EntityFrameworkCore.DbContext> 物件和移轉作業的工具。</span><span class="sxs-lookup"><span data-stu-id="8c760-134">`dotnet ef` is a tool for managing databases, <xref:Microsoft.EntityFrameworkCore.DbContext> objects, and migrations in Entity Framework Core applications.</span></span> <span data-ttu-id="8c760-135">如需詳細資訊，請參閱 [EF Core .NET 命令列工具](/ef/core/miscellaneous/cli/dotnet)。</span><span class="sxs-lookup"><span data-stu-id="8c760-135">For more information, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

### <a name="global-tools"></a><span data-ttu-id="8c760-136">通用工具</span><span class="sxs-lookup"><span data-stu-id="8c760-136">Global Tools</span></span>

<span data-ttu-id="8c760-137">.NET Core 2.1 支援*通用工具*，亦即從命令列以通用方式提供的自訂工具。</span><span class="sxs-lookup"><span data-stu-id="8c760-137">.NET Core 2.1 supports *Global Tools* -- that is, custom tools that are available globally from the command line.</span></span> <span data-ttu-id="8c760-138">舊版 .NET Core 的擴充性模型，只能透過使用 [`DotnetCliToolReference`](../tools/extensibility.md#consuming-per-project-tools) 來使自訂工具可供每個專案使用。</span><span class="sxs-lookup"><span data-stu-id="8c760-138">The extensibility model in previous versions of .NET Core made custom tools available on a per project basis only by using [`DotnetCliToolReference`](../tools/extensibility.md#consuming-per-project-tools).</span></span>

<span data-ttu-id="8c760-139">若要安裝通用工具，您需使用 [dotnet tool install](..\tools\dotnet-tool-install.md) 命令。</span><span class="sxs-lookup"><span data-stu-id="8c760-139">To install a Global Tool, you use the [dotnet tool install](..\tools\dotnet-tool-install.md) command.</span></span> <span data-ttu-id="8c760-140">例如: </span><span class="sxs-lookup"><span data-stu-id="8c760-140">For example:</span></span>

```console
dotnet tool install -g dotnetsay
```

<span data-ttu-id="8c760-141">安裝之後，您就可在命令列中指定工具名稱來執行該工具。</span><span class="sxs-lookup"><span data-stu-id="8c760-141">Once installed, the tool can be run from the command line by specifying the tool name.</span></span> <span data-ttu-id="8c760-142">如需詳細資訊，請參閱 [.NET Core 通用工具概觀](../tools/global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="8c760-142">For more information, see [.NET Core Global Tools overview](../tools/global-tools.md).</span></span>

### <a name="tool-management-with-the-dotnet-tool-command"></a><span data-ttu-id="8c760-143">使用 `dotnet tool` 命令來管理工具</span><span class="sxs-lookup"><span data-stu-id="8c760-143">Tool management with the `dotnet tool` command</span></span>

<span data-ttu-id="8c760-144">在 .NET Core SDK 2.1 (2.1.300 版) 中，所有工具作業都是使用 `dotnet tool` 命令。</span><span class="sxs-lookup"><span data-stu-id="8c760-144">In .NET Core SDK 2.1 (v 2.1.300), all tools operations use the `dotnet tool` command.</span></span> <span data-ttu-id="8c760-145">有下列選項可供使用：</span><span class="sxs-lookup"><span data-stu-id="8c760-145">The following options are available:</span></span>

- <span data-ttu-id="8c760-146">使用 [`dotnet tool install`](../tools/dotnet-tool-install.md) 來安裝工具。</span><span class="sxs-lookup"><span data-stu-id="8c760-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) to install a tool.</span></span>

- <span data-ttu-id="8c760-147">使用 [`dotnet tool update`](../tools/dotnet-tool-update.md) 來解除安裝並重新安裝工具，這可有效地更新該工具。</span><span class="sxs-lookup"><span data-stu-id="8c760-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) to uninstall and reinstall a tool, which effectively updates it.</span></span>

- <span data-ttu-id="8c760-148">使用 [`dotnet tool list`](../tools/dotnet-tool-list.md) 來列出目前已安裝的工具。</span><span class="sxs-lookup"><span data-stu-id="8c760-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) to list currently installed tools.</span></span>

- <span data-ttu-id="8c760-149">使用 [`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) 來解除安裝目前已安裝的工具。</span><span class="sxs-lookup"><span data-stu-id="8c760-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) to uninstall currently installed tools.</span></span>

## <a name="roll-forward"></a><span data-ttu-id="8c760-150">向前復原</span><span class="sxs-lookup"><span data-stu-id="8c760-150">Roll forward</span></span>

<span data-ttu-id="8c760-151">從 .NET Core 2.0 開始，所有 .NET Core 應用程式都會自動向前復原至系統上安裝的最新*次要版本*。</span><span class="sxs-lookup"><span data-stu-id="8c760-151">All .NET Core applications starting with the .NET Core 2.0 automatically roll forward to the latest *minor version* installed on a system.</span></span> 

<span data-ttu-id="8c760-152">從 .NET Core 2.0 開始，如果用來建置應用程式的 .NET Core 版本不存在於執行階段中，則應用程式會自動針對已安裝的最新 .NET Core *次要版本*執行。</span><span class="sxs-lookup"><span data-stu-id="8c760-152">Starting with .NET Core 2.0, if the version of .NET Core that an application was built with is not present at runtime, the application automatically runs against the latest installed *minor version* of .NET Core.</span></span> <span data-ttu-id="8c760-153">換句話說，如果應用程式是使用 .NET Core 2.0 建置，而主機系統上不存在 .NET Core 2.0，但是有 .NET Core 2.1，則該應用程式會搭配 NET Core 2.1 執行。</span><span class="sxs-lookup"><span data-stu-id="8c760-153">In other words, if an application is built with .NET Core 2.0, and .NET Core 2.0 is not present on the host system but .NET Core 2.1 is, the application runs with .NET Core 2.1.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8c760-154">此向前復原行為不適用於預覽版本。</span><span class="sxs-lookup"><span data-stu-id="8c760-154">This roll-forward behavior doesn't apply to preview releases.</span></span> <span data-ttu-id="8c760-155">也不適用於主要版本。</span><span class="sxs-lookup"><span data-stu-id="8c760-155">Nor does it apply to major releases.</span></span> <span data-ttu-id="8c760-156">例如，.NET Core 1.0 應用程式不會向前復原至 .NET Core 2.0 或 .NET Core 2.1。</span><span class="sxs-lookup"><span data-stu-id="8c760-156">For example, a .NET Core 1.0 application wouldn't roll forward to .NET Core 2.0 or .NET Core 2.1.</span></span>

<span data-ttu-id="8c760-157">您也可以使用下列三種方式的其中一種，來停用次要版本向前復原：</span><span class="sxs-lookup"><span data-stu-id="8c760-157">You can also disable minor version roll forward in any of three ways:</span></span>

- <span data-ttu-id="8c760-158">將 `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` 環境變數設為 0。</span><span class="sxs-lookup"><span data-stu-id="8c760-158">Set the `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` environment variable to 0.</span></span>

- <span data-ttu-id="8c760-159">在 runtimeconfig.json 檔案中新增下列程式碼行：</span><span class="sxs-lookup"><span data-stu-id="8c760-159">Add the following line to the runtimeconfig.json file:</span></span>

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- <span data-ttu-id="8c760-160">使用 [.NET Core CLI 工具](../tools/index.md)時，使用 .NET Core 命令 (例如 `run`) 來包含下列選項：</span><span class="sxs-lookup"><span data-stu-id="8c760-160">When using [.NET Core CLI tools](../tools/index.md), include the following option with a .NET Core command such as `run`:</span></span>

   ```console
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

## <a name="deployment"></a><span data-ttu-id="8c760-161">部署</span><span class="sxs-lookup"><span data-stu-id="8c760-161">Deployment</span></span>

### <a name="self-contained-application-servicing"></a><span data-ttu-id="8c760-162">獨立的應用程式服務</span><span class="sxs-lookup"><span data-stu-id="8c760-162">Self-contained application servicing</span></span>

<span data-ttu-id="8c760-163">`dotnet publish` 現在會搭配服務執行階段版本發佈獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="8c760-163">`dotnet publish` now publishes self-contained applications with a serviced runtime version.</span></span> <span data-ttu-id="8c760-164">當您搭配 .NET Core 2.1 SDK (2.1.300 版) 發佈獨立應用程式時，應用程式就會包含該 SDK 已知的最新服務執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="8c760-164">When you publish a self-contained application with the .NET Core 2.1 SDK (v 2.1.300), your application includes the latest serviced runtime version known by that SDK.</span></span> <span data-ttu-id="8c760-165">當您升級至最新的 SDK 時，將會搭配最新的 .NET Core 執行階段版本一起發佈。</span><span class="sxs-lookup"><span data-stu-id="8c760-165">When you upgrade to the latest SDK, you’ll publish with the latest .NET Core runtime version.</span></span> <span data-ttu-id="8c760-166">這適用於 .NET Core 1.0 執行階段和更新版本。</span><span class="sxs-lookup"><span data-stu-id="8c760-166">This applies for .NET Core 1.0 runtimes and later.</span></span>

<span data-ttu-id="8c760-167">獨立發佈會仰賴 NuGet.org 上的執行階段版本。您的電腦上不需要有服務執行階段。</span><span class="sxs-lookup"><span data-stu-id="8c760-167">Self-contained publishing relies on runtime versions on NuGet.org. You do not need to have the serviced runtime on your machine.</span></span>

<span data-ttu-id="8c760-168">使用 .NET Core 2.0 SDK 時，獨立應用程式會搭配 .NET Core 2.0.0 執行階段一起發佈，除非有透過 `RuntimeFrameworkVersion` 屬性指定其他版本。</span><span class="sxs-lookup"><span data-stu-id="8c760-168">Using the .NET Core 2.0 SDK, self-contained applications are published with the .NET Core 2.0.0 runtime unless a different version is specified via the `RuntimeFrameworkVersion` property.</span></span> <span data-ttu-id="8c760-169">藉由這項新行為，您將不再需要設定此屬性來為獨立應用程式選取較新的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="8c760-169">With this new behavior, you’ll no longer need to set this property to select a higher runtime version for a self-contained application.</span></span> <span data-ttu-id="8c760-170">從現在起，最簡單的方法將會是一律搭配 .NET Core 2.1 SDK (2.1.300 版) 發佈。</span><span class="sxs-lookup"><span data-stu-id="8c760-170">The easiest approach going forward is to always publish with .NET Core 2.1 SDK (v 2.1.300).</span></span>

## <a name="windows-compatibility-pack"></a><span data-ttu-id="8c760-171">Windows 相容性套件</span><span class="sxs-lookup"><span data-stu-id="8c760-171">Windows Compatibility Pack</span></span>

<span data-ttu-id="8c760-172">當您從 .NET Framework 將現有的程式碼移植到 .NET Core 時，可以使用 [Windows 相容性套件](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="8c760-172">When you port existing code from the .NET Framework to .NET Core, you can use the [Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span> <span data-ttu-id="8c760-173">與 .NET Core 所提供 API 相比，它還額外提供超過 20,000 個 API。</span><span class="sxs-lookup"><span data-stu-id="8c760-173">It provides access to 20,000 more APIs than are available in .NET Core.</span></span> <span data-ttu-id="8c760-174">這些 API 包括 <xref:System.Drawing?displayProperty="nameWithType"> 命名空間中的類型、<xref:System.Diagnostics.EventLog> 類別、WMI、效能計數器、Windows 服務，以及Windows 登錄類型和成員。</span><span class="sxs-lookup"><span data-stu-id="8c760-174">These APIs include types in the <xref:System.Drawing?displayProperty="nameWithType"> namespace, the <xref:System.Diagnostics.EventLog> class, WMI, Performance Counters, Windows Services, and the Windows registry types and members.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="8c760-175">JIT 編譯器的改進項目</span><span class="sxs-lookup"><span data-stu-id="8c760-175">JIT compiler improvements</span></span>

<span data-ttu-id="8c760-176">.NET Core 併入新的 JIT 編譯器技術，稱為「階層式編譯」(也稱為「調適型最佳化」)，可大幅地提升效能。</span><span class="sxs-lookup"><span data-stu-id="8c760-176">.NET Core incorporates a new JIT compiler technology called *tiered compilation* (also known as *adaptive optimization*) that can significantly improve performance.</span></span> <span data-ttu-id="8c760-177">階層式編譯是可選擇加入的設定。</span><span class="sxs-lookup"><span data-stu-id="8c760-177">Tiered compilation is an opt-in setting.</span></span>

<span data-ttu-id="8c760-178">由 JIT 編譯器所執行的其中一項重要工作，是將程式碼的執行最佳化。</span><span class="sxs-lookup"><span data-stu-id="8c760-178">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="8c760-179">不過，針對很少使用的程式碼路徑，編譯器將程式碼最佳化的時間，可能會比執行階段執行未最佳化程式碼的時間還要久。</span><span class="sxs-lookup"><span data-stu-id="8c760-179">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends running unoptimized code.</span></span> <span data-ttu-id="8c760-180">階層式編譯會在 JIT 編譯中引入兩個階段：</span><span class="sxs-lookup"><span data-stu-id="8c760-180">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="8c760-181">**第一層**：盡快產生程式碼。</span><span class="sxs-lookup"><span data-stu-id="8c760-181">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="8c760-182">**第二層**：針對那些經常執行的方法產生最佳化的程式碼。</span><span class="sxs-lookup"><span data-stu-id="8c760-182">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="8c760-183">編譯的第二層會以平行方式執行以增強效能。</span><span class="sxs-lookup"><span data-stu-id="8c760-183">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="8c760-184">您能以兩種方式選擇加入階層式編譯。</span><span class="sxs-lookup"><span data-stu-id="8c760-184">You can opt into tiered compilation in either of two ways.</span></span>

- <span data-ttu-id="8c760-185">若要在使用 .NET Core 2.1 SDK 的所有專案中使用階層式編譯，請設定下列環境變數：</span><span class="sxs-lookup"><span data-stu-id="8c760-185">To use tiered compilation in all projects that use the .NET Core 2.1 SDK, set the following environment variable:</span></span>

  ```console
  COMPlus_TieredCompilation="1"
  ```

- <span data-ttu-id="8c760-186">若要針對個別專案使用階層式編譯，請在 MSBuild 專案檔的 `<PropertyGroup>` 區段中加入 `<TieredCompilation>` 屬性，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8c760-186">To use tiered compilation on a per-project basis, add the `<TieredCompilation>` property to the `<PropertyGroup>` section of the MSBuild project file, as the following example shows:</span></span>

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a><span data-ttu-id="8c760-187">API 變更</span><span class="sxs-lookup"><span data-stu-id="8c760-187">API changes</span></span>

### <a name="spant-and-memoryt"></a><span data-ttu-id="8c760-188">`Span<T>` 和 `Memory<T>`</span><span class="sxs-lookup"><span data-stu-id="8c760-188">`Span<T>` and `Memory<T>`</span></span>

<span data-ttu-id="8c760-189">.NET core 2.1 包含一些新的類型，可讓處理陣列和其他記憶體類型變得更有效率。</span><span class="sxs-lookup"><span data-stu-id="8c760-189">.NET Core 2.1 includes some new types that make working with arrays and other types of memory much more efficient.</span></span> <span data-ttu-id="8c760-190">新的類型包括：</span><span class="sxs-lookup"><span data-stu-id="8c760-190">The new types include:</span></span>

- <span data-ttu-id="8c760-191"><xref:System.Span%601?displayProperty=nameWithType> 和 <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="8c760-191"><xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="8c760-192"><xref:System.Memory%601?displayProperty=nameWithType> 和 <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="8c760-192"><xref:System.Memory%601?displayProperty=nameWithType> and <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="8c760-193">沒有這些類型的話，當您傳遞項目作為陣列的一部份或記憶體緩衝區的某個區段時，必須先複製該資料的某些部分，然後才能將它傳遞給方法。</span><span class="sxs-lookup"><span data-stu-id="8c760-193">Without these types, when passing such items as a portion of an array or a section of a memory buffer, you have to make a copy of some portion of the data before passing it to a method.</span></span> <span data-ttu-id="8c760-194">這些類型能提供該資料的虛擬檢視，以免除額外配置記憶體和複製作業的需求。</span><span class="sxs-lookup"><span data-stu-id="8c760-194">These types provide a virtual view of that data that eliminates the need for the additional memory allocation and copy operations.</span></span>

<span data-ttu-id="8c760-195">下列範例使用 <xref:System.Span%601> 執行個體來提供陣列中 10 個元素的虛擬檢視。</span><span class="sxs-lookup"><span data-stu-id="8c760-195">The following example uses a <xref:System.Span%601> instance to provide a virtual view of 10 elements of an array.</span></span>

[!CODE-csharp[Span\<T>](~/samples/core/whats-new/whats-new-in-21/cs/program.cs)]

### <a name="brotli-compression"></a><span data-ttu-id="8c760-196">Brotli 壓縮</span><span class="sxs-lookup"><span data-stu-id="8c760-196">Brotli compression</span></span>

<span data-ttu-id="8c760-197">.NET Core 2.1 新增對 Brotli 壓縮和解壓縮的支援。</span><span class="sxs-lookup"><span data-stu-id="8c760-197">.NET Core 2.1 adds support for Brotli compression and decompression.</span></span> <span data-ttu-id="8c760-198">Brotli 是定義於 [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) \(英文\) 中的一般用途無失真壓縮演算法，並受到大部分網頁瀏覽器和主流 Web 伺服器的支援。</span><span class="sxs-lookup"><span data-stu-id="8c760-198">Brotli is a general-purpose lossless compression algorithm that is defined in [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) and is supported by most web browsers and major web servers.</span></span> <span data-ttu-id="8c760-199">您可以使用資料流形式的 <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> 類別，或是高效能範圍型的 <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> 和 <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> 類別。</span><span class="sxs-lookup"><span data-stu-id="8c760-199">You can use the stream-based <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> class or the high-performance span-based <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> and <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> classes.</span></span> <span data-ttu-id="8c760-200">下列範例說明搭配 <xref:System.IO.Compression.BrotliStream> 類別進行壓縮：</span><span class="sxs-lookup"><span data-stu-id="8c760-200">The following example illustrates compression with the <xref:System.IO.Compression.BrotliStream> class:</span></span>

[!CODE-csharp[Brotli compression](~/samples/core/whats-new/whats-new-in-21/cs/brotli.cs#1)]

<span data-ttu-id="8c760-201"><xref:System.IO.Compression.BrotliStream> 行為與 <xref:System.IO.Compression.DeflateStream> 和 <xref:System.IO.Compression.GZipStream> 相同，這可讓您輕鬆地將呼叫這些 API 的程式碼轉換為 <xref:System.IO.Compression.BrotliStream>。</span><span class="sxs-lookup"><span data-stu-id="8c760-201">The <xref:System.IO.Compression.BrotliStream> behavior is the same as <xref:System.IO.Compression.DeflateStream> and <xref:System.IO.Compression.GZipStream>, which makes it easy to convert code that calls these APIs to <xref:System.IO.Compression.BrotliStream>.</span></span>

### <a name="new-cryptography-apis-and-cryptography-improvements"></a><span data-ttu-id="8c760-202">新的密碼編譯 API 和密碼編譯改進功能</span><span class="sxs-lookup"><span data-stu-id="8c760-202">New cryptography APIs and cryptography improvements</span></span>

<span data-ttu-id="8c760-203">.NET Core 2.1 包含許多針對密碼編譯 API 的增強功能：</span><span class="sxs-lookup"><span data-stu-id="8c760-203">.NET Core 2.1 includes numerous enhancements to the cryptography APIs:</span></span>

- <span data-ttu-id="8c760-204"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> 可在 System.Security.Cryptography.Pkcs 套件中取得。</span><span class="sxs-lookup"><span data-stu-id="8c760-204"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> is available in the System.Security.Cryptography.Pkcs package.</span></span> <span data-ttu-id="8c760-205">其實作與 .NET Framework 中的 <xref:System.Security.Cryptography.Pkcs.SignedCms> 類別相同。</span><span class="sxs-lookup"><span data-stu-id="8c760-205">The implementation is the same as the <xref:System.Security.Cryptography.Pkcs.SignedCms> class in the .NET Framework.</span></span>

- <span data-ttu-id="8c760-206"><xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> 和 <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> 方法的新多載能接受雜湊演算法識別項，使呼叫端可使用 SHA-1 以外的演算法來取得憑證指紋值。</span><span class="sxs-lookup"><span data-stu-id="8c760-206">New overloads of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> and <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> methods accept a hash algorithm identifier to enable callers to get certificate thumbprint values using algorithms other than SHA-1.</span></span>

- <span data-ttu-id="8c760-207">新的 <xref:System.Span%601> 型密碼編譯 API 可用於雜湊、HMAC、亂數密碼編譯產生、非對稱簽章產生、非對稱簽章處理，以及 RSA 加密。</span><span class="sxs-lookup"><span data-stu-id="8c760-207">New <xref:System.Span%601>-based cryptography APIs are available for hashing, HMAC, cryptographic random number generation, asymmetric signature generation, asymmetric signature processing, and RSA encryption.</span></span>

- <span data-ttu-id="8c760-208">透過使用以 <xref:System.Span%601> 為基礎的實作，能使 <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> 的效能提升大約 15%。</span><span class="sxs-lookup"><span data-stu-id="8c760-208">The performance of <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> has improved by about 15% by using a <xref:System.Span%601>-based implementation.</span></span>

- <span data-ttu-id="8c760-209">新的 <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> 類別包含兩種新方法：</span><span class="sxs-lookup"><span data-stu-id="8c760-209">The new <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> class includes two new methods:</span></span>

  - <span data-ttu-id="8c760-210"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> 會在固定的一段時間傳回任意兩個相同長度的輸入，這很適合用於密碼編譯驗證來避免影響計時側邊通道資訊。</span><span class="sxs-lookup"><span data-stu-id="8c760-210"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> takes a fixed amount of time to return for any two inputs of the same length, which makes it suitable for use in cryptographic verification to avoid contributing to timing side-channel information.</span></span>

  - <span data-ttu-id="8c760-211"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> 為會清除記憶體的常式，且無法進行最佳化。</span><span class="sxs-lookup"><span data-stu-id="8c760-211"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> is a memory-clearing routine that cannot be optimized.</span></span>

- <span data-ttu-id="8c760-212">靜態 <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=fullName> 方法會以隨機值填滿 <xref:System.Span%601>。</span><span class="sxs-lookup"><span data-stu-id="8c760-212">The static <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=fullName> method fills a <xref:System.Span%601> with random values.</span></span>

- <span data-ttu-id="8c760-213"><xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> 現在支援 Linux 和 maxOS。</span><span class="sxs-lookup"><span data-stu-id="8c760-213">The <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> is now supported on Linux and maxOS.</span></span>

- <span data-ttu-id="8c760-214">橢圓曲線 Diffie-Hellman (ECDH) 現在可用於 <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> 類別系列。</span><span class="sxs-lookup"><span data-stu-id="8c760-214">Elliptic-Curve Diffie-Hellman (ECDH) is now available in the <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> class family.</span></span> <span data-ttu-id="8c760-215">介面區與在 .NET Framework 中的介面區相同。</span><span class="sxs-lookup"><span data-stu-id="8c760-215">The surface area is the same as in the .NET Framework.</span></span>

- <span data-ttu-id="8c760-216"><xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> 傳回的執行個體可使用 SHA-2 摘要搭配 OAEP 進行加密或解密，以及使用 RSA-PSS 來產生或驗證簽章。</span><span class="sxs-lookup"><span data-stu-id="8c760-216">The instance returned by <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> can encrypt or decrypt with OAEP using a SHA-2 digest, as well as generate or validate signatures using RSA-PSS.</span></span>

### <a name="sockets-improvements"></a><span data-ttu-id="8c760-217">通訊端增強功能</span><span class="sxs-lookup"><span data-stu-id="8c760-217">Sockets improvements</span></span>

<span data-ttu-id="8c760-218">.NET Core 包含新的類型 <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>，以及重新撰寫的 <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>，來形成較高層級網路 API 的基礎。</span><span class="sxs-lookup"><span data-stu-id="8c760-218">.NET Core includes a new type, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, and a rewritten <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, that form the basis of higher-level networking APIs.</span></span>  <span data-ttu-id="8c760-219">舉例來說，<xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> 是 <xref:System.Net.Http.HttpClient> 實作的基礎。</span><span class="sxs-lookup"><span data-stu-id="8c760-219"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, for example, is the basis of the <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="8c760-220">在舊版的 .NET Core 當中，較高層級的 API 是以原生網路實作為基礎。</span><span class="sxs-lookup"><span data-stu-id="8c760-220">In previous versions of .NET Core, higher-level APIs were based on native networking implementations.</span></span>

<span data-ttu-id="8c760-221">在 .NET Core 2.1 中導入的通訊端實作有一些優點：</span><span class="sxs-lookup"><span data-stu-id="8c760-221">The sockets implementation introduced in .NET Core 2.1 has a number of advantages:</span></span>

- <span data-ttu-id="8c760-222">與之前的實作相比，能提供顯著的效能提升。</span><span class="sxs-lookup"><span data-stu-id="8c760-222">A significant performance improvement when compared with the previous implementation.</span></span>

- <span data-ttu-id="8c760-223">消除平台相依性，並進一步簡化部署和維護作業。</span><span class="sxs-lookup"><span data-stu-id="8c760-223">Elimination of platform dependencies, which simplifies deployment and servicing.</span></span>

- <span data-ttu-id="8c760-224">橫跨所有 .NET Core 平台的一致行為。</span><span class="sxs-lookup"><span data-stu-id="8c760-224">Consistent behavior across all .NET Core platforms.</span></span>

<span data-ttu-id="8c760-225"><xref:System.Net.Http.SocketsHttpHandler> 是 .NET Core 2.1 中的預設實作。</span><span class="sxs-lookup"><span data-stu-id="8c760-225"><xref:System.Net.Http.SocketsHttpHandler> is the default implementation in .NET Core 2.1.</span></span> <span data-ttu-id="8c760-226">不過，您可以呼叫 <xref:System.AppContext.SetSwitch%2A?displayProperty="nameWithType"> 方法來將應用程式設定為使用舊版的 <xref:System.Net.Http.HttpClientHandler> 類別：</span><span class="sxs-lookup"><span data-stu-id="8c760-226">However, you can configure your application to use the older <xref:System.Net.Http.HttpClientHandler> class by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty="nameWithType"> method:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", False)
```

<span data-ttu-id="8c760-227">您也可以使用環境變數來選擇退出使用以 <xref:System.Net.Http.SocketsHttpHandler> 為基礎的通訊端實作。</span><span class="sxs-lookup"><span data-stu-id="8c760-227">You can also use an environment variable to opt out of using sockets implementations based on <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="8c760-228">若要這麼做，請將 `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` 設為 `false` 或 0。</span><span class="sxs-lookup"><span data-stu-id="8c760-228">To do this, set the `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` to either `false` or 0.</span></span>

<span data-ttu-id="8c760-229">在 Windows 上，您也可以選擇使用依賴原生實作的 <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>，或是將 <xref:System.Net.Http.SocketsHttpHandler> 類別的執行個體傳遞到 <xref:System.Net.Http.HttpClient> 建構函式來使用該類別。</span><span class="sxs-lookup"><span data-stu-id="8c760-229">On Windows, you can also choose to use <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, which relies on a native implementation, or the <xref:System.Net.Http.SocketsHttpHandler> class by passing an instance of the class to the <xref:System.Net.Http.HttpClient> constructor.</span></span>

<span data-ttu-id="8c760-230">在 Linux 和 macOS 上，您只能針對個別處理序設定 <xref:System.Net.Http.HttpClient>。</span><span class="sxs-lookup"><span data-stu-id="8c760-230">On Linux and macOS, you can only configure <xref:System.Net.Http.HttpClient> on a per-process basis.</span></span> <span data-ttu-id="8c760-231">在 Linux 上，如果您要使用舊的 <xref:System.Net.Http.HttpClient> 實作，便需要部署 [libcurl](https://curl.haxx.se/libcurl/) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="8c760-231">On Linux, you need to deploy [libcurl](https://curl.haxx.se/libcurl/) if you want to use the old <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="8c760-232">(它會隨 .NET Core 2.0 一起安裝)</span><span class="sxs-lookup"><span data-stu-id="8c760-232">(It is installed with .NET Core 2.0.)</span></span>

## <a name="see-also"></a><span data-ttu-id="8c760-233">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c760-233">See also</span></span>

[<span data-ttu-id="8c760-234">.NET Core 的新功能</span><span class="sxs-lookup"><span data-stu-id="8c760-234">What's new in .NET Core</span></span>](index.md)  
[<span data-ttu-id="8c760-235">EF Core 2.1 的新功能</span><span class="sxs-lookup"><span data-stu-id="8c760-235">New features in EF Core 2.1</span></span>](/ef/core/what-is-new/ef-core-2.1)  
[<span data-ttu-id="8c760-236">ASP.NET Core 2.1 的新功能</span><span class="sxs-lookup"><span data-stu-id="8c760-236">What's new in ASP.NET Core 2.1</span></span>](/aspnet/core/aspnetcore-2.1)
