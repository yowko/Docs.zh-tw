---
title: dotnet test 命令
description: dotnet test 命令是用來在指定的專案中執行單元測試。
ms.date: 05/29/2018
ms.openlocfilehash: 49926b35b418e93237a159758903c535ec6c4006
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988558"
---
# <a name="dotnet-test"></a><span data-ttu-id="85d25-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="85d25-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="85d25-104">名稱</span><span class="sxs-lookup"><span data-stu-id="85d25-104">Name</span></span>

<span data-ttu-id="85d25-105">`dotnet test` - 用來執行單元測試的 .NET 測試驅動程式。</span><span class="sxs-lookup"><span data-stu-id="85d25-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="85d25-106">概要</span><span class="sxs-lookup"><span data-stu-id="85d25-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="85d25-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="85d25-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] 
    [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="85d25-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="85d25-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]

dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="85d25-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="85d25-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]

dotnet test [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="85d25-110">描述</span><span class="sxs-lookup"><span data-stu-id="85d25-110">Description</span></span>

<span data-ttu-id="85d25-111">`dotnet test` 命令是用來在指定的專案中執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="85d25-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="85d25-112">`dotnet test` 命令會啟動為專案指定的測試執行器主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="85d25-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="85d25-113">測試執行器會執行針對單元測試架構 (例如 MSTest、NUnit 或 xUnit) 定義的測試，並報告每項測試成功還是失敗。</span><span class="sxs-lookup"><span data-stu-id="85d25-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="85d25-114">如果所有測試都成功，則測試執行器會傳回 0 作為結束代碼；如果有任何測試失敗，則會傳回 1。</span><span class="sxs-lookup"><span data-stu-id="85d25-114">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="85d25-115">測試執行器和單元測試程式庫會封裝為 NuGet 套件，並還原為專案的一般相依性。</span><span class="sxs-lookup"><span data-stu-id="85d25-115">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="85d25-116">測試專案會使用一般 `<PackageReference>` 元素指定測試執行器，如下列範例專案檔中所示：</span><span class="sxs-lookup"><span data-stu-id="85d25-116">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="85d25-117">引數</span><span class="sxs-lookup"><span data-stu-id="85d25-117">Arguments</span></span>

`PROJECT`

<span data-ttu-id="85d25-118">測試專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="85d25-118">Path to the test project.</span></span> <span data-ttu-id="85d25-119">如果未指定，則會預設為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="85d25-119">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="85d25-120">選項</span><span class="sxs-lookup"><span data-stu-id="85d25-120">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="85d25-121">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="85d25-121">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="85d25-122">在測試執行中，從指定的路徑使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="85d25-122">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="85d25-123">在歸責模式下執行測試。</span><span class="sxs-lookup"><span data-stu-id="85d25-123">Runs the tests in blame mode.</span></span> <span data-ttu-id="85d25-124">這個選項有助於隔離造成測試主機損毀的問題。</span><span class="sxs-lookup"><span data-stu-id="85d25-124">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="85d25-125">它會以 *Sequence.xml* 的形式在目前目錄中建立一個輸出檔，用來擷取損毀前的測試執行順序。</span><span class="sxs-lookup"><span data-stu-id="85d25-125">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="85d25-126">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="85d25-126">Defines the build configuration.</span></span> <span data-ttu-id="85d25-127">預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。</span><span class="sxs-lookup"><span data-stu-id="85d25-127">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="85d25-128">測試回合啟用資料收集器。</span><span class="sxs-lookup"><span data-stu-id="85d25-128">Enables data collector for the test run.</span></span> <span data-ttu-id="85d25-129">如需詳細資訊，請參閱[監視及分析測試回合](https://aka.ms/vstest-collect)。</span><span class="sxs-lookup"><span data-stu-id="85d25-129">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="85d25-130">針對測試平台啟用診斷模式，並將診斷訊息寫入至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="85d25-130">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="85d25-131">尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。</span><span class="sxs-lookup"><span data-stu-id="85d25-131">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="85d25-132">使用指定的運算式篩選出目前專案中的測試。</span><span class="sxs-lookup"><span data-stu-id="85d25-132">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="85d25-133">如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。</span><span class="sxs-lookup"><span data-stu-id="85d25-133">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="85d25-134">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="85d25-134">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="85d25-135">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="85d25-135">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="85d25-136">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="85d25-136">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="85d25-137">不會在執行前建置測試專案。</span><span class="sxs-lookup"><span data-stu-id="85d25-137">Doesn't build the test project before running it.</span></span> <span data-ttu-id="85d25-138">它也會隱含設定 `--no-restore` 旗標。</span><span class="sxs-lookup"><span data-stu-id="85d25-138">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="85d25-139">執行命令時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="85d25-139">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="85d25-140">在其中尋找要執行的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="85d25-140">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="85d25-141">要放置測試結果的目錄。</span><span class="sxs-lookup"><span data-stu-id="85d25-141">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="85d25-142">如果指定的目錄不存在，則會建立該目錄。</span><span class="sxs-lookup"><span data-stu-id="85d25-142">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="85d25-143">用來執行測試的 `.runsettings` 檔案。</span><span class="sxs-lookup"><span data-stu-id="85d25-143">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="85d25-144">[使用 `.runsettings` 檔案設定單元測試](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)。</span><span class="sxs-lookup"><span data-stu-id="85d25-144">[Configure unit tests by using a `.runsettings` file.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)</span></span>

`-t|--list-tests`

<span data-ttu-id="85d25-145">列出在目前專案中探索到的所有測試。</span><span class="sxs-lookup"><span data-stu-id="85d25-145">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="85d25-146">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="85d25-146">Sets the verbosity level of the command.</span></span> <span data-ttu-id="85d25-147">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="85d25-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`RunSettings arguments`

<span data-ttu-id="85d25-148">針對測試傳遞為 RunSettings 設定的引數。</span><span class="sxs-lookup"><span data-stu-id="85d25-148">Arguments passed as RunSettings configurations for the test.</span></span> <span data-ttu-id="85d25-149">指定為 "-- " 後 (注意 -- 後方的空格) 之 `[name]=[value]` 組的引數。</span><span class="sxs-lookup"><span data-stu-id="85d25-149">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="85d25-150">空格適用來分隔多個 `[name]=[value]` 組。</span><span class="sxs-lookup"><span data-stu-id="85d25-150">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

<span data-ttu-id="85d25-151">範例：`dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="85d25-151">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

<span data-ttu-id="85d25-152">如需 RunSettings 的詳細資訊，請參閱 [vstest.console.exe：傳遞 RunSettings 引數](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)。</span><span class="sxs-lookup"><span data-stu-id="85d25-152">For more information about RunSettings, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="85d25-153">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="85d25-153">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="85d25-154">在測試執行中，從指定的路徑使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="85d25-154">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="85d25-155">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="85d25-155">Defines the build configuration.</span></span> <span data-ttu-id="85d25-156">預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。</span><span class="sxs-lookup"><span data-stu-id="85d25-156">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="85d25-157">測試回合啟用資料收集器。</span><span class="sxs-lookup"><span data-stu-id="85d25-157">Enables data collector for the test run.</span></span> <span data-ttu-id="85d25-158">如需詳細資訊，請參閱[監視及分析測試回合](https://aka.ms/vstest-collect)。</span><span class="sxs-lookup"><span data-stu-id="85d25-158">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="85d25-159">針對測試平台啟用診斷模式，並將診斷訊息寫入至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="85d25-159">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="85d25-160">尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。</span><span class="sxs-lookup"><span data-stu-id="85d25-160">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="85d25-161">使用指定的運算式篩選出目前專案中的測試。</span><span class="sxs-lookup"><span data-stu-id="85d25-161">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="85d25-162">如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。</span><span class="sxs-lookup"><span data-stu-id="85d25-162">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="85d25-163">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="85d25-163">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="85d25-164">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="85d25-164">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="85d25-165">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="85d25-165">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="85d25-166">不會在執行前建置測試專案。</span><span class="sxs-lookup"><span data-stu-id="85d25-166">Doesn't build the test project before running it.</span></span> <span data-ttu-id="85d25-167">它也會隱含設定 `--no-restore` 旗標。</span><span class="sxs-lookup"><span data-stu-id="85d25-167">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="85d25-168">執行命令時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="85d25-168">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="85d25-169">在其中尋找要執行的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="85d25-169">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="85d25-170">要放置測試結果的目錄。</span><span class="sxs-lookup"><span data-stu-id="85d25-170">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="85d25-171">如果指定的目錄不存在，則會建立該目錄。</span><span class="sxs-lookup"><span data-stu-id="85d25-171">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="85d25-172">用來執行測試的 `.runsettings` 檔案。</span><span class="sxs-lookup"><span data-stu-id="85d25-172">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="85d25-173">[使用 `.runsettings` 檔案設定單元測試](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)。</span><span class="sxs-lookup"><span data-stu-id="85d25-173">[Configure unit tests by using a `.runsettings` file.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)</span></span>

`-t|--list-tests`

<span data-ttu-id="85d25-174">列出在目前專案中探索到的所有測試。</span><span class="sxs-lookup"><span data-stu-id="85d25-174">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="85d25-175">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="85d25-175">Sets the verbosity level of the command.</span></span> <span data-ttu-id="85d25-176">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="85d25-176">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="85d25-177">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="85d25-177">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="85d25-178">在測試執行中，從指定的路徑使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="85d25-178">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="85d25-179">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="85d25-179">Defines the build configuration.</span></span> <span data-ttu-id="85d25-180">預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。</span><span class="sxs-lookup"><span data-stu-id="85d25-180">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="85d25-181">針對測試平台啟用診斷模式，並將診斷訊息寫入至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="85d25-181">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="85d25-182">尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。</span><span class="sxs-lookup"><span data-stu-id="85d25-182">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="85d25-183">使用指定的運算式篩選出目前專案中的測試。</span><span class="sxs-lookup"><span data-stu-id="85d25-183">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="85d25-184">如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。</span><span class="sxs-lookup"><span data-stu-id="85d25-184">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="85d25-185">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="85d25-185">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="85d25-186">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="85d25-186">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="85d25-187">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="85d25-187">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="85d25-188">不會在執行前建置測試專案。</span><span class="sxs-lookup"><span data-stu-id="85d25-188">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="85d25-189">在其中尋找要執行的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="85d25-189">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="85d25-190">用來執行測試的 `.runsettings` 檔案。</span><span class="sxs-lookup"><span data-stu-id="85d25-190">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="85d25-191">[使用 `.runsettings` 檔案設定單元測試](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)。</span><span class="sxs-lookup"><span data-stu-id="85d25-191">[Configure unit tests by using a `.runsettings` file.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)</span></span>

`-t|--list-tests`

<span data-ttu-id="85d25-192">列出在目前專案中探索到的所有測試。</span><span class="sxs-lookup"><span data-stu-id="85d25-192">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="85d25-193">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="85d25-193">Sets the verbosity level of the command.</span></span> <span data-ttu-id="85d25-194">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="85d25-194">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="85d25-195">範例</span><span class="sxs-lookup"><span data-stu-id="85d25-195">Examples</span></span>

<span data-ttu-id="85d25-196">執行目前目錄之專案中的測試：</span><span class="sxs-lookup"><span data-stu-id="85d25-196">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="85d25-197">執行 `test1` 專案中的測試︰</span><span class="sxs-lookup"><span data-stu-id="85d25-197">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

<span data-ttu-id="85d25-198">在目前目錄中的專案中執行測試，並以 trx 格式產生測試結果檔案：</span><span class="sxs-lookup"><span data-stu-id="85d25-198">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

`dotnet test --logger trx`

## <a name="filter-option-details"></a><span data-ttu-id="85d25-199">篩選選項詳細資料</span><span class="sxs-lookup"><span data-stu-id="85d25-199">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="85d25-200">`<Expression>` 的格式為 `<property><operator><value>[|&<Expression>]`。</span><span class="sxs-lookup"><span data-stu-id="85d25-200">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="85d25-201">`<property>` 為 `Test Case` 的屬性。</span><span class="sxs-lookup"><span data-stu-id="85d25-201">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="85d25-202">以下為熱門單元測試架構所支援的屬性：</span><span class="sxs-lookup"><span data-stu-id="85d25-202">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="85d25-203">測試架構</span><span class="sxs-lookup"><span data-stu-id="85d25-203">Test Framework</span></span> | <span data-ttu-id="85d25-204">支援的屬性</span><span class="sxs-lookup"><span data-stu-id="85d25-204">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="85d25-205">MSTest</span><span class="sxs-lookup"><span data-stu-id="85d25-205">MSTest</span></span>         | <ul><li><span data-ttu-id="85d25-206">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="85d25-206">FullyQualifiedName</span></span></li><li><span data-ttu-id="85d25-207">名稱</span><span class="sxs-lookup"><span data-stu-id="85d25-207">Name</span></span></li><li><span data-ttu-id="85d25-208">ClassName</span><span class="sxs-lookup"><span data-stu-id="85d25-208">ClassName</span></span></li><li><span data-ttu-id="85d25-209">優先權</span><span class="sxs-lookup"><span data-stu-id="85d25-209">Priority</span></span></li><li><span data-ttu-id="85d25-210">TestCategory</span><span class="sxs-lookup"><span data-stu-id="85d25-210">TestCategory</span></span></li></ul> |
| <span data-ttu-id="85d25-211">xUnit</span><span class="sxs-lookup"><span data-stu-id="85d25-211">xUnit</span></span>          | <ul><li><span data-ttu-id="85d25-212">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="85d25-212">FullyQualifiedName</span></span></li><li><span data-ttu-id="85d25-213">DisplayName</span><span class="sxs-lookup"><span data-stu-id="85d25-213">DisplayName</span></span></li><li><span data-ttu-id="85d25-214">特性</span><span class="sxs-lookup"><span data-stu-id="85d25-214">Traits</span></span></li></ul>                                   |

<span data-ttu-id="85d25-215">`<operator>` 描述屬性和值之間的關聯性：</span><span class="sxs-lookup"><span data-stu-id="85d25-215">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="85d25-216">運算子</span><span class="sxs-lookup"><span data-stu-id="85d25-216">Operator</span></span> | <span data-ttu-id="85d25-217">函數</span><span class="sxs-lookup"><span data-stu-id="85d25-217">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="85d25-218">完全相符</span><span class="sxs-lookup"><span data-stu-id="85d25-218">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="85d25-219">不完全相符</span><span class="sxs-lookup"><span data-stu-id="85d25-219">Not exact match</span></span> |
| `~`      | <span data-ttu-id="85d25-220">Contains</span><span class="sxs-lookup"><span data-stu-id="85d25-220">Contains</span></span>        |

<span data-ttu-id="85d25-221">`<value>` 為字串。</span><span class="sxs-lookup"><span data-stu-id="85d25-221">`<value>` is a string.</span></span> <span data-ttu-id="85d25-222">所有的查閱皆不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="85d25-222">All the lookups are case insensitive.</span></span>

<span data-ttu-id="85d25-223">沒有 `<operator>` 的運算式會自動被視為 `FullyQualifiedName` 屬性上的 `contains` (例如，`dotnet test --filter xyz` 等同於 `dotnet test --filter FullyQualifiedName~xyz`)。</span><span class="sxs-lookup"><span data-stu-id="85d25-223">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="85d25-224">運算式可以使用條件運算子聯結：</span><span class="sxs-lookup"><span data-stu-id="85d25-224">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="85d25-225">運算子</span><span class="sxs-lookup"><span data-stu-id="85d25-225">Operator</span></span>            | <span data-ttu-id="85d25-226">函數</span><span class="sxs-lookup"><span data-stu-id="85d25-226">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="85d25-227">OR</span><span class="sxs-lookup"><span data-stu-id="85d25-227">OR</span></span>       |
| `&`                 | <span data-ttu-id="85d25-228">AND</span><span class="sxs-lookup"><span data-stu-id="85d25-228">AND</span></span>      |

<span data-ttu-id="85d25-229">使用條件運算子時，您可以使用括弧括住運算式 (例如，`(Name~TestMethod1) | (Name~TestMethod2)`)。</span><span class="sxs-lookup"><span data-stu-id="85d25-229">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="85d25-230">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="85d25-230">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="85d25-231">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85d25-231">See also</span></span>

- [<span data-ttu-id="85d25-232">架構與目標</span><span class="sxs-lookup"><span data-stu-id="85d25-232">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="85d25-233">.NET Core 執行階段識別項 (RID) 目錄</span><span class="sxs-lookup"><span data-stu-id="85d25-233">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
