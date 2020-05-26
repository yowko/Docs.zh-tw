---
title: dotnet test 命令
description: dotnet test 命令是用來在指定的專案中執行單元測試。
ms.date: 04/29/2020
ms.openlocfilehash: 22b27007d26c98cff40733ef8d449ce334f87848
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802685"
---
# <a name="dotnet-test"></a><span data-ttu-id="924ff-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="924ff-103">dotnet test</span></span>

<span data-ttu-id="924ff-104">**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="924ff-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="924ff-105">名稱</span><span class="sxs-lookup"><span data-stu-id="924ff-105">Name</span></span>

<span data-ttu-id="924ff-106">`dotnet test` - 用來執行單元測試的 .NET 測試驅動程式。</span><span class="sxs-lookup"><span data-stu-id="924ff-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="924ff-107">概要</span><span class="sxs-lookup"><span data-stu-id="924ff-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION> | <DIRECTORY> | <DLL>]
    [-a|--test-adapter-path <PATH_TO_ADAPTER>] [--blame]
    [-c|--configuration <CONFIGURATION>]
    [--collect <DATA_COLLECTOR_FRIENDLY_NAME>]
    [-d|--diag <PATH_TO_DIAGNOSTICS_FILE>] [-f|--framework <FRAMEWORK>]
    [--filter <EXPRESSION>] [--interactive]
    [-l|--logger <LOGGER_URI/FRIENDLY_NAME>] [--no-build]
    [--nologo] [--no-restore] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--results-directory <PATH>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--settings <SETTINGS_FILE>] [-t|--list-tests]
    [-v|--verbosity <LEVEL>] [[--] <RunSettings arguments>]

