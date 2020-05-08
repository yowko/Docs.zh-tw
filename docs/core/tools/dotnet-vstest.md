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
# <a name="dotnet-vstest"></a>dotnet vstest

**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本

> [!IMPORTANT]
> `dotnet vstest`命令已由`dotnet test`取代，現在可用來執行元件。 請參閱 [`dotnet test`](dotnet-test.md)。

## <a name="name"></a>名稱

`dotnet-vstest`-從指定的元件執行測試。

## <a name="synopsis"></a>概要

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

## <a name="description"></a>描述

`dotnet-vstest` 命令會執行 `VSTest.Console` 命令列應用程式，以執行自動化的單元測試。

## <a name="arguments"></a>引數

- **`TEST_FILE_NAMES`**

  從指定的組件執行測試。 以空格分隔多個測試組件名稱。 支援萬用字元。

## <a name="options"></a>選項

- **`--Blame`**

  在歸責模式下執行測試。 這個選項有助於隔離造成測試主機損毀的問題。 它會以 *Sequence.xml* 的形式在目前目錄中建立一個輸出檔，用來擷取損毀前的測試執行順序。

- **`--Diag <PATH_TO_LOG_FILE>`**

  啟用測試平台的詳細資訊記錄檔。 記錄檔會寫入提供的檔案。

- **`--Framework <FRAMEWORK>`**

  用於測試執行的目標 .NET Framework 版本。 有效值的範例包括 `.NETFramework,Version=v4.6` 或 `.NETCoreApp,Version=v1.0`。 其他支援的值為 `Framework40`、`Framework45`、`FrameworkCore10` 和 `FrameworkUap10`。

- **`--InIsolation`**

  在獨立的處理序中執行測試。 這樣會降低 *vstest.console.exe* 處理序在測試中錯誤處停止的可能性，但是測試的速度可能會比較慢。

- **`-lt|--ListTests <FILE_NAME>`**

  列出所有從指定之測試容器探索到的測試。

- **`--logger <LOGGER_URI/FRIENDLY_NAME>`**

  指定測試結果的記錄器。

  - 若要將測試結果發行至 Team Foundation Server 中，使用 `TfsPublisher` 記錄器提供者：

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - 若要將結果記錄到 Visual Studio 測試結果檔案 (TRX)，使用 `trx` 記錄器提供者。 這個參數會以指定的記錄檔名稱，在測試結果目錄中建立檔案。 如果沒有提供 `LogFileName`，會建立唯一的檔案名稱以保留測試結果。

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`--Parallel`**

  以平行方式執行測試。 根據預設，電腦上所有的可用核心都可供使用。 在 *.runsettings*檔案中的`RunConfiguration`節點下設定屬性`MaxCpuCount` ，以指定明確的核心數目。

- **`--ParentProcessId <PROCESS_ID>`**

  負責啟動目前處理序之父處理序的處理序識別碼。

- **`--Platform <PLATFORM_TYPE>`**

  用於測試執行的目標平台架構。 有效值是 `x86`、`x64` 和 `ARM`。

- **`--Port <PORT>`**

  指定通訊端連線和接收事件訊息的連接埠。

- **`--ResultsDirectory:<PATH>`**

  如果測試結果目錄不存在，則會在指定的路徑中建立該目錄。

- **`--Settings <SETTINGS_FILE>`**

  執行測試時要使用的設定。

- **`--TestAdapterPath <PATH>`**

  在測試回合中，從指定的路徑 (如果有的話) 使用自訂測試配接器。

- **`--TestCaseFilter <EXPRESSION>`**

  執行符合指定之運算式的測試。 `<EXPRESSION>` 的格式為 `<property>Operator<value>[|&<EXPRESSION>]`，其中 Operator (運算子) 為 `=`、`!=` 或 `~` 其中之一。 運算子 `~` 具有「包含」語意，且適用於像是 `DisplayName` 的字串屬性。 括弧`()`是用來將子運算式分組。 如需詳細資訊，請參閱[TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md)。

- **`--Tests <TEST_NAMES>`**

  執行測試，其名稱符合所提供的值。 請使用逗號分隔多個值。

- **`-?|--Help`**

  印出命令的簡短說明。

- **`@<file>`**

  請讀取回應檔以取得更多選項。

- **`args`**

  指定要傳遞至配接器的額外引數。 引數指定為格式 `<n>=<v>` 的名稱/值組，其中 `<n>` 是引數名稱而 `<v>` 是引數值。 使用空格來分隔多個引數。

## <a name="examples"></a>範例

在*mytestproject.dll*中執行測試：

```dotnetcli
dotnet vstest mytestproject.dll
```

在*mytestproject.dll*中執行測試，並使用自訂名稱匯出至自訂資料夾：

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

在*mytestproject.dll*和*myothertestproject.exe*中執行測試：

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

執行 `TestMethod1` 測試：

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

執行 `TestMethod1` 和 `TestMethod2` 測試：

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```

## <a name="see-also"></a>另請參閱

- [VSTest.Console.exe 命令列選項](/visualstudio/test/vstest-console-options)
