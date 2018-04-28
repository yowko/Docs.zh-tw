---
title: dotnet vstest 命令 - .NET Core CLI
description: dotnet vstest 命令會建置專案和其所有相依性。
author: guardrex
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: e11b193ff7a8c639078c5cf279b7fbbeab553c92
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-vstest"></a><span data-ttu-id="a27dd-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="a27dd-103">dotnet vstest</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a27dd-104">名稱</span><span class="sxs-lookup"><span data-stu-id="a27dd-104">Name</span></span>

<span data-ttu-id="a27dd-105">`dotnet-vstest` - 從指定的檔案執行測試。</span><span class="sxs-lookup"><span data-stu-id="a27dd-105">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a27dd-106">概要</span><span class="sxs-lookup"><span data-stu-id="a27dd-106">Synopsis</span></span>

`dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]`

## <a name="description"></a><span data-ttu-id="a27dd-107">描述</span><span class="sxs-lookup"><span data-stu-id="a27dd-107">Description</span></span>

<span data-ttu-id="a27dd-108">`dotnet-vstest` 命令會執行 `VSTest.Console` 命令列應用程式，以執行自動化單元以及自動程式化 UI 應用程式測試。</span><span class="sxs-lookup"><span data-stu-id="a27dd-108">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit and coded UI application tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="a27dd-109">引數</span><span class="sxs-lookup"><span data-stu-id="a27dd-109">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="a27dd-110">從指定的組件執行測試。</span><span class="sxs-lookup"><span data-stu-id="a27dd-110">Run tests from the specified assemblies.</span></span> <span data-ttu-id="a27dd-111">以空格分隔多個測試組件名稱。</span><span class="sxs-lookup"><span data-stu-id="a27dd-111">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="a27dd-112">選項</span><span class="sxs-lookup"><span data-stu-id="a27dd-112">Options</span></span>

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="a27dd-113">執行測試時要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="a27dd-113">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="a27dd-114">執行測試，其名稱符合所提供的值。</span><span class="sxs-lookup"><span data-stu-id="a27dd-114">Run tests with names that match the provided values.</span></span> <span data-ttu-id="a27dd-115">以逗號分隔多個值。</span><span class="sxs-lookup"><span data-stu-id="a27dd-115">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="a27dd-116">在測試回合中，從指定的路徑 (如果有的話) 使用自訂測試配接器。</span><span class="sxs-lookup"><span data-stu-id="a27dd-116">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="a27dd-117">用於測試執行的目標平台架構。</span><span class="sxs-lookup"><span data-stu-id="a27dd-117">Target platform architecture used for test execution.</span></span> <span data-ttu-id="a27dd-118">有效值為 `x86`、`x64` 及 `ARM`。</span><span class="sxs-lookup"><span data-stu-id="a27dd-118">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="a27dd-119">用於測試執行的目標 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="a27dd-119">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="a27dd-120">有效值的範例包括 `.NETFramework,Version=v4.6`、`.NETCoreApp,Version=v1.0` 等等。其他支援的值為 `Framework35`、`Framework40`、`Framework45` 和 `FrameworkCore10`。</span><span class="sxs-lookup"><span data-stu-id="a27dd-120">Examples of valid values are `.NETFramework,Version=v4.6`, `.NETCoreApp,Version=v1.0`, etc. Other supported values are `Framework35`, `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="a27dd-121">以平行方式執行測試。</span><span class="sxs-lookup"><span data-stu-id="a27dd-121">Execute tests in parallel.</span></span> <span data-ttu-id="a27dd-122">根據預設，電腦上所有的可用核心都可供使用。</span><span class="sxs-lookup"><span data-stu-id="a27dd-122">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="a27dd-123">以設定檔設定明確的核心數目。</span><span class="sxs-lookup"><span data-stu-id="a27dd-123">Set an explicit number of cores with a settings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="a27dd-124">執行符合指定之運算式的測試。</span><span class="sxs-lookup"><span data-stu-id="a27dd-124">Run tests that match the given expression.</span></span> <span data-ttu-id="a27dd-125">`<Expression>` 的格式為 `<property>Operator<value>[|&<Expression>]`，其中 Operator (運算子) 為 `=`、`!=` 或 `~` 其中之一。</span><span class="sxs-lookup"><span data-stu-id="a27dd-125">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span>  <span data-ttu-id="a27dd-126">運算子 `~` 具有「包含」語意，且適用於像是 `DisplayName` 的字串屬性。</span><span class="sxs-lookup"><span data-stu-id="a27dd-126">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="a27dd-127">括號 `()` 是用來分組子運算式。</span><span class="sxs-lookup"><span data-stu-id="a27dd-127">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="a27dd-128">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="a27dd-128">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="a27dd-129">指定測試結果的記錄器。</span><span class="sxs-lookup"><span data-stu-id="a27dd-129">Specify a logger for test results.</span></span>  

* <span data-ttu-id="a27dd-130">若要將測試結果發行至 Team Foundation Server 中，使用 `TfsPublisher` 記錄器提供者：</span><span class="sxs-lookup"><span data-stu-id="a27dd-130">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="a27dd-131">若要將結果記錄到 Visual Studio 測試結果檔案 (TRX)，使用 `trx` 記錄器提供者。</span><span class="sxs-lookup"><span data-stu-id="a27dd-131">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="a27dd-132">這個參數會以指定的記錄檔名稱，在測試結果目錄中建立檔案。</span><span class="sxs-lookup"><span data-stu-id="a27dd-132">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="a27dd-133">如果沒有提供 `LogFileName`，會建立唯一的檔案名稱以保留測試結果。</span><span class="sxs-lookup"><span data-stu-id="a27dd-133">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="a27dd-134">列出從指定之測試容器探索到的測試。</span><span class="sxs-lookup"><span data-stu-id="a27dd-134">Lists discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="a27dd-135">負責啟動目前處理序之父處理序的處理序 ID。</span><span class="sxs-lookup"><span data-stu-id="a27dd-135">Process Id of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="a27dd-136">指定通訊端連線和接收事件訊息的連接埠。</span><span class="sxs-lookup"><span data-stu-id="a27dd-136">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="a27dd-137">啟用測試平台的詳細資訊記錄檔。</span><span class="sxs-lookup"><span data-stu-id="a27dd-137">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="a27dd-138">記錄檔會寫入提供的檔案。</span><span class="sxs-lookup"><span data-stu-id="a27dd-138">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="a27dd-139">指定要傳遞至配接器的額外引數。</span><span class="sxs-lookup"><span data-stu-id="a27dd-139">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="a27dd-140">引數指定為格式 `<n>=<v>` 的名稱/值組，其中 `<n>` 是引數名稱而 `<v>` 是引數值。</span><span class="sxs-lookup"><span data-stu-id="a27dd-140">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="a27dd-141">使用空格來分隔多個引數。</span><span class="sxs-lookup"><span data-stu-id="a27dd-141">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="a27dd-142">範例</span><span class="sxs-lookup"><span data-stu-id="a27dd-142">Examples</span></span>

<span data-ttu-id="a27dd-143">以 `mytestproject.dll` 執行測試：</span><span class="sxs-lookup"><span data-stu-id="a27dd-143">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="a27dd-144">在 `mytestproject.dll` 中執行測試，以自訂名稱匯出到自訂資料夾：</span><span class="sxs-lookup"><span data-stu-id="a27dd-144">Run tests in `mytestproject.dll`, exporting to custom folder with custom name:</span></span>

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

<span data-ttu-id="a27dd-145">以 `mytestproject.dll` 和 `myothertestproject.exe` 執行測試：</span><span class="sxs-lookup"><span data-stu-id="a27dd-145">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="a27dd-146">執行 `TestMethod1` 測試：</span><span class="sxs-lookup"><span data-stu-id="a27dd-146">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="a27dd-147">執行 `TestMethod1` 和 `TestMethod2` 測試：</span><span class="sxs-lookup"><span data-stu-id="a27dd-147">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`

