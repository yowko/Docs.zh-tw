---
title: dotnet test 命令
description: dotnet test 命令是用來在指定的專案中執行單元測試。
ms.date: 04/29/2020
ms.openlocfilehash: 5ecfa24905537a663cd967142b765c258495fb22
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537729"
---
# <a name="dotnet-test"></a><span data-ttu-id="81f34-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="81f34-103">dotnet test</span></span>

<span data-ttu-id="81f34-104">本文**適用于：** ✔️ .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="81f34-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="81f34-105">名稱</span><span class="sxs-lookup"><span data-stu-id="81f34-105">Name</span></span>

<span data-ttu-id="81f34-106">`dotnet test` - 用來執行單元測試的 .NET 測試驅動程式。</span><span class="sxs-lookup"><span data-stu-id="81f34-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="81f34-107">概要</span><span class="sxs-lookup"><span data-stu-id="81f34-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION> | <DIRECTORY> | <DLL>]
    [-a|--test-adapter-path <ADAPTER_PATH>] [--blame] [--blame-crash]
    [--blame-crash-dump-type <DUMP_TYPE>] [--blame-crash-collect-always]
    [--blame-hang] [--blame-hang-dump-type <DUMP_TYPE>]
    [--blame-hang-timeout <TIMESPAN>]
    [-c|--configuration <CONFIGURATION>]
    [--collect <DATA_COLLECTOR_NAME>]
    [-d|--diag <LOG_FILE>] [-f|--framework <FRAMEWORK>]
    [--filter <EXPRESSION>] [--interactive]
    [-l|--logger <LOGGER>] [--no-build]
    [--nologo] [--no-restore] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--results-directory <RESULTS_DIR>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--settings <SETTINGS_FILE>] [-t|--list-tests]
    [-v|--verbosity <LEVEL>] [[--] <RunSettings arguments>]

