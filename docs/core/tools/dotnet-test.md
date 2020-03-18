---
title: dotnet test 命令
description: dotnet test 命令是用來在指定的專案中執行單元測試。
ms.date: 02/27/2020
ms.openlocfilehash: bac2f0e613c34bc9f657551a5eac4038207a93ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847894"
---
# <a name="dotnet-test"></a><span data-ttu-id="b280e-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="b280e-103">dotnet test</span></span>

<span data-ttu-id="b280e-104">**本文適用于：✔️** .NET 核心 2.1 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="b280e-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="b280e-105">名稱</span><span class="sxs-lookup"><span data-stu-id="b280e-105">Name</span></span>

<span data-ttu-id="b280e-106">`dotnet test` - 用來執行單元測試的 .NET 測試驅動程式。</span><span class="sxs-lookup"><span data-stu-id="b280e-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b280e-107">概要</span><span class="sxs-lookup"><span data-stu-id="b280e-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION>]
    [-a|--test-adapter-path] [--blame] [-c|--configuration]
    [--collect] [-d|--diag] [-f|--framework] [--filter]
    [--interactive] [-l|--logger] [--no-build] [--nologo]
    [--no-restore] [-o|--output] [-r|--results-directory]
    [--runtime] [-s|--settings] [-t|--list-tests]
    [-v|--verbosity] [[--] <RunSettings arguments>]

dotnet test [-h|--help]
```

## <a name="description"></a><span data-ttu-id="b280e-108">描述</span><span class="sxs-lookup"><span data-stu-id="b280e-108">Description</span></span>

<span data-ttu-id="b280e-109">`dotnet test` 命令是用來在指定的專案中執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="b280e-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="b280e-110">`dotnet test` 命令會啟動為專案指定的測試執行器主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="b280e-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="b280e-111">測試執行器會執行針對單元測試架構 (例如 MSTest、NUnit 或 xUnit) 定義的測試，並報告每項測試成功還是失敗。</span><span class="sxs-lookup"><span data-stu-id="b280e-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="b280e-112">如果所有測試都成功，則測試執行器會傳回 0 作為結束代碼；如果有任何測試失敗，則會傳回 1。</span><span class="sxs-lookup"><span data-stu-id="b280e-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="b280e-113">測試執行器和單元測試程式庫會封裝為 NuGet 套件，並還原為專案的一般相依性。</span><span class="sxs-lookup"><span data-stu-id="b280e-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="b280e-114">測試專案會使用一般 `<PackageReference>` 元素指定測試執行器，如下列範例專案檔中所示：</span><span class="sxs-lookup"><span data-stu-id="b280e-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="b280e-115">引數</span><span class="sxs-lookup"><span data-stu-id="b280e-115">Arguments</span></span>

- **`PROJECT | SOLUTION`**

  <span data-ttu-id="b280e-116">測試專案或解決方案的路徑。</span><span class="sxs-lookup"><span data-stu-id="b280e-116">Path to the test project or solution.</span></span> <span data-ttu-id="b280e-117">如果未指定，則會預設為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="b280e-117">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="b280e-118">選項。</span><span class="sxs-lookup"><span data-stu-id="b280e-118">Options</span></span>

- **`a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="b280e-119">在測試執行中，從指定的路徑使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="b280e-119">Use the custom test adapters from the specified path in the test run.</span></span>

