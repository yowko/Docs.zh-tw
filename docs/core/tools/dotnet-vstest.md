---
title: dotnet vstest 命令
description: dotnet vstest 命令會建置專案和其所有相依性。
ms.date: 02/27/2020
ms.openlocfilehash: f7db58f4aab59354b8c69ce0371324c23482dafe
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975390"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="1bd08-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="1bd08-103">dotnet vstest</span></span>

<span data-ttu-id="1bd08-104">**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="1bd08-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1bd08-105">`dotnet vstest`命令已由`dotnet test`取代，現在可用來執行元件。</span><span class="sxs-lookup"><span data-stu-id="1bd08-105">The `dotnet vstest` command is superseded by `dotnet test`, which can now be used to run assemblies.</span></span> <span data-ttu-id="1bd08-106">請參閱 [`dotnet test`](dotnet-test.md)。</span><span class="sxs-lookup"><span data-stu-id="1bd08-106">See [`dotnet test`](dotnet-test.md).</span></span>

## <a name="name"></a><span data-ttu-id="1bd08-107">名稱</span><span class="sxs-lookup"><span data-stu-id="1bd08-107">Name</span></span>

<span data-ttu-id="1bd08-108">`dotnet-vstest`-從指定的元件執行測試。</span><span class="sxs-lookup"><span data-stu-id="1bd08-108">`dotnet-vstest` - Runs tests from the specified assemblies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1bd08-109">概要</span><span class="sxs-lookup"><span data-stu-id="1bd08-109">Synopsis</span></span>

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Blame] [--Diag <PATH_TO_LOG_FILE>]
    [--Framework <FRAMEWORK>] [--InIsolation] [-lt|--ListTests <FILE_NAME>]
    [--logger <LOGGER_URI/FRIENDLY_NAME>] [--Parallel]
    [--ParentProcessId <PROCESS_ID>] [--Platform] <PLATFORM_TYPE>
    [--Port <PORT>] [--ResultsDirectory<PATH>] [--Settings <SETTINGS_FILE>]
    [--TestAdapterPath <PATH>] [--TestCaseFilter <EXPRESSION>]
    [--Tests <TEST_NAMES>] [[--] <args>...]]