dotnet test -h|--help
```

## <a name="description"></a><span data-ttu-id="81f34-108">描述</span><span class="sxs-lookup"><span data-stu-id="81f34-108">Description</span></span>

<span data-ttu-id="81f34-109">此 `dotnet test` 命令可用來在指定的解決方案中執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="81f34-109">The `dotnet test` command is used to execute unit tests in a given solution.</span></span> <span data-ttu-id="81f34-110">此 `dotnet test` 命令會建立方案，並針對方案中的每個測試專案執行測試主機應用程式。</span><span class="sxs-lookup"><span data-stu-id="81f34-110">The `dotnet test` command builds the solution and runs a test host application for each test project in the solution.</span></span> <span data-ttu-id="81f34-111">測試主機會使用測試架構在指定的專案中執行測試，例如： MSTest、NUnit 或 xUnit，並報告每項測試的成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="81f34-111">The test host executes tests in the given project using a test framework, for example: MSTest, NUnit, or xUnit, and reports the success or failure of each test.</span></span> <span data-ttu-id="81f34-112">如果所有測試都成功，則測試執行器會傳回 0 作為結束代碼；如果有任何測試失敗，則會傳回 1。</span><span class="sxs-lookup"><span data-stu-id="81f34-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span>

<span data-ttu-id="81f34-113">針對多目標專案，會針對每個目標架構執行測試。</span><span class="sxs-lookup"><span data-stu-id="81f34-113">For multi-targeted projects, tests are run for each targeted framework.</span></span> <span data-ttu-id="81f34-114">測試主機和單元測試架構會封裝為 NuGet 套件，並還原為專案的一般相依性。</span><span class="sxs-lookup"><span data-stu-id="81f34-114">The test host and the unit test framework are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="81f34-115">測試專案會使用一般 `<PackageReference>` 元素指定測試執行器，如下列範例專案檔中所示：</span><span class="sxs-lookup"><span data-stu-id="81f34-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

<span data-ttu-id="81f34-116">測試 `Microsoft.NET.Test.Sdk` 主控制項 `xunit` 是測試架構。</span><span class="sxs-lookup"><span data-stu-id="81f34-116">Where `Microsoft.NET.Test.Sdk` is the test host, `xunit` is the test framework.</span></span> <span data-ttu-id="81f34-117">和 `xunit.runner.visualstudio` 是測試介面卡，可讓 xUnit 架構搭配測試主機使用。</span><span class="sxs-lookup"><span data-stu-id="81f34-117">And `xunit.runner.visualstudio` is a test adapter, which allows the xUnit framework to work with the test host.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="81f34-118">隱含還原</span><span class="sxs-lookup"><span data-stu-id="81f34-118">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="81f34-119">引數</span><span class="sxs-lookup"><span data-stu-id="81f34-119">Arguments</span></span>

- **`PROJECT | SOLUTION | DIRECTORY | DLL`**

  - <span data-ttu-id="81f34-120">測試專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="81f34-120">Path to the test project.</span></span>
  - <span data-ttu-id="81f34-121">解決方案的路徑。</span><span class="sxs-lookup"><span data-stu-id="81f34-121">Path to the solution.</span></span>
  - <span data-ttu-id="81f34-122">包含專案或方案之目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="81f34-122">Path to a directory that contains a project or a solution.</span></span>
  - <span data-ttu-id="81f34-123">測試專案 *.dll* 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="81f34-123">Path to a test project *.dll* file.</span></span>

  <span data-ttu-id="81f34-124">如果未指定，則會在目前的目錄中搜尋專案或方案。</span><span class="sxs-lookup"><span data-stu-id="81f34-124">If not specified, it searches for a project or a solution in the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="81f34-125">選項</span><span class="sxs-lookup"><span data-stu-id="81f34-125">Options</span></span>

- **`-a|--test-adapter-path <ADAPTER_PATH>`**

  <span data-ttu-id="81f34-126">要在其中搜尋其他測試介面卡之目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="81f34-126">Path to a directory to be searched for additional test adapters.</span></span> <span data-ttu-id="81f34-127">只會檢查具有尾碼的 *.dll*檔案。 `.TestAdapter.dll`</span><span class="sxs-lookup"><span data-stu-id="81f34-127">Only *.dll* files with suffix `.TestAdapter.dll` are inspected.</span></span> <span data-ttu-id="81f34-128">如果未指定，則會搜尋 test *.dll* 的目錄。</span><span class="sxs-lookup"><span data-stu-id="81f34-128">If not specified, the directory of the test *.dll* is searched.</span></span>

- **`--blame`**

  <span data-ttu-id="81f34-129">在歸責模式下執行測試。</span><span class="sxs-lookup"><span data-stu-id="81f34-129">Runs the tests in blame mode.</span></span> <span data-ttu-id="81f34-130">此選項有助於隔離導致測試主機損毀的有問題的測試。</span><span class="sxs-lookup"><span data-stu-id="81f34-130">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="81f34-131">當偵測到損毀時，它會在中建立一個序列檔案 `TestResults/<Guid>/<Guid>_Sequence.xml` ，該檔案會捕捉損毀之前執行的測試順序。</span><span class="sxs-lookup"><span data-stu-id="81f34-131">When a crash is detected, it creates a sequence file in `TestResults/<Guid>/<Guid>_Sequence.xml` that captures the order of tests that were run before the crash.</span></span>

- <span data-ttu-id="81f34-132">**`--blame-crash`** 自 .NET 5.0 preview SDK 起可用 () </span><span class="sxs-lookup"><span data-stu-id="81f34-132">**`--blame-crash`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="81f34-133">在有問題的模式下執行測試，並在測試主機非預期地結束時收集損毀傾印。</span><span class="sxs-lookup"><span data-stu-id="81f34-133">Runs the tests in blame mode and collects a crash dump when the test host exits unexpectedly.</span></span> <span data-ttu-id="81f34-134">只有在 Windows 上才支援此選項。</span><span class="sxs-lookup"><span data-stu-id="81f34-134">This option is only supported on Windows.</span></span> <span data-ttu-id="81f34-135">包含 *procdump.exe* 和 *procdump64.exe* 的目錄必須在 PATH 或 PROCDUMP_PATH 環境變數中。</span><span class="sxs-lookup"><span data-stu-id="81f34-135">A directory that contains *procdump.exe* and *procdump64.exe* must be in the PATH or PROCDUMP_PATH environment variable.</span></span> <span data-ttu-id="81f34-136">[下載工具](/sysinternals/downloads/procdump)。</span><span class="sxs-lookup"><span data-stu-id="81f34-136">[Download the tools](/sysinternals/downloads/procdump).</span></span> <span data-ttu-id="81f34-137">意指 `--blame` 。</span><span class="sxs-lookup"><span data-stu-id="81f34-137">Implies `--blame`.</span></span>

- <span data-ttu-id="81f34-138">**`--blame-crash-dump-type <DUMP_TYPE>`** 自 .NET 5.0 preview SDK 起可用 () </span><span class="sxs-lookup"><span data-stu-id="81f34-138">**`--blame-crash-dump-type <DUMP_TYPE>`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="81f34-139">要收集的損毀傾印類型。</span><span class="sxs-lookup"><span data-stu-id="81f34-139">The type of crash dump to be collected.</span></span> <span data-ttu-id="81f34-140">意指 `--blame-crash` 。</span><span class="sxs-lookup"><span data-stu-id="81f34-140">Implies `--blame-crash`.</span></span>

- <span data-ttu-id="81f34-141">**`--blame-crash-collect-always`** 自 .NET 5.0 preview SDK 起可用 () </span><span class="sxs-lookup"><span data-stu-id="81f34-141">**`--blame-crash-collect-always`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="81f34-142">收集預期的損毀傾印，以及未預期的測試主機結束。</span><span class="sxs-lookup"><span data-stu-id="81f34-142">Collects a crash dump on expected as well as unexpected test host exit.</span></span>

- <span data-ttu-id="81f34-143">**`--blame-hang`** 自 .NET 5.0 preview SDK 起可用 () </span><span class="sxs-lookup"><span data-stu-id="81f34-143">**`--blame-hang`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="81f34-144">在有阻礙的模式下執行測試，並在測試超過指定的超時時間時收集停止回應傾印。</span><span class="sxs-lookup"><span data-stu-id="81f34-144">Run the tests in blame mode and collects a hang dump when a test exceeds the given timeout.</span></span>

- <span data-ttu-id="81f34-145">**`--blame-hang-dump-type <DUMP_TYPE>`** 自 .NET 5.0 preview SDK 起可用 () </span><span class="sxs-lookup"><span data-stu-id="81f34-145">**`--blame-hang-dump-type <DUMP_TYPE>`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="81f34-146">要收集的損毀傾印類型。</span><span class="sxs-lookup"><span data-stu-id="81f34-146">The type of crash dump to be collected.</span></span> <span data-ttu-id="81f34-147">它應該是 `full` 、 `mini` 或 `none` 。</span><span class="sxs-lookup"><span data-stu-id="81f34-147">It should be `full`, `mini`, or `none`.</span></span> <span data-ttu-id="81f34-148">當 `none` 指定時，會在超時時終止測試主機，但不會收集任何傾印。</span><span class="sxs-lookup"><span data-stu-id="81f34-148">When `none` is specified, test host is terminated on timeout, but no dump is collected.</span></span> <span data-ttu-id="81f34-149">意指 `--blame-hang` 。</span><span class="sxs-lookup"><span data-stu-id="81f34-149">Implies `--blame-hang`.</span></span>

- <span data-ttu-id="81f34-150">**`--blame-hang-timeout <TIMESPAN>`** 自 .NET 5.0 preview SDK 起可用 () </span><span class="sxs-lookup"><span data-stu-id="81f34-150">**`--blame-hang-timeout <TIMESPAN>`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="81f34-151">每個測試的超時時間，在此時間之後，就會觸發停止回應傾印，並終止測試主機進程。</span><span class="sxs-lookup"><span data-stu-id="81f34-151">Per-test timeout, after which a hang dump is triggered and the test host process is terminated.</span></span> <span data-ttu-id="81f34-152">Timeout 值是以下列其中一種格式來指定：</span><span class="sxs-lookup"><span data-stu-id="81f34-152">The timeout value is specified in one of the following formats:</span></span>
  
  - <span data-ttu-id="81f34-153">1.5 h</span><span class="sxs-lookup"><span data-stu-id="81f34-153">1.5h</span></span>
  - <span data-ttu-id="81f34-154">90m</span><span class="sxs-lookup"><span data-stu-id="81f34-154">90m</span></span>
  - <span data-ttu-id="81f34-155">5400s</span><span class="sxs-lookup"><span data-stu-id="81f34-155">5400s</span></span>
  - <span data-ttu-id="81f34-156">5400000ms</span><span class="sxs-lookup"><span data-stu-id="81f34-156">5400000ms</span></span>

  <span data-ttu-id="81f34-157">如果未使用任何單位 (例如 5400000) ，則會假設值為毫秒。</span><span class="sxs-lookup"><span data-stu-id="81f34-157">When no unit is used (for example, 5400000), the value is assumed to be in milliseconds.</span></span> <span data-ttu-id="81f34-158">搭配資料驅動的測試使用時，超時行為取決於所使用的測試介面卡。</span><span class="sxs-lookup"><span data-stu-id="81f34-158">When used together with data driven tests, the timeout behavior depends on the test adapter used.</span></span> <span data-ttu-id="81f34-159">若為 xUnit 和 NUnit，則會在每個測試案例之後更新 timeout。</span><span class="sxs-lookup"><span data-stu-id="81f34-159">For xUnit and NUnit the timeout is renewed after every test case.</span></span> <span data-ttu-id="81f34-160">針對 MSTest，所有測試案例都會使用此超時時間。</span><span class="sxs-lookup"><span data-stu-id="81f34-160">For MSTest, the timeout is used for all test cases.</span></span> <span data-ttu-id="81f34-161">使用 netcoreapp 2.1 和更新版本的 Windows，以及 Linux 上的 netcoreapp 3.1 和更新版本都支援此選項。</span><span class="sxs-lookup"><span data-stu-id="81f34-161">This option is supported on Windows with netcoreapp2.1 and later, and on Linux with netcoreapp3.1 and later.</span></span> <span data-ttu-id="81f34-162">不支援 macOS。</span><span class="sxs-lookup"><span data-stu-id="81f34-162">macOS is not supported.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="81f34-163">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="81f34-163">Defines the build configuration.</span></span> <span data-ttu-id="81f34-164">預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。</span><span class="sxs-lookup"><span data-stu-id="81f34-164">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_NAME>`**

  <span data-ttu-id="81f34-165">測試回合啟用資料收集器。</span><span class="sxs-lookup"><span data-stu-id="81f34-165">Enables data collector for the test run.</span></span> <span data-ttu-id="81f34-166">如需詳細資訊，請參閱[監視及分析測試回合](https://aka.ms/vstest-collect)。</span><span class="sxs-lookup"><span data-stu-id="81f34-166">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>
  
  <span data-ttu-id="81f34-167">若要在 .NET Core 支援的任何平臺上收集程式碼涵蓋範圍，請安裝 [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) 並使用 `--collect:"XPlat Code Coverage"` 選項。</span><span class="sxs-lookup"><span data-stu-id="81f34-167">To collect code coverage on any platform that is supported by .NET Core, install [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) and use the `--collect:"XPlat Code Coverage"` option.</span></span>

  <span data-ttu-id="81f34-168">在 Windows 上，您可以使用選項來收集程式碼涵蓋範圍 `--collect "Code Coverage"` 。</span><span class="sxs-lookup"><span data-stu-id="81f34-168">On Windows, you can collect code coverage by using the `--collect "Code Coverage"` option.</span></span> <span data-ttu-id="81f34-169">此選項會產生一個 *涵蓋範圍* 檔案，該檔案可在 Visual Studio 2019 Enterprise 中開啟。</span><span class="sxs-lookup"><span data-stu-id="81f34-169">This option generates a *.coverage* file, which can be opened in Visual Studio 2019 Enterprise.</span></span> <span data-ttu-id="81f34-170">如需詳細資訊，請參閱 [使用程式碼涵蓋範圍](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested) 和 [自訂程式碼涵蓋範圍分析](/visualstudio/test/customizing-code-coverage-analysis)。</span><span class="sxs-lookup"><span data-stu-id="81f34-170">For more information, see [Use code coverage](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested) and [Customize code coverage analysis](/visualstudio/test/customizing-code-coverage-analysis).</span></span>

- **`-d|--diag <LOG_FILE>`**

  <span data-ttu-id="81f34-171">針對測試平臺啟用診斷模式，並將診斷訊息寫入至指定的檔案和其旁邊的檔案。</span><span class="sxs-lookup"><span data-stu-id="81f34-171">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file and to files next to it.</span></span> <span data-ttu-id="81f34-172">記錄訊息的程式會決定要建立哪些檔案，例如 `*.host_<date>.txt` 用於測試主機記錄檔，以及 `*.datacollector_<date>.txt` 資料收集器記錄檔。</span><span class="sxs-lookup"><span data-stu-id="81f34-172">The process that is logging the messages determines which files are created, such as `*.host_<date>.txt` for test host log, and `*.datacollector_<date>.txt` for data collector log.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="81f34-173">強制將 `dotnet` 或 .NET Framework 測試主機用於測試二進位檔。</span><span class="sxs-lookup"><span data-stu-id="81f34-173">Forces the use of `dotnet` or .NET Framework test host for the test binaries.</span></span> <span data-ttu-id="81f34-174">此選項只會決定要使用的主機類型。</span><span class="sxs-lookup"><span data-stu-id="81f34-174">This option only determines which type of host to use.</span></span> <span data-ttu-id="81f34-175">實際要使用的 framework 版本取決於測試專案的 *runtimeconfig.js* 。</span><span class="sxs-lookup"><span data-stu-id="81f34-175">The actual framework version to be used is determined by the *runtimeconfig.json* of the test project.</span></span> <span data-ttu-id="81f34-176">如果未指定，則會使用 [TargetFramework 元件屬性](/dotnet/api/system.runtime.versioning.targetframeworkattribute) 來判斷主機的類型。</span><span class="sxs-lookup"><span data-stu-id="81f34-176">When not specified, the [TargetFramework assembly attribute](/dotnet/api/system.runtime.versioning.targetframeworkattribute) is used to determine the type of host.</span></span> <span data-ttu-id="81f34-177">從 *.dll*中移除該屬性時，會使用 .NET Framework 主機。</span><span class="sxs-lookup"><span data-stu-id="81f34-177">When that attribute is stripped from the *.dll*, the .NET Framework host is used.</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="81f34-178">使用指定的運算式篩選出目前專案中的測試。</span><span class="sxs-lookup"><span data-stu-id="81f34-178">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="81f34-179">如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。</span><span class="sxs-lookup"><span data-stu-id="81f34-179">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="81f34-180">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="81f34-180">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="81f34-181">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="81f34-181">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="81f34-182">可讓命令停止，並等候使用者輸入或進行動作。</span><span class="sxs-lookup"><span data-stu-id="81f34-182">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="81f34-183">例如完成驗證。</span><span class="sxs-lookup"><span data-stu-id="81f34-183">For example, to complete authentication.</span></span> <span data-ttu-id="81f34-184">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="81f34-184">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER>`**

  <span data-ttu-id="81f34-185">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="81f34-185">Specifies a logger for test results.</span></span> <span data-ttu-id="81f34-186">與 MSBuild 不同的是，dotnet test 不接受縮寫：而不是 `-l "console;v=d"` 使用 `-l "console;verbosity=detailed"` 。</span><span class="sxs-lookup"><span data-stu-id="81f34-186">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="81f34-187">不會在執行前建置測試專案。</span><span class="sxs-lookup"><span data-stu-id="81f34-187">Doesn't build the test project before running it.</span></span> <span data-ttu-id="81f34-188">它也會隱含地設定- `--no-restore` 旗標。</span><span class="sxs-lookup"><span data-stu-id="81f34-188">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="81f34-189">執行測試而不顯示 Microsoft TestPlatform 橫幅。</span><span class="sxs-lookup"><span data-stu-id="81f34-189">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="81f34-190">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="81f34-190">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="81f34-191">執行命令時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="81f34-191">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="81f34-192">在其中尋找要執行的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="81f34-192">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="81f34-193">如果未指定，則預設路徑為 `./bin/<configuration>/<framework>/`。</span><span class="sxs-lookup"><span data-stu-id="81f34-193">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="81f34-194">針對具有多個目標 framework 的專案 (透過 `TargetFrameworks` 屬性) ，您也需要在 `--framework` 指定此選項時定義。</span><span class="sxs-lookup"><span data-stu-id="81f34-194">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="81f34-195">`dotnet test` 一律從輸出目錄執行測試。</span><span class="sxs-lookup"><span data-stu-id="81f34-195">`dotnet test` always runs tests from the output directory.</span></span> <span data-ttu-id="81f34-196">您可以使用 <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> 來取用輸出目錄中的測試資產。</span><span class="sxs-lookup"><span data-stu-id="81f34-196">You can use <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> to consume test assets in the output directory.</span></span>

- **`-r|--results-directory <RESULTS_DIR>`**

  <span data-ttu-id="81f34-197">要放置測試結果的目錄。</span><span class="sxs-lookup"><span data-stu-id="81f34-197">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="81f34-198">如果指定的目錄不存在，則會建立該目錄。</span><span class="sxs-lookup"><span data-stu-id="81f34-198">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="81f34-199">預設值 `TestResults` 在包含專案檔的目錄中。</span><span class="sxs-lookup"><span data-stu-id="81f34-199">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="81f34-200">要測試的目標執行時間。</span><span class="sxs-lookup"><span data-stu-id="81f34-200">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="81f34-201">用來執行測試的 `.runsettings` 檔案。</span><span class="sxs-lookup"><span data-stu-id="81f34-201">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="81f34-202">`TargetPlatform` (x86 | x64) 的元素沒有任何作用 `dotnet test` 。</span><span class="sxs-lookup"><span data-stu-id="81f34-202">The `TargetPlatform` element (x86|x64) has no effect for `dotnet test`.</span></span> <span data-ttu-id="81f34-203">若要執行以 x86 為目標的測試，請安裝 .NET Core 的 x86 版本。</span><span class="sxs-lookup"><span data-stu-id="81f34-203">To run tests that target x86, install the x86 version of .NET Core.</span></span> <span data-ttu-id="81f34-204">路徑上的 *dotnet.exe* 位是將用來執行測試的。</span><span class="sxs-lookup"><span data-stu-id="81f34-204">The bitness of the *dotnet.exe* that is on the path is what will be used for running tests.</span></span> <span data-ttu-id="81f34-205">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="81f34-205">For more information, see the following resources:</span></span>

  - <span data-ttu-id="81f34-206">[使用 `.runsettings` 檔案設定單元測試](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)。</span><span class="sxs-lookup"><span data-stu-id="81f34-206">[Configure unit tests by using a `.runsettings` file.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)</span></span>
  - <span data-ttu-id="81f34-207">[設定測試回合](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="81f34-207">[Configure a test run](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)</span></span>

- **`-t|--list-tests`**

  <span data-ttu-id="81f34-208">列出探索到的測試，而不是執行測試。</span><span class="sxs-lookup"><span data-stu-id="81f34-208">List the discovered tests instead of running the tests.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="81f34-209">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="81f34-209">Sets the verbosity level of the command.</span></span> <span data-ttu-id="81f34-210">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="81f34-210">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="81f34-211">預設為 `minimal`。</span><span class="sxs-lookup"><span data-stu-id="81f34-211">The default is `minimal`.</span></span> <span data-ttu-id="81f34-212">如需詳細資訊，請參閱<xref:Microsoft.Build.Framework.LoggerVerbosity>。</span><span class="sxs-lookup"><span data-stu-id="81f34-212">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="81f34-213">**`RunSettings`** 參數</span><span class="sxs-lookup"><span data-stu-id="81f34-213">**`RunSettings`** arguments</span></span>

 <span data-ttu-id="81f34-214">在 `RunSettings` "--" 之後，命令列上的最後一個引數會以內嵌的形式傳遞， (記下的空格--) 。</span><span class="sxs-lookup"><span data-stu-id="81f34-214">Inline `RunSettings` are passed as the last arguments on the command line after "-- " (note the space after --).</span></span> <span data-ttu-id="81f34-215">內嵌 `RunSettings` 是指定 `[name]=[value]` 成對的。</span><span class="sxs-lookup"><span data-stu-id="81f34-215">Inline `RunSettings` are specified as `[name]=[value]` pairs.</span></span> <span data-ttu-id="81f34-216">空格適用來分隔多個 `[name]=[value]` 組。</span><span class="sxs-lookup"><span data-stu-id="81f34-216">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="81f34-217">範例： `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="81f34-217">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="81f34-218">如需詳細資訊，請參閱 [透過命令列傳遞 .runsettings 引數](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)。</span><span class="sxs-lookup"><span data-stu-id="81f34-218">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="81f34-219">範例</span><span class="sxs-lookup"><span data-stu-id="81f34-219">Examples</span></span>

- <span data-ttu-id="81f34-220">執行目前目錄之專案中的測試：</span><span class="sxs-lookup"><span data-stu-id="81f34-220">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="81f34-221">執行 `test1` 專案中的測試︰</span><span class="sxs-lookup"><span data-stu-id="81f34-221">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="81f34-222">在目前目錄中的專案中執行測試，並以 .trx 格式產生測試結果檔案：</span><span class="sxs-lookup"><span data-stu-id="81f34-222">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="81f34-223">在目前目錄中的專案中執行測試，並在安裝 [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/Documentation/VSTestIntegration.md) 收集器整合) 之後產生程式碼涵蓋範圍檔案 (：</span><span class="sxs-lookup"><span data-stu-id="81f34-223">Run the tests in the project in the current directory, and generate a code coverage file (after installing [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/Documentation/VSTestIntegration.md) collectors integration):</span></span>

  ```dotnetcli
  dotnet test --collect:"XPlat Code Coverage"
  ```

- <span data-ttu-id="81f34-224">在目前目錄中的專案中執行測試，並將程式碼涵蓋範圍檔案 (僅限 Windows) ：</span><span class="sxs-lookup"><span data-stu-id="81f34-224">Run the tests in the project in the current directory, and generate a code coverage file (Windows only):</span></span>

  ```dotnetcli
  dotnet test --collect "Code Coverage"
  ```

- <span data-ttu-id="81f34-225">在目前目錄中的專案中執行測試，並以詳細的詳細資訊記錄到主控台：</span><span class="sxs-lookup"><span data-stu-id="81f34-225">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

- <span data-ttu-id="81f34-226">在目前目錄中的專案中執行測試，並在測試主機當機時進行報表測試：</span><span class="sxs-lookup"><span data-stu-id="81f34-226">Run the tests in the project in the current directory, and report tests that were in progress when the test host crashed:</span></span>

  ```dotnetcli
  dotnet test --blame
  ```

## <a name="filter-option-details"></a><span data-ttu-id="81f34-227">篩選選項詳細資料</span><span class="sxs-lookup"><span data-stu-id="81f34-227">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="81f34-228">`<Expression>` 的格式為 `<property><operator><value>[|&<Expression>]`。</span><span class="sxs-lookup"><span data-stu-id="81f34-228">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="81f34-229">`<property>` 為 `Test Case` 的屬性。</span><span class="sxs-lookup"><span data-stu-id="81f34-229">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="81f34-230">以下為熱門單元測試架構所支援的屬性：</span><span class="sxs-lookup"><span data-stu-id="81f34-230">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="81f34-231">測試架構</span><span class="sxs-lookup"><span data-stu-id="81f34-231">Test Framework</span></span> | <span data-ttu-id="81f34-232">支援的屬性</span><span class="sxs-lookup"><span data-stu-id="81f34-232">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="81f34-233">MSTest</span><span class="sxs-lookup"><span data-stu-id="81f34-233">MSTest</span></span>         | <ul><li><span data-ttu-id="81f34-234">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="81f34-234">FullyQualifiedName</span></span></li><li><span data-ttu-id="81f34-235">名稱</span><span class="sxs-lookup"><span data-stu-id="81f34-235">Name</span></span></li><li><span data-ttu-id="81f34-236">ClassName</span><span class="sxs-lookup"><span data-stu-id="81f34-236">ClassName</span></span></li><li><span data-ttu-id="81f34-237">優先順序</span><span class="sxs-lookup"><span data-stu-id="81f34-237">Priority</span></span></li><li><span data-ttu-id="81f34-238">TestCategory</span><span class="sxs-lookup"><span data-stu-id="81f34-238">TestCategory</span></span></li></ul> |
| <span data-ttu-id="81f34-239">xUnit</span><span class="sxs-lookup"><span data-stu-id="81f34-239">xUnit</span></span>          | <ul><li><span data-ttu-id="81f34-240">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="81f34-240">FullyQualifiedName</span></span></li><li><span data-ttu-id="81f34-241">DisplayName</span><span class="sxs-lookup"><span data-stu-id="81f34-241">DisplayName</span></span></li><li><span data-ttu-id="81f34-242">特性</span><span class="sxs-lookup"><span data-stu-id="81f34-242">Traits</span></span></li></ul>                                   |
| <span data-ttu-id="81f34-243">NUnit</span><span class="sxs-lookup"><span data-stu-id="81f34-243">NUnit</span></span>          | <ul><li><span data-ttu-id="81f34-244">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="81f34-244">FullyQualifiedName</span></span></li><li><span data-ttu-id="81f34-245">名稱</span><span class="sxs-lookup"><span data-stu-id="81f34-245">Name</span></span></li><li><span data-ttu-id="81f34-246">TestCategory</span><span class="sxs-lookup"><span data-stu-id="81f34-246">TestCategory</span></span></li><li><span data-ttu-id="81f34-247">優先順序</span><span class="sxs-lookup"><span data-stu-id="81f34-247">Priority</span></span></li></ul>                                   |

<span data-ttu-id="81f34-248">`<operator>` 描述屬性和值之間的關聯性：</span><span class="sxs-lookup"><span data-stu-id="81f34-248">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="81f34-249">運算子</span><span class="sxs-lookup"><span data-stu-id="81f34-249">Operator</span></span> | <span data-ttu-id="81f34-250">函式</span><span class="sxs-lookup"><span data-stu-id="81f34-250">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="81f34-251">完全相符</span><span class="sxs-lookup"><span data-stu-id="81f34-251">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="81f34-252">不完全相符</span><span class="sxs-lookup"><span data-stu-id="81f34-252">Not exact match</span></span> |
| `~`      | <span data-ttu-id="81f34-253">包含</span><span class="sxs-lookup"><span data-stu-id="81f34-253">Contains</span></span>        |
| `!~`     | <span data-ttu-id="81f34-254">Not contains</span><span class="sxs-lookup"><span data-stu-id="81f34-254">Not contains</span></span>    |

<span data-ttu-id="81f34-255">`<value>` 為字串。</span><span class="sxs-lookup"><span data-stu-id="81f34-255">`<value>` is a string.</span></span> <span data-ttu-id="81f34-256">所有的查閱皆不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="81f34-256">All the lookups are case insensitive.</span></span>

<span data-ttu-id="81f34-257">沒有 `<operator>` 的運算式會自動被視為 `FullyQualifiedName` 屬性上的 `contains` (例如，`dotnet test --filter xyz` 等同於 `dotnet test --filter FullyQualifiedName~xyz`)。</span><span class="sxs-lookup"><span data-stu-id="81f34-257">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="81f34-258">運算式可以使用條件運算子聯結：</span><span class="sxs-lookup"><span data-stu-id="81f34-258">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="81f34-259">運算子</span><span class="sxs-lookup"><span data-stu-id="81f34-259">Operator</span></span>            | <span data-ttu-id="81f34-260">函式</span><span class="sxs-lookup"><span data-stu-id="81f34-260">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="81f34-261">或者</span><span class="sxs-lookup"><span data-stu-id="81f34-261">OR</span></span>       |
| `&`                 | <span data-ttu-id="81f34-262">AND</span><span class="sxs-lookup"><span data-stu-id="81f34-262">AND</span></span>      |

<span data-ttu-id="81f34-263">使用條件運算子時，您可以使用括弧括住運算式 (例如，`(Name~TestMethod1) | (Name~TestMethod2)`)。</span><span class="sxs-lookup"><span data-stu-id="81f34-263">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="81f34-264">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="81f34-264">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="81f34-265">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81f34-265">See also</span></span>

- [<span data-ttu-id="81f34-266">架構與目標</span><span class="sxs-lookup"><span data-stu-id="81f34-266">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="81f34-267">.NET Core 執行時間識別碼 (RID) 目錄</span><span class="sxs-lookup"><span data-stu-id="81f34-267">.NET Core Runtime Identifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="81f34-268">透過命令列傳遞 .runsettings 引數</span><span class="sxs-lookup"><span data-stu-id="81f34-268">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
