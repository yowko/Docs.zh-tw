---
title: dotnet test 命令
description: dotnet test 命令是用來在指定的專案中執行單元測試。
ms.date: 02/27/2020
ms.openlocfilehash: 69b8101f9b1052f4726dce8a86234da99f5dc89c
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102735"
---
# <a name="dotnet-test"></a><span data-ttu-id="294bb-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="294bb-103">dotnet test</span></span>

<span data-ttu-id="294bb-104">**本文適用於:✔️** .NET 核心 2.1 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="294bb-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="294bb-105">名稱</span><span class="sxs-lookup"><span data-stu-id="294bb-105">Name</span></span>

<span data-ttu-id="294bb-106">`dotnet test` - 用來執行單元測試的 .NET 測試驅動程式。</span><span class="sxs-lookup"><span data-stu-id="294bb-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="294bb-107">概要</span><span class="sxs-lookup"><span data-stu-id="294bb-107">Synopsis</span></span>

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

## <a name="description"></a><span data-ttu-id="294bb-108">描述</span><span class="sxs-lookup"><span data-stu-id="294bb-108">Description</span></span>

<span data-ttu-id="294bb-109">`dotnet test` 命令是用來在指定的專案中執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="294bb-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="294bb-110">`dotnet test` 命令會啟動為專案指定的測試執行器主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="294bb-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="294bb-111">測試執行器會執行針對單元測試架構 (例如 MSTest、NUnit 或 xUnit) 定義的測試，並報告每項測試成功還是失敗。</span><span class="sxs-lookup"><span data-stu-id="294bb-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="294bb-112">如果所有測試都成功，則測試執行器會傳回 0 作為結束代碼；如果有任何測試失敗，則會傳回 1。</span><span class="sxs-lookup"><span data-stu-id="294bb-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="294bb-113">測試執行器和單元測試程式庫會封裝為 NuGet 套件，並還原為專案的一般相依性。</span><span class="sxs-lookup"><span data-stu-id="294bb-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="294bb-114">測試專案會使用一般 `<PackageReference>` 元素指定測試執行器，如下列範例專案檔中所示：</span><span class="sxs-lookup"><span data-stu-id="294bb-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

### <a name="implicit-restore"></a><span data-ttu-id="294bb-115">隱式還原</span><span class="sxs-lookup"><span data-stu-id="294bb-115">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="294bb-116">引數</span><span class="sxs-lookup"><span data-stu-id="294bb-116">Arguments</span></span>

- **`PROJECT | SOLUTION`**

  <span data-ttu-id="294bb-117">測試專案或解決方案的路徑。</span><span class="sxs-lookup"><span data-stu-id="294bb-117">Path to the test project or solution.</span></span> <span data-ttu-id="294bb-118">如果未指定，則會預設為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="294bb-118">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="294bb-119">選項。</span><span class="sxs-lookup"><span data-stu-id="294bb-119">Options</span></span>

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="294bb-120">在測試執行中，從指定的路徑使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="294bb-120">Use the custom test adapters from the specified path in the test run.</span></span>