dotnet test -h|--help
```

## <a name="description"></a><span data-ttu-id="924ff-108">描述</span><span class="sxs-lookup"><span data-stu-id="924ff-108">Description</span></span>

<span data-ttu-id="924ff-109">`dotnet test`命令是用來在指定的方案中執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="924ff-109">The `dotnet test` command is used to execute unit tests in a given solution.</span></span> <span data-ttu-id="924ff-110">此 `dotnet test` 命令會建立方案，並針對方案中的每個測試專案執行測試主機應用程式。</span><span class="sxs-lookup"><span data-stu-id="924ff-110">The `dotnet test` command builds the solution and runs a test host application for each test project in the solution.</span></span> <span data-ttu-id="924ff-111">測試主機會使用測試架構在指定的專案中執行測試，例如： MSTest、NUnit 或 xUnit，並報告每項測試的成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="924ff-111">The test host executes tests in the given project using a test framework, for example: MSTest, NUnit, or xUnit, and reports the success or failure of each test.</span></span> <span data-ttu-id="924ff-112">如果所有測試都成功，則測試執行器會傳回 0 作為結束代碼；如果有任何測試失敗，則會傳回 1。</span><span class="sxs-lookup"><span data-stu-id="924ff-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span>

<span data-ttu-id="924ff-113">針對多目標專案，會針對每個目標架構執行測試。</span><span class="sxs-lookup"><span data-stu-id="924ff-113">For multi-targeted projects, tests are run for each targeted framework.</span></span> <span data-ttu-id="924ff-114">測試主機和單元測試架構會封裝為 NuGet 套件，並還原為專案的一般相依性。</span><span class="sxs-lookup"><span data-stu-id="924ff-114">The test host and the unit test framework are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="924ff-115">測試專案會使用一般 `<PackageReference>` 元素指定測試執行器，如下列範例專案檔中所示：</span><span class="sxs-lookup"><span data-stu-id="924ff-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

<span data-ttu-id="924ff-116">其中 `Microsoft.NET.Test.Sdk` 是測試主機， `xunit` 是測試架構。</span><span class="sxs-lookup"><span data-stu-id="924ff-116">Where `Microsoft.NET.Test.Sdk` is the test host, `xunit` is the test framework.</span></span> <span data-ttu-id="924ff-117">和 `xunit.runner.visualstudio` 是一個測試介面卡，可讓 xUnit 架構與測試主機搭配使用。</span><span class="sxs-lookup"><span data-stu-id="924ff-117">And `xunit.runner.visualstudio` is a test adapter, which allows the xUnit framework to work with the test host.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="924ff-118">隱含還原</span><span class="sxs-lookup"><span data-stu-id="924ff-118">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="924ff-119">引數</span><span class="sxs-lookup"><span data-stu-id="924ff-119">Arguments</span></span>

- **`PROJECT | SOLUTION | DIRECTORY | DLL`**

  - <span data-ttu-id="924ff-120">測試專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="924ff-120">Path to the test project.</span></span>
  - <span data-ttu-id="924ff-121">解決方案的路徑。</span><span class="sxs-lookup"><span data-stu-id="924ff-121">Path to the solution.</span></span>
  - <span data-ttu-id="924ff-122">包含專案或方案之目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="924ff-122">Path to a directory that contains a project or a solution.</span></span>
  - <span data-ttu-id="924ff-123">測試專案 *.dll*檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="924ff-123">Path to a test project *.dll* file.</span></span>

  <span data-ttu-id="924ff-124">如果未指定，則會搜尋目前目錄中的專案或方案。</span><span class="sxs-lookup"><span data-stu-id="924ff-124">If not specified, it searches for a project or a solution in the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="924ff-125">選項</span><span class="sxs-lookup"><span data-stu-id="924ff-125">Options</span></span>

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="924ff-126">要搜尋其他測試介面卡之目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="924ff-126">Path to a directory to be searched for additional test adapters.</span></span> <span data-ttu-id="924ff-127">只會檢查具有尾碼的 *.dll*檔案 `.TestAdapter.dll` 。</span><span class="sxs-lookup"><span data-stu-id="924ff-127">Only *.dll* files with suffix `.TestAdapter.dll` are inspected.</span></span> <span data-ttu-id="924ff-128">如果未指定，則會搜尋 test *.dll*的目錄。</span><span class="sxs-lookup"><span data-stu-id="924ff-128">If not specified, the directory of the test *.dll* is searched.</span></span>

- **`--blame`**

  <span data-ttu-id="924ff-129">在歸責模式下執行測試。</span><span class="sxs-lookup"><span data-stu-id="924ff-129">Runs the tests in blame mode.</span></span> <span data-ttu-id="924ff-130">此選項有助於隔離導致測試主控制項損毀的問題測試。</span><span class="sxs-lookup"><span data-stu-id="924ff-130">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="924ff-131">當偵測到損毀時，它會在中建立一個序列檔案 `TestResults/<Guid>/<Guid>_Sequence.xml` ，以捕捉損毀前執行的測試順序。</span><span class="sxs-lookup"><span data-stu-id="924ff-131">When a crash is detected, it creates an sequence file in `TestResults/<Guid>/<Guid>_Sequence.xml` that captures the order of tests that were run before the crash.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="924ff-132">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="924ff-132">Defines the build configuration.</span></span> <span data-ttu-id="924ff-133">預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。</span><span class="sxs-lookup"><span data-stu-id="924ff-133">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="924ff-134">測試回合啟用資料收集器。</span><span class="sxs-lookup"><span data-stu-id="924ff-134">Enables data collector for the test run.</span></span> <span data-ttu-id="924ff-135">如需詳細資訊，請參閱[監視及分析測試回合](https://aka.ms/vstest-collect)。</span><span class="sxs-lookup"><span data-stu-id="924ff-135">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="924ff-136">啟用測試平臺的診斷模式，並將診斷訊息寫入至指定的檔案和其旁邊的檔案。</span><span class="sxs-lookup"><span data-stu-id="924ff-136">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file and to files next to it.</span></span> <span data-ttu-id="924ff-137">記錄訊息的程式會決定要建立哪些檔案（例如， `*.host_<date>.txt` 用於測試主機記錄檔），以及 `*.datacollector_<date>.txt` 用於資料收集器記錄檔的進程。</span><span class="sxs-lookup"><span data-stu-id="924ff-137">The process that is logging the messages determines which files are created, such as `*.host_<date>.txt` for test host log, and `*.datacollector_<date>.txt` for data collector log.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="924ff-138">強制 `dotnet` 針對測試二進位檔使用或 .NET Framework 測試主機。</span><span class="sxs-lookup"><span data-stu-id="924ff-138">Forces the use of `dotnet` or .NET Framework test host for the test binaries.</span></span> <span data-ttu-id="924ff-139">此選項只會決定要使用的主機類型。</span><span class="sxs-lookup"><span data-stu-id="924ff-139">This option only determines which type of host to use.</span></span> <span data-ttu-id="924ff-140">實際使用的 framework 版本是由測試專案的 *.runtimeconfig.json*所決定。</span><span class="sxs-lookup"><span data-stu-id="924ff-140">The actual framework version to be used is determined by the *runtimeconfig.json* of the test project.</span></span> <span data-ttu-id="924ff-141">若未指定，則會使用[TargetFramework 元件屬性](/dotnet/api/system.runtime.versioning.targetframeworkattribute)來判斷主機的類型。</span><span class="sxs-lookup"><span data-stu-id="924ff-141">When not specified, the [TargetFramework assembly attribute](/dotnet/api/system.runtime.versioning.targetframeworkattribute) is used to determine the type of host.</span></span> <span data-ttu-id="924ff-142">從 *.dll*中移除該屬性時，會使用 .NET Framework 主機。</span><span class="sxs-lookup"><span data-stu-id="924ff-142">When that attribute is stripped from the *.dll*, the .NET Framework host is used.</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="924ff-143">使用指定的運算式篩選出目前專案中的測試。</span><span class="sxs-lookup"><span data-stu-id="924ff-143">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="924ff-144">如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。</span><span class="sxs-lookup"><span data-stu-id="924ff-144">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="924ff-145">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="924ff-145">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="924ff-146">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="924ff-146">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="924ff-147">可讓命令停止，並等候使用者輸入或進行動作。</span><span class="sxs-lookup"><span data-stu-id="924ff-147">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="924ff-148">例如完成驗證。</span><span class="sxs-lookup"><span data-stu-id="924ff-148">For example, to complete authentication.</span></span> <span data-ttu-id="924ff-149">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="924ff-149">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="924ff-150">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="924ff-150">Specifies a logger for test results.</span></span> <span data-ttu-id="924ff-151">不同于 MSBuild，dotnet 測試不接受縮寫：而不是 `-l "console;v=d"` 使用 `-l "console;verbosity=detailed"` 。</span><span class="sxs-lookup"><span data-stu-id="924ff-151">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="924ff-152">不會在執行前建置測試專案。</span><span class="sxs-lookup"><span data-stu-id="924ff-152">Doesn't build the test project before running it.</span></span> <span data-ttu-id="924ff-153">它也會隱含地設定- `--no-restore` 旗標。</span><span class="sxs-lookup"><span data-stu-id="924ff-153">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="924ff-154">執行測試而不顯示 Microsoft TestPlatform 橫幅。</span><span class="sxs-lookup"><span data-stu-id="924ff-154">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="924ff-155">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="924ff-155">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="924ff-156">執行命令時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="924ff-156">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="924ff-157">在其中尋找要執行的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="924ff-157">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="924ff-158">如果未指定，則預設路徑為 `./bin/<configuration>/<framework>/`。</span><span class="sxs-lookup"><span data-stu-id="924ff-158">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="924ff-159">針對具有多個目標 framework 的專案（透過 `TargetFrameworks` 屬性），您也需要在 `--framework` 指定此選項時定義。</span><span class="sxs-lookup"><span data-stu-id="924ff-159">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="924ff-160">`dotnet test`一律從輸出目錄執行測試。</span><span class="sxs-lookup"><span data-stu-id="924ff-160">`dotnet test` always runs tests from the output directory.</span></span> <span data-ttu-id="924ff-161">您可以使用 <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> 來取用輸出目錄中的測試資產。</span><span class="sxs-lookup"><span data-stu-id="924ff-161">You can use <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> to consume test assets in the output directory.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="924ff-162">要放置測試結果的目錄。</span><span class="sxs-lookup"><span data-stu-id="924ff-162">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="924ff-163">如果指定的目錄不存在，則會建立該目錄。</span><span class="sxs-lookup"><span data-stu-id="924ff-163">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="924ff-164">預設值是 `TestResults` 在包含專案檔的目錄中。</span><span class="sxs-lookup"><span data-stu-id="924ff-164">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="924ff-165">要測試的目標執行時間。</span><span class="sxs-lookup"><span data-stu-id="924ff-165">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="924ff-166">用來執行測試的 `.runsettings` 檔案。</span><span class="sxs-lookup"><span data-stu-id="924ff-166">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="924ff-167">請注意， `TargetPlatform` 元素（x86 | x64）對沒有任何作用 `dotnet test` 。</span><span class="sxs-lookup"><span data-stu-id="924ff-167">Note that the `TargetPlatform` element (x86|x64) has no effect for `dotnet test`.</span></span> <span data-ttu-id="924ff-168">若要執行以 x86 為目標的測試，請安裝 x86 版本的 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="924ff-168">To run tests that target x86, install the x86 version of .NET Core.</span></span> <span data-ttu-id="924ff-169">路徑上*dotnet*的位就是用來執行測試的。</span><span class="sxs-lookup"><span data-stu-id="924ff-169">The bitness of the *dotnet.exe* that is on the path is what will be used for running tests.</span></span> <span data-ttu-id="924ff-170">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="924ff-170">For more information, see the following resources:</span></span>

  - <span data-ttu-id="924ff-171">[使用 `.runsettings` 檔案設定單元測試](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)。</span><span class="sxs-lookup"><span data-stu-id="924ff-171">[Configure unit tests by using a `.runsettings` file.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)</span></span>
  - <span data-ttu-id="924ff-172">[設定測試回合](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="924ff-172">[Configure a test run](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)</span></span>

- **`-t|--list-tests`**

  <span data-ttu-id="924ff-173">列出在目前專案中探索到的所有測試。</span><span class="sxs-lookup"><span data-stu-id="924ff-173">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="924ff-174">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="924ff-174">Sets the verbosity level of the command.</span></span> <span data-ttu-id="924ff-175">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="924ff-175">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="924ff-176">預設值為 `minimal`。</span><span class="sxs-lookup"><span data-stu-id="924ff-176">The default is `minimal`.</span></span> <span data-ttu-id="924ff-177">如需詳細資訊，請參閱<xref:Microsoft.Build.Framework.LoggerVerbosity>。</span><span class="sxs-lookup"><span data-stu-id="924ff-177">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="924ff-178">**`RunSettings`** 參量</span><span class="sxs-lookup"><span data-stu-id="924ff-178">**`RunSettings`** arguments</span></span>

 <span data-ttu-id="924ff-179">在 `RunSettings` "--" 之後，內嵌會當做命令列上的最後一個引數傳遞（請注意--後面的空格）。</span><span class="sxs-lookup"><span data-stu-id="924ff-179">Inline `RunSettings` are passed as the last arguments on the command line after "-- " (note the space after --).</span></span> <span data-ttu-id="924ff-180">Inline `RunSettings` 會指定 `[name]=[value]` 成對的。</span><span class="sxs-lookup"><span data-stu-id="924ff-180">Inline `RunSettings` are specified as `[name]=[value]` pairs.</span></span> <span data-ttu-id="924ff-181">空格適用來分隔多個 `[name]=[value]` 組。</span><span class="sxs-lookup"><span data-stu-id="924ff-181">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="924ff-182">範例：`dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="924ff-182">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="924ff-183">如需詳細資訊，請參閱[透過命令列傳遞 .runsettings 引數](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)。</span><span class="sxs-lookup"><span data-stu-id="924ff-183">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="924ff-184">範例</span><span class="sxs-lookup"><span data-stu-id="924ff-184">Examples</span></span>

