---
title: dotnet test 命令 - .NET Core CLI
description: dotnet test 命令是用來在指定的專案中執行單元測試。
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 8a10ac9175ee5fcf8649efbb07d8d382ac3afdc7
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696266"
---
# <a name="dotnet-test"></a><span data-ttu-id="4d8db-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="4d8db-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="4d8db-104">名稱</span><span class="sxs-lookup"><span data-stu-id="4d8db-104">Name</span></span>

<span data-ttu-id="4d8db-105">`dotnet test` - 用來執行單元測試的 .NET 測試驅動程式。</span><span class="sxs-lookup"><span data-stu-id="4d8db-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4d8db-106">概要</span><span class="sxs-lookup"><span data-stu-id="4d8db-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="4d8db-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="4d8db-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="4d8db-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="4d8db-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4d8db-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4d8db-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="4d8db-110">描述</span><span class="sxs-lookup"><span data-stu-id="4d8db-110">Description</span></span>

<span data-ttu-id="4d8db-111">`dotnet test` 命令是用來在指定的專案中執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="4d8db-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="4d8db-112">`dotnet test` 命令會啟動為專案指定的測試執行器主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="4d8db-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="4d8db-113">測試執行器會執行針對單元測試架構 (例如 MSTest、NUnit 或 xUnit) 定義的測試，並報告每項測試成功還是失敗。</span><span class="sxs-lookup"><span data-stu-id="4d8db-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="4d8db-114">測試執行器和單元測試程式庫會封裝為 NuGet 套件，並還原為專案的一般相依性。</span><span class="sxs-lookup"><span data-stu-id="4d8db-114">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="4d8db-115">測試專案會使用一般 `<PackageReference>` 元素指定測試執行器，如下列範例專案檔中所示：</span><span class="sxs-lookup"><span data-stu-id="4d8db-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="4d8db-116">引數</span><span class="sxs-lookup"><span data-stu-id="4d8db-116">Arguments</span></span>

`PROJECT`