dotnet vstest -?|--Help
```

## <a name="description"></a><span data-ttu-id="1bd08-110">描述</span><span class="sxs-lookup"><span data-stu-id="1bd08-110">Description</span></span>

<span data-ttu-id="1bd08-111">`dotnet-vstest` 命令會執行 `VSTest.Console` 命令列應用程式，以執行自動化的單元測試。</span><span class="sxs-lookup"><span data-stu-id="1bd08-111">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="1bd08-112">引數</span><span class="sxs-lookup"><span data-stu-id="1bd08-112">Arguments</span></span>

- **`TEST_FILE_NAMES`**

  <span data-ttu-id="1bd08-113">從指定的組件執行測試。</span><span class="sxs-lookup"><span data-stu-id="1bd08-113">Run tests from the specified assemblies.</span></span> <span data-ttu-id="1bd08-114">以空格分隔多個測試組件名稱。</span><span class="sxs-lookup"><span data-stu-id="1bd08-114">Separate multiple test assembly names with spaces.</span></span> <span data-ttu-id="1bd08-115">支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="1bd08-115">Wildcards are supported.</span></span>

## <a name="options"></a><span data-ttu-id="1bd08-116">選項</span><span class="sxs-lookup"><span data-stu-id="1bd08-116">Options</span></span>

- **`--Blame`**

  <span data-ttu-id="1bd08-117">在歸責模式下執行測試。</span><span class="sxs-lookup"><span data-stu-id="1bd08-117">Runs the tests in blame mode.</span></span> <span data-ttu-id="1bd08-118">這個選項有助於隔離造成測試主機損毀的問題。</span><span class="sxs-lookup"><span data-stu-id="1bd08-118">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="1bd08-119">它會以 *Sequence.xml* 的形式在目前目錄中建立一個輸出檔，用來擷取損毀前的測試執行順序。</span><span class="sxs-lookup"><span data-stu-id="1bd08-119">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`--Diag <PATH_TO_LOG_FILE>`**

  <span data-ttu-id="1bd08-120">啟用測試平台的詳細資訊記錄檔。</span><span class="sxs-lookup"><span data-stu-id="1bd08-120">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="1bd08-121">記錄檔會寫入提供的檔案。</span><span class="sxs-lookup"><span data-stu-id="1bd08-121">Logs are written to the provided file.</span></span>

- **`--Framework <FRAMEWORK>`**

  <span data-ttu-id="1bd08-122">用於測試執行的目標 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="1bd08-122">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="1bd08-123">有效值的範例包括 `.NETFramework,Version=v4.6` 或 `.NETCoreApp,Version=v1.0`。</span><span class="sxs-lookup"><span data-stu-id="1bd08-123">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="1bd08-124">其他支援的值為 `Framework40`、`Framework45`、`FrameworkCore10` 和 `FrameworkUap10`。</span><span class="sxs-lookup"><span data-stu-id="1bd08-124">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

- **`--InIsolation`**

  <span data-ttu-id="1bd08-125">在獨立的處理序中執行測試。</span><span class="sxs-lookup"><span data-stu-id="1bd08-125">Runs the tests in an isolated process.</span></span> <span data-ttu-id="1bd08-126">這樣會降低 *vstest.console.exe* 處理序在測試中錯誤處停止的可能性，但是測試的速度可能會比較慢。</span><span class="sxs-lookup"><span data-stu-id="1bd08-126">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

- **`-lt|--ListTests <FILE_NAME>`**

  <span data-ttu-id="1bd08-127">列出所有從指定之測試容器探索到的測試。</span><span class="sxs-lookup"><span data-stu-id="1bd08-127">Lists all discovered tests from the given test container.</span></span>

- **`--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="1bd08-128">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="1bd08-128">Specify a logger for test results.</span></span>

  - <span data-ttu-id="1bd08-129">若要將測試結果發行至 Team Foundation Server 中，使用 `TfsPublisher` 記錄器提供者：</span><span class="sxs-lookup"><span data-stu-id="1bd08-129">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - <span data-ttu-id="1bd08-130">若要將結果記錄到 Visual Studio 測試結果檔案 (TRX)，使用 `trx` 記錄器提供者。</span><span class="sxs-lookup"><span data-stu-id="1bd08-130">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="1bd08-131">這個參數會以指定的記錄檔名稱，在測試結果目錄中建立檔案。</span><span class="sxs-lookup"><span data-stu-id="1bd08-131">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="1bd08-132">如果沒有提供 `LogFileName`，會建立唯一的檔案名稱以保留測試結果。</span><span class="sxs-lookup"><span data-stu-id="1bd08-132">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`--Parallel`**

  <span data-ttu-id="1bd08-133">以平行方式執行測試。</span><span class="sxs-lookup"><span data-stu-id="1bd08-133">Run tests in parallel.</span></span> <span data-ttu-id="1bd08-134">根據預設，電腦上所有的可用核心都可供使用。</span><span class="sxs-lookup"><span data-stu-id="1bd08-134">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="1bd08-135">在 *.runsettings*檔案中的`RunConfiguration`節點下設定屬性`MaxCpuCount` ，以指定明確的核心數目。</span><span class="sxs-lookup"><span data-stu-id="1bd08-135">Specify an explicit number of cores by setting the `MaxCpuCount` property under the `RunConfiguration` node in the *runsettings* file.</span></span>

- **`--ParentProcessId <PROCESS_ID>`**

  <span data-ttu-id="1bd08-136">負責啟動目前處理序之父處理序的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="1bd08-136">Process ID of the parent process responsible for launching the current process.</span></span>

- **`--Platform <PLATFORM_TYPE>`**

  <span data-ttu-id="1bd08-137">用於測試執行的目標平台架構。</span><span class="sxs-lookup"><span data-stu-id="1bd08-137">Target platform architecture used for test execution.</span></span> <span data-ttu-id="1bd08-138">有效值是 `x86`、`x64` 和 `ARM`。</span><span class="sxs-lookup"><span data-stu-id="1bd08-138">Valid values are `x86`, `x64`, and `ARM`.</span></span>

- **`--Port <PORT>`**

  <span data-ttu-id="1bd08-139">指定通訊端連線和接收事件訊息的連接埠。</span><span class="sxs-lookup"><span data-stu-id="1bd08-139">Specifies the port for the socket connection and receiving the event messages.</span></span>

- **`--ResultsDirectory:<PATH>`**

  <span data-ttu-id="1bd08-140">如果測試結果目錄不存在，則會在指定的路徑中建立該目錄。</span><span class="sxs-lookup"><span data-stu-id="1bd08-140">Test results directory will be created in specified path if not exists.</span></span>

- **`--Settings <SETTINGS_FILE>`**

  <span data-ttu-id="1bd08-141">執行測試時要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="1bd08-141">Settings to use when running tests.</span></span>

