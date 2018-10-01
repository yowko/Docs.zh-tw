---
title: dotnet test 命令 - .NET Core CLI
description: dotnet test 命令是用來在指定的專案中執行單元測試。
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 7946196b27489870da1c16b15cbf5f078ae89c61
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44137196"
---
# <a name="dotnet-test"></a><span data-ttu-id="4f33e-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="4f33e-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="4f33e-104">名稱</span><span class="sxs-lookup"><span data-stu-id="4f33e-104">Name</span></span>

<span data-ttu-id="4f33e-105">`dotnet test` - 用來執行單元測試的 .NET 測試驅動程式。</span><span class="sxs-lookup"><span data-stu-id="4f33e-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4f33e-106">概要</span><span class="sxs-lookup"><span data-stu-id="4f33e-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="4f33e-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="4f33e-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="4f33e-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="4f33e-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4f33e-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4f33e-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="4f33e-110">描述</span><span class="sxs-lookup"><span data-stu-id="4f33e-110">Description</span></span>

<span data-ttu-id="4f33e-111">`dotnet test` 命令是用來在指定的專案中執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="4f33e-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="4f33e-112">`dotnet test` 命令會啟動為專案指定的測試執行器主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="4f33e-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="4f33e-113">測試執行器會執行針對單元測試架構 (例如 MSTest、NUnit 或 xUnit) 定義的測試，並報告每項測試成功還是失敗。</span><span class="sxs-lookup"><span data-stu-id="4f33e-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="4f33e-114">測試執行器和單元測試程式庫會封裝為 NuGet 套件，並還原為專案的一般相依性。</span><span class="sxs-lookup"><span data-stu-id="4f33e-114">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="4f33e-115">測試專案會使用一般 `<PackageReference>` 元素指定測試執行器，如下列範例專案檔中所示：</span><span class="sxs-lookup"><span data-stu-id="4f33e-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="4f33e-116">引數</span><span class="sxs-lookup"><span data-stu-id="4f33e-116">Arguments</span></span>

`PROJECT`

