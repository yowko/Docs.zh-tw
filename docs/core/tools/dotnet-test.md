---
title: dotnet test 命令 - .NET Core CLI
description: dotnet test 命令是用來在指定的專案中執行單元測試。
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: e80ba874ec8d0fbc49858719dc3b9b6e02254c78
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2018
ms.locfileid: "46696452"
---
# <a name="dotnet-test"></a><span data-ttu-id="93d07-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="93d07-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="93d07-104">名稱</span><span class="sxs-lookup"><span data-stu-id="93d07-104">Name</span></span>

<span data-ttu-id="93d07-105">`dotnet test` - 用來執行單元測試的 .NET 測試驅動程式。</span><span class="sxs-lookup"><span data-stu-id="93d07-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="93d07-106">概要</span><span class="sxs-lookup"><span data-stu-id="93d07-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="93d07-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="93d07-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="93d07-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="93d07-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="93d07-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="93d07-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="93d07-110">描述</span><span class="sxs-lookup"><span data-stu-id="93d07-110">Description</span></span>

<span data-ttu-id="93d07-111">`dotnet test` 命令是用來在指定的專案中執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="93d07-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="93d07-112">`dotnet test` 命令會啟動為專案指定的測試執行器主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="93d07-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="93d07-113">測試執行器會執行針對單元測試架構 (例如 MSTest、NUnit 或 xUnit) 定義的測試，並報告每項測試成功還是失敗。</span><span class="sxs-lookup"><span data-stu-id="93d07-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="93d07-114">如果所有測試都成功，則測試執行器會傳回 0 作為結束代碼；如果有任何測試失敗，則會傳回 1。</span><span class="sxs-lookup"><span data-stu-id="93d07-114">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="93d07-115">測試執行器和單元測試程式庫會封裝為 NuGet 套件，並還原為專案的一般相依性。</span><span class="sxs-lookup"><span data-stu-id="93d07-115">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="93d07-116">測試專案會使用一般 `<PackageReference>` 元素指定測試執行器，如下列範例專案檔中所示：</span><span class="sxs-lookup"><span data-stu-id="93d07-116">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="93d07-117">引數</span><span class="sxs-lookup"><span data-stu-id="93d07-117">Arguments</span></span>

`PROJECT`

