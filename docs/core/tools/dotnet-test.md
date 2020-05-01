---
title: dotnet test 命令
description: dotnet test 命令是用來在指定的專案中執行單元測試。
ms.date: 04/29/2020
ms.openlocfilehash: a8218b6596601069b89a60ad018adf89a1f47cf6
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624887"
---
# <a name="dotnet-test"></a><span data-ttu-id="f78fa-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="f78fa-103">dotnet test</span></span>

<span data-ttu-id="f78fa-104">**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="f78fa-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f78fa-105">名稱</span><span class="sxs-lookup"><span data-stu-id="f78fa-105">Name</span></span>

<span data-ttu-id="f78fa-106">`dotnet test` - 用來執行單元測試的 .NET 測試驅動程式。</span><span class="sxs-lookup"><span data-stu-id="f78fa-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f78fa-107">概要</span><span class="sxs-lookup"><span data-stu-id="f78fa-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION>]
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

## <a name="description"></a><span data-ttu-id="f78fa-108">描述</span><span class="sxs-lookup"><span data-stu-id="f78fa-108">Description</span></span>

<span data-ttu-id="f78fa-109">`dotnet test` 命令是用來在指定的專案中執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="f78fa-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="f78fa-110">`dotnet test` 命令會啟動為專案指定的測試執行器主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="f78fa-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="f78fa-111">測試執行器會執行針對單元測試架構 (例如 MSTest、NUnit 或 xUnit) 定義的測試，並報告每項測試成功還是失敗。</span><span class="sxs-lookup"><span data-stu-id="f78fa-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="f78fa-112">如果所有測試都成功，則測試執行器會傳回 0 作為結束代碼；如果有任何測試失敗，則會傳回 1。</span><span class="sxs-lookup"><span data-stu-id="f78fa-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="f78fa-113">針對多目標專案，會針對每個目標架構執行測試。</span><span class="sxs-lookup"><span data-stu-id="f78fa-113">For multi-targeted projects, tests are run for each targeted framework.</span></span> <span data-ttu-id="f78fa-114">測試執行器和單元測試程式庫會封裝為 NuGet 套件，並還原為專案的一般相依性。</span><span class="sxs-lookup"><span data-stu-id="f78fa-114">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="f78fa-115">測試專案會使用一般 `<PackageReference>` 元素指定測試執行器，如下列範例專案檔中所示：</span><span class="sxs-lookup"><span data-stu-id="f78fa-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

### <a name="implicit-restore"></a><span data-ttu-id="f78fa-116">隱含還原</span><span class="sxs-lookup"><span data-stu-id="f78fa-116">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="f78fa-117">引數</span><span class="sxs-lookup"><span data-stu-id="f78fa-117">Arguments</span></span>

- **`PROJECT | SOLUTION`**

  <span data-ttu-id="f78fa-118">測試專案或方案的路徑。</span><span class="sxs-lookup"><span data-stu-id="f78fa-118">Path to the test project or solution.</span></span> <span data-ttu-id="f78fa-119">如果未指定，則會預設為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="f78fa-119">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="f78fa-120">選項。</span><span class="sxs-lookup"><span data-stu-id="f78fa-120">Options</span></span>

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="f78fa-121">在測試執行中，從指定的路徑使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="f78fa-121">Use the custom test adapters from the specified path in the test run.</span></span>

