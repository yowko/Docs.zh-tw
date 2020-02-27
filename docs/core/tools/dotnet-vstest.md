---
title: dotnet vstest 命令
description: dotnet vstest 命令會建置專案和其所有相依性。
ms.date: 05/30/2018
ms.openlocfilehash: fc0aa4f9abf069f78e27692ee84aea2559109c98
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626017"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="0eb9a-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="0eb9a-103">dotnet vstest</span></span>

<span data-ttu-id="0eb9a-104">**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="0eb9a-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="0eb9a-105">名稱</span><span class="sxs-lookup"><span data-stu-id="0eb9a-105">Name</span></span>

<span data-ttu-id="0eb9a-106">`dotnet-vstest` - 從指定的檔案執行測試。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-106">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0eb9a-107">概要</span><span class="sxs-lookup"><span data-stu-id="0eb9a-107">Synopsis</span></span>

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings] [--Tests]
    [--TestAdapterPath] [--Platform] [--Framework] [--Parallel]
    [--TestCaseFilter] [--logger] [-lt|--ListTests]
    [--ParentProcessId] [--Port] [--Diag] [--Blame]
    [--InIsolation] [[--] <args>...]] [-?|--Help]
```

## <a name="description"></a><span data-ttu-id="0eb9a-108">描述</span><span class="sxs-lookup"><span data-stu-id="0eb9a-108">Description</span></span>

<span data-ttu-id="0eb9a-109">`dotnet-vstest` 命令會執行 `VSTest.Console` 命令列應用程式，以執行自動化的單元測試。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-109">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="0eb9a-110">引數</span><span class="sxs-lookup"><span data-stu-id="0eb9a-110">Arguments</span></span>

- **`TEST_FILE_NAMES`**

  <span data-ttu-id="0eb9a-111">從指定的組件執行測試。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-111">Run tests from the specified assemblies.</span></span> <span data-ttu-id="0eb9a-112">以空格分隔多個測試組件名稱。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-112">Separate multiple test assembly names with spaces.</span></span> <span data-ttu-id="0eb9a-113">支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-113">Wildcards are supported.</span></span>

## <a name="options"></a><span data-ttu-id="0eb9a-114">選項。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-114">Options</span></span>

- **`--Settings <Settings File>`**

  <span data-ttu-id="0eb9a-115">執行測試時要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-115">Settings to use when running tests.</span></span>

- **`--Tests <Test Names>`**

  <span data-ttu-id="0eb9a-116">執行測試，其名稱符合所提供的值。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-116">Run tests with names that match the provided values.</span></span> <span data-ttu-id="0eb9a-117">以逗號分隔多個值。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-117">Separate multiple values with commas.</span></span>

- **`--TestAdapterPath`**

  <span data-ttu-id="0eb9a-118">在測試回合中，從指定的路徑 (如果有的話) 使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-118">Use custom test adapters from a given path (if any) in the test run.</span></span>

- **`--Platform <Platform type>`**

  <span data-ttu-id="0eb9a-119">用於測試執行的目標平台架構。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-119">Target platform architecture used for test execution.</span></span> <span data-ttu-id="0eb9a-120">有效值是 `x86`、`x64` 和 `ARM`。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-120">Valid values are `x86`, `x64`, and `ARM`.</span></span>

- **`--Framework <Framework Version>`**

  <span data-ttu-id="0eb9a-121">用於測試執行的目標 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-121">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="0eb9a-122">有效值的範例包括 `.NETFramework,Version=v4.6` 或 `.NETCoreApp,Version=v1.0`。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-122">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="0eb9a-123">其他支援的值為 `Framework40`、`Framework45`、`FrameworkCore10` 和 `FrameworkUap10`。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-123">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

- **`--Parallel`**

  <span data-ttu-id="0eb9a-124">以平行方式執行測試。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-124">Run tests in parallel.</span></span> <span data-ttu-id="0eb9a-125">根據預設，電腦上所有的可用核心都可供使用。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-125">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="0eb9a-126">在 *.runsettings*檔案中的 [`RunConfiguration`] 節點底下設定 [`MaxCpuCount`] 屬性，以指定明確的核心數目。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-126">Specify an explicit number of cores by setting the `MaxCpuCount` property under the `RunConfiguration` node in the *runsettings* file.</span></span>

- **`--TestCaseFilter <Expression>`**

  <span data-ttu-id="0eb9a-127">執行符合指定之運算式的測試。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-127">Run tests that match the given expression.</span></span> <span data-ttu-id="0eb9a-128">`<Expression>` 的格式為 `<property>Operator<value>[|&<Expression>]`，其中 Operator (運算子) 為 `=`、`!=` 或 `~` 其中之一。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-128">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="0eb9a-129">運算子 `~` 具有「包含」語意，且適用於像是 `DisplayName` 的字串屬性。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-129">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="0eb9a-130">括弧 `()` 用來將子運算式分組。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-130">Parenthesis `()` are used to group subexpressions.</span></span>

- **`-?|--Help`**

  <span data-ttu-id="0eb9a-131">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-131">Prints out a short help for the command.</span></span>

- **`--logger <Logger Uri/FriendlyName>`**

  <span data-ttu-id="0eb9a-132">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-132">Specify a logger for test results.</span></span>

  - <span data-ttu-id="0eb9a-133">若要將測試結果發行至 Team Foundation Server 中，使用 `TfsPublisher` 記錄器提供者：</span><span class="sxs-lookup"><span data-stu-id="0eb9a-133">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - <span data-ttu-id="0eb9a-134">若要將結果記錄到 Visual Studio 測試結果檔案 (TRX)，使用 `trx` 記錄器提供者。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-134">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="0eb9a-135">這個參數會以指定的記錄檔名稱，在測試結果目錄中建立檔案。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-135">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="0eb9a-136">如果沒有提供 `LogFileName`，會建立唯一的檔案名稱以保留測試結果。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-136">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`-lt|--ListTests <File Name>`**

  <span data-ttu-id="0eb9a-137">列出所有從指定之測試容器探索到的測試。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-137">Lists all discovered tests from the given test container.</span></span>

- **`--ParentProcessId <ParentProcessId>`**

  <span data-ttu-id="0eb9a-138">負責啟動目前處理序之父處理序的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-138">Process ID of the parent process responsible for launching the current process.</span></span>

- **`--Port <Port>`**

  <span data-ttu-id="0eb9a-139">指定通訊端連線和接收事件訊息的連接埠。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-139">Specifies the port for the socket connection and receiving the event messages.</span></span>

- **`--Diag <Path to log file>`**

  <span data-ttu-id="0eb9a-140">啟用測試平台的詳細資訊記錄檔。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-140">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="0eb9a-141">記錄檔會寫入提供的檔案。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-141">Logs are written to the provided file.</span></span>

- **`--Blame`**

  <span data-ttu-id="0eb9a-142">在歸責模式下執行測試。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-142">Runs the tests in blame mode.</span></span> <span data-ttu-id="0eb9a-143">這個選項有助於隔離造成測試主機損毀的問題。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-143">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="0eb9a-144">它會以 *Sequence.xml* 的形式在目前目錄中建立一個輸出檔，用來擷取損毀前的測試執行順序。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-144">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`--InIsolation`**

  <span data-ttu-id="0eb9a-145">在獨立的處理序中執行測試。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-145">Runs the tests in an isolated process.</span></span> <span data-ttu-id="0eb9a-146">這樣會降低 *vstest.console.exe* 處理序在測試中錯誤處停止的可能性，但是測試的速度可能會比較慢。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-146">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

- **`@<file>`**

  <span data-ttu-id="0eb9a-147">請讀取回應檔以取得更多選項。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-147">Reads response file for more options.</span></span>

- **`args`**

  <span data-ttu-id="0eb9a-148">指定要傳遞至配接器的額外引數。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-148">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="0eb9a-149">引數指定為格式 `<n>=<v>` 的名稱/值組，其中 `<n>` 是引數名稱而 `<v>` 是引數值。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-149">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="0eb9a-150">使用空格來分隔多個引數。</span><span class="sxs-lookup"><span data-stu-id="0eb9a-150">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="0eb9a-151">範例</span><span class="sxs-lookup"><span data-stu-id="0eb9a-151">Examples</span></span>

<span data-ttu-id="0eb9a-152">在*mytestproject.dll*中執行測試：</span><span class="sxs-lookup"><span data-stu-id="0eb9a-152">Run tests in *mytestproject.dll*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll
```

<span data-ttu-id="0eb9a-153">在*mytestproject.dll*中執行測試，並使用自訂名稱匯出至自訂資料夾：</span><span class="sxs-lookup"><span data-stu-id="0eb9a-153">Run tests in *mytestproject.dll*, exporting to custom folder with custom name:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

<span data-ttu-id="0eb9a-154">在*mytestproject.dll*和*myothertestproject.exe*中執行測試：</span><span class="sxs-lookup"><span data-stu-id="0eb9a-154">Run tests in *mytestproject.dll* and *myothertestproject.exe*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

<span data-ttu-id="0eb9a-155">執行 `TestMethod1` 測試：</span><span class="sxs-lookup"><span data-stu-id="0eb9a-155">Run `TestMethod1` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

<span data-ttu-id="0eb9a-156">執行 `TestMethod1` 和 `TestMethod2` 測試：</span><span class="sxs-lookup"><span data-stu-id="0eb9a-156">Run `TestMethod1` and `TestMethod2` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```
