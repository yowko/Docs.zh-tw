---
title: dotnet test 命令 - .NET Core CLI
description: dotnet test 命令是用來在指定的專案中執行單元測試。
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 6102281c4daf149f31e65ef8360831fe9e0ef4f6
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="dotnet-test"></a><span data-ttu-id="3c91f-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="3c91f-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="3c91f-104">名稱</span><span class="sxs-lookup"><span data-stu-id="3c91f-104">Name</span></span>

<span data-ttu-id="3c91f-105">`dotnet test` - 用來執行單元測試的 .NET 測試驅動程式。</span><span class="sxs-lookup"><span data-stu-id="3c91f-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3c91f-106">概要</span><span class="sxs-lookup"><span data-stu-id="3c91f-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="3c91f-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="3c91f-107">.NET Core 2.x</span></span>](#tab/netcore2x)


```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3c91f-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="3c91f-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="3c91f-109">描述</span><span class="sxs-lookup"><span data-stu-id="3c91f-109">Description</span></span>

<span data-ttu-id="3c91f-110">`dotnet test` 命令是用來在指定的專案中執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="3c91f-110">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="3c91f-111">`dotnet test` 命令會啟動為專案指定的測試執行器主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="3c91f-111">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="3c91f-112">測試執行器會執行針對單元測試架構 (例如 MSTest、NUnit 或 xUnit) 定義的測試，並報告每項測試成功還是失敗。</span><span class="sxs-lookup"><span data-stu-id="3c91f-112">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="3c91f-113">測試執行器和單元測試程式庫會封裝為 NuGet 套件，並還原為專案的一般相依性。</span><span class="sxs-lookup"><span data-stu-id="3c91f-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="3c91f-114">測試專案會使用一般 `<PackageReference>` 元素指定測試執行器，如下列範例專案檔中所示：</span><span class="sxs-lookup"><span data-stu-id="3c91f-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="3c91f-115">引數</span><span class="sxs-lookup"><span data-stu-id="3c91f-115">Arguments</span></span>

`PROJECT`

<span data-ttu-id="3c91f-116">指定測試專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="3c91f-116">Specifies a path to the test project.</span></span> <span data-ttu-id="3c91f-117">如果省略，則會預設為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="3c91f-117">If omitted, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="3c91f-118">選項</span><span class="sxs-lookup"><span data-stu-id="3c91f-118">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="3c91f-119">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="3c91f-119">.NET Core 2.x</span></span>](#tab/netcore2x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="3c91f-120">在測試執行中，從指定的路徑使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="3c91f-120">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="3c91f-121">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="3c91f-121">Defines the build configuration.</span></span> <span data-ttu-id="3c91f-122">預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。</span><span class="sxs-lookup"><span data-stu-id="3c91f-122">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="3c91f-123">測試回合啟用資料收集器。</span><span class="sxs-lookup"><span data-stu-id="3c91f-123">Enables data collector for the test run.</span></span> <span data-ttu-id="3c91f-124">如需詳細資訊，請參閱[監視及分析測試回合](https://aka.ms/vstest-collect)。</span><span class="sxs-lookup"><span data-stu-id="3c91f-124">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="3c91f-125">針對測試平台啟用診斷模式，並將診斷訊息寫入至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="3c91f-125">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="3c91f-126">尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。</span><span class="sxs-lookup"><span data-stu-id="3c91f-126">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="3c91f-127">使用指定的運算式篩選出目前專案中的測試。</span><span class="sxs-lookup"><span data-stu-id="3c91f-127">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="3c91f-128">如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。</span><span class="sxs-lookup"><span data-stu-id="3c91f-128">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="3c91f-129">如需如何使用選擇性單元測試篩選的其他資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="3c91f-129">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="3c91f-130">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="3c91f-130">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="3c91f-131">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="3c91f-131">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="3c91f-132">請不要在執行之前建置測試專案。</span><span class="sxs-lookup"><span data-stu-id="3c91f-132">Does not build the test project prior to running it.</span></span>

`--no-restore`

<span data-ttu-id="3c91f-133">執行命令時，不執行隱含的還原。</span><span class="sxs-lookup"><span data-stu-id="3c91f-133">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="3c91f-134">在其中尋找要執行的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="3c91f-134">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="3c91f-135">要放置測試結果的目錄。</span><span class="sxs-lookup"><span data-stu-id="3c91f-135">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="3c91f-136">指定的目錄如不存在即建立。</span><span class="sxs-lookup"><span data-stu-id="3c91f-136">The specified directory will be created if it doesn't exist.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="3c91f-137">執行測試時要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="3c91f-137">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="3c91f-138">列出在目前專案中探索到的所有測試。</span><span class="sxs-lookup"><span data-stu-id="3c91f-138">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="3c91f-139">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="3c91f-139">Sets the verbosity level of the command.</span></span> <span data-ttu-id="3c91f-140">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="3c91f-140">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3c91f-141">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="3c91f-141">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="3c91f-142">在測試執行中，從指定的路徑使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="3c91f-142">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="3c91f-143">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="3c91f-143">Defines the build configuration.</span></span> <span data-ttu-id="3c91f-144">預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。</span><span class="sxs-lookup"><span data-stu-id="3c91f-144">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="3c91f-145">針對測試平台啟用診斷模式，並將診斷訊息寫入至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="3c91f-145">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="3c91f-146">尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。</span><span class="sxs-lookup"><span data-stu-id="3c91f-146">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="3c91f-147">使用指定的運算式篩選出目前專案中的測試。</span><span class="sxs-lookup"><span data-stu-id="3c91f-147">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="3c91f-148">如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。</span><span class="sxs-lookup"><span data-stu-id="3c91f-148">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="3c91f-149">如需如何使用選擇性單元測試篩選的其他資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="3c91f-149">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="3c91f-150">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="3c91f-150">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="3c91f-151">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="3c91f-151">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="3c91f-152">請不要在執行之前建置測試專案。</span><span class="sxs-lookup"><span data-stu-id="3c91f-152">Does not build the test project prior to running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="3c91f-153">在其中尋找要執行的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="3c91f-153">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="3c91f-154">執行測試時要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="3c91f-154">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="3c91f-155">列出在目前專案中探索到的所有測試。</span><span class="sxs-lookup"><span data-stu-id="3c91f-155">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="3c91f-156">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="3c91f-156">Sets the verbosity level of the command.</span></span> <span data-ttu-id="3c91f-157">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="3c91f-157">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="3c91f-158">範例</span><span class="sxs-lookup"><span data-stu-id="3c91f-158">Examples</span></span>

<span data-ttu-id="3c91f-159">執行目前目錄之專案中的測試：</span><span class="sxs-lookup"><span data-stu-id="3c91f-159">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="3c91f-160">執行 `test1` 專案中的測試︰</span><span class="sxs-lookup"><span data-stu-id="3c91f-160">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

## <a name="filter-option-details"></a><span data-ttu-id="3c91f-161">篩選選項詳細資料</span><span class="sxs-lookup"><span data-stu-id="3c91f-161">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="3c91f-162">`<Expression>` 的格式為 `<property><operator><value>[|&<Expression>]`。</span><span class="sxs-lookup"><span data-stu-id="3c91f-162">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="3c91f-163">`<property>` 為 `Test Case` 的屬性。</span><span class="sxs-lookup"><span data-stu-id="3c91f-163">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="3c91f-164">以下為熱門單元測試架構所支援的屬性：</span><span class="sxs-lookup"><span data-stu-id="3c91f-164">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="3c91f-165">測試架構</span><span class="sxs-lookup"><span data-stu-id="3c91f-165">Test Framework</span></span> | <span data-ttu-id="3c91f-166">支援的屬性</span><span class="sxs-lookup"><span data-stu-id="3c91f-166">Supported properties</span></span>                                                                                      |
| :------------: | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="3c91f-167">MSTest</span><span class="sxs-lookup"><span data-stu-id="3c91f-167">MSTest</span></span>         | <ul><li><span data-ttu-id="3c91f-168">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="3c91f-168">FullyQualifiedName</span></span></li><li><span data-ttu-id="3c91f-169">名稱</span><span class="sxs-lookup"><span data-stu-id="3c91f-169">Name</span></span></li><li><span data-ttu-id="3c91f-170">ClassName</span><span class="sxs-lookup"><span data-stu-id="3c91f-170">ClassName</span></span></li><li><span data-ttu-id="3c91f-171">優先權</span><span class="sxs-lookup"><span data-stu-id="3c91f-171">Priority</span></span></li><li><span data-ttu-id="3c91f-172">TestCategory</span><span class="sxs-lookup"><span data-stu-id="3c91f-172">TestCategory</span></span></li></ul> |
| <span data-ttu-id="3c91f-173">xUnit</span><span class="sxs-lookup"><span data-stu-id="3c91f-173">Xunit</span></span>          | <ul><li><span data-ttu-id="3c91f-174">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="3c91f-174">FullyQualifiedName</span></span></li><li><span data-ttu-id="3c91f-175">DisplayName</span><span class="sxs-lookup"><span data-stu-id="3c91f-175">DisplayName</span></span></li><li><span data-ttu-id="3c91f-176">特性</span><span class="sxs-lookup"><span data-stu-id="3c91f-176">Traits</span></span></li></ul>                                   |

<span data-ttu-id="3c91f-177">`<operator>` 描述屬性和值之間的關聯性：</span><span class="sxs-lookup"><span data-stu-id="3c91f-177">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="3c91f-178">運算子</span><span class="sxs-lookup"><span data-stu-id="3c91f-178">Operator</span></span> | <span data-ttu-id="3c91f-179">功能</span><span class="sxs-lookup"><span data-stu-id="3c91f-179">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="3c91f-180">完全相符</span><span class="sxs-lookup"><span data-stu-id="3c91f-180">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="3c91f-181">不完全相符</span><span class="sxs-lookup"><span data-stu-id="3c91f-181">Not exact match</span></span> |
| `~`      | <span data-ttu-id="3c91f-182">包含</span><span class="sxs-lookup"><span data-stu-id="3c91f-182">Contains</span></span>        |

<span data-ttu-id="3c91f-183">`<value>` 為字串。</span><span class="sxs-lookup"><span data-stu-id="3c91f-183">`<value>` is a string.</span></span> <span data-ttu-id="3c91f-184">所有的查閱皆不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="3c91f-184">All the lookups are case insensitive.</span></span>

<span data-ttu-id="3c91f-185">沒有 `<operator>` 的運算式會自動被視為 `FullyQualifiedName` 屬性上的 `contains` (例如，`dotnet test --filter xyz` 等同於 `dotnet test --filter FullyQualifiedName~xyz`)。</span><span class="sxs-lookup"><span data-stu-id="3c91f-185">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="3c91f-186">運算式可以使用條件運算子聯結：</span><span class="sxs-lookup"><span data-stu-id="3c91f-186">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="3c91f-187">運算子</span><span class="sxs-lookup"><span data-stu-id="3c91f-187">Operator</span></span> | <span data-ttu-id="3c91f-188">功能</span><span class="sxs-lookup"><span data-stu-id="3c91f-188">Function</span></span> |
| :------: | :------: |
| <code>&#124;</code>      | <span data-ttu-id="3c91f-189">OR</span><span class="sxs-lookup"><span data-stu-id="3c91f-189">OR</span></span>       |
| `&`      | <span data-ttu-id="3c91f-190">AND</span><span class="sxs-lookup"><span data-stu-id="3c91f-190">AND</span></span>      |

<span data-ttu-id="3c91f-191">使用條件運算子時，您可以使用括弧括住運算式 (例如，`(Name~TestMethod1) | (Name~TestMethod2)`)。</span><span class="sxs-lookup"><span data-stu-id="3c91f-191">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="3c91f-192">如需如何使用選擇性單元測試篩選的其他資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="3c91f-192">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3c91f-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c91f-193">See also</span></span>

 [<span data-ttu-id="3c91f-194">架構與目標</span><span class="sxs-lookup"><span data-stu-id="3c91f-194">Frameworks and Targets</span></span>](../../standard/frameworks.md)  
 [<span data-ttu-id="3c91f-195">.NET Core 執行階段識別項 (RID) 目錄</span><span class="sxs-lookup"><span data-stu-id="3c91f-195">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
