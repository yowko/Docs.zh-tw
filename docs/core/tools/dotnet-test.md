---
title: dotnet test 命令
description: dotnet test 命令是用來在指定的專案中執行單元測試。
ms.date: 05/29/2018
ms.openlocfilehash: 890d1fc3fd9d47f2bdcd63f2a25248c3edd705e4
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626043"
---
# <a name="dotnet-test"></a><span data-ttu-id="c4200-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="c4200-103">dotnet test</span></span>

<span data-ttu-id="c4200-104">**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="c4200-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c4200-105">名稱</span><span class="sxs-lookup"><span data-stu-id="c4200-105">Name</span></span>

<span data-ttu-id="c4200-106">`dotnet test` - 用來執行單元測試的 .NET 測試驅動程式。</span><span class="sxs-lookup"><span data-stu-id="c4200-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c4200-107">概要</span><span class="sxs-lookup"><span data-stu-id="c4200-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame]
    [-c|--configuration] [--collect] [-d|--diag] [-f|--framework]
    [--filter] [-l|--logger] [--no-build] [--no-restore]
    [-o|--output] [-r|--results-directory] [-s|--settings]
    [-t|--list-tests] [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

## <a name="description"></a><span data-ttu-id="c4200-108">描述</span><span class="sxs-lookup"><span data-stu-id="c4200-108">Description</span></span>

<span data-ttu-id="c4200-109">`dotnet test` 命令是用來在指定的專案中執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="c4200-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="c4200-110">`dotnet test` 命令會啟動為專案指定的測試執行器主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="c4200-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="c4200-111">測試執行器會執行針對單元測試架構 (例如 MSTest、NUnit 或 xUnit) 定義的測試，並報告每項測試成功還是失敗。</span><span class="sxs-lookup"><span data-stu-id="c4200-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="c4200-112">如果所有測試都成功，則測試執行器會傳回 0 作為結束代碼；如果有任何測試失敗，則會傳回 1。</span><span class="sxs-lookup"><span data-stu-id="c4200-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="c4200-113">測試執行器和單元測試程式庫會封裝為 NuGet 套件，並還原為專案的一般相依性。</span><span class="sxs-lookup"><span data-stu-id="c4200-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="c4200-114">測試專案會使用一般 `<PackageReference>` 元素指定測試執行器，如下列範例專案檔中所示：</span><span class="sxs-lookup"><span data-stu-id="c4200-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="c4200-115">引數</span><span class="sxs-lookup"><span data-stu-id="c4200-115">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="c4200-116">測試專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="c4200-116">Path to the test project.</span></span> <span data-ttu-id="c4200-117">如果未指定，則會預設為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="c4200-117">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="c4200-118">選項。</span><span class="sxs-lookup"><span data-stu-id="c4200-118">Options</span></span>

- **`a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="c4200-119">在測試執行中，從指定的路徑使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="c4200-119">Use the custom test adapters from the specified path in the test run.</span></span>

- **`-blame`**

  <span data-ttu-id="c4200-120">在歸責模式下執行測試。</span><span class="sxs-lookup"><span data-stu-id="c4200-120">Runs the tests in blame mode.</span></span> <span data-ttu-id="c4200-121">此選項有助於隔離導致測試主控制項損毀的問題測試。</span><span class="sxs-lookup"><span data-stu-id="c4200-121">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="c4200-122">它會以 *Sequence.xml* 的形式在目前目錄中建立一個輸出檔，用來擷取損毀前的測試執行順序。</span><span class="sxs-lookup"><span data-stu-id="c4200-122">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`c|--configuration {Debug|Release}`**

  <span data-ttu-id="c4200-123">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="c4200-123">Defines the build configuration.</span></span> <span data-ttu-id="c4200-124">預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。</span><span class="sxs-lookup"><span data-stu-id="c4200-124">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`-collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="c4200-125">測試回合啟用資料收集器。</span><span class="sxs-lookup"><span data-stu-id="c4200-125">Enables data collector for the test run.</span></span> <span data-ttu-id="c4200-126">如需詳細資訊，請參閱[監視及分析測試回合](https://aka.ms/vstest-collect)。</span><span class="sxs-lookup"><span data-stu-id="c4200-126">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="c4200-127">針對測試平台啟用診斷模式，並將診斷訊息寫入至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="c4200-127">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

- **`f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c4200-128">尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。</span><span class="sxs-lookup"><span data-stu-id="c4200-128">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="c4200-129">使用指定的運算式篩選出目前專案中的測試。</span><span class="sxs-lookup"><span data-stu-id="c4200-129">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="c4200-130">如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。</span><span class="sxs-lookup"><span data-stu-id="c4200-130">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="c4200-131">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="c4200-131">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`h|--help`**

  <span data-ttu-id="c4200-132">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="c4200-132">Prints out a short help for the command.</span></span>

- **`l|--logger <LoggerUri/FriendlyName>`**

  <span data-ttu-id="c4200-133">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="c4200-133">Specifies a logger for test results.</span></span>

- **`--no-build`**

  <span data-ttu-id="c4200-134">不會在執行前建置測試專案。</span><span class="sxs-lookup"><span data-stu-id="c4200-134">Doesn't build the test project before running it.</span></span> <span data-ttu-id="c4200-135">它也會以隱含方式設定-`--no-restore` 旗標。</span><span class="sxs-lookup"><span data-stu-id="c4200-135">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--no-restore`**

  <span data-ttu-id="c4200-136">執行命令時，不會執行隱含的還原。</span><span class="sxs-lookup"><span data-stu-id="c4200-136">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="c4200-137">在其中尋找要執行的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="c4200-137">Directory in which to find the binaries to run.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="c4200-138">要放置測試結果的目錄。</span><span class="sxs-lookup"><span data-stu-id="c4200-138">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="c4200-139">如果指定的目錄不存在，則會建立該目錄。</span><span class="sxs-lookup"><span data-stu-id="c4200-139">If the specified directory doesn't exist, it's created.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="c4200-140">用來執行測試的 `.runsettings` 檔案。</span><span class="sxs-lookup"><span data-stu-id="c4200-140">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="c4200-141">[使用 `.runsettings` 檔案設定單元測試](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)。</span><span class="sxs-lookup"><span data-stu-id="c4200-141">[Configure unit tests by using a `.runsettings` file.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)</span></span>

- **`-t|--list-tests`**

  <span data-ttu-id="c4200-142">列出在目前專案中探索到的所有測試。</span><span class="sxs-lookup"><span data-stu-id="c4200-142">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="c4200-143">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="c4200-143">Sets the verbosity level of the command.</span></span> <span data-ttu-id="c4200-144">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="c4200-144">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- <span data-ttu-id="c4200-145">`RunSettings` 引數</span><span class="sxs-lookup"><span data-stu-id="c4200-145">`RunSettings` arguments</span></span>

  <span data-ttu-id="c4200-146">引數會當做測試的 `RunSettings` 設定來傳遞。</span><span class="sxs-lookup"><span data-stu-id="c4200-146">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="c4200-147">指定為 "-- " 後 (注意 -- 後方的空格) 之 `[name]=[value]` 組的引數。</span><span class="sxs-lookup"><span data-stu-id="c4200-147">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="c4200-148">空格適用來分隔多個 `[name]=[value]` 組。</span><span class="sxs-lookup"><span data-stu-id="c4200-148">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="c4200-149">範例： `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="c4200-149">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="c4200-150">如需詳細資訊，請參閱[vstest：傳遞 .runsettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)。</span><span class="sxs-lookup"><span data-stu-id="c4200-150">For more information, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="c4200-151">範例</span><span class="sxs-lookup"><span data-stu-id="c4200-151">Examples</span></span>

- <span data-ttu-id="c4200-152">執行目前目錄之專案中的測試：</span><span class="sxs-lookup"><span data-stu-id="c4200-152">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="c4200-153">執行 `test1` 專案中的測試︰</span><span class="sxs-lookup"><span data-stu-id="c4200-153">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="c4200-154">在目前目錄中的專案中執行測試，並以 trx 格式產生測試結果檔案：</span><span class="sxs-lookup"><span data-stu-id="c4200-154">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

## <a name="filter-option-details"></a><span data-ttu-id="c4200-155">篩選選項詳細資料</span><span class="sxs-lookup"><span data-stu-id="c4200-155">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="c4200-156">`<Expression>` 的格式為 `<property><operator><value>[|&<Expression>]`。</span><span class="sxs-lookup"><span data-stu-id="c4200-156">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="c4200-157">`<property>` 為 `Test Case` 的屬性。</span><span class="sxs-lookup"><span data-stu-id="c4200-157">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="c4200-158">以下為熱門單元測試架構所支援的屬性：</span><span class="sxs-lookup"><span data-stu-id="c4200-158">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="c4200-159">測試架構</span><span class="sxs-lookup"><span data-stu-id="c4200-159">Test Framework</span></span> | <span data-ttu-id="c4200-160">支援的屬性</span><span class="sxs-lookup"><span data-stu-id="c4200-160">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="c4200-161">MSTest</span><span class="sxs-lookup"><span data-stu-id="c4200-161">MSTest</span></span>         | <ul><li><span data-ttu-id="c4200-162">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="c4200-162">FullyQualifiedName</span></span></li><li><span data-ttu-id="c4200-163">名稱</span><span class="sxs-lookup"><span data-stu-id="c4200-163">Name</span></span></li><li><span data-ttu-id="c4200-164">ClassName</span><span class="sxs-lookup"><span data-stu-id="c4200-164">ClassName</span></span></li><li><span data-ttu-id="c4200-165">優先順序</span><span class="sxs-lookup"><span data-stu-id="c4200-165">Priority</span></span></li><li><span data-ttu-id="c4200-166">TestCategory</span><span class="sxs-lookup"><span data-stu-id="c4200-166">TestCategory</span></span></li></ul> |
| <span data-ttu-id="c4200-167">xUnit</span><span class="sxs-lookup"><span data-stu-id="c4200-167">xUnit</span></span>          | <ul><li><span data-ttu-id="c4200-168">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="c4200-168">FullyQualifiedName</span></span></li><li><span data-ttu-id="c4200-169">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c4200-169">DisplayName</span></span></li><li><span data-ttu-id="c4200-170">特性</span><span class="sxs-lookup"><span data-stu-id="c4200-170">Traits</span></span></li></ul>                                   |

<span data-ttu-id="c4200-171">`<operator>` 描述屬性和值之間的關聯性：</span><span class="sxs-lookup"><span data-stu-id="c4200-171">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="c4200-172">運算子</span><span class="sxs-lookup"><span data-stu-id="c4200-172">Operator</span></span> | <span data-ttu-id="c4200-173">函式</span><span class="sxs-lookup"><span data-stu-id="c4200-173">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="c4200-174">完全相符</span><span class="sxs-lookup"><span data-stu-id="c4200-174">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="c4200-175">不完全相符</span><span class="sxs-lookup"><span data-stu-id="c4200-175">Not exact match</span></span> |
| `~`      | <span data-ttu-id="c4200-176">包含</span><span class="sxs-lookup"><span data-stu-id="c4200-176">Contains</span></span>        |
| `!~`     | <span data-ttu-id="c4200-177">不包含</span><span class="sxs-lookup"><span data-stu-id="c4200-177">Not contains</span></span>    |

<span data-ttu-id="c4200-178">`<value>` 為字串。</span><span class="sxs-lookup"><span data-stu-id="c4200-178">`<value>` is a string.</span></span> <span data-ttu-id="c4200-179">所有的查閱皆不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="c4200-179">All the lookups are case insensitive.</span></span>

<span data-ttu-id="c4200-180">沒有 `<operator>` 的運算式會自動被視為 `contains` 屬性上的 `FullyQualifiedName` (例如，`dotnet test --filter xyz` 等同於 `dotnet test --filter FullyQualifiedName~xyz`)。</span><span class="sxs-lookup"><span data-stu-id="c4200-180">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="c4200-181">運算式可以使用條件運算子聯結：</span><span class="sxs-lookup"><span data-stu-id="c4200-181">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="c4200-182">運算子</span><span class="sxs-lookup"><span data-stu-id="c4200-182">Operator</span></span>            | <span data-ttu-id="c4200-183">函式</span><span class="sxs-lookup"><span data-stu-id="c4200-183">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="c4200-184">OR</span><span class="sxs-lookup"><span data-stu-id="c4200-184">OR</span></span>       |
| `&`                 | <span data-ttu-id="c4200-185">AND</span><span class="sxs-lookup"><span data-stu-id="c4200-185">AND</span></span>      |

<span data-ttu-id="c4200-186">使用條件運算子時，您可以使用括弧括住運算式 (例如，`(Name~TestMethod1) | (Name~TestMethod2)`)。</span><span class="sxs-lookup"><span data-stu-id="c4200-186">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="c4200-187">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="c4200-187">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c4200-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4200-188">See also</span></span>

- [<span data-ttu-id="c4200-189">架構與目標</span><span class="sxs-lookup"><span data-stu-id="c4200-189">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="c4200-190">.NET Core 執行階段識別項 (RID) 目錄</span><span class="sxs-lookup"><span data-stu-id="c4200-190">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
