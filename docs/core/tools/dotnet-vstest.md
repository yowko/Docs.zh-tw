---
title: dotnet vstest 命令
description: dotnet vstest 命令會建置專案和其所有相依性。
ms.date: 05/30/2018
ms.openlocfilehash: c3838617ed539cf56f2840b826e9de58833820fd
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215304"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="3b7ad-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="3b7ad-103">dotnet vstest</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="3b7ad-104">名稱</span><span class="sxs-lookup"><span data-stu-id="3b7ad-104">Name</span></span>

<span data-ttu-id="3b7ad-105">`dotnet-vstest` - 從指定的檔案執行測試。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-105">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3b7ad-106">概要</span><span class="sxs-lookup"><span data-stu-id="3b7ad-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="3b7ad-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3b7ad-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="3b7ad-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="3b7ad-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3b7ad-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="3b7ad-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

---

## <a name="description"></a><span data-ttu-id="3b7ad-110">描述</span><span class="sxs-lookup"><span data-stu-id="3b7ad-110">Description</span></span>

<span data-ttu-id="3b7ad-111">`dotnet-vstest` 命令會執行 `VSTest.Console` 命令列應用程式，以執行自動化的單元測試。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-111">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="3b7ad-112">引數</span><span class="sxs-lookup"><span data-stu-id="3b7ad-112">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="3b7ad-113">從指定的組件執行測試。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-113">Run tests from the specified assemblies.</span></span> <span data-ttu-id="3b7ad-114">以空格分隔多個測試組件名稱。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-114">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="3b7ad-115">選項。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-115">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="3b7ad-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3b7ad-116">.NET Core 2.1</span></span>](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="3b7ad-117">執行測試時要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-117">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="3b7ad-118">執行測試，其名稱符合所提供的值。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-118">Run tests with names that match the provided values.</span></span> <span data-ttu-id="3b7ad-119">以逗號分隔多個值。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-119">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="3b7ad-120">在測試回合中，從指定的路徑 (如果有的話) 使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-120">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="3b7ad-121">用於測試執行的目標平台架構。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-121">Target platform architecture used for test execution.</span></span> <span data-ttu-id="3b7ad-122">有效值是 `x86`、`x64` 和 `ARM`。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-122">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="3b7ad-123">用於測試執行的目標 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-123">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="3b7ad-124">有效值的範例包括 `.NETFramework,Version=v4.6` 或 `.NETCoreApp,Version=v1.0`。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-124">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="3b7ad-125">其他支援的值為 `Framework40`、`Framework45`、`FrameworkCore10` 和 `FrameworkUap10`。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-125">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="3b7ad-126">以平行方式執行測試。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-126">Execute tests in parallel.</span></span> <span data-ttu-id="3b7ad-127">根據預設，電腦上所有的可用核心都可供使用。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-127">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="3b7ad-128">在 runsettings 檔案中的 RunConfiguration 節點下設定 MaxCpuCount 屬性，以指定明確的核心數目。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-128">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="3b7ad-129">執行符合指定之運算式的測試。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-129">Run tests that match the given expression.</span></span> <span data-ttu-id="3b7ad-130">`<Expression>` 的格式為 `<property>Operator<value>[|&<Expression>]`，其中 Operator (運算子) 為 `=`、`!=` 或 `~` 其中之一。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-130">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="3b7ad-131">運算子 `~` 具有「包含」語意，且適用於像是 `DisplayName` 的字串屬性。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-131">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="3b7ad-132">括號 `()` 是用來分組子運算式。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-132">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="3b7ad-133">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-133">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="3b7ad-134">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-134">Specify a logger for test results.</span></span>

* <span data-ttu-id="3b7ad-135">若要將測試結果發行至 Team Foundation Server 中，使用 `TfsPublisher` 記錄器提供者：</span><span class="sxs-lookup"><span data-stu-id="3b7ad-135">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="3b7ad-136">若要將結果記錄到 Visual Studio 測試結果檔案 (TRX)，使用 `trx` 記錄器提供者。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-136">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="3b7ad-137">這個參數會以指定的記錄檔名稱，在測試結果目錄中建立檔案。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-137">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="3b7ad-138">如果沒有提供 `LogFileName`，會建立唯一的檔案名稱以保留測試結果。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-138">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="3b7ad-139">列出所有從指定之測試容器探索到的測試。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-139">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="3b7ad-140">負責啟動目前處理序之父處理序的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-140">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="3b7ad-141">指定通訊端連線和接收事件訊息的連接埠。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-141">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="3b7ad-142">啟用測試平台的詳細資訊記錄檔。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-142">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="3b7ad-143">記錄檔會寫入提供的檔案。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-143">Logs are written to the provided file.</span></span>

`--Blame|/Blame`

<span data-ttu-id="3b7ad-144">在歸責模式下執行測試。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-144">Runs the tests in blame mode.</span></span> <span data-ttu-id="3b7ad-145">這個選項有助於隔離造成測試主機損毀的問題。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-145">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="3b7ad-146">它會以 *Sequence.xml* 的形式在目前目錄中建立一個輸出檔，用來擷取損毀前的測試執行順序。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-146">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`--InIsolation|/InIsolation`

<span data-ttu-id="3b7ad-147">在獨立的處理序中執行測試。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-147">Runs the tests in an isolated process.</span></span> <span data-ttu-id="3b7ad-148">這樣會降低 *vstest.console.exe* 處理序在測試中錯誤處停止的可能性，但是測試的速度可能會比較慢。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-148">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

`@<file>`

<span data-ttu-id="3b7ad-149">請讀取回應檔以取得更多選項。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-149">Reads response file for more options.</span></span>

`args`

<span data-ttu-id="3b7ad-150">指定要傳遞至配接器的額外引數。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-150">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="3b7ad-151">引數指定為格式 `<n>=<v>` 的名稱/值組，其中 `<n>` 是引數名稱而 `<v>` 是引數值。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-151">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="3b7ad-152">使用空格來分隔多個引數。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-152">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="3b7ad-153">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="3b7ad-153">.NET Core 2.0</span></span>](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="3b7ad-154">執行測試時要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-154">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="3b7ad-155">執行測試，其名稱符合所提供的值。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-155">Run tests with names that match the provided values.</span></span> <span data-ttu-id="3b7ad-156">以逗號分隔多個值。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-156">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="3b7ad-157">在測試回合中，從指定的路徑 (如果有的話) 使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-157">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="3b7ad-158">用於測試執行的目標平台架構。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-158">Target platform architecture used for test execution.</span></span> <span data-ttu-id="3b7ad-159">有效值是 `x86`、`x64` 和 `ARM`。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-159">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="3b7ad-160">用於測試執行的目標 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-160">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="3b7ad-161">有效值的範例包括 `.NETFramework,Version=v4.6` 或 `.NETCoreApp,Version=v1.0`。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-161">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="3b7ad-162">其他支援的值為 `Framework40`、`Framework45` 和 `FrameworkCore10`。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-162">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="3b7ad-163">以平行方式執行測試。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-163">Execute tests in parallel.</span></span> <span data-ttu-id="3b7ad-164">根據預設，電腦上所有的可用核心都可供使用。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-164">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="3b7ad-165">在 runsettings 檔案中的 RunConfiguration 節點下設定 MaxCpuCount 屬性，以指定明確的核心數目。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-165">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="3b7ad-166">執行符合指定之運算式的測試。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-166">Run tests that match the given expression.</span></span> <span data-ttu-id="3b7ad-167">`<Expression>` 的格式為 `<property>Operator<value>[|&<Expression>]`，其中 Operator (運算子) 為 `=`、`!=` 或 `~` 其中之一。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-167">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="3b7ad-168">運算子 `~` 具有「包含」語意，且適用於像是 `DisplayName` 的字串屬性。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-168">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="3b7ad-169">括號 `()` 是用來分組子運算式。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-169">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="3b7ad-170">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-170">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="3b7ad-171">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-171">Specify a logger for test results.</span></span>

* <span data-ttu-id="3b7ad-172">若要將測試結果發行至 Team Foundation Server 中，使用 `TfsPublisher` 記錄器提供者：</span><span class="sxs-lookup"><span data-stu-id="3b7ad-172">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="3b7ad-173">若要將結果記錄到 Visual Studio 測試結果檔案 (TRX)，使用 `trx` 記錄器提供者。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-173">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="3b7ad-174">這個參數會以指定的記錄檔名稱，在測試結果目錄中建立檔案。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-174">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="3b7ad-175">如果沒有提供 `LogFileName`，會建立唯一的檔案名稱以保留測試結果。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-175">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="3b7ad-176">列出所有從指定之測試容器探索到的測試。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-176">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="3b7ad-177">負責啟動目前處理序之父處理序的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-177">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="3b7ad-178">指定通訊端連線和接收事件訊息的連接埠。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-178">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="3b7ad-179">啟用測試平台的詳細資訊記錄檔。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-179">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="3b7ad-180">記錄檔會寫入提供的檔案。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-180">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="3b7ad-181">指定要傳遞至配接器的額外引數。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-181">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="3b7ad-182">引數指定為格式 `<n>=<v>` 的名稱/值組，其中 `<n>` 是引數名稱而 `<v>` 是引數值。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-182">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="3b7ad-183">使用空格來分隔多個引數。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-183">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3b7ad-184">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="3b7ad-184">.NET Core 1.x</span></span>](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="3b7ad-185">執行測試時要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-185">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="3b7ad-186">執行測試，其名稱符合所提供的值。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-186">Run tests with names that match the provided values.</span></span> <span data-ttu-id="3b7ad-187">以逗號分隔多個值。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-187">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="3b7ad-188">在測試回合中，從指定的路徑 (如果有的話) 使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-188">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="3b7ad-189">用於測試執行的目標平台架構。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-189">Target platform architecture used for test execution.</span></span> <span data-ttu-id="3b7ad-190">有效值是 `x86`、`x64` 和 `ARM`。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-190">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="3b7ad-191">用於測試執行的目標 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-191">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="3b7ad-192">有效值的範例包括 `.NETFramework,Version=v4.6` 或 `.NETCoreApp,Version=v1.0`。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-192">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="3b7ad-193">其他支援的值為 `Framework40`、`Framework45` 和 `FrameworkCore10`。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-193">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="3b7ad-194">以平行方式執行測試。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-194">Execute tests in parallel.</span></span> <span data-ttu-id="3b7ad-195">根據預設，電腦上所有的可用核心都可供使用。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-195">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="3b7ad-196">在 runsettings 檔案中的 RunConfiguration 節點下設定 MaxCpuCount 屬性，以指定明確的核心數目。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-196">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="3b7ad-197">執行符合指定之運算式的測試。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-197">Run tests that match the given expression.</span></span> <span data-ttu-id="3b7ad-198">`<Expression>` 的格式為 `<property>Operator<value>[|&<Expression>]`，其中 Operator (運算子) 為 `=`、`!=` 或 `~` 其中之一。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-198">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="3b7ad-199">運算子 `~` 具有「包含」語意，且適用於像是 `DisplayName` 的字串屬性。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-199">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="3b7ad-200">括號 `()` 是用來分組子運算式。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-200">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="3b7ad-201">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-201">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="3b7ad-202">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-202">Specify a logger for test results.</span></span>

* <span data-ttu-id="3b7ad-203">若要將測試結果發行至 Team Foundation Server 中，使用 `TfsPublisher` 記錄器提供者：</span><span class="sxs-lookup"><span data-stu-id="3b7ad-203">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="3b7ad-204">若要將結果記錄到 Visual Studio 測試結果檔案 (TRX)，使用 `trx` 記錄器提供者。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-204">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="3b7ad-205">這個參數會以指定的記錄檔名稱，在測試結果目錄中建立檔案。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-205">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="3b7ad-206">如果沒有提供 `LogFileName`，會建立唯一的檔案名稱以保留測試結果。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-206">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="3b7ad-207">列出所有從指定之測試容器探索到的測試。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-207">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="3b7ad-208">負責啟動目前處理序之父處理序的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-208">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="3b7ad-209">指定通訊端連線和接收事件訊息的連接埠。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-209">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="3b7ad-210">啟用測試平台的詳細資訊記錄檔。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-210">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="3b7ad-211">記錄檔會寫入提供的檔案。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-211">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="3b7ad-212">指定要傳遞至配接器的額外引數。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-212">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="3b7ad-213">引數指定為格式 `<n>=<v>` 的名稱/值組，其中 `<n>` 是引數名稱而 `<v>` 是引數值。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-213">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="3b7ad-214">使用空格來分隔多個引數。</span><span class="sxs-lookup"><span data-stu-id="3b7ad-214">Use a space to separate multiple arguments.</span></span>

---

## <a name="examples"></a><span data-ttu-id="3b7ad-215">範例</span><span class="sxs-lookup"><span data-stu-id="3b7ad-215">Examples</span></span>

<span data-ttu-id="3b7ad-216">以 `mytestproject.dll` 執行測試：</span><span class="sxs-lookup"><span data-stu-id="3b7ad-216">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="3b7ad-217">在 `mytestproject.dll` 中執行測試，以自訂名稱匯出到自訂資料夾：</span><span class="sxs-lookup"><span data-stu-id="3b7ad-217">Run tests in `mytestproject.dll`, exporting to custom folder with custom name:</span></span>

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

<span data-ttu-id="3b7ad-218">以 `mytestproject.dll` 和 `myothertestproject.exe` 執行測試：</span><span class="sxs-lookup"><span data-stu-id="3b7ad-218">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="3b7ad-219">執行 `TestMethod1` 測試：</span><span class="sxs-lookup"><span data-stu-id="3b7ad-219">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="3b7ad-220">執行 `TestMethod1` 和 `TestMethod2` 測試：</span><span class="sxs-lookup"><span data-stu-id="3b7ad-220">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`
