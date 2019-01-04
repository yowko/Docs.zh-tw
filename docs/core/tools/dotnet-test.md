---
title: dotnet test 命令
description: dotnet test 命令是用來在指定的專案中執行單元測試。
ms.date: 05/29/2018
ms.openlocfilehash: 2cfe96b24e5f46ae679c970a1df028d38ebf6037
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170836"
---
# <a name="dotnet-test"></a><span data-ttu-id="15adc-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="15adc-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="15adc-104">名稱</span><span class="sxs-lookup"><span data-stu-id="15adc-104">Name</span></span>

<span data-ttu-id="15adc-105">`dotnet test` - 用來執行單元測試的 .NET 測試驅動程式。</span><span class="sxs-lookup"><span data-stu-id="15adc-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="15adc-106">概要</span><span class="sxs-lookup"><span data-stu-id="15adc-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="15adc-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="15adc-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] 
    [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="15adc-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="15adc-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]

dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="15adc-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="15adc-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]

dotnet test [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="15adc-110">說明</span><span class="sxs-lookup"><span data-stu-id="15adc-110">Description</span></span>

<span data-ttu-id="15adc-111">`dotnet test` 命令是用來在指定的專案中執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="15adc-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="15adc-112">`dotnet test` 命令會啟動為專案指定的測試執行器主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="15adc-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="15adc-113">測試執行器會執行針對單元測試架構 (例如 MSTest、NUnit 或 xUnit) 定義的測試，並報告每項測試成功還是失敗。</span><span class="sxs-lookup"><span data-stu-id="15adc-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="15adc-114">如果所有測試都成功，則測試執行器會傳回 0 作為結束代碼；如果有任何測試失敗，則會傳回 1。</span><span class="sxs-lookup"><span data-stu-id="15adc-114">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="15adc-115">測試執行器和單元測試程式庫會封裝為 NuGet 套件，並還原為專案的一般相依性。</span><span class="sxs-lookup"><span data-stu-id="15adc-115">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="15adc-116">測試專案會使用一般 `<PackageReference>` 元素指定測試執行器，如下列範例專案檔中所示：</span><span class="sxs-lookup"><span data-stu-id="15adc-116">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="15adc-117">引數</span><span class="sxs-lookup"><span data-stu-id="15adc-117">Arguments</span></span>

`PROJECT`

<span data-ttu-id="15adc-118">測試專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="15adc-118">Path to the test project.</span></span> <span data-ttu-id="15adc-119">如果未指定，則會預設為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="15adc-119">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="15adc-120">選項</span><span class="sxs-lookup"><span data-stu-id="15adc-120">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="15adc-121">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="15adc-121">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="15adc-122">在測試執行中，從指定的路徑使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="15adc-122">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="15adc-123">在歸責模式下執行測試。</span><span class="sxs-lookup"><span data-stu-id="15adc-123">Runs the tests in blame mode.</span></span> <span data-ttu-id="15adc-124">這個選項有助於隔離造成測試主機損毀的問題。</span><span class="sxs-lookup"><span data-stu-id="15adc-124">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="15adc-125">它會以 *Sequence.xml* 的形式在目前目錄中建立一個輸出檔，用來擷取損毀前的測試執行順序。</span><span class="sxs-lookup"><span data-stu-id="15adc-125">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="15adc-126">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="15adc-126">Defines the build configuration.</span></span> <span data-ttu-id="15adc-127">預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。</span><span class="sxs-lookup"><span data-stu-id="15adc-127">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="15adc-128">測試回合啟用資料收集器。</span><span class="sxs-lookup"><span data-stu-id="15adc-128">Enables data collector for the test run.</span></span> <span data-ttu-id="15adc-129">如需詳細資訊，請參閱[監視及分析測試回合](https://aka.ms/vstest-collect)。</span><span class="sxs-lookup"><span data-stu-id="15adc-129">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="15adc-130">針對測試平台啟用診斷模式，並將診斷訊息寫入至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="15adc-130">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="15adc-131">尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。</span><span class="sxs-lookup"><span data-stu-id="15adc-131">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="15adc-132">使用指定的運算式篩選出目前專案中的測試。</span><span class="sxs-lookup"><span data-stu-id="15adc-132">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="15adc-133">如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。</span><span class="sxs-lookup"><span data-stu-id="15adc-133">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="15adc-134">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="15adc-134">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="15adc-135">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="15adc-135">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="15adc-136">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="15adc-136">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="15adc-137">不會在執行前建置測試專案。</span><span class="sxs-lookup"><span data-stu-id="15adc-137">Doesn't build the test project before running it.</span></span> <span data-ttu-id="15adc-138">它也會隱含設定 `--no-restore` 旗標。</span><span class="sxs-lookup"><span data-stu-id="15adc-138">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="15adc-139">執行命令時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="15adc-139">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="15adc-140">在其中尋找要執行的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="15adc-140">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="15adc-141">要放置測試結果的目錄。</span><span class="sxs-lookup"><span data-stu-id="15adc-141">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="15adc-142">如果指定的目錄不存在，則會建立該目錄。</span><span class="sxs-lookup"><span data-stu-id="15adc-142">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="15adc-143">執行測試時要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="15adc-143">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="15adc-144">列出在目前專案中探索到的所有測試。</span><span class="sxs-lookup"><span data-stu-id="15adc-144">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="15adc-145">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="15adc-145">Sets the verbosity level of the command.</span></span> <span data-ttu-id="15adc-146">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="15adc-146">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`RunSettings arguments`

<span data-ttu-id="15adc-147">針對測試傳遞為 RunSettings 設定的引數。</span><span class="sxs-lookup"><span data-stu-id="15adc-147">Arguments passed as RunSettings configurations for the test.</span></span> <span data-ttu-id="15adc-148">指定為 "-- " 後 (注意 -- 後方的空格) 之 `[name]=[value]` 組的引數。</span><span class="sxs-lookup"><span data-stu-id="15adc-148">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="15adc-149">空格適用來分隔多個 `[name]=[value]` 組。</span><span class="sxs-lookup"><span data-stu-id="15adc-149">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

<span data-ttu-id="15adc-150">範例：`dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="15adc-150">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

<span data-ttu-id="15adc-151">如需 RunSettings 的詳細資訊，請參閱 [vstest.console.exe：傳遞 RunSettings 引數](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)。</span><span class="sxs-lookup"><span data-stu-id="15adc-151">For more information about RunSettings, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="15adc-152">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="15adc-152">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="15adc-153">在測試執行中，從指定的路徑使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="15adc-153">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="15adc-154">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="15adc-154">Defines the build configuration.</span></span> <span data-ttu-id="15adc-155">預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。</span><span class="sxs-lookup"><span data-stu-id="15adc-155">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="15adc-156">測試回合啟用資料收集器。</span><span class="sxs-lookup"><span data-stu-id="15adc-156">Enables data collector for the test run.</span></span> <span data-ttu-id="15adc-157">如需詳細資訊，請參閱[監視及分析測試回合](https://aka.ms/vstest-collect)。</span><span class="sxs-lookup"><span data-stu-id="15adc-157">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="15adc-158">針對測試平台啟用診斷模式，並將診斷訊息寫入至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="15adc-158">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="15adc-159">尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。</span><span class="sxs-lookup"><span data-stu-id="15adc-159">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="15adc-160">使用指定的運算式篩選出目前專案中的測試。</span><span class="sxs-lookup"><span data-stu-id="15adc-160">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="15adc-161">如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。</span><span class="sxs-lookup"><span data-stu-id="15adc-161">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="15adc-162">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="15adc-162">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="15adc-163">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="15adc-163">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="15adc-164">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="15adc-164">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="15adc-165">不會在執行前建置測試專案。</span><span class="sxs-lookup"><span data-stu-id="15adc-165">Doesn't build the test project before running it.</span></span> <span data-ttu-id="15adc-166">它也會隱含設定 `--no-restore` 旗標。</span><span class="sxs-lookup"><span data-stu-id="15adc-166">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="15adc-167">執行命令時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="15adc-167">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="15adc-168">在其中尋找要執行的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="15adc-168">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="15adc-169">要放置測試結果的目錄。</span><span class="sxs-lookup"><span data-stu-id="15adc-169">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="15adc-170">如果指定的目錄不存在，則會建立該目錄。</span><span class="sxs-lookup"><span data-stu-id="15adc-170">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="15adc-171">執行測試時要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="15adc-171">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="15adc-172">列出在目前專案中探索到的所有測試。</span><span class="sxs-lookup"><span data-stu-id="15adc-172">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="15adc-173">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="15adc-173">Sets the verbosity level of the command.</span></span> <span data-ttu-id="15adc-174">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="15adc-174">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="15adc-175">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="15adc-175">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="15adc-176">在測試執行中，從指定的路徑使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="15adc-176">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="15adc-177">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="15adc-177">Defines the build configuration.</span></span> <span data-ttu-id="15adc-178">預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。</span><span class="sxs-lookup"><span data-stu-id="15adc-178">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="15adc-179">針對測試平台啟用診斷模式，並將診斷訊息寫入至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="15adc-179">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="15adc-180">尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。</span><span class="sxs-lookup"><span data-stu-id="15adc-180">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="15adc-181">使用指定的運算式篩選出目前專案中的測試。</span><span class="sxs-lookup"><span data-stu-id="15adc-181">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="15adc-182">如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。</span><span class="sxs-lookup"><span data-stu-id="15adc-182">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="15adc-183">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="15adc-183">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="15adc-184">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="15adc-184">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="15adc-185">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="15adc-185">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="15adc-186">不會在執行前建置測試專案。</span><span class="sxs-lookup"><span data-stu-id="15adc-186">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="15adc-187">在其中尋找要執行的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="15adc-187">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="15adc-188">執行測試時要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="15adc-188">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="15adc-189">列出在目前專案中探索到的所有測試。</span><span class="sxs-lookup"><span data-stu-id="15adc-189">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="15adc-190">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="15adc-190">Sets the verbosity level of the command.</span></span> <span data-ttu-id="15adc-191">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="15adc-191">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="15adc-192">範例</span><span class="sxs-lookup"><span data-stu-id="15adc-192">Examples</span></span>

<span data-ttu-id="15adc-193">執行目前目錄之專案中的測試：</span><span class="sxs-lookup"><span data-stu-id="15adc-193">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="15adc-194">執行 `test1` 專案中的測試︰</span><span class="sxs-lookup"><span data-stu-id="15adc-194">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

<span data-ttu-id="15adc-195">在目前目錄中的專案中執行測試，並以 trx 格式產生測試結果檔案：</span><span class="sxs-lookup"><span data-stu-id="15adc-195">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

`dotnet test --logger:trx`

## <a name="filter-option-details"></a><span data-ttu-id="15adc-196">篩選選項詳細資料</span><span class="sxs-lookup"><span data-stu-id="15adc-196">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="15adc-197">`<Expression>` 的格式為 `<property><operator><value>[|&<Expression>]`。</span><span class="sxs-lookup"><span data-stu-id="15adc-197">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="15adc-198">`<property>` 為 `Test Case` 的屬性。</span><span class="sxs-lookup"><span data-stu-id="15adc-198">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="15adc-199">以下為熱門單元測試架構所支援的屬性：</span><span class="sxs-lookup"><span data-stu-id="15adc-199">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="15adc-200">測試架構</span><span class="sxs-lookup"><span data-stu-id="15adc-200">Test Framework</span></span> | <span data-ttu-id="15adc-201">支援的屬性</span><span class="sxs-lookup"><span data-stu-id="15adc-201">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="15adc-202">MSTest</span><span class="sxs-lookup"><span data-stu-id="15adc-202">MSTest</span></span>         | <ul><li><span data-ttu-id="15adc-203">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="15adc-203">FullyQualifiedName</span></span></li><li><span data-ttu-id="15adc-204">名稱</span><span class="sxs-lookup"><span data-stu-id="15adc-204">Name</span></span></li><li><span data-ttu-id="15adc-205">ClassName</span><span class="sxs-lookup"><span data-stu-id="15adc-205">ClassName</span></span></li><li><span data-ttu-id="15adc-206">優先權</span><span class="sxs-lookup"><span data-stu-id="15adc-206">Priority</span></span></li><li><span data-ttu-id="15adc-207">TestCategory</span><span class="sxs-lookup"><span data-stu-id="15adc-207">TestCategory</span></span></li></ul> |
| <span data-ttu-id="15adc-208">xUnit</span><span class="sxs-lookup"><span data-stu-id="15adc-208">xUnit</span></span>          | <ul><li><span data-ttu-id="15adc-209">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="15adc-209">FullyQualifiedName</span></span></li><li><span data-ttu-id="15adc-210">DisplayName</span><span class="sxs-lookup"><span data-stu-id="15adc-210">DisplayName</span></span></li><li><span data-ttu-id="15adc-211">特性</span><span class="sxs-lookup"><span data-stu-id="15adc-211">Traits</span></span></li></ul>                                   |

<span data-ttu-id="15adc-212">`<operator>` 描述屬性和值之間的關聯性：</span><span class="sxs-lookup"><span data-stu-id="15adc-212">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="15adc-213">運算子</span><span class="sxs-lookup"><span data-stu-id="15adc-213">Operator</span></span> | <span data-ttu-id="15adc-214">功能</span><span class="sxs-lookup"><span data-stu-id="15adc-214">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="15adc-215">完全相符</span><span class="sxs-lookup"><span data-stu-id="15adc-215">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="15adc-216">不完全相符</span><span class="sxs-lookup"><span data-stu-id="15adc-216">Not exact match</span></span> |
| `~`      | <span data-ttu-id="15adc-217">包含</span><span class="sxs-lookup"><span data-stu-id="15adc-217">Contains</span></span>        |

<span data-ttu-id="15adc-218">`<value>` 為字串。</span><span class="sxs-lookup"><span data-stu-id="15adc-218">`<value>` is a string.</span></span> <span data-ttu-id="15adc-219">所有的查閱皆不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="15adc-219">All the lookups are case insensitive.</span></span>

<span data-ttu-id="15adc-220">沒有 `<operator>` 的運算式會自動被視為 `FullyQualifiedName` 屬性上的 `contains` (例如，`dotnet test --filter xyz` 等同於 `dotnet test --filter FullyQualifiedName~xyz`)。</span><span class="sxs-lookup"><span data-stu-id="15adc-220">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="15adc-221">運算式可以使用條件運算子聯結：</span><span class="sxs-lookup"><span data-stu-id="15adc-221">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="15adc-222">運算子</span><span class="sxs-lookup"><span data-stu-id="15adc-222">Operator</span></span>            | <span data-ttu-id="15adc-223">功能</span><span class="sxs-lookup"><span data-stu-id="15adc-223">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="15adc-224">OR</span><span class="sxs-lookup"><span data-stu-id="15adc-224">OR</span></span>       |
| `&`                 | <span data-ttu-id="15adc-225">AND</span><span class="sxs-lookup"><span data-stu-id="15adc-225">AND</span></span>      |

<span data-ttu-id="15adc-226">使用條件運算子時，您可以使用括弧括住運算式 (例如，`(Name~TestMethod1) | (Name~TestMethod2)`)。</span><span class="sxs-lookup"><span data-stu-id="15adc-226">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="15adc-227">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="15adc-227">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="15adc-228">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15adc-228">See also</span></span>

* [<span data-ttu-id="15adc-229">架構與目標</span><span class="sxs-lookup"><span data-stu-id="15adc-229">Frameworks and Targets</span></span>](../../standard/frameworks.md)  
* [<span data-ttu-id="15adc-230">.NET Core 執行階段識別項 (RID) 目錄</span><span class="sxs-lookup"><span data-stu-id="15adc-230">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
