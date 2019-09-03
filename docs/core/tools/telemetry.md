---
title: .NET Core SDK 遙測
description: 探索收集使用方式資訊以進行分析的 .NET Core SDK 遙測功能，它會收集哪些資料以及如何停用。
author: KathleenDollard
ms.date: 08/27/2019
ms.custom: seodec18
ms.openlocfilehash: 253f69392f034e330a75ed387d9346e8a5ae2a08
ms.sourcegitcommit: 77e33b682db39955e331b8e8eda4ef1925a24e78
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2019
ms.locfileid: "70133690"
---
# <a name="net-core-sdk-telemetry"></a>.NET Core SDK 遙測

[.NET Core SDK](index.md) 包含遙測功能，可在 .NET Core CLI 損毀時收集使用方式資料和例外狀況資訊。 .NET Core CLI 隨附 .NET Core SDK，是可讓您建置、測試及發佈 .NET Core 應用程式的動詞集。 .NET 小組必須了解使用者如何使用這些工具，以便進行改善。 失敗資訊可協助小組解決問題並修正 Bug。

根據 [Creative Commons Attribution 授權](https://creativecommons.org/licenses/by/4.0/)，所收集的資料為匿名，且將會以彙總形式發佈。 

## <a name="scope"></a>範圍

`dotnet` 有兩個功能：執行應用程式，以及執行 CLI 命令。 使用 `dotnet` 啟動應用程式時 (格式如下)，「不會收集」  遙測：

- `dotnet [path-to-app].dll`

使用以下任何 [.NET Core CLI 命令](index.md) 時，則「會收集」  遙測：

- `dotnet build`
- `dotnet pack`
- `dotnet run`

## <a name="how-to-opt-out"></a>如何選擇退出

預設會啟用 .NET Core SDK 遙測功能。 若要退出遙測功能，請將 `DOTNET_CLI_TELEMETRY_OPTOUT` 環境變數設定為 `1` 或 `true`。 

當安裝成功時，.NET Core SDK 安裝程式也會傳送單一遙測項目。 若要退出，請在安裝 .NET Core SDK 之前，先設定 `DOTNET_CLI_TELEMETRY_OPTOUT` 環境變數。

## <a name="disclosure"></a>公開

.NET Core SDK 會在您第一次執行其中一個 [.NET Core CLI 命令](index.md)時 (例如 `dotnet build`)，顯示類似如下的文字。 文字可能略有不同，視執行中的 SDK 版本而定。 這個「第一次執行」經驗是 Microsoft 如何通知您有關資料收集。

```console
Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience. The data is anonymous. It is collected by Microsoft and shared with the community. You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

## <a name="data-points"></a>資料點

遙測功能不會收集個人資料，例如使用者名稱或電子郵件地址。 它不會掃描您的程式碼，也不會擷取專案層級資料，例如名稱、存放庫或作者。 資料使用 [Azure 監視器](https://azure.microsoft.com/services/monitor/)技術安全地傳送至 Microsoft 伺服器、在限制存取下保留，並在嚴格安全性控制下從安全的 [Azure 儲存體](https://azure.microsoft.com/services/storage/)系統發佈。

保護您的隱私權對我們而言很重要。 如果您懷疑遙測收集敏感性資料或資料處理的方式不安全或不適當，請在 [dotnet/cli](https://github.com/dotnet/cli/issues) 存放庫中提出問題或傳送電子郵件至 [dotnet@microsoft.com](mailto:dotnet@microsoft.com) 以進行調查。

遙測功能會收集下列資料：

| SDK 版本 | 資料 |
|--------------|------|
| All          | 叫用的時間戳記。 |
| All          | 叫用的命令 (例如 "build")，從 2.1 開始已雜湊。 |
| All          | 用來判斷地理位置的三個八位元 IP 位址。 |
| All          | 作業系統和版本。 |
| All          | SDK 正在執行的執行階段識別碼 (RID)。 |
| All          | .NET Core SDK 版本。 |
| All          | 遙測設定檔：選擇性值，只能透過明確的使用者加入使用，且只能在 Microsoft 內部使用。 |
| >=2.0        | 命令引數和選項：會收集數個引數和選項 (不是任意字串)。 請參閱[收集的選項](#collected-options)。 2\.1.300 之後已雜湊。 |
| >=2.0         | SDK 是否正在容器中執行。 |
| >=2.0         | 目標 Framework (來自 `TargetFramework` 事件)，從 2.1 開始已雜湊。 |
| >=2.0         | 雜湊的媒體存取控制 (MAC) 位址：電腦的密碼編譯 (SHA256) 匿名唯一識別碼。 |
| >=2.0         | 雜湊的目前工作目錄。 |
| >=2.0         | 使用雜湊的安裝程式 exe 檔名來安裝成功報告。 |
| >=2.1.300     | 核心版本。 |
| >=2.1.300     | Libc 發行/版本。 |
| >=3.0.100     | 輸出是否已重新導向 (true 或 false)。 |
| >=3.0.100     | CLI/SDK 損毀時的例外狀況類型及其堆疊追蹤 (只有 CLI/SDK 程式碼會包含在傳送的堆疊追蹤中)。 如需詳細資訊，請參閱[收集的 .NET Core CLI/SDK 損毀例外狀況遙測](#net-core-clisdk-crash-exception-telemetry-collected)。 |

### <a name="collected-options"></a>收集的選項

某些命令會傳送額外的資料。 命令的子集會傳送第一個引數：

| 命令               | 傳送的第一個引數資料                |
|-----------------------|-----------------------------------------|
| `dotnet help <arg>`   | 要查詢的命令說明。  |
| `dotnet new <arg>`    | 範本名稱 (已雜湊)。             |
| `dotnet add <arg>`    | `package` 或 `reference` 一字。      |
| `dotnet remove <arg>` | `package` 或 `reference` 一字。      |
| `dotnet list <arg>`   | `package` 或 `reference` 一字。      |
| `dotnet sln <arg>`    | `add`、`list` 或 `remove` 一字。    |
| `dotnet nuget <arg>`  | `delete`、`locals` 或 `push` 一字。 |

命令的子集會傳送所選取選項 (如果已使用) 及其值：

| 選項                  | 命令                                                                                       |
|-------------------------|------------------------------------------------------------------------------------------------|
| `--verbosity`           | 所有命令                                                                                   |
| `--language`            | `dotnet new`                                                                                   |
| `--configuration`       | `dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`                  |
| `--framework`           | `dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest` |
| `--runtime`             | `dotnet build`、`dotnet publish`                                                              |
| `--platform`            | `dotnet vstest`                                                                                |
| `--logger`              | `dotnet vstest`                                                                                |
| `--sdk-package-version` | `dotnet migrate`                                                                               |

除了 `--verbosity` 和 `--sdk-package-version` 以外，所有其他值都會從 .NET Core 2.1.100 SDK 開始進行雜湊。

## <a name="net-core-clisdk-crash-exception-telemetry-collected"></a>收集的 .NET Core CLI/SDK 損毀例外狀況遙測

如果 .NET Core CLI/SDK 損毀，它會收集例外狀況名稱和 CLI/SDK 程式碼的堆疊追蹤。 收集這項資訊的目的在於評定問題，並改善 .NET Core SDK 和 CLI 的品質。 本文提供我們所收集資料的相關資訊。 它也提供有關建置自有 .NET Core SDK 版本的使用者如何避免意外洩漏個人或敏感性資訊的祕訣。

### <a name="types-of-collected-data"></a>收集的資料類型

.NET Core CLI 只會收集 CLI/SDK 例外狀況的資訊，而不會收集您應用程式中的例外狀況資訊。 所收集資料包含例外狀況的名稱和堆疊追蹤。 此堆疊追蹤是 CLI/SDK 程式碼的堆疊追蹤。

下列範例會顯示所收集的資料類型：

```
System.IO.IOException
at System.ConsolePal.WindowsConsoleStream.Write(Byte[] buffer, Int32 offset, Int32 count)
at System.IO.StreamWriter.Flush(Boolean flushStream, Boolean flushEncoder)
at System.IO.StreamWriter.Write(Char[] buffer)
at System.IO.TextWriter.WriteLine()
at System.IO.TextWriter.SyncTextWriter.WriteLine()
at Microsoft.DotNet.Cli.Utils.Reporter.WriteLine()
at Microsoft.DotNet.Tools.Run.RunCommand.EnsureProjectIsBuilt()
at Microsoft.DotNet.Tools.Run.RunCommand.Execute()
at Microsoft.DotNet.Tools.Run.RunCommand.Run(String[] args)
at Microsoft.DotNet.Cli.Program.ProcessArgs(String[] args, ITelemetry telemetryClient)
at Microsoft.DotNet.Cli.Program.Main(String[] args)
```

### <a name="avoid-inadvertent-disclosure-information"></a>避免意外洩漏資訊

.NET Core 參與者及執行其自行建置之 .NET Core SDK 版本的任何其他人，都應該考慮其 SDK 原始程式碼的路徑。 如果使用 .NET Core SDK 時發生損毀，且該 SDK是自訂偵錯組建或透過自訂組建符號檔所設定，則會在堆疊追蹤過程中從組建電腦收集 SDK 來源檔案路徑，且不會進行雜湊處理。

因此，.NET Core SDK 自訂組建不應該位於其路徑名稱會公開個人或敏感性資訊的目錄中。 

## <a name="see-also"></a>另請參閱

- [.NET Core CLI Telemetry - 2019 Q2 Data](https://dotnet.microsoft.com/platform/telemetry/dotnet-core-cli-2019q2) (.NET Core CLI 遙測 - 2019 年第 2 季資料)
- [遙測參考來源 (dotnet/cli 存放庫)](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)
