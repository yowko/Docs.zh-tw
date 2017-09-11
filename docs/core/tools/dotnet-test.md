---
title: "dotnet test 命令 - .NET Core CLI"
description: "dotnet test 命令是用來在指定的專案中執行單元測試。"
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.translationtype: HT
ms.sourcegitcommit: a19ab54a6cc44bd7acd1e40a4ca94da52bf14297
ms.openlocfilehash: 55329bed71be21a787d6e77d8c0ea67d607676b8
ms.contentlocale: zh-tw
ms.lasthandoff: 08/14/2017

---
# <a name="dotnet-test"></a><span data-ttu-id="2de65-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="2de65-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="2de65-104">name</span><span class="sxs-lookup"><span data-stu-id="2de65-104">Name</span></span>

<span data-ttu-id="2de65-105">`dotnet test` - 用來執行單元測試的 .NET 測試驅動程式。</span><span class="sxs-lookup"><span data-stu-id="2de65-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2de65-106">概要</span><span class="sxs-lookup"><span data-stu-id="2de65-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="2de65-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="2de65-107">.NET Core 2.x</span></span>](#tab/netcore2x)


```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="2de65-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="2de65-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="2de65-109">說明</span><span class="sxs-lookup"><span data-stu-id="2de65-109">Description</span></span>

<span data-ttu-id="2de65-110">`dotnet test` 命令是用來在指定的專案中執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="2de65-110">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="2de65-111">單元測試是與單元測試架構 (例如 MSTest、NUnit 或 xUnit) 具有相依性的主控台應用程式專案，以及該單元測試架構的 dotnet 測試執行器。</span><span class="sxs-lookup"><span data-stu-id="2de65-111">Unit tests are console application projects that have dependencies on the unit test framework (for example, MSTest, NUnit, or xUnit) and the dotnet test runner for the unit testing framework.</span></span> <span data-ttu-id="2de65-112">這些會封裝為 NuGet 套件，並還原為專案的一般相依性。</span><span class="sxs-lookup"><span data-stu-id="2de65-112">These are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="2de65-113">測試專案也必須指定測試執行器。</span><span class="sxs-lookup"><span data-stu-id="2de65-113">Test projects also must specify the test runner.</span></span> <span data-ttu-id="2de65-114">這是使用一般 `<PackageReference>` 元素所指定，如下列範例專案檔中所示：</span><span class="sxs-lookup"><span data-stu-id="2de65-114">This is specified using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

<span data-ttu-id="2de65-115">[!code-xml[XUnit 基本範本](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]</span><span class="sxs-lookup"><span data-stu-id="2de65-115">[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]</span></span>

## <a name="arguments"></a><span data-ttu-id="2de65-116">引數</span><span class="sxs-lookup"><span data-stu-id="2de65-116">Arguments</span></span>

`PROJECT`

<span data-ttu-id="2de65-117">指定測試專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="2de65-117">Specifies a path to the test project.</span></span> <span data-ttu-id="2de65-118">如果省略，則會預設為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="2de65-118">If omitted, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="2de65-119">選項</span><span class="sxs-lookup"><span data-stu-id="2de65-119">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="2de65-120">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="2de65-120">.NET Core 2.x</span></span>](#tab/netcore2x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="2de65-121">在測試執行中，從指定的路徑使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="2de65-121">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="2de65-122">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="2de65-122">Defines the build configuration.</span></span> <span data-ttu-id="2de65-123">預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。</span><span class="sxs-lookup"><span data-stu-id="2de65-123">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="2de65-124">測試回合啟用資料收集器。</span><span class="sxs-lookup"><span data-stu-id="2de65-124">Enables data collector for the test run.</span></span> <span data-ttu-id="2de65-125">如需詳細資訊，請參閱[監視及分析測試回合](https://aka.ms/vstest-collect)。</span><span class="sxs-lookup"><span data-stu-id="2de65-125">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="2de65-126">針對測試平台啟用診斷模式，並將診斷訊息寫入至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="2de65-126">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="2de65-127">尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。</span><span class="sxs-lookup"><span data-stu-id="2de65-127">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="2de65-128">使用指定的運算式篩選出目前專案中的測試。</span><span class="sxs-lookup"><span data-stu-id="2de65-128">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="2de65-129">如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。</span><span class="sxs-lookup"><span data-stu-id="2de65-129">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="2de65-130">如需如何使用選擇性單元測試篩選的其他資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="2de65-130">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="2de65-131">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="2de65-131">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="2de65-132">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="2de65-132">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="2de65-133">請不要在執行之前建置測試專案。</span><span class="sxs-lookup"><span data-stu-id="2de65-133">Does not build the test project prior to running it.</span></span>

`--no-restore`

<span data-ttu-id="2de65-134">執行命令時，不執行隱含的還原。</span><span class="sxs-lookup"><span data-stu-id="2de65-134">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="2de65-135">在其中尋找要執行的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="2de65-135">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="2de65-136">要放置測試結果的目錄。</span><span class="sxs-lookup"><span data-stu-id="2de65-136">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="2de65-137">指定的目錄如不存在即建立。</span><span class="sxs-lookup"><span data-stu-id="2de65-137">The specified directory will be created if it doesn't exist.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="2de65-138">執行測試時要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="2de65-138">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="2de65-139">列出在目前專案中探索到的所有測試。</span><span class="sxs-lookup"><span data-stu-id="2de65-139">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="2de65-140">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="2de65-140">Sets the verbosity level of the command.</span></span> <span data-ttu-id="2de65-141">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="2de65-141">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="2de65-142">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="2de65-142">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="2de65-143">在測試執行中，從指定的路徑使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="2de65-143">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="2de65-144">定義組建組態。</span><span class="sxs-lookup"><span data-stu-id="2de65-144">Defines the build configuration.</span></span> <span data-ttu-id="2de65-145">預設值是 `Debug`，但您的專案組態無法覆寫這個預設的 SDK 設定。</span><span class="sxs-lookup"><span data-stu-id="2de65-145">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="2de65-146">針對測試平台啟用診斷模式，並將診斷訊息寫入至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="2de65-146">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="2de65-147">尋找特定[架構](../../standard/frameworks.md)的測試二進位檔。</span><span class="sxs-lookup"><span data-stu-id="2de65-147">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="2de65-148">使用指定的運算式篩選出目前專案中的測試。</span><span class="sxs-lookup"><span data-stu-id="2de65-148">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="2de65-149">如需詳細資訊，請參閱[篩選選項詳細資料](#filter-option-details)一節。</span><span class="sxs-lookup"><span data-stu-id="2de65-149">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="2de65-150">如需如何使用選擇性單元測試篩選的其他資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="2de65-150">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="2de65-151">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="2de65-151">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="2de65-152">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="2de65-152">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="2de65-153">請不要在執行之前建置測試專案。</span><span class="sxs-lookup"><span data-stu-id="2de65-153">Does not build the test project prior to running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="2de65-154">在其中尋找要執行的二進位檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="2de65-154">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="2de65-155">執行測試時要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="2de65-155">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="2de65-156">列出在目前專案中探索到的所有測試。</span><span class="sxs-lookup"><span data-stu-id="2de65-156">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="2de65-157">設定命令的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="2de65-157">Sets the verbosity level of the command.</span></span> <span data-ttu-id="2de65-158">允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="2de65-158">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="2de65-159">範例</span><span class="sxs-lookup"><span data-stu-id="2de65-159">Examples</span></span>

<span data-ttu-id="2de65-160">執行目前目錄之專案中的測試：</span><span class="sxs-lookup"><span data-stu-id="2de65-160">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="2de65-161">執行 `test1` 專案中的測試︰</span><span class="sxs-lookup"><span data-stu-id="2de65-161">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

## <a name="filter-option-details"></a><span data-ttu-id="2de65-162">篩選選項詳細資料</span><span class="sxs-lookup"><span data-stu-id="2de65-162">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="2de65-163">`<Expression>` 的格式為 `<property><operator><value>[|&<Expression>]`。</span><span class="sxs-lookup"><span data-stu-id="2de65-163">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="2de65-164">`<property>` 為 `Test Case` 的屬性。</span><span class="sxs-lookup"><span data-stu-id="2de65-164">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="2de65-165">以下為熱門單元測試架構所支援的屬性：</span><span class="sxs-lookup"><span data-stu-id="2de65-165">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="2de65-166">測試架構</span><span class="sxs-lookup"><span data-stu-id="2de65-166">Test Framework</span></span> | <span data-ttu-id="2de65-167">支援的屬性</span><span class="sxs-lookup"><span data-stu-id="2de65-167">Supported properties</span></span>                                                                                      |
| :------------: | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="2de65-168">MSTest</span><span class="sxs-lookup"><span data-stu-id="2de65-168">MSTest</span></span>         | <ul><li><span data-ttu-id="2de65-169">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="2de65-169">FullyQualifiedName</span></span></li><li><span data-ttu-id="2de65-170">名稱</span><span class="sxs-lookup"><span data-stu-id="2de65-170">Name</span></span></li><li><span data-ttu-id="2de65-171">ClassName</span><span class="sxs-lookup"><span data-stu-id="2de65-171">ClassName</span></span></li><li><span data-ttu-id="2de65-172">優先權</span><span class="sxs-lookup"><span data-stu-id="2de65-172">Priority</span></span></li><li><span data-ttu-id="2de65-173">TestCategory</span><span class="sxs-lookup"><span data-stu-id="2de65-173">TestCategory</span></span></li></ul> |
| <span data-ttu-id="2de65-174">xUnit</span><span class="sxs-lookup"><span data-stu-id="2de65-174">Xunit</span></span>          | <ul><li><span data-ttu-id="2de65-175">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="2de65-175">FullyQualifiedName</span></span></li><li><span data-ttu-id="2de65-176">DisplayName</span><span class="sxs-lookup"><span data-stu-id="2de65-176">DisplayName</span></span></li><li><span data-ttu-id="2de65-177">特性</span><span class="sxs-lookup"><span data-stu-id="2de65-177">Traits</span></span></li></ul>                                   |

<span data-ttu-id="2de65-178">`<operator>` 描述屬性和值之間的關聯性：</span><span class="sxs-lookup"><span data-stu-id="2de65-178">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="2de65-179">運算子</span><span class="sxs-lookup"><span data-stu-id="2de65-179">Operator</span></span> | <span data-ttu-id="2de65-180">函式</span><span class="sxs-lookup"><span data-stu-id="2de65-180">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="2de65-181">完全相符</span><span class="sxs-lookup"><span data-stu-id="2de65-181">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="2de65-182">不完全相符</span><span class="sxs-lookup"><span data-stu-id="2de65-182">Not exact match</span></span> |
| `~`      | <span data-ttu-id="2de65-183">包含</span><span class="sxs-lookup"><span data-stu-id="2de65-183">Contains</span></span>        |

<span data-ttu-id="2de65-184">`<value>` 為字串。</span><span class="sxs-lookup"><span data-stu-id="2de65-184">`<value>` is a string.</span></span> <span data-ttu-id="2de65-185">所有的查閱皆不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="2de65-185">All the lookups are case insensitive.</span></span>

<span data-ttu-id="2de65-186">沒有 `<operator>` 的運算式會自動被視為 `FullyQualifiedName` 屬性上的 `contains` (例如，`dotnet test --filter xyz` 等同於 `dotnet test --filter FullyQualifiedName~xyz`)。</span><span class="sxs-lookup"><span data-stu-id="2de65-186">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="2de65-187">運算式可以使用條件運算子聯結：</span><span class="sxs-lookup"><span data-stu-id="2de65-187">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="2de65-188">運算子</span><span class="sxs-lookup"><span data-stu-id="2de65-188">Operator</span></span> | <span data-ttu-id="2de65-189">函式</span><span class="sxs-lookup"><span data-stu-id="2de65-189">Function</span></span> |
| :------: | :------: |
| <code>&#124;</code>      | <span data-ttu-id="2de65-190">或</span><span class="sxs-lookup"><span data-stu-id="2de65-190">OR</span></span>       |
| `&`      | <span data-ttu-id="2de65-191">AND</span><span class="sxs-lookup"><span data-stu-id="2de65-191">AND</span></span>      |

<span data-ttu-id="2de65-192">使用條件運算子時，您可以用括弧括住運算式 (例如，`(Name~TestMethod1) | (Name~TestMethod2)`)。</span><span class="sxs-lookup"><span data-stu-id="2de65-192">You can enclose expressions in paranthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="2de65-193">如需如何使用選擇性單元測試篩選的其他資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="2de65-193">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2de65-194">請參閱</span><span class="sxs-lookup"><span data-stu-id="2de65-194">See also</span></span>

 <span data-ttu-id="2de65-195">[架構與目標](../../standard/frameworks.md) </span><span class="sxs-lookup"><span data-stu-id="2de65-195">[Frameworks and Targets](../../standard/frameworks.md) </span></span>  
 [<span data-ttu-id="2de65-196">.NET Core 執行階段識別項 (RID) 目錄</span><span class="sxs-lookup"><span data-stu-id="2de65-196">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)