- **`--blame`**

  <span data-ttu-id="294bb-121">在歸責模式下執行測試。</span><span class="sxs-lookup"><span data-stu-id="294bb-121">Runs the tests in blame mode.</span></span> <span data-ttu-id="294bb-122">此選項有助於隔離導致測試主機崩潰的問題測試。</span><span class="sxs-lookup"><span data-stu-id="294bb-122">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="294bb-123">它會以 *Sequence.xml* 的形式在目前目錄中建立一個輸出檔，用來擷取損毀前的測試執行順序。</span><span class="sxs-lookup"><span data-stu-id="294bb-123">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="294bb-124">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="294bb-124">Defines the build configuration.</span></span> <span data-ttu-id="294bb-125">預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。</span><span class="sxs-lookup"><span data-stu-id="294bb-125">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="294bb-126">測試回合啟用資料收集器。</span><span class="sxs-lookup"><span data-stu-id="294bb-126">Enables data collector for the test run.</span></span> <span data-ttu-id="294bb-127">如需詳細資訊，請參閱[監視及分析測試回合](https://aka.ms/vstest-collect)。</span><span class="sxs-lookup"><span data-stu-id="294bb-127">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="294bb-128">啟用測試平台的診斷模式,並將診斷消息寫入指定的檔。</span><span class="sxs-lookup"><span data-stu-id="294bb-128">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="294bb-129">尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。</span><span class="sxs-lookup"><span data-stu-id="294bb-129">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="294bb-130">使用指定的運算式篩選出目前專案中的測試。</span><span class="sxs-lookup"><span data-stu-id="294bb-130">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="294bb-131">如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。</span><span class="sxs-lookup"><span data-stu-id="294bb-131">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="294bb-132">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="294bb-132">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="294bb-133">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="294bb-133">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="294bb-134">可讓命令停止，並等候使用者輸入或進行動作。</span><span class="sxs-lookup"><span data-stu-id="294bb-134">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="294bb-135">例如完成驗證。</span><span class="sxs-lookup"><span data-stu-id="294bb-135">For example, to complete authentication.</span></span> <span data-ttu-id="294bb-136">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="294bb-136">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="294bb-137">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="294bb-137">Specifies a logger for test results.</span></span> <span data-ttu-id="294bb-138">與 MSBuild 不同,dotnet 測試不接受縮`-l "console;v=d"`寫`-l "console;verbosity=detailed"`:而不是使用 。</span><span class="sxs-lookup"><span data-stu-id="294bb-138">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="294bb-139">不會在執行前建置測試專案。</span><span class="sxs-lookup"><span data-stu-id="294bb-139">Doesn't build the test project before running it.</span></span> <span data-ttu-id="294bb-140">它還隱式設置`--no-restore`- 標誌。</span><span class="sxs-lookup"><span data-stu-id="294bb-140">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="294bb-141">在不顯示 Microsoft 測試平台橫幅的情況下運行測試。</span><span class="sxs-lookup"><span data-stu-id="294bb-141">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="294bb-142">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="294bb-142">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="294bb-143">執行命令時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="294bb-143">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="294bb-144">在其中尋找要執行的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="294bb-144">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="294bb-145">如果未指定，則預設路徑為 `./bin/<configuration>/<framework>/`。</span><span class="sxs-lookup"><span data-stu-id="294bb-145">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="294bb-146">對於具有多個目標框架的專案(通過`TargetFrameworks`屬性),還需要在指定此選項`--framework`時 定義。</span><span class="sxs-lookup"><span data-stu-id="294bb-146">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="294bb-147">要放置測試結果的目錄。</span><span class="sxs-lookup"><span data-stu-id="294bb-147">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="294bb-148">如果指定的目錄不存在，則會建立該目錄。</span><span class="sxs-lookup"><span data-stu-id="294bb-148">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="294bb-149">預設值在`TestResults`包含專案檔的目錄中。</span><span class="sxs-lookup"><span data-stu-id="294bb-149">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="294bb-150">要測試的目標運行時。</span><span class="sxs-lookup"><span data-stu-id="294bb-150">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="294bb-151">用來執行測試的 `.runsettings` 檔案。</span><span class="sxs-lookup"><span data-stu-id="294bb-151">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="294bb-152">[使用 `.runsettings` 檔案設定單元測試](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)。</span><span class="sxs-lookup"><span data-stu-id="294bb-152">[Configure unit tests by using a `.runsettings` file.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)</span></span>

- **`-t|--list-tests`**

  <span data-ttu-id="294bb-153">列出在目前專案中探索到的所有測試。</span><span class="sxs-lookup"><span data-stu-id="294bb-153">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="294bb-154">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="294bb-154">Sets the verbosity level of the command.</span></span> <span data-ttu-id="294bb-155">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="294bb-155">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="294bb-156">預設值為 `minimal`。</span><span class="sxs-lookup"><span data-stu-id="294bb-156">The default is `minimal`.</span></span> <span data-ttu-id="294bb-157">如需詳細資訊，請參閱 <xref:Microsoft.Build.Framework.LoggerVerbosity>。</span><span class="sxs-lookup"><span data-stu-id="294bb-157">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="294bb-158">**`RunSettings`** 參數</span><span class="sxs-lookup"><span data-stu-id="294bb-158">**`RunSettings`** arguments</span></span>

  <span data-ttu-id="294bb-159">參數作為`RunSettings`測試的配置傳遞。</span><span class="sxs-lookup"><span data-stu-id="294bb-159">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="294bb-160">指定為 "-- " 後 (注意 -- 後方的空格) 之 `[name]=[value]` 組的引數。</span><span class="sxs-lookup"><span data-stu-id="294bb-160">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="294bb-161">空格適用來分隔多個 `[name]=[value]` 組。</span><span class="sxs-lookup"><span data-stu-id="294bb-161">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="294bb-162">範例： `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="294bb-162">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="294bb-163">有關詳細資訊,請參閱[透過命令列傳遞 RunSettings 參數](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)。</span><span class="sxs-lookup"><span data-stu-id="294bb-163">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="294bb-164">範例</span><span class="sxs-lookup"><span data-stu-id="294bb-164">Examples</span></span>

- <span data-ttu-id="294bb-165">執行目前目錄之專案中的測試：</span><span class="sxs-lookup"><span data-stu-id="294bb-165">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="294bb-166">執行 `test1` 專案中的測試︰</span><span class="sxs-lookup"><span data-stu-id="294bb-166">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="294bb-167">在目前的目錄中執行項目中的測試,並產生 trx 格式的測試結果檔:</span><span class="sxs-lookup"><span data-stu-id="294bb-167">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="294bb-168">在目前目錄中的項目中執行測試,並記錄到主控台的詳細詳細詳細內容:</span><span class="sxs-lookup"><span data-stu-id="294bb-168">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

## <a name="filter-option-details"></a><span data-ttu-id="294bb-169">篩選選項詳細資料</span><span class="sxs-lookup"><span data-stu-id="294bb-169">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="294bb-170">`<Expression>` 的格式為 `<property><operator><value>[|&<Expression>]`。</span><span class="sxs-lookup"><span data-stu-id="294bb-170">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="294bb-171">`<property>` 為 `Test Case` 的屬性。</span><span class="sxs-lookup"><span data-stu-id="294bb-171">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="294bb-172">以下為熱門單元測試架構所支援的屬性：</span><span class="sxs-lookup"><span data-stu-id="294bb-172">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="294bb-173">測試架構</span><span class="sxs-lookup"><span data-stu-id="294bb-173">Test Framework</span></span> | <span data-ttu-id="294bb-174">支援的屬性</span><span class="sxs-lookup"><span data-stu-id="294bb-174">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="294bb-175">MSTest</span><span class="sxs-lookup"><span data-stu-id="294bb-175">MSTest</span></span>         | <ul><li><span data-ttu-id="294bb-176">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="294bb-176">FullyQualifiedName</span></span></li><li><span data-ttu-id="294bb-177">名稱</span><span class="sxs-lookup"><span data-stu-id="294bb-177">Name</span></span></li><li><span data-ttu-id="294bb-178">ClassName</span><span class="sxs-lookup"><span data-stu-id="294bb-178">ClassName</span></span></li><li><span data-ttu-id="294bb-179">優先順序</span><span class="sxs-lookup"><span data-stu-id="294bb-179">Priority</span></span></li><li><span data-ttu-id="294bb-180">TestCategory</span><span class="sxs-lookup"><span data-stu-id="294bb-180">TestCategory</span></span></li></ul> |
| <span data-ttu-id="294bb-181">xUnit</span><span class="sxs-lookup"><span data-stu-id="294bb-181">xUnit</span></span>          | <ul><li><span data-ttu-id="294bb-182">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="294bb-182">FullyQualifiedName</span></span></li><li><span data-ttu-id="294bb-183">DisplayName</span><span class="sxs-lookup"><span data-stu-id="294bb-183">DisplayName</span></span></li><li><span data-ttu-id="294bb-184">特性</span><span class="sxs-lookup"><span data-stu-id="294bb-184">Traits</span></span></li></ul>                                   |

<span data-ttu-id="294bb-185">`<operator>` 描述屬性和值之間的關聯性：</span><span class="sxs-lookup"><span data-stu-id="294bb-185">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="294bb-186">運算子</span><span class="sxs-lookup"><span data-stu-id="294bb-186">Operator</span></span> | <span data-ttu-id="294bb-187">函式</span><span class="sxs-lookup"><span data-stu-id="294bb-187">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="294bb-188">完全相符</span><span class="sxs-lookup"><span data-stu-id="294bb-188">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="294bb-189">不完全相符</span><span class="sxs-lookup"><span data-stu-id="294bb-189">Not exact match</span></span> |
| `~`      | <span data-ttu-id="294bb-190">包含</span><span class="sxs-lookup"><span data-stu-id="294bb-190">Contains</span></span>        |
| `!~`     | <span data-ttu-id="294bb-191">不包含</span><span class="sxs-lookup"><span data-stu-id="294bb-191">Not contains</span></span>    |

<span data-ttu-id="294bb-192">`<value>` 為字串。</span><span class="sxs-lookup"><span data-stu-id="294bb-192">`<value>` is a string.</span></span> <span data-ttu-id="294bb-193">所有的查閱皆不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="294bb-193">All the lookups are case insensitive.</span></span>

<span data-ttu-id="294bb-194">沒有 `<operator>` 的運算式會自動被視為 `FullyQualifiedName` 屬性上的 `contains` (例如，`dotnet test --filter xyz` 等同於 `dotnet test --filter FullyQualifiedName~xyz`)。</span><span class="sxs-lookup"><span data-stu-id="294bb-194">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="294bb-195">運算式可以使用條件運算子聯結：</span><span class="sxs-lookup"><span data-stu-id="294bb-195">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="294bb-196">運算子</span><span class="sxs-lookup"><span data-stu-id="294bb-196">Operator</span></span>            | <span data-ttu-id="294bb-197">函式</span><span class="sxs-lookup"><span data-stu-id="294bb-197">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="294bb-198">OR</span><span class="sxs-lookup"><span data-stu-id="294bb-198">OR</span></span>       |
| `&`                 | <span data-ttu-id="294bb-199">AND</span><span class="sxs-lookup"><span data-stu-id="294bb-199">AND</span></span>      |

<span data-ttu-id="294bb-200">使用條件運算子時，您可以使用括弧括住運算式 (例如，`(Name~TestMethod1) | (Name~TestMethod2)`)。</span><span class="sxs-lookup"><span data-stu-id="294bb-200">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="294bb-201">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="294bb-201">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="294bb-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="294bb-202">See also</span></span>

- [<span data-ttu-id="294bb-203">框架與目標</span><span class="sxs-lookup"><span data-stu-id="294bb-203">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="294bb-204">.NET Core 執行階段識別項 (RID) 目錄</span><span class="sxs-lookup"><span data-stu-id="294bb-204">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="294bb-205">以命令列傳遞執行設定參數</span><span class="sxs-lookup"><span data-stu-id="294bb-205">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