<span data-ttu-id="93d07-118">測試專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="93d07-118">Path to the test project.</span></span> <span data-ttu-id="93d07-119">如果未指定，則會預設為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="93d07-119">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="93d07-120">選項</span><span class="sxs-lookup"><span data-stu-id="93d07-120">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="93d07-121">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="93d07-121">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="93d07-122">在測試執行中，從指定的路徑使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="93d07-122">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="93d07-123">在歸責模式下執行測試。</span><span class="sxs-lookup"><span data-stu-id="93d07-123">Runs the tests in blame mode.</span></span> <span data-ttu-id="93d07-124">這個選項有助於隔離造成測試主機損毀的問題。</span><span class="sxs-lookup"><span data-stu-id="93d07-124">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="93d07-125">它會以 *Sequence.xml* 的形式在目前目錄中建立一個輸出檔，用來擷取損毀前的測試執行順序。</span><span class="sxs-lookup"><span data-stu-id="93d07-125">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="93d07-126">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="93d07-126">Defines the build configuration.</span></span> <span data-ttu-id="93d07-127">預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。</span><span class="sxs-lookup"><span data-stu-id="93d07-127">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="93d07-128">測試回合啟用資料收集器。</span><span class="sxs-lookup"><span data-stu-id="93d07-128">Enables data collector for the test run.</span></span> <span data-ttu-id="93d07-129">如需詳細資訊，請參閱[監視及分析測試回合](https://aka.ms/vstest-collect)。</span><span class="sxs-lookup"><span data-stu-id="93d07-129">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="93d07-130">針對測試平台啟用診斷模式，並將診斷訊息寫入至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="93d07-130">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="93d07-131">尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。</span><span class="sxs-lookup"><span data-stu-id="93d07-131">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="93d07-132">使用指定的運算式篩選出目前專案中的測試。</span><span class="sxs-lookup"><span data-stu-id="93d07-132">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="93d07-133">如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。</span><span class="sxs-lookup"><span data-stu-id="93d07-133">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="93d07-134">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="93d07-134">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="93d07-135">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="93d07-135">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="93d07-136">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="93d07-136">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="93d07-137">不會在執行前建置測試專案。</span><span class="sxs-lookup"><span data-stu-id="93d07-137">Doesn't build the test project before running it.</span></span> <span data-ttu-id="93d07-138">它也會隱含設定 `--no-restore` 旗標。</span><span class="sxs-lookup"><span data-stu-id="93d07-138">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="93d07-139">執行命令時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="93d07-139">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="93d07-140">在其中尋找要執行的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="93d07-140">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="93d07-141">要放置測試結果的目錄。</span><span class="sxs-lookup"><span data-stu-id="93d07-141">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="93d07-142">如果指定的目錄不存在，則會建立該目錄。</span><span class="sxs-lookup"><span data-stu-id="93d07-142">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="93d07-143">執行測試時要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="93d07-143">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="93d07-144">列出在目前專案中探索到的所有測試。</span><span class="sxs-lookup"><span data-stu-id="93d07-144">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="93d07-145">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="93d07-145">Sets the verbosity level of the command.</span></span> <span data-ttu-id="93d07-146">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="93d07-146">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="93d07-147">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="93d07-147">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="93d07-148">在測試執行中，從指定的路徑使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="93d07-148">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="93d07-149">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="93d07-149">Defines the build configuration.</span></span> <span data-ttu-id="93d07-150">預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。</span><span class="sxs-lookup"><span data-stu-id="93d07-150">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="93d07-151">測試回合啟用資料收集器。</span><span class="sxs-lookup"><span data-stu-id="93d07-151">Enables data collector for the test run.</span></span> <span data-ttu-id="93d07-152">如需詳細資訊，請參閱[監視及分析測試回合](https://aka.ms/vstest-collect)。</span><span class="sxs-lookup"><span data-stu-id="93d07-152">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="93d07-153">針對測試平台啟用診斷模式，並將診斷訊息寫入至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="93d07-153">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="93d07-154">尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。</span><span class="sxs-lookup"><span data-stu-id="93d07-154">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="93d07-155">使用指定的運算式篩選出目前專案中的測試。</span><span class="sxs-lookup"><span data-stu-id="93d07-155">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="93d07-156">如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。</span><span class="sxs-lookup"><span data-stu-id="93d07-156">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="93d07-157">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="93d07-157">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="93d07-158">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="93d07-158">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="93d07-159">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="93d07-159">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="93d07-160">不會在執行前建置測試專案。</span><span class="sxs-lookup"><span data-stu-id="93d07-160">Doesn't build the test project before running it.</span></span> <span data-ttu-id="93d07-161">它也會隱含設定 `--no-restore` 旗標。</span><span class="sxs-lookup"><span data-stu-id="93d07-161">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="93d07-162">執行命令時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="93d07-162">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="93d07-163">在其中尋找要執行的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="93d07-163">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="93d07-164">要放置測試結果的目錄。</span><span class="sxs-lookup"><span data-stu-id="93d07-164">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="93d07-165">如果指定的目錄不存在，則會建立該目錄。</span><span class="sxs-lookup"><span data-stu-id="93d07-165">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="93d07-166">執行測試時要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="93d07-166">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="93d07-167">列出在目前專案中探索到的所有測試。</span><span class="sxs-lookup"><span data-stu-id="93d07-167">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="93d07-168">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="93d07-168">Sets the verbosity level of the command.</span></span> <span data-ttu-id="93d07-169">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="93d07-169">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="93d07-170">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="93d07-170">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="93d07-171">在測試執行中，從指定的路徑使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="93d07-171">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="93d07-172">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="93d07-172">Defines the build configuration.</span></span> <span data-ttu-id="93d07-173">預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。</span><span class="sxs-lookup"><span data-stu-id="93d07-173">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="93d07-174">針對測試平台啟用診斷模式，並將診斷訊息寫入至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="93d07-174">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="93d07-175">尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。</span><span class="sxs-lookup"><span data-stu-id="93d07-175">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="93d07-176">使用指定的運算式篩選出目前專案中的測試。</span><span class="sxs-lookup"><span data-stu-id="93d07-176">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="93d07-177">如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。</span><span class="sxs-lookup"><span data-stu-id="93d07-177">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="93d07-178">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="93d07-178">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="93d07-179">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="93d07-179">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="93d07-180">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="93d07-180">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="93d07-181">不會在執行前建置測試專案。</span><span class="sxs-lookup"><span data-stu-id="93d07-181">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="93d07-182">在其中尋找要執行的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="93d07-182">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="93d07-183">執行測試時要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="93d07-183">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="93d07-184">列出在目前專案中探索到的所有測試。</span><span class="sxs-lookup"><span data-stu-id="93d07-184">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="93d07-185">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="93d07-185">Sets the verbosity level of the command.</span></span> <span data-ttu-id="93d07-186">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="93d07-186">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="93d07-187">範例</span><span class="sxs-lookup"><span data-stu-id="93d07-187">Examples</span></span>

<span data-ttu-id="93d07-188">執行目前目錄之專案中的測試：</span><span class="sxs-lookup"><span data-stu-id="93d07-188">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="93d07-189">執行 `test1` 專案中的測試︰</span><span class="sxs-lookup"><span data-stu-id="93d07-189">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

<span data-ttu-id="93d07-190">在目前目錄中的專案中執行測試，並以 trx 格式產生測試結果檔案：</span><span class="sxs-lookup"><span data-stu-id="93d07-190">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

`dotnet test --logger:trx`

## <a name="filter-option-details"></a><span data-ttu-id="93d07-191">篩選選項詳細資料</span><span class="sxs-lookup"><span data-stu-id="93d07-191">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="93d07-192">`<Expression>` 的格式為 `<property><operator><value>[|&<Expression>]`。</span><span class="sxs-lookup"><span data-stu-id="93d07-192">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="93d07-193">`<property>` 為 `Test Case` 的屬性。</span><span class="sxs-lookup"><span data-stu-id="93d07-193">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="93d07-194">以下為熱門單元測試架構所支援的屬性：</span><span class="sxs-lookup"><span data-stu-id="93d07-194">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="93d07-195">測試架構</span><span class="sxs-lookup"><span data-stu-id="93d07-195">Test Framework</span></span> | <span data-ttu-id="93d07-196">支援的屬性</span><span class="sxs-lookup"><span data-stu-id="93d07-196">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="93d07-197">MSTest</span><span class="sxs-lookup"><span data-stu-id="93d07-197">MSTest</span></span>         | <ul><li><span data-ttu-id="93d07-198">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="93d07-198">FullyQualifiedName</span></span></li><li><span data-ttu-id="93d07-199">名稱</span><span class="sxs-lookup"><span data-stu-id="93d07-199">Name</span></span></li><li><span data-ttu-id="93d07-200">ClassName</span><span class="sxs-lookup"><span data-stu-id="93d07-200">ClassName</span></span></li><li><span data-ttu-id="93d07-201">優先權</span><span class="sxs-lookup"><span data-stu-id="93d07-201">Priority</span></span></li><li><span data-ttu-id="93d07-202">TestCategory</span><span class="sxs-lookup"><span data-stu-id="93d07-202">TestCategory</span></span></li></ul> |
| <span data-ttu-id="93d07-203">xUnit</span><span class="sxs-lookup"><span data-stu-id="93d07-203">xUnit</span></span>          | <ul><li><span data-ttu-id="93d07-204">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="93d07-204">FullyQualifiedName</span></span></li><li><span data-ttu-id="93d07-205">DisplayName</span><span class="sxs-lookup"><span data-stu-id="93d07-205">DisplayName</span></span></li><li><span data-ttu-id="93d07-206">特性</span><span class="sxs-lookup"><span data-stu-id="93d07-206">Traits</span></span></li></ul>                                   |

<span data-ttu-id="93d07-207">`<operator>` 描述屬性和值之間的關聯性：</span><span class="sxs-lookup"><span data-stu-id="93d07-207">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="93d07-208">運算子</span><span class="sxs-lookup"><span data-stu-id="93d07-208">Operator</span></span> | <span data-ttu-id="93d07-209">功能</span><span class="sxs-lookup"><span data-stu-id="93d07-209">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="93d07-210">完全相符</span><span class="sxs-lookup"><span data-stu-id="93d07-210">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="93d07-211">不完全相符</span><span class="sxs-lookup"><span data-stu-id="93d07-211">Not exact match</span></span> |
| `~`      | <span data-ttu-id="93d07-212">包含</span><span class="sxs-lookup"><span data-stu-id="93d07-212">Contains</span></span>        |

<span data-ttu-id="93d07-213">`<value>` 為字串。</span><span class="sxs-lookup"><span data-stu-id="93d07-213">`<value>` is a string.</span></span> <span data-ttu-id="93d07-214">所有的查閱皆不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="93d07-214">All the lookups are case insensitive.</span></span>

<span data-ttu-id="93d07-215">沒有 `<operator>` 的運算式會自動被視為 `FullyQualifiedName` 屬性上的 `contains` (例如，`dotnet test --filter xyz` 等同於 `dotnet test --filter FullyQualifiedName~xyz`)。</span><span class="sxs-lookup"><span data-stu-id="93d07-215">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="93d07-216">運算式可以使用條件運算子聯結：</span><span class="sxs-lookup"><span data-stu-id="93d07-216">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="93d07-217">運算子</span><span class="sxs-lookup"><span data-stu-id="93d07-217">Operator</span></span>            | <span data-ttu-id="93d07-218">功能</span><span class="sxs-lookup"><span data-stu-id="93d07-218">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="93d07-219">OR</span><span class="sxs-lookup"><span data-stu-id="93d07-219">OR</span></span>       |
| `&`                 | <span data-ttu-id="93d07-220">AND</span><span class="sxs-lookup"><span data-stu-id="93d07-220">AND</span></span>      |

<span data-ttu-id="93d07-221">使用條件運算子時，您可以使用括弧括住運算式 (例如，`(Name~TestMethod1) | (Name~TestMethod2)`)。</span><span class="sxs-lookup"><span data-stu-id="93d07-221">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="93d07-222">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="93d07-222">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="93d07-223">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93d07-223">See also</span></span>

* [<span data-ttu-id="93d07-224">架構與目標</span><span class="sxs-lookup"><span data-stu-id="93d07-224">Frameworks and Targets</span></span>](../../standard/frameworks.md)  
* [<span data-ttu-id="93d07-225">.NET Core 執行階段識別項 (RID) 目錄</span><span class="sxs-lookup"><span data-stu-id="93d07-225">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