- **`--blame`**

  <span data-ttu-id="f78fa-122">在歸責模式下執行測試。</span><span class="sxs-lookup"><span data-stu-id="f78fa-122">Runs the tests in blame mode.</span></span> <span data-ttu-id="f78fa-123">此選項有助於隔離導致測試主控制項損毀的問題測試。</span><span class="sxs-lookup"><span data-stu-id="f78fa-123">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="f78fa-124">它會以 *Sequence.xml* 的形式在目前目錄中建立一個輸出檔，用來擷取損毀前的測試執行順序。</span><span class="sxs-lookup"><span data-stu-id="f78fa-124">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="f78fa-125">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="f78fa-125">Defines the build configuration.</span></span> <span data-ttu-id="f78fa-126">預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。</span><span class="sxs-lookup"><span data-stu-id="f78fa-126">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="f78fa-127">測試回合啟用資料收集器。</span><span class="sxs-lookup"><span data-stu-id="f78fa-127">Enables data collector for the test run.</span></span> <span data-ttu-id="f78fa-128">如需詳細資訊，請參閱[監視及分析測試回合](https://aka.ms/vstest-collect)。</span><span class="sxs-lookup"><span data-stu-id="f78fa-128">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="f78fa-129">啟用測試平臺的診斷模式，並將診斷訊息寫入至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="f78fa-129">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f78fa-130">尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。</span><span class="sxs-lookup"><span data-stu-id="f78fa-130">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="f78fa-131">使用指定的運算式篩選出目前專案中的測試。</span><span class="sxs-lookup"><span data-stu-id="f78fa-131">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="f78fa-132">如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。</span><span class="sxs-lookup"><span data-stu-id="f78fa-132">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="f78fa-133">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="f78fa-133">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="f78fa-134">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="f78fa-134">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="f78fa-135">可讓命令停止，並等候使用者輸入或進行動作。</span><span class="sxs-lookup"><span data-stu-id="f78fa-135">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="f78fa-136">例如完成驗證。</span><span class="sxs-lookup"><span data-stu-id="f78fa-136">For example, to complete authentication.</span></span> <span data-ttu-id="f78fa-137">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="f78fa-137">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="f78fa-138">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="f78fa-138">Specifies a logger for test results.</span></span> <span data-ttu-id="f78fa-139">不同于`-l "console;v=d"` MSBuild，dotnet 測試不接受縮寫：而不`-l "console;verbosity=detailed"`是使用。</span><span class="sxs-lookup"><span data-stu-id="f78fa-139">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="f78fa-140">不會在執行前建置測試專案。</span><span class="sxs-lookup"><span data-stu-id="f78fa-140">Doesn't build the test project before running it.</span></span> <span data-ttu-id="f78fa-141">它也會隱含地設定`--no-restore` -旗標。</span><span class="sxs-lookup"><span data-stu-id="f78fa-141">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="f78fa-142">執行測試而不顯示 Microsoft TestPlatform 橫幅。</span><span class="sxs-lookup"><span data-stu-id="f78fa-142">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="f78fa-143">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="f78fa-143">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="f78fa-144">執行命令時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="f78fa-144">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="f78fa-145">在其中尋找要執行的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="f78fa-145">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="f78fa-146">如果未指定，則預設路徑為 `./bin/<configuration>/<framework>/`。</span><span class="sxs-lookup"><span data-stu-id="f78fa-146">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="f78fa-147">針對具有多個目標 framework 的專案（ `TargetFrameworks`透過屬性），您也需要在`--framework`指定此選項時定義。</span><span class="sxs-lookup"><span data-stu-id="f78fa-147">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="f78fa-148">`dotnet test`一律從輸出目錄執行測試。</span><span class="sxs-lookup"><span data-stu-id="f78fa-148">`dotnet test` always run tests from the output directory.</span></span> <span data-ttu-id="f78fa-149">您可以使用<xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType>來取用輸出目錄中的測試資產。</span><span class="sxs-lookup"><span data-stu-id="f78fa-149">You can use <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> to consume test assets in the output directory.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="f78fa-150">要放置測試結果的目錄。</span><span class="sxs-lookup"><span data-stu-id="f78fa-150">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="f78fa-151">如果指定的目錄不存在，則會建立該目錄。</span><span class="sxs-lookup"><span data-stu-id="f78fa-151">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="f78fa-152">預設值是`TestResults`在包含專案檔的目錄中。</span><span class="sxs-lookup"><span data-stu-id="f78fa-152">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="f78fa-153">要測試的目標執行時間。</span><span class="sxs-lookup"><span data-stu-id="f78fa-153">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="f78fa-154">用來執行測試的 `.runsettings` 檔案。</span><span class="sxs-lookup"><span data-stu-id="f78fa-154">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="f78fa-155">請注意， `TargetPlatform`元素（x86 | x64）對沒有任何作用`dotnet test`。</span><span class="sxs-lookup"><span data-stu-id="f78fa-155">Note that the `TargetPlatform` element (x86|x64) has no effect for `dotnet test`.</span></span> <span data-ttu-id="f78fa-156">若要執行以 x86 為目標的測試，請安裝 x86 版本的 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="f78fa-156">To run tests that target x86, install the x86 version of .NET Core.</span></span> <span data-ttu-id="f78fa-157">路徑上*dotnet*的位就是用來執行測試的。</span><span class="sxs-lookup"><span data-stu-id="f78fa-157">The bitness of the *dotnet.exe* that is on the path is what will be used for running tests.</span></span> <span data-ttu-id="f78fa-158">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="f78fa-158">for more information, see the following resources:</span></span>

  - <span data-ttu-id="f78fa-159">[使用 `.runsettings` 檔案設定單元測試](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)。</span><span class="sxs-lookup"><span data-stu-id="f78fa-159">[Configure unit tests by using a `.runsettings` file.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)</span></span>
  - <span data-ttu-id="f78fa-160">[設定測試回合](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="f78fa-160">[Configure a test run](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)</span></span>

- **`-t|--list-tests`**

  <span data-ttu-id="f78fa-161">列出在目前專案中探索到的所有測試。</span><span class="sxs-lookup"><span data-stu-id="f78fa-161">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="f78fa-162">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="f78fa-162">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f78fa-163">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="f78fa-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="f78fa-164">預設值為 `minimal`。</span><span class="sxs-lookup"><span data-stu-id="f78fa-164">The default is `minimal`.</span></span> <span data-ttu-id="f78fa-165">如需詳細資訊，請參閱 <xref:Microsoft.Build.Framework.LoggerVerbosity>。</span><span class="sxs-lookup"><span data-stu-id="f78fa-165">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="f78fa-166">**`RunSettings`** 參量</span><span class="sxs-lookup"><span data-stu-id="f78fa-166">**`RunSettings`** arguments</span></span>

  <span data-ttu-id="f78fa-167">引數會當做`RunSettings`測試的設定來傳遞。</span><span class="sxs-lookup"><span data-stu-id="f78fa-167">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="f78fa-168">指定為 "-- " 後 (注意 -- 後方的空格) 之 `[name]=[value]` 組的引數。</span><span class="sxs-lookup"><span data-stu-id="f78fa-168">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="f78fa-169">空格適用來分隔多個 `[name]=[value]` 組。</span><span class="sxs-lookup"><span data-stu-id="f78fa-169">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="f78fa-170">範例： `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="f78fa-170">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="f78fa-171">如需詳細資訊，請參閱[透過命令列傳遞 .runsettings 引數](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)。</span><span class="sxs-lookup"><span data-stu-id="f78fa-171">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="f78fa-172">範例</span><span class="sxs-lookup"><span data-stu-id="f78fa-172">Examples</span></span>

- <span data-ttu-id="f78fa-173">執行目前目錄之專案中的測試：</span><span class="sxs-lookup"><span data-stu-id="f78fa-173">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="f78fa-174">執行 `test1` 專案中的測試︰</span><span class="sxs-lookup"><span data-stu-id="f78fa-174">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="f78fa-175">在目前目錄的專案中執行測試，並產生 .trx 格式的測試結果檔案：</span><span class="sxs-lookup"><span data-stu-id="f78fa-175">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="f78fa-176">在目前目錄中執行專案中的測試，並使用主控台的詳細詳細資訊記錄：</span><span class="sxs-lookup"><span data-stu-id="f78fa-176">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

## <a name="filter-option-details"></a><span data-ttu-id="f78fa-177">篩選選項詳細資料</span><span class="sxs-lookup"><span data-stu-id="f78fa-177">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="f78fa-178">`<Expression>` 的格式為 `<property><operator><value>[|&<Expression>]`。</span><span class="sxs-lookup"><span data-stu-id="f78fa-178">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="f78fa-179">`<property>` 為 `Test Case` 的屬性。</span><span class="sxs-lookup"><span data-stu-id="f78fa-179">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="f78fa-180">以下為熱門單元測試架構所支援的屬性：</span><span class="sxs-lookup"><span data-stu-id="f78fa-180">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="f78fa-181">測試架構</span><span class="sxs-lookup"><span data-stu-id="f78fa-181">Test Framework</span></span> | <span data-ttu-id="f78fa-182">支援的屬性</span><span class="sxs-lookup"><span data-stu-id="f78fa-182">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="f78fa-183">MSTest</span><span class="sxs-lookup"><span data-stu-id="f78fa-183">MSTest</span></span>         | <ul><li><span data-ttu-id="f78fa-184">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="f78fa-184">FullyQualifiedName</span></span></li><li><span data-ttu-id="f78fa-185">名稱</span><span class="sxs-lookup"><span data-stu-id="f78fa-185">Name</span></span></li><li><span data-ttu-id="f78fa-186">ClassName</span><span class="sxs-lookup"><span data-stu-id="f78fa-186">ClassName</span></span></li><li><span data-ttu-id="f78fa-187">優先順序</span><span class="sxs-lookup"><span data-stu-id="f78fa-187">Priority</span></span></li><li><span data-ttu-id="f78fa-188">TestCategory</span><span class="sxs-lookup"><span data-stu-id="f78fa-188">TestCategory</span></span></li></ul> |
| <span data-ttu-id="f78fa-189">xUnit</span><span class="sxs-lookup"><span data-stu-id="f78fa-189">xUnit</span></span>          | <ul><li><span data-ttu-id="f78fa-190">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="f78fa-190">FullyQualifiedName</span></span></li><li><span data-ttu-id="f78fa-191">DisplayName</span><span class="sxs-lookup"><span data-stu-id="f78fa-191">DisplayName</span></span></li><li><span data-ttu-id="f78fa-192">特性</span><span class="sxs-lookup"><span data-stu-id="f78fa-192">Traits</span></span></li></ul>                                   |

<span data-ttu-id="f78fa-193">`<operator>` 描述屬性和值之間的關聯性：</span><span class="sxs-lookup"><span data-stu-id="f78fa-193">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="f78fa-194">運算子</span><span class="sxs-lookup"><span data-stu-id="f78fa-194">Operator</span></span> | <span data-ttu-id="f78fa-195">函式</span><span class="sxs-lookup"><span data-stu-id="f78fa-195">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="f78fa-196">完全相符</span><span class="sxs-lookup"><span data-stu-id="f78fa-196">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="f78fa-197">不完全相符</span><span class="sxs-lookup"><span data-stu-id="f78fa-197">Not exact match</span></span> |
| `~`      | <span data-ttu-id="f78fa-198">包含</span><span class="sxs-lookup"><span data-stu-id="f78fa-198">Contains</span></span>        |
| `!~`     | <span data-ttu-id="f78fa-199">不包含</span><span class="sxs-lookup"><span data-stu-id="f78fa-199">Not contains</span></span>    |

<span data-ttu-id="f78fa-200">`<value>` 為字串。</span><span class="sxs-lookup"><span data-stu-id="f78fa-200">`<value>` is a string.</span></span> <span data-ttu-id="f78fa-201">所有的查閱皆不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="f78fa-201">All the lookups are case insensitive.</span></span>

<span data-ttu-id="f78fa-202">沒有 `<operator>` 的運算式會自動被視為 `FullyQualifiedName` 屬性上的 `contains` (例如，`dotnet test --filter xyz` 等同於 `dotnet test --filter FullyQualifiedName~xyz`)。</span><span class="sxs-lookup"><span data-stu-id="f78fa-202">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="f78fa-203">運算式可以使用條件運算子聯結：</span><span class="sxs-lookup"><span data-stu-id="f78fa-203">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="f78fa-204">運算子</span><span class="sxs-lookup"><span data-stu-id="f78fa-204">Operator</span></span>            | <span data-ttu-id="f78fa-205">函式</span><span class="sxs-lookup"><span data-stu-id="f78fa-205">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="f78fa-206">或者</span><span class="sxs-lookup"><span data-stu-id="f78fa-206">OR</span></span>       |
| `&`                 | <span data-ttu-id="f78fa-207">AND</span><span class="sxs-lookup"><span data-stu-id="f78fa-207">AND</span></span>      |

<span data-ttu-id="f78fa-208">使用條件運算子時，您可以使用括弧括住運算式 (例如，`(Name~TestMethod1) | (Name~TestMethod2)`)。</span><span class="sxs-lookup"><span data-stu-id="f78fa-208">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="f78fa-209">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="f78fa-209">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f78fa-210">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f78fa-210">See also</span></span>

- [<span data-ttu-id="f78fa-211">架構和目標</span><span class="sxs-lookup"><span data-stu-id="f78fa-211">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="f78fa-212">.NET Core 執行階段識別項 (RID) 目錄</span><span class="sxs-lookup"><span data-stu-id="f78fa-212">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="f78fa-213">透過命令列傳遞 .runsettings 引數</span><span class="sxs-lookup"><span data-stu-id="f78fa-213">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