- **`--TestAdapterPath <PATH>`**

  <span data-ttu-id="1bd08-142">在測試回合中，從指定的路徑 (如果有的話) 使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="1bd08-142">Use custom test adapters from a given path (if any) in the test run.</span></span>

- **`--TestCaseFilter <EXPRESSION>`**

  <span data-ttu-id="1bd08-143">執行符合指定之運算式的測試。</span><span class="sxs-lookup"><span data-stu-id="1bd08-143">Run tests that match the given expression.</span></span> <span data-ttu-id="1bd08-144">`<EXPRESSION>` 的格式為 `<property>Operator<value>[|&<EXPRESSION>]`，其中 Operator (運算子) 為 `=`、`!=` 或 `~` 其中之一。</span><span class="sxs-lookup"><span data-stu-id="1bd08-144">`<EXPRESSION>` is of the format `<property>Operator<value>[|&<EXPRESSION>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="1bd08-145">運算子 `~` 具有「包含」語意，且適用於像是 `DisplayName` 的字串屬性。</span><span class="sxs-lookup"><span data-stu-id="1bd08-145">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="1bd08-146">括弧`()`是用來將子運算式分組。</span><span class="sxs-lookup"><span data-stu-id="1bd08-146">Parentheses `()` are used to group subexpressions.</span></span> <span data-ttu-id="1bd08-147">如需詳細資訊，請參閱[TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md)。</span><span class="sxs-lookup"><span data-stu-id="1bd08-147">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>

- **`--Tests <TEST_NAMES>`**

  <span data-ttu-id="1bd08-148">執行測試，其名稱符合所提供的值。</span><span class="sxs-lookup"><span data-stu-id="1bd08-148">Run tests with names that match the provided values.</span></span> <span data-ttu-id="1bd08-149">請使用逗號分隔多個值。</span><span class="sxs-lookup"><span data-stu-id="1bd08-149">Separate multiple values with commas.</span></span>

- **`-?|--Help`**

  <span data-ttu-id="1bd08-150">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="1bd08-150">Prints out a short help for the command.</span></span>

- **`@<file>`**

  <span data-ttu-id="1bd08-151">請讀取回應檔以取得更多選項。</span><span class="sxs-lookup"><span data-stu-id="1bd08-151">Reads response file for more options.</span></span>

- **`args`**

  <span data-ttu-id="1bd08-152">指定要傳遞至配接器的額外引數。</span><span class="sxs-lookup"><span data-stu-id="1bd08-152">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="1bd08-153">引數指定為格式 `<n>=<v>` 的名稱/值組，其中 `<n>` 是引數名稱而 `<v>` 是引數值。</span><span class="sxs-lookup"><span data-stu-id="1bd08-153">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="1bd08-154">使用空格來分隔多個引數。</span><span class="sxs-lookup"><span data-stu-id="1bd08-154">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="1bd08-155">範例</span><span class="sxs-lookup"><span data-stu-id="1bd08-155">Examples</span></span>

<span data-ttu-id="1bd08-156">在*mytestproject.dll*中執行測試：</span><span class="sxs-lookup"><span data-stu-id="1bd08-156">Run tests in *mytestproject.dll*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll
```

<span data-ttu-id="1bd08-157">在*mytestproject.dll*中執行測試，並使用自訂名稱匯出至自訂資料夾：</span><span class="sxs-lookup"><span data-stu-id="1bd08-157">Run tests in *mytestproject.dll*, exporting to custom folder with custom name:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

<span data-ttu-id="1bd08-158">在*mytestproject.dll*和*myothertestproject.exe*中執行測試：</span><span class="sxs-lookup"><span data-stu-id="1bd08-158">Run tests in *mytestproject.dll* and *myothertestproject.exe*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

<span data-ttu-id="1bd08-159">執行 `TestMethod1` 測試：</span><span class="sxs-lookup"><span data-stu-id="1bd08-159">Run `TestMethod1` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

<span data-ttu-id="1bd08-160">執行 `TestMethod1` 和 `TestMethod2` 測試：</span><span class="sxs-lookup"><span data-stu-id="1bd08-160">Run `TestMethod1` and `TestMethod2` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```

## <a name="see-also"></a><span data-ttu-id="1bd08-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bd08-161">See also</span></span>

- [<span data-ttu-id="1bd08-162">VSTest.Console.exe 命令列選項</span><span class="sxs-lookup"><span data-stu-id="1bd08-162">VSTest.Console.exe command-line options</span></span>](/visualstudio/test/vstest-console-options)