- <span data-ttu-id="924ff-185">執行目前目錄之專案中的測試：</span><span class="sxs-lookup"><span data-stu-id="924ff-185">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="924ff-186">執行 `test1` 專案中的測試︰</span><span class="sxs-lookup"><span data-stu-id="924ff-186">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="924ff-187">在目前目錄的專案中執行測試，並產生 .trx 格式的測試結果檔案：</span><span class="sxs-lookup"><span data-stu-id="924ff-187">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="924ff-188">在目前目錄中執行專案中的測試，並使用主控台的詳細詳細資訊記錄：</span><span class="sxs-lookup"><span data-stu-id="924ff-188">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```
  
  - <span data-ttu-id="924ff-189">在目前目錄中的專案中執行測試，並在測試主控制項損毀時回報進行中的測試：</span><span class="sxs-lookup"><span data-stu-id="924ff-189">Run the tests in the project in the current directory, and report tests that were in progress when the test host crashed:</span></span>

  ```dotnetcli
  dotnet test --blame
  ```

## <a name="filter-option-details"></a><span data-ttu-id="924ff-190">篩選選項詳細資料</span><span class="sxs-lookup"><span data-stu-id="924ff-190">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="924ff-191">`<Expression>` 的格式為 `<property><operator><value>[|&<Expression>]`。</span><span class="sxs-lookup"><span data-stu-id="924ff-191">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="924ff-192">`<property>` 為 `Test Case` 的屬性。</span><span class="sxs-lookup"><span data-stu-id="924ff-192">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="924ff-193">以下為熱門單元測試架構所支援的屬性：</span><span class="sxs-lookup"><span data-stu-id="924ff-193">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="924ff-194">測試架構</span><span class="sxs-lookup"><span data-stu-id="924ff-194">Test Framework</span></span> | <span data-ttu-id="924ff-195">支援的屬性</span><span class="sxs-lookup"><span data-stu-id="924ff-195">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="924ff-196">MSTest</span><span class="sxs-lookup"><span data-stu-id="924ff-196">MSTest</span></span>         | <ul><li><span data-ttu-id="924ff-197">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="924ff-197">FullyQualifiedName</span></span></li><li><span data-ttu-id="924ff-198">名稱</span><span class="sxs-lookup"><span data-stu-id="924ff-198">Name</span></span></li><li><span data-ttu-id="924ff-199">ClassName</span><span class="sxs-lookup"><span data-stu-id="924ff-199">ClassName</span></span></li><li><span data-ttu-id="924ff-200">優先順序</span><span class="sxs-lookup"><span data-stu-id="924ff-200">Priority</span></span></li><li><span data-ttu-id="924ff-201">TestCategory</span><span class="sxs-lookup"><span data-stu-id="924ff-201">TestCategory</span></span></li></ul> |
| <span data-ttu-id="924ff-202">xUnit</span><span class="sxs-lookup"><span data-stu-id="924ff-202">xUnit</span></span>          | <ul><li><span data-ttu-id="924ff-203">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="924ff-203">FullyQualifiedName</span></span></li><li><span data-ttu-id="924ff-204">DisplayName</span><span class="sxs-lookup"><span data-stu-id="924ff-204">DisplayName</span></span></li><li><span data-ttu-id="924ff-205">特性</span><span class="sxs-lookup"><span data-stu-id="924ff-205">Traits</span></span></li></ul>                                   |

<span data-ttu-id="924ff-206">`<operator>` 描述屬性和值之間的關聯性：</span><span class="sxs-lookup"><span data-stu-id="924ff-206">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="924ff-207">運算子</span><span class="sxs-lookup"><span data-stu-id="924ff-207">Operator</span></span> | <span data-ttu-id="924ff-208">函式</span><span class="sxs-lookup"><span data-stu-id="924ff-208">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="924ff-209">完全相符</span><span class="sxs-lookup"><span data-stu-id="924ff-209">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="924ff-210">不完全相符</span><span class="sxs-lookup"><span data-stu-id="924ff-210">Not exact match</span></span> |
| `~`      | <span data-ttu-id="924ff-211">包含</span><span class="sxs-lookup"><span data-stu-id="924ff-211">Contains</span></span>        |
| `!~`     | <span data-ttu-id="924ff-212">不包含</span><span class="sxs-lookup"><span data-stu-id="924ff-212">Not contains</span></span>    |

<span data-ttu-id="924ff-213">`<value>` 為字串。</span><span class="sxs-lookup"><span data-stu-id="924ff-213">`<value>` is a string.</span></span> <span data-ttu-id="924ff-214">所有的查閱皆不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="924ff-214">All the lookups are case insensitive.</span></span>

<span data-ttu-id="924ff-215">沒有 `<operator>` 的運算式會自動被視為 `FullyQualifiedName` 屬性上的 `contains` (例如，`dotnet test --filter xyz` 等同於 `dotnet test --filter FullyQualifiedName~xyz`)。</span><span class="sxs-lookup"><span data-stu-id="924ff-215">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="924ff-216">運算式可以使用條件運算子聯結：</span><span class="sxs-lookup"><span data-stu-id="924ff-216">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="924ff-217">運算子</span><span class="sxs-lookup"><span data-stu-id="924ff-217">Operator</span></span>            | <span data-ttu-id="924ff-218">函式</span><span class="sxs-lookup"><span data-stu-id="924ff-218">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="924ff-219">OR</span><span class="sxs-lookup"><span data-stu-id="924ff-219">OR</span></span>       |
| `&`                 | <span data-ttu-id="924ff-220">AND</span><span class="sxs-lookup"><span data-stu-id="924ff-220">AND</span></span>      |

<span data-ttu-id="924ff-221">使用條件運算子時，您可以使用括弧括住運算式 (例如，`(Name~TestMethod1) | (Name~TestMethod2)`)。</span><span class="sxs-lookup"><span data-stu-id="924ff-221">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="924ff-222">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="924ff-222">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="924ff-223">另請參閱</span><span class="sxs-lookup"><span data-stu-id="924ff-223">See also</span></span>

- [<span data-ttu-id="924ff-224">架構和目標</span><span class="sxs-lookup"><span data-stu-id="924ff-224">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="924ff-225">.NET Core 執行階段識別項 (RID) 目錄</span><span class="sxs-lookup"><span data-stu-id="924ff-225">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="924ff-226">透過命令列傳遞 .runsettings 引數</span><span class="sxs-lookup"><span data-stu-id="924ff-226">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