<span data-ttu-id="4d8db-117">測試專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="4d8db-117">Path to the test project.</span></span> <span data-ttu-id="4d8db-118">如果未指定，則會預設為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="4d8db-118">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="4d8db-119">選項</span><span class="sxs-lookup"><span data-stu-id="4d8db-119">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="4d8db-120">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="4d8db-120">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="4d8db-121">在測試執行中，從指定的路徑使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="4d8db-121">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="4d8db-122">在歸責模式下執行測試。</span><span class="sxs-lookup"><span data-stu-id="4d8db-122">Runs the tests in blame mode.</span></span> <span data-ttu-id="4d8db-123">這個選項有助於隔離造成測試主機損毀的問題。</span><span class="sxs-lookup"><span data-stu-id="4d8db-123">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="4d8db-124">它會以 *Sequence.xml* 的形式在目前目錄中建立一個輸出檔，用來擷取損毀前的測試執行順序。</span><span class="sxs-lookup"><span data-stu-id="4d8db-124">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="4d8db-125">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="4d8db-125">Defines the build configuration.</span></span> <span data-ttu-id="4d8db-126">預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。</span><span class="sxs-lookup"><span data-stu-id="4d8db-126">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="4d8db-127">測試回合啟用資料收集器。</span><span class="sxs-lookup"><span data-stu-id="4d8db-127">Enables data collector for the test run.</span></span> <span data-ttu-id="4d8db-128">如需詳細資訊，請參閱[監視及分析測試回合](https://aka.ms/vstest-collect)。</span><span class="sxs-lookup"><span data-stu-id="4d8db-128">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="4d8db-129">針對測試平台啟用診斷模式，並將診斷訊息寫入至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="4d8db-129">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="4d8db-130">尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。</span><span class="sxs-lookup"><span data-stu-id="4d8db-130">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="4d8db-131">使用指定的運算式篩選出目前專案中的測試。</span><span class="sxs-lookup"><span data-stu-id="4d8db-131">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="4d8db-132">如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。</span><span class="sxs-lookup"><span data-stu-id="4d8db-132">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="4d8db-133">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="4d8db-133">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="4d8db-134">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="4d8db-134">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="4d8db-135">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="4d8db-135">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="4d8db-136">不會在執行前建置測試專案。</span><span class="sxs-lookup"><span data-stu-id="4d8db-136">Doesn't build the test project before running it.</span></span> <span data-ttu-id="4d8db-137">它也會隱含設定 `--no-restore` 旗標。</span><span class="sxs-lookup"><span data-stu-id="4d8db-137">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="4d8db-138">執行命令時，不會執行隱含的還原。</span><span class="sxs-lookup"><span data-stu-id="4d8db-138">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="4d8db-139">在其中尋找要執行的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="4d8db-139">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="4d8db-140">要放置測試結果的目錄。</span><span class="sxs-lookup"><span data-stu-id="4d8db-140">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="4d8db-141">如果指定的目錄不存在，則會建立該目錄。</span><span class="sxs-lookup"><span data-stu-id="4d8db-141">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="4d8db-142">執行測試時要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="4d8db-142">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="4d8db-143">列出在目前專案中探索到的所有測試。</span><span class="sxs-lookup"><span data-stu-id="4d8db-143">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="4d8db-144">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="4d8db-144">Sets the verbosity level of the command.</span></span> <span data-ttu-id="4d8db-145">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="4d8db-145">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="4d8db-146">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="4d8db-146">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="4d8db-147">在測試執行中，從指定的路徑使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="4d8db-147">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="4d8db-148">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="4d8db-148">Defines the build configuration.</span></span> <span data-ttu-id="4d8db-149">預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。</span><span class="sxs-lookup"><span data-stu-id="4d8db-149">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="4d8db-150">測試回合啟用資料收集器。</span><span class="sxs-lookup"><span data-stu-id="4d8db-150">Enables data collector for the test run.</span></span> <span data-ttu-id="4d8db-151">如需詳細資訊，請參閱[監視及分析測試回合](https://aka.ms/vstest-collect)。</span><span class="sxs-lookup"><span data-stu-id="4d8db-151">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="4d8db-152">針對測試平台啟用診斷模式，並將診斷訊息寫入至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="4d8db-152">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="4d8db-153">尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。</span><span class="sxs-lookup"><span data-stu-id="4d8db-153">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="4d8db-154">使用指定的運算式篩選出目前專案中的測試。</span><span class="sxs-lookup"><span data-stu-id="4d8db-154">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="4d8db-155">如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。</span><span class="sxs-lookup"><span data-stu-id="4d8db-155">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="4d8db-156">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="4d8db-156">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="4d8db-157">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="4d8db-157">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="4d8db-158">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="4d8db-158">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="4d8db-159">不會在執行前建置測試專案。</span><span class="sxs-lookup"><span data-stu-id="4d8db-159">Doesn't build the test project before running it.</span></span> <span data-ttu-id="4d8db-160">它也會隱含設定 `--no-restore` 旗標。</span><span class="sxs-lookup"><span data-stu-id="4d8db-160">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="4d8db-161">執行命令時，不會執行隱含的還原。</span><span class="sxs-lookup"><span data-stu-id="4d8db-161">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="4d8db-162">在其中尋找要執行的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="4d8db-162">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="4d8db-163">要放置測試結果的目錄。</span><span class="sxs-lookup"><span data-stu-id="4d8db-163">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="4d8db-164">如果指定的目錄不存在，則會建立該目錄。</span><span class="sxs-lookup"><span data-stu-id="4d8db-164">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="4d8db-165">執行測試時要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="4d8db-165">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="4d8db-166">列出在目前專案中探索到的所有測試。</span><span class="sxs-lookup"><span data-stu-id="4d8db-166">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="4d8db-167">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="4d8db-167">Sets the verbosity level of the command.</span></span> <span data-ttu-id="4d8db-168">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="4d8db-168">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4d8db-169">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4d8db-169">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="4d8db-170">在測試執行中，從指定的路徑使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="4d8db-170">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="4d8db-171">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="4d8db-171">Defines the build configuration.</span></span> <span data-ttu-id="4d8db-172">預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。</span><span class="sxs-lookup"><span data-stu-id="4d8db-172">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="4d8db-173">針對測試平台啟用診斷模式，並將診斷訊息寫入至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="4d8db-173">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="4d8db-174">尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。</span><span class="sxs-lookup"><span data-stu-id="4d8db-174">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="4d8db-175">使用指定的運算式篩選出目前專案中的測試。</span><span class="sxs-lookup"><span data-stu-id="4d8db-175">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="4d8db-176">如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。</span><span class="sxs-lookup"><span data-stu-id="4d8db-176">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="4d8db-177">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="4d8db-177">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="4d8db-178">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="4d8db-178">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="4d8db-179">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="4d8db-179">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="4d8db-180">不會在執行前建置測試專案。</span><span class="sxs-lookup"><span data-stu-id="4d8db-180">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="4d8db-181">在其中尋找要執行的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="4d8db-181">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="4d8db-182">執行測試時要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="4d8db-182">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="4d8db-183">列出在目前專案中探索到的所有測試。</span><span class="sxs-lookup"><span data-stu-id="4d8db-183">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="4d8db-184">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="4d8db-184">Sets the verbosity level of the command.</span></span> <span data-ttu-id="4d8db-185">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="4d8db-185">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="4d8db-186">範例</span><span class="sxs-lookup"><span data-stu-id="4d8db-186">Examples</span></span>

<span data-ttu-id="4d8db-187">執行目前目錄之專案中的測試：</span><span class="sxs-lookup"><span data-stu-id="4d8db-187">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="4d8db-188">執行 `test1` 專案中的測試︰</span><span class="sxs-lookup"><span data-stu-id="4d8db-188">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

## <a name="filter-option-details"></a><span data-ttu-id="4d8db-189">篩選選項詳細資料</span><span class="sxs-lookup"><span data-stu-id="4d8db-189">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="4d8db-190">`<Expression>` 的格式為 `<property><operator><value>[|&<Expression>]`。</span><span class="sxs-lookup"><span data-stu-id="4d8db-190">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="4d8db-191">`<property>` 為 `Test Case` 的屬性。</span><span class="sxs-lookup"><span data-stu-id="4d8db-191">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="4d8db-192">以下為熱門單元測試架構所支援的屬性：</span><span class="sxs-lookup"><span data-stu-id="4d8db-192">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="4d8db-193">測試架構</span><span class="sxs-lookup"><span data-stu-id="4d8db-193">Test Framework</span></span> | <span data-ttu-id="4d8db-194">支援的屬性</span><span class="sxs-lookup"><span data-stu-id="4d8db-194">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="4d8db-195">MSTest</span><span class="sxs-lookup"><span data-stu-id="4d8db-195">MSTest</span></span>         | <ul><li><span data-ttu-id="4d8db-196">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="4d8db-196">FullyQualifiedName</span></span></li><li><span data-ttu-id="4d8db-197">名稱</span><span class="sxs-lookup"><span data-stu-id="4d8db-197">Name</span></span></li><li><span data-ttu-id="4d8db-198">ClassName</span><span class="sxs-lookup"><span data-stu-id="4d8db-198">ClassName</span></span></li><li><span data-ttu-id="4d8db-199">優先權</span><span class="sxs-lookup"><span data-stu-id="4d8db-199">Priority</span></span></li><li><span data-ttu-id="4d8db-200">TestCategory</span><span class="sxs-lookup"><span data-stu-id="4d8db-200">TestCategory</span></span></li></ul> |
| <span data-ttu-id="4d8db-201">xUnit</span><span class="sxs-lookup"><span data-stu-id="4d8db-201">xUnit</span></span>          | <ul><li><span data-ttu-id="4d8db-202">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="4d8db-202">FullyQualifiedName</span></span></li><li><span data-ttu-id="4d8db-203">DisplayName</span><span class="sxs-lookup"><span data-stu-id="4d8db-203">DisplayName</span></span></li><li><span data-ttu-id="4d8db-204">特性</span><span class="sxs-lookup"><span data-stu-id="4d8db-204">Traits</span></span></li></ul>                                   |

<span data-ttu-id="4d8db-205">`<operator>` 描述屬性和值之間的關聯性：</span><span class="sxs-lookup"><span data-stu-id="4d8db-205">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="4d8db-206">運算子</span><span class="sxs-lookup"><span data-stu-id="4d8db-206">Operator</span></span> | <span data-ttu-id="4d8db-207">功能</span><span class="sxs-lookup"><span data-stu-id="4d8db-207">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="4d8db-208">完全相符</span><span class="sxs-lookup"><span data-stu-id="4d8db-208">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="4d8db-209">不完全相符</span><span class="sxs-lookup"><span data-stu-id="4d8db-209">Not exact match</span></span> |
| `~`      | <span data-ttu-id="4d8db-210">包含</span><span class="sxs-lookup"><span data-stu-id="4d8db-210">Contains</span></span>        |

<span data-ttu-id="4d8db-211">`<value>` 為字串。</span><span class="sxs-lookup"><span data-stu-id="4d8db-211">`<value>` is a string.</span></span> <span data-ttu-id="4d8db-212">所有的查閱皆不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="4d8db-212">All the lookups are case insensitive.</span></span>

<span data-ttu-id="4d8db-213">沒有 `<operator>` 的運算式會自動被視為 `FullyQualifiedName` 屬性上的 `contains` (例如，`dotnet test --filter xyz` 等同於 `dotnet test --filter FullyQualifiedName~xyz`)。</span><span class="sxs-lookup"><span data-stu-id="4d8db-213">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="4d8db-214">運算式可以使用條件運算子聯結：</span><span class="sxs-lookup"><span data-stu-id="4d8db-214">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="4d8db-215">運算子</span><span class="sxs-lookup"><span data-stu-id="4d8db-215">Operator</span></span>            | <span data-ttu-id="4d8db-216">功能</span><span class="sxs-lookup"><span data-stu-id="4d8db-216">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="4d8db-217">OR</span><span class="sxs-lookup"><span data-stu-id="4d8db-217">OR</span></span>       |
| `&`                 | <span data-ttu-id="4d8db-218">AND</span><span class="sxs-lookup"><span data-stu-id="4d8db-218">AND</span></span>      |

<span data-ttu-id="4d8db-219">使用條件運算子時，您可以使用括弧括住運算式 (例如，`(Name~TestMethod1) | (Name~TestMethod2)`)。</span><span class="sxs-lookup"><span data-stu-id="4d8db-219">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="4d8db-220">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="4d8db-220">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4d8db-221">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d8db-221">See also</span></span>

[<span data-ttu-id="4d8db-222">架構與目標</span><span class="sxs-lookup"><span data-stu-id="4d8db-222">Frameworks and Targets</span></span>](../../standard/frameworks.md)  
[<span data-ttu-id="4d8db-223">.NET Core 執行階段識別項 (RID) 目錄</span><span class="sxs-lookup"><span data-stu-id="4d8db-223">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