<span data-ttu-id="4f33e-117">測試專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="4f33e-117">Path to the test project.</span></span> <span data-ttu-id="4f33e-118">如果未指定，則會預設為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="4f33e-118">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="4f33e-119">選項</span><span class="sxs-lookup"><span data-stu-id="4f33e-119">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="4f33e-120">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="4f33e-120">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="4f33e-121">在測試執行中，從指定的路徑使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="4f33e-121">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="4f33e-122">在歸責模式下執行測試。</span><span class="sxs-lookup"><span data-stu-id="4f33e-122">Runs the tests in blame mode.</span></span> <span data-ttu-id="4f33e-123">這個選項有助於隔離造成測試主機損毀的問題。</span><span class="sxs-lookup"><span data-stu-id="4f33e-123">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="4f33e-124">它會以 *Sequence.xml* 的形式在目前目錄中建立一個輸出檔，用來擷取損毀前的測試執行順序。</span><span class="sxs-lookup"><span data-stu-id="4f33e-124">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="4f33e-125">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="4f33e-125">Defines the build configuration.</span></span> <span data-ttu-id="4f33e-126">預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。</span><span class="sxs-lookup"><span data-stu-id="4f33e-126">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="4f33e-127">測試回合啟用資料收集器。</span><span class="sxs-lookup"><span data-stu-id="4f33e-127">Enables data collector for the test run.</span></span> <span data-ttu-id="4f33e-128">如需詳細資訊，請參閱[監視及分析測試回合](https://aka.ms/vstest-collect)。</span><span class="sxs-lookup"><span data-stu-id="4f33e-128">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="4f33e-129">針對測試平台啟用診斷模式，並將診斷訊息寫入至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="4f33e-129">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="4f33e-130">尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。</span><span class="sxs-lookup"><span data-stu-id="4f33e-130">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="4f33e-131">使用指定的運算式篩選出目前專案中的測試。</span><span class="sxs-lookup"><span data-stu-id="4f33e-131">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="4f33e-132">如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。</span><span class="sxs-lookup"><span data-stu-id="4f33e-132">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="4f33e-133">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="4f33e-133">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="4f33e-134">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="4f33e-134">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="4f33e-135">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="4f33e-135">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="4f33e-136">不會在執行前建置測試專案。</span><span class="sxs-lookup"><span data-stu-id="4f33e-136">Doesn't build the test project before running it.</span></span> <span data-ttu-id="4f33e-137">它也會隱含設定 `--no-restore` 旗標。</span><span class="sxs-lookup"><span data-stu-id="4f33e-137">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="4f33e-138">執行命令時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="4f33e-138">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="4f33e-139">在其中尋找要執行的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="4f33e-139">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="4f33e-140">要放置測試結果的目錄。</span><span class="sxs-lookup"><span data-stu-id="4f33e-140">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="4f33e-141">如果指定的目錄不存在，則會建立該目錄。</span><span class="sxs-lookup"><span data-stu-id="4f33e-141">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="4f33e-142">執行測試時要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="4f33e-142">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="4f33e-143">列出在目前專案中探索到的所有測試。</span><span class="sxs-lookup"><span data-stu-id="4f33e-143">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="4f33e-144">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="4f33e-144">Sets the verbosity level of the command.</span></span> <span data-ttu-id="4f33e-145">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="4f33e-145">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="4f33e-146">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="4f33e-146">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="4f33e-147">在測試執行中，從指定的路徑使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="4f33e-147">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="4f33e-148">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="4f33e-148">Defines the build configuration.</span></span> <span data-ttu-id="4f33e-149">預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。</span><span class="sxs-lookup"><span data-stu-id="4f33e-149">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="4f33e-150">測試回合啟用資料收集器。</span><span class="sxs-lookup"><span data-stu-id="4f33e-150">Enables data collector for the test run.</span></span> <span data-ttu-id="4f33e-151">如需詳細資訊，請參閱[監視及分析測試回合](https://aka.ms/vstest-collect)。</span><span class="sxs-lookup"><span data-stu-id="4f33e-151">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="4f33e-152">針對測試平台啟用診斷模式，並將診斷訊息寫入至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="4f33e-152">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="4f33e-153">尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。</span><span class="sxs-lookup"><span data-stu-id="4f33e-153">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="4f33e-154">使用指定的運算式篩選出目前專案中的測試。</span><span class="sxs-lookup"><span data-stu-id="4f33e-154">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="4f33e-155">如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。</span><span class="sxs-lookup"><span data-stu-id="4f33e-155">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="4f33e-156">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="4f33e-156">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="4f33e-157">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="4f33e-157">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="4f33e-158">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="4f33e-158">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="4f33e-159">不會在執行前建置測試專案。</span><span class="sxs-lookup"><span data-stu-id="4f33e-159">Doesn't build the test project before running it.</span></span> <span data-ttu-id="4f33e-160">它也會隱含設定 `--no-restore` 旗標。</span><span class="sxs-lookup"><span data-stu-id="4f33e-160">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="4f33e-161">執行命令時，不會執行隱含還原。</span><span class="sxs-lookup"><span data-stu-id="4f33e-161">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="4f33e-162">在其中尋找要執行的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="4f33e-162">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="4f33e-163">要放置測試結果的目錄。</span><span class="sxs-lookup"><span data-stu-id="4f33e-163">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="4f33e-164">如果指定的目錄不存在，則會建立該目錄。</span><span class="sxs-lookup"><span data-stu-id="4f33e-164">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="4f33e-165">執行測試時要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="4f33e-165">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="4f33e-166">列出在目前專案中探索到的所有測試。</span><span class="sxs-lookup"><span data-stu-id="4f33e-166">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="4f33e-167">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="4f33e-167">Sets the verbosity level of the command.</span></span> <span data-ttu-id="4f33e-168">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="4f33e-168">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4f33e-169">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4f33e-169">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="4f33e-170">在測試執行中，從指定的路徑使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="4f33e-170">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="4f33e-171">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="4f33e-171">Defines the build configuration.</span></span> <span data-ttu-id="4f33e-172">預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。</span><span class="sxs-lookup"><span data-stu-id="4f33e-172">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="4f33e-173">針對測試平台啟用診斷模式，並將診斷訊息寫入至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="4f33e-173">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="4f33e-174">尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。</span><span class="sxs-lookup"><span data-stu-id="4f33e-174">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="4f33e-175">使用指定的運算式篩選出目前專案中的測試。</span><span class="sxs-lookup"><span data-stu-id="4f33e-175">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="4f33e-176">如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。</span><span class="sxs-lookup"><span data-stu-id="4f33e-176">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="4f33e-177">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="4f33e-177">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="4f33e-178">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="4f33e-178">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="4f33e-179">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="4f33e-179">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="4f33e-180">不會在執行前建置測試專案。</span><span class="sxs-lookup"><span data-stu-id="4f33e-180">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="4f33e-181">在其中尋找要執行的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="4f33e-181">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="4f33e-182">執行測試時要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="4f33e-182">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="4f33e-183">列出在目前專案中探索到的所有測試。</span><span class="sxs-lookup"><span data-stu-id="4f33e-183">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="4f33e-184">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="4f33e-184">Sets the verbosity level of the command.</span></span> <span data-ttu-id="4f33e-185">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="4f33e-185">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="4f33e-186">範例</span><span class="sxs-lookup"><span data-stu-id="4f33e-186">Examples</span></span>

<span data-ttu-id="4f33e-187">執行目前目錄之專案中的測試：</span><span class="sxs-lookup"><span data-stu-id="4f33e-187">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="4f33e-188">執行 `test1` 專案中的測試︰</span><span class="sxs-lookup"><span data-stu-id="4f33e-188">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

<span data-ttu-id="4f33e-189">在目前目錄中的專案中執行測試，並以 trx 格式產生測試結果檔案：</span><span class="sxs-lookup"><span data-stu-id="4f33e-189">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

`dotnet test --logger:trx`

## <a name="filter-option-details"></a><span data-ttu-id="4f33e-190">篩選選項詳細資料</span><span class="sxs-lookup"><span data-stu-id="4f33e-190">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="4f33e-191">`<Expression>` 的格式為 `<property><operator><value>[|&<Expression>]`。</span><span class="sxs-lookup"><span data-stu-id="4f33e-191">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="4f33e-192">`<property>` 為 `Test Case` 的屬性。</span><span class="sxs-lookup"><span data-stu-id="4f33e-192">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="4f33e-193">以下為熱門單元測試架構所支援的屬性：</span><span class="sxs-lookup"><span data-stu-id="4f33e-193">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="4f33e-194">測試架構</span><span class="sxs-lookup"><span data-stu-id="4f33e-194">Test Framework</span></span> | <span data-ttu-id="4f33e-195">支援的屬性</span><span class="sxs-lookup"><span data-stu-id="4f33e-195">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="4f33e-196">MSTest</span><span class="sxs-lookup"><span data-stu-id="4f33e-196">MSTest</span></span>         | <ul><li><span data-ttu-id="4f33e-197">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="4f33e-197">FullyQualifiedName</span></span></li><li><span data-ttu-id="4f33e-198">名稱</span><span class="sxs-lookup"><span data-stu-id="4f33e-198">Name</span></span></li><li><span data-ttu-id="4f33e-199">ClassName</span><span class="sxs-lookup"><span data-stu-id="4f33e-199">ClassName</span></span></li><li><span data-ttu-id="4f33e-200">優先權</span><span class="sxs-lookup"><span data-stu-id="4f33e-200">Priority</span></span></li><li><span data-ttu-id="4f33e-201">TestCategory</span><span class="sxs-lookup"><span data-stu-id="4f33e-201">TestCategory</span></span></li></ul> |
| <span data-ttu-id="4f33e-202">xUnit</span><span class="sxs-lookup"><span data-stu-id="4f33e-202">xUnit</span></span>          | <ul><li><span data-ttu-id="4f33e-203">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="4f33e-203">FullyQualifiedName</span></span></li><li><span data-ttu-id="4f33e-204">DisplayName</span><span class="sxs-lookup"><span data-stu-id="4f33e-204">DisplayName</span></span></li><li><span data-ttu-id="4f33e-205">特性</span><span class="sxs-lookup"><span data-stu-id="4f33e-205">Traits</span></span></li></ul>                                   |

<span data-ttu-id="4f33e-206">`<operator>` 描述屬性和值之間的關聯性：</span><span class="sxs-lookup"><span data-stu-id="4f33e-206">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="4f33e-207">運算子</span><span class="sxs-lookup"><span data-stu-id="4f33e-207">Operator</span></span> | <span data-ttu-id="4f33e-208">功能</span><span class="sxs-lookup"><span data-stu-id="4f33e-208">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="4f33e-209">完全相符</span><span class="sxs-lookup"><span data-stu-id="4f33e-209">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="4f33e-210">不完全相符</span><span class="sxs-lookup"><span data-stu-id="4f33e-210">Not exact match</span></span> |
| `~`      | <span data-ttu-id="4f33e-211">包含</span><span class="sxs-lookup"><span data-stu-id="4f33e-211">Contains</span></span>        |

<span data-ttu-id="4f33e-212">`<value>` 為字串。</span><span class="sxs-lookup"><span data-stu-id="4f33e-212">`<value>` is a string.</span></span> <span data-ttu-id="4f33e-213">所有的查閱皆不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="4f33e-213">All the lookups are case insensitive.</span></span>

<span data-ttu-id="4f33e-214">沒有 `<operator>` 的運算式會自動被視為 `FullyQualifiedName` 屬性上的 `contains` (例如，`dotnet test --filter xyz` 等同於 `dotnet test --filter FullyQualifiedName~xyz`)。</span><span class="sxs-lookup"><span data-stu-id="4f33e-214">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="4f33e-215">運算式可以使用條件運算子聯結：</span><span class="sxs-lookup"><span data-stu-id="4f33e-215">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="4f33e-216">運算子</span><span class="sxs-lookup"><span data-stu-id="4f33e-216">Operator</span></span>            | <span data-ttu-id="4f33e-217">功能</span><span class="sxs-lookup"><span data-stu-id="4f33e-217">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="4f33e-218">OR</span><span class="sxs-lookup"><span data-stu-id="4f33e-218">OR</span></span>       |
| `&`                 | <span data-ttu-id="4f33e-219">AND</span><span class="sxs-lookup"><span data-stu-id="4f33e-219">AND</span></span>      |

<span data-ttu-id="4f33e-220">使用條件運算子時，您可以使用括弧括住運算式 (例如，`(Name~TestMethod1) | (Name~TestMethod2)`)。</span><span class="sxs-lookup"><span data-stu-id="4f33e-220">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="4f33e-221">如需如何使用選擇性單元測試篩選的詳細資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="4f33e-221">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4f33e-222">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f33e-222">See also</span></span>

* [<span data-ttu-id="4f33e-223">架構與目標</span><span class="sxs-lookup"><span data-stu-id="4f33e-223">Frameworks and Targets</span></span>](../../standard/frameworks.md)  
* [<span data-ttu-id="4f33e-224">.NET Core 執行階段識別項 (RID) 目錄</span><span class="sxs-lookup"><span data-stu-id="4f33e-224">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
