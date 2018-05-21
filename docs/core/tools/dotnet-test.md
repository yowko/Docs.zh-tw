---
title: dotnet test 命令 - .NET Core CLI
description: dotnet test 命令是用來在指定的專案中執行單元測試。
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.openlocfilehash: d85ca0bf75baa94e63358bd66d11bc29e8b9284b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-test"></a><span data-ttu-id="df26a-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="df26a-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="df26a-104">名稱</span><span class="sxs-lookup"><span data-stu-id="df26a-104">Name</span></span>

<span data-ttu-id="df26a-105">`dotnet test` - 用來執行單元測試的 .NET 測試驅動程式。</span><span class="sxs-lookup"><span data-stu-id="df26a-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="df26a-106">概要</span><span class="sxs-lookup"><span data-stu-id="df26a-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="df26a-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="df26a-107">.NET Core 2.x</span></span>](#tab/netcore2x)


```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="df26a-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="df26a-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="df26a-109">描述</span><span class="sxs-lookup"><span data-stu-id="df26a-109">Description</span></span>

<span data-ttu-id="df26a-110">`dotnet test` 命令是用來在指定的專案中執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="df26a-110">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="df26a-111">`dotnet test` 命令會啟動為專案指定的測試執行器主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="df26a-111">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="df26a-112">測試執行器會執行針對單元測試架構 (例如 MSTest、NUnit 或 xUnit) 定義的測試，並報告每項測試成功還是失敗。</span><span class="sxs-lookup"><span data-stu-id="df26a-112">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="df26a-113">測試執行器和單元測試程式庫會封裝為 NuGet 套件，並還原為專案的一般相依性。</span><span class="sxs-lookup"><span data-stu-id="df26a-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="df26a-114">測試專案會使用一般 `<PackageReference>` 元素指定測試執行器，如下列範例專案檔中所示：</span><span class="sxs-lookup"><span data-stu-id="df26a-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="df26a-115">引數</span><span class="sxs-lookup"><span data-stu-id="df26a-115">Arguments</span></span>

`PROJECT`

<span data-ttu-id="df26a-116">指定測試專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="df26a-116">Specifies a path to the test project.</span></span> <span data-ttu-id="df26a-117">如果省略，則會預設為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="df26a-117">If omitted, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="df26a-118">選項</span><span class="sxs-lookup"><span data-stu-id="df26a-118">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="df26a-119">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="df26a-119">.NET Core 2.x</span></span>](#tab/netcore2x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="df26a-120">在測試執行中，從指定的路徑使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="df26a-120">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="df26a-121">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="df26a-121">Defines the build configuration.</span></span> <span data-ttu-id="df26a-122">預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。</span><span class="sxs-lookup"><span data-stu-id="df26a-122">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="df26a-123">測試回合啟用資料收集器。</span><span class="sxs-lookup"><span data-stu-id="df26a-123">Enables data collector for the test run.</span></span> <span data-ttu-id="df26a-124">如需詳細資訊，請參閱[監視及分析測試回合](https://aka.ms/vstest-collect)。</span><span class="sxs-lookup"><span data-stu-id="df26a-124">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="df26a-125">針對測試平台啟用診斷模式，並將診斷訊息寫入至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="df26a-125">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="df26a-126">尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。</span><span class="sxs-lookup"><span data-stu-id="df26a-126">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="df26a-127">使用指定的運算式篩選出目前專案中的測試。</span><span class="sxs-lookup"><span data-stu-id="df26a-127">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="df26a-128">如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。</span><span class="sxs-lookup"><span data-stu-id="df26a-128">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="df26a-129">如需如何使用選擇性單元測試篩選的其他資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="df26a-129">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="df26a-130">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="df26a-130">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="df26a-131">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="df26a-131">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="df26a-132">請不要在執行之前建置測試專案。</span><span class="sxs-lookup"><span data-stu-id="df26a-132">Does not build the test project prior to running it.</span></span>

`--no-restore`

<span data-ttu-id="df26a-133">執行命令時，不執行隱含的還原。</span><span class="sxs-lookup"><span data-stu-id="df26a-133">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="df26a-134">在其中尋找要執行的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="df26a-134">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="df26a-135">要放置測試結果的目錄。</span><span class="sxs-lookup"><span data-stu-id="df26a-135">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="df26a-136">指定的目錄如不存在即建立。</span><span class="sxs-lookup"><span data-stu-id="df26a-136">The specified directory will be created if it doesn't exist.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="df26a-137">執行測試時要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="df26a-137">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="df26a-138">列出在目前專案中探索到的所有測試。</span><span class="sxs-lookup"><span data-stu-id="df26a-138">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="df26a-139">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="df26a-139">Sets the verbosity level of the command.</span></span> <span data-ttu-id="df26a-140">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="df26a-140">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="df26a-141">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="df26a-141">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="df26a-142">在測試執行中，從指定的路徑使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="df26a-142">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="df26a-143">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="df26a-143">Defines the build configuration.</span></span> <span data-ttu-id="df26a-144">預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。</span><span class="sxs-lookup"><span data-stu-id="df26a-144">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="df26a-145">針對測試平台啟用診斷模式，並將診斷訊息寫入至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="df26a-145">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="df26a-146">尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。</span><span class="sxs-lookup"><span data-stu-id="df26a-146">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="df26a-147">使用指定的運算式篩選出目前專案中的測試。</span><span class="sxs-lookup"><span data-stu-id="df26a-147">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="df26a-148">如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。</span><span class="sxs-lookup"><span data-stu-id="df26a-148">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="df26a-149">如需如何使用選擇性單元測試篩選的其他資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="df26a-149">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="df26a-150">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="df26a-150">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="df26a-151">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="df26a-151">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="df26a-152">請不要在執行之前建置測試專案。</span><span class="sxs-lookup"><span data-stu-id="df26a-152">Does not build the test project prior to running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="df26a-153">在其中尋找要執行的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="df26a-153">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="df26a-154">執行測試時要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="df26a-154">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="df26a-155">列出在目前專案中探索到的所有測試。</span><span class="sxs-lookup"><span data-stu-id="df26a-155">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="df26a-156">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="df26a-156">Sets the verbosity level of the command.</span></span> <span data-ttu-id="df26a-157">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="df26a-157">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="df26a-158">範例</span><span class="sxs-lookup"><span data-stu-id="df26a-158">Examples</span></span>

<span data-ttu-id="df26a-159">執行目前目錄之專案中的測試：</span><span class="sxs-lookup"><span data-stu-id="df26a-159">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="df26a-160">執行 `test1` 專案中的測試︰</span><span class="sxs-lookup"><span data-stu-id="df26a-160">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

## <a name="filter-option-details"></a><span data-ttu-id="df26a-161">篩選選項詳細資料</span><span class="sxs-lookup"><span data-stu-id="df26a-161">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="df26a-162">`<Expression>` 的格式為 `<property><operator><value>[|&<Expression>]`。</span><span class="sxs-lookup"><span data-stu-id="df26a-162">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="df26a-163">`<property>` 為 `Test Case` 的屬性。</span><span class="sxs-lookup"><span data-stu-id="df26a-163">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="df26a-164">以下為熱門單元測試架構所支援的屬性：</span><span class="sxs-lookup"><span data-stu-id="df26a-164">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="df26a-165">測試架構</span><span class="sxs-lookup"><span data-stu-id="df26a-165">Test Framework</span></span> | <span data-ttu-id="df26a-166">支援的屬性</span><span class="sxs-lookup"><span data-stu-id="df26a-166">Supported properties</span></span>                                                                                      |
| :------------: | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="df26a-167">MSTest</span><span class="sxs-lookup"><span data-stu-id="df26a-167">MSTest</span></span>         | <ul><li><span data-ttu-id="df26a-168">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="df26a-168">FullyQualifiedName</span></span></li><li><span data-ttu-id="df26a-169">名稱</span><span class="sxs-lookup"><span data-stu-id="df26a-169">Name</span></span></li><li><span data-ttu-id="df26a-170">ClassName</span><span class="sxs-lookup"><span data-stu-id="df26a-170">ClassName</span></span></li><li><span data-ttu-id="df26a-171">優先權</span><span class="sxs-lookup"><span data-stu-id="df26a-171">Priority</span></span></li><li><span data-ttu-id="df26a-172">TestCategory</span><span class="sxs-lookup"><span data-stu-id="df26a-172">TestCategory</span></span></li></ul> |
| <span data-ttu-id="df26a-173">xUnit</span><span class="sxs-lookup"><span data-stu-id="df26a-173">Xunit</span></span>          | <ul><li><span data-ttu-id="df26a-174">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="df26a-174">FullyQualifiedName</span></span></li><li><span data-ttu-id="df26a-175">DisplayName</span><span class="sxs-lookup"><span data-stu-id="df26a-175">DisplayName</span></span></li><li><span data-ttu-id="df26a-176">特性</span><span class="sxs-lookup"><span data-stu-id="df26a-176">Traits</span></span></li></ul>                                   |

<span data-ttu-id="df26a-177">`<operator>` 描述屬性和值之間的關聯性：</span><span class="sxs-lookup"><span data-stu-id="df26a-177">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="df26a-178">運算子</span><span class="sxs-lookup"><span data-stu-id="df26a-178">Operator</span></span> | <span data-ttu-id="df26a-179">功能</span><span class="sxs-lookup"><span data-stu-id="df26a-179">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="df26a-180">完全相符</span><span class="sxs-lookup"><span data-stu-id="df26a-180">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="df26a-181">不完全相符</span><span class="sxs-lookup"><span data-stu-id="df26a-181">Not exact match</span></span> |
| `~`      | <span data-ttu-id="df26a-182">包含</span><span class="sxs-lookup"><span data-stu-id="df26a-182">Contains</span></span>        |

<span data-ttu-id="df26a-183">`<value>` 為字串。</span><span class="sxs-lookup"><span data-stu-id="df26a-183">`<value>` is a string.</span></span> <span data-ttu-id="df26a-184">所有的查閱皆不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="df26a-184">All the lookups are case insensitive.</span></span>

<span data-ttu-id="df26a-185">沒有 `<operator>` 的運算式會自動被視為 `FullyQualifiedName` 屬性上的 `contains` (例如，`dotnet test --filter xyz` 等同於 `dotnet test --filter FullyQualifiedName~xyz`)。</span><span class="sxs-lookup"><span data-stu-id="df26a-185">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="df26a-186">運算式可以使用條件運算子聯結：</span><span class="sxs-lookup"><span data-stu-id="df26a-186">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="df26a-187">運算子</span><span class="sxs-lookup"><span data-stu-id="df26a-187">Operator</span></span> | <span data-ttu-id="df26a-188">功能</span><span class="sxs-lookup"><span data-stu-id="df26a-188">Function</span></span> |
| :------: | :------: |
| <code>&#124;</code>      | <span data-ttu-id="df26a-189">OR</span><span class="sxs-lookup"><span data-stu-id="df26a-189">OR</span></span>       |
| `&`      | <span data-ttu-id="df26a-190">AND</span><span class="sxs-lookup"><span data-stu-id="df26a-190">AND</span></span>      |

<span data-ttu-id="df26a-191">使用條件運算子時，您可以使用括弧括住運算式 (例如，`(Name~TestMethod1) | (Name~TestMethod2)`)。</span><span class="sxs-lookup"><span data-stu-id="df26a-191">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="df26a-192">如需如何使用選擇性單元測試篩選的其他資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="df26a-192">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="df26a-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df26a-193">See also</span></span>

 [<span data-ttu-id="df26a-194">架構與目標</span><span class="sxs-lookup"><span data-stu-id="df26a-194">Frameworks and Targets</span></span>](../../standard/frameworks.md)  
 [<span data-ttu-id="df26a-195">.NET Core 執行階段識別項 (RID) 目錄</span><span class="sxs-lookup"><span data-stu-id="df26a-195">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