- **`-blame`**

  <span data-ttu-id="b280e-120">在歸責模式下執行測試。</span><span class="sxs-lookup"><span data-stu-id="b280e-120">Runs the tests in blame mode.</span></span> <span data-ttu-id="b280e-121">此選項有助於隔離導致測試主機崩潰的問題測試。</span><span class="sxs-lookup"><span data-stu-id="b280e-121">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="b280e-122">它會以 *Sequence.xml* 的形式在目前目錄中建立一個輸出檔，用來擷取損毀前的測試執行順序。</span><span class="sxs-lookup"><span data-stu-id="b280e-122">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="b280e-123">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="b280e-123">Defines the build configuration.</span></span> <span data-ttu-id="b280e-124">預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。</span><span class="sxs-lookup"><span data-stu-id="b280e-124">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`-collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="b280e-125">測試回合啟用資料收集器。</span><span class="sxs-lookup"><span data-stu-id="b280e-125">Enables data collector for the test run.</span></span> <span data-ttu-id="b280e-126">如需詳細資訊，請參閱[監視及分析測試回合](https://aka.ms/vstest-collect)。</span><span class="sxs-lookup"><span data-stu-id="b280e-126">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="b280e-127">針對測試平台啟用診斷模式，並將診斷訊息寫入至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="b280e-127">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

- **`f|--framework <FRAMEWORK>`**

  <span data-ttu-id="b280e-128">尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。</span><span class="sxs-lookup"><span data-stu-id="b280e-128">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="b280e-129">使用指定的運算式篩選出目前專案中的測試。</span><span class="sxs-lookup"><span data-stu-id="b280e-129">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="b280e-130">如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。</span><span class="sxs-lookup"><span data-stu-id="b280e-130">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="b280e-131">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="b280e-131">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`h|--help`**

  <span data-ttu-id="b280e-132">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="b280e-132">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="b280e-133">可讓命令停止，並等候使用者輸入或進行動作。</span><span class="sxs-lookup"><span data-stu-id="b280e-133">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="b280e-134">例如完成驗證。</span><span class="sxs-lookup"><span data-stu-id="b280e-134">For example, to complete authentication.</span></span> <span data-ttu-id="b280e-135">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="b280e-135">Available since .NET Core 3.0 SDK.</span></span>

- **`l|--logger <LoggerUri/FriendlyName>`**

  <span data-ttu-id="b280e-136">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="b280e-136">Specifies a logger for test results.</span></span>

- **`--no-build`**

  <span data-ttu-id="b280e-137">不會在執行前建置測試專案。</span><span class="sxs-lookup"><span data-stu-id="b280e-137">Doesn't build the test project before running it.</span></span> <span data-ttu-id="b280e-138">它還隱式設置 -`--no-restore`標誌。</span><span class="sxs-lookup"><span data-stu-id="b280e-138">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="b280e-139">在不顯示 Microsoft 測試平臺橫幅的情況下運行測試。</span><span class="sxs-lookup"><span data-stu-id="b280e-139">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="b280e-140">自 .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="b280e-140">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="b280e-141">執行命令時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="b280e-141">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="b280e-142">在其中尋找要執行的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="b280e-142">Directory in which to find the binaries to run.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="b280e-143">要放置測試結果的目錄。</span><span class="sxs-lookup"><span data-stu-id="b280e-143">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="b280e-144">如果指定的目錄不存在，則會建立該目錄。</span><span class="sxs-lookup"><span data-stu-id="b280e-144">If the specified directory doesn't exist, it's created.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="b280e-145">要測試的目標運行時。</span><span class="sxs-lookup"><span data-stu-id="b280e-145">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="b280e-146">用來執行測試的 `.runsettings` 檔案。</span><span class="sxs-lookup"><span data-stu-id="b280e-146">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="b280e-147">[使用 `.runsettings` 檔案設定單元測試](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)。</span><span class="sxs-lookup"><span data-stu-id="b280e-147">[Configure unit tests by using a `.runsettings` file.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)</span></span>

- **`-t|--list-tests`**

  <span data-ttu-id="b280e-148">列出在目前專案中探索到的所有測試。</span><span class="sxs-lookup"><span data-stu-id="b280e-148">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="b280e-149">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="b280e-149">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b280e-150">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="b280e-150">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- <span data-ttu-id="b280e-151">`RunSettings`參數</span><span class="sxs-lookup"><span data-stu-id="b280e-151">`RunSettings` arguments</span></span>

  <span data-ttu-id="b280e-152">參數作為`RunSettings`測試的配置傳遞。</span><span class="sxs-lookup"><span data-stu-id="b280e-152">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="b280e-153">指定為 "-- " 後 (注意 -- 後方的空格) 之 `[name]=[value]` 組的引數。</span><span class="sxs-lookup"><span data-stu-id="b280e-153">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="b280e-154">空格適用來分隔多個 `[name]=[value]` 組。</span><span class="sxs-lookup"><span data-stu-id="b280e-154">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="b280e-155">範例： `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="b280e-155">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="b280e-156">有關詳細資訊，請參閱[vstest.console.exe： 傳遞回合設定 args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)。</span><span class="sxs-lookup"><span data-stu-id="b280e-156">For more information, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="b280e-157">範例</span><span class="sxs-lookup"><span data-stu-id="b280e-157">Examples</span></span>

- <span data-ttu-id="b280e-158">執行目前目錄之專案中的測試：</span><span class="sxs-lookup"><span data-stu-id="b280e-158">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="b280e-159">執行 `test1` 專案中的測試︰</span><span class="sxs-lookup"><span data-stu-id="b280e-159">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="b280e-160">在目前目錄中的專案中執行測試，並以 trx 格式產生測試結果檔案：</span><span class="sxs-lookup"><span data-stu-id="b280e-160">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

## <a name="filter-option-details"></a><span data-ttu-id="b280e-161">篩選選項詳細資料</span><span class="sxs-lookup"><span data-stu-id="b280e-161">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="b280e-162">`<Expression>` 的格式為 `<property><operator><value>[|&<Expression>]`。</span><span class="sxs-lookup"><span data-stu-id="b280e-162">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="b280e-163">`<property>` 為 `Test Case` 的屬性。</span><span class="sxs-lookup"><span data-stu-id="b280e-163">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="b280e-164">以下為熱門單元測試架構所支援的屬性：</span><span class="sxs-lookup"><span data-stu-id="b280e-164">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="b280e-165">測試架構</span><span class="sxs-lookup"><span data-stu-id="b280e-165">Test Framework</span></span> | <span data-ttu-id="b280e-166">支援的屬性</span><span class="sxs-lookup"><span data-stu-id="b280e-166">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="b280e-167">MSTest</span><span class="sxs-lookup"><span data-stu-id="b280e-167">MSTest</span></span>         | <ul><li><span data-ttu-id="b280e-168">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="b280e-168">FullyQualifiedName</span></span></li><li><span data-ttu-id="b280e-169">名稱</span><span class="sxs-lookup"><span data-stu-id="b280e-169">Name</span></span></li><li><span data-ttu-id="b280e-170">ClassName</span><span class="sxs-lookup"><span data-stu-id="b280e-170">ClassName</span></span></li><li><span data-ttu-id="b280e-171">優先順序</span><span class="sxs-lookup"><span data-stu-id="b280e-171">Priority</span></span></li><li><span data-ttu-id="b280e-172">TestCategory</span><span class="sxs-lookup"><span data-stu-id="b280e-172">TestCategory</span></span></li></ul> |
| <span data-ttu-id="b280e-173">xUnit</span><span class="sxs-lookup"><span data-stu-id="b280e-173">xUnit</span></span>          | <ul><li><span data-ttu-id="b280e-174">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="b280e-174">FullyQualifiedName</span></span></li><li><span data-ttu-id="b280e-175">DisplayName</span><span class="sxs-lookup"><span data-stu-id="b280e-175">DisplayName</span></span></li><li><span data-ttu-id="b280e-176">特性</span><span class="sxs-lookup"><span data-stu-id="b280e-176">Traits</span></span></li></ul>                                   |

<span data-ttu-id="b280e-177">`<operator>` 描述屬性和值之間的關聯性：</span><span class="sxs-lookup"><span data-stu-id="b280e-177">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="b280e-178">運算子</span><span class="sxs-lookup"><span data-stu-id="b280e-178">Operator</span></span> | <span data-ttu-id="b280e-179">函式</span><span class="sxs-lookup"><span data-stu-id="b280e-179">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="b280e-180">完全相符</span><span class="sxs-lookup"><span data-stu-id="b280e-180">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="b280e-181">不完全相符</span><span class="sxs-lookup"><span data-stu-id="b280e-181">Not exact match</span></span> |
| `~`      | <span data-ttu-id="b280e-182">包含</span><span class="sxs-lookup"><span data-stu-id="b280e-182">Contains</span></span>        |
| `!~`     | <span data-ttu-id="b280e-183">不包含</span><span class="sxs-lookup"><span data-stu-id="b280e-183">Not contains</span></span>    |

<span data-ttu-id="b280e-184">`<value>` 為字串。</span><span class="sxs-lookup"><span data-stu-id="b280e-184">`<value>` is a string.</span></span> <span data-ttu-id="b280e-185">所有的查閱皆不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="b280e-185">All the lookups are case insensitive.</span></span>

<span data-ttu-id="b280e-186">沒有 `<operator>` 的運算式會自動被視為 `FullyQualifiedName` 屬性上的 `contains` (例如，`dotnet test --filter xyz` 等同於 `dotnet test --filter FullyQualifiedName~xyz`)。</span><span class="sxs-lookup"><span data-stu-id="b280e-186">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="b280e-187">運算式可以使用條件運算子聯結：</span><span class="sxs-lookup"><span data-stu-id="b280e-187">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="b280e-188">運算子</span><span class="sxs-lookup"><span data-stu-id="b280e-188">Operator</span></span>            | <span data-ttu-id="b280e-189">函式</span><span class="sxs-lookup"><span data-stu-id="b280e-189">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="b280e-190">OR</span><span class="sxs-lookup"><span data-stu-id="b280e-190">OR</span></span>       |
| `&`                 | <span data-ttu-id="b280e-191">AND</span><span class="sxs-lookup"><span data-stu-id="b280e-191">AND</span></span>      |

<span data-ttu-id="b280e-192">使用條件運算子時，您可以使用括弧括住運算式 (例如，`(Name~TestMethod1) | (Name~TestMethod2)`)。</span><span class="sxs-lookup"><span data-stu-id="b280e-192">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="b280e-193">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="b280e-193">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b280e-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b280e-194">See also</span></span>

- [<span data-ttu-id="b280e-195">框架和目標</span><span class="sxs-lookup"><span data-stu-id="b280e-195">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="b280e-196">.NET Core 執行階段識別項 (RID) 目錄</span><span class="sxs-lookup"><span data-stu-id="b280e-196">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
