---
title: .NET SDK 遙測
description: 探索收集使用量資訊以進行分析的 .NET SDK 遙測功能、收集的資料，以及如何停用。
author: KathleenDollard
ms.date: 08/27/2019
ms.openlocfilehash: 137b703dc9369f09fb535af40edf057e4e02117a
ms.sourcegitcommit: 2b878d7011306b215dbf3d5dc9c1e78355a6dcd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2021
ms.locfileid: "98757833"
---
# <a name="net-sdk-telemetry"></a>.NET SDK 遙測

[.NET SDK](index.md)包含遙測功能，可在 .net CLI 損毀時，收集使用方式資料和例外狀況資訊。 .Net CLI 隨附 .NET SDK，是一組可讓您建立、測試和發佈 .NET 應用程式的動詞命令。 .NET 小組必須了解使用者如何使用這些工具，以便進行改善。 失敗資訊可協助小組解決問題並修正 Bug。

收集的資料會在「 [創意 Commons](https://creativecommons.org/licenses/by/4.0/)屬性」授權下的匯總中發行。

## <a name="scope"></a>影響範圍

`dotnet` 有兩個功能：執行應用程式，以及執行 CLI 命令。 使用 `dotnet` 啟動應用程式時 (格式如下)，「不會收集」遙測：

- `dotnet [path-to-app].dll`

使用任何 [.NET CLI 命令](index.md)時，*會收集* 遙測，例如：

- `dotnet build`
- `dotnet pack`
- `dotnet run`

## <a name="how-to-opt-out"></a>如何選擇退出

預設會啟用 .NET SDK 遙測功能。 若要退出遙測功能，請將 `DOTNET_CLI_TELEMETRY_OPTOUT` 環境變數設定為 `1` 或 `true`。

當安裝成功時，.NET SDK 安裝程式也會傳送單一遙測專案。 若要退出，請在 `DOTNET_CLI_TELEMETRY_OPTOUT` 安裝 .NET SDK 之前先設定環境變數。

> [!IMPORTANT]
> 若要在啟動安裝程式之後退出，請關閉安裝程式、設定環境變數，然後使用該設定的值重新執行安裝程式。

## <a name="disclosure"></a>公開

當您第一次執行其中一個 [.NET CLI 命令](index.md) 時，.net SDK 會顯示與下列類似的文字 (例如 `dotnet build`) 。 文字可能略有不同，視執行中的 SDK 版本而定。 這個「第一次執行」經驗是 Microsoft 如何通知您有關資料收集。

```console
Telemetry
---------
The .NET tools collect usage data in order to help us improve your experience. The data is collected by Microsoft and shared with the community. You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

若要停用此訊息和 .NET 歡迎使用訊息，請將 `DOTNET_NOLOGO` 環境變數設為 `true` 。 請注意，此變數不會影響已退出的遙測。

## <a name="data-points"></a>資料點

遙測功能不會收集個人資料，例如使用者名稱或電子郵件地址。 它不會掃描您的程式碼，也不會擷取專案層級資料，例如名稱、存放庫或作者。 資料使用 [Azure 監視器](https://azure.microsoft.com/services/monitor/)技術安全地傳送至 Microsoft 伺服器、在限制存取下保留，並在嚴格安全性控制下從安全的 [Azure 儲存體](https://azure.microsoft.com/services/storage/)系統發佈。

保護您的隱私權對我們而言很重要。 如果您懷疑遙測收集敏感性資料或資料正在, 或不當處理，請在 [dotnet/sdk](https://github.com/dotnet/sdk/issues) 存放庫中提出問題，或傳送電子郵件以 [dotnet@microsoft.com](mailto:dotnet@microsoft.com) 供調查。

遙測功能會收集下列資料：

| SDK 版本 | 資料 |
|--------------|------|
| 全部          | 叫用的時間戳記。 |
| 全部          | 叫用的命令 (例如 "build")，從 2.1 開始已雜湊。 |
| 全部          | 用來判斷地理位置的三個八位元 IP 位址。 |
| 全部          | 作業系統和版本。 |
| 全部          | SDK 正在執行的執行階段識別碼 (RID)。 |
| 全部          | .NET SDK 版本。 |
| 全部          | 遙測設定檔：選擇性值，只能透過明確的使用者加入使用，且只能在 Microsoft 內部使用。 |
| >=2.0        | 命令引數和選項：會收集數個引數和選項 (不是任意字串)。 請參閱[收集的選項](#collected-options)。 2.1.300 之後已雜湊。 |
| >=2.0         | SDK 是否正在容器中執行。 |
| >=2.0         | 目標 Framework (來自 `TargetFramework` 事件)，從 2.1 開始已雜湊。 |
| >=2.0         | 雜湊媒體存取控制 (MAC) 位址 (SHA256) 。 |
| >=2.0         | 雜湊的目前工作目錄。 |
| >=2.0         | 使用雜湊的安裝程式 exe 檔名來安裝成功報告。 |
| >=2.1.300     | 核心版本。 |
| >=2.1.300     | Libc 發行/版本。 |
| >=3.0.100     | 輸出是否已重新導向 (true 或 false)。 |
| >=3.0.100     | CLI/SDK 損毀時的例外狀況類型及其堆疊追蹤 (只有 CLI/SDK 程式碼會包含在傳送的堆疊追蹤中)。 如需詳細資訊，請參閱 [收集的 .NET CLI/SDK 損毀例外狀況遙測](#net-clisdk-crash-exception-telemetry-collected)。 |

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
| `--runtime`             | `dotnet build`,  `dotnet publish`                                                              |
| `--platform`            | `dotnet vstest`                                                                                |
| `--logger`              | `dotnet vstest`                                                                                |
| `--sdk-package-version` | `dotnet migrate`                                                                               |

除了 `--verbosity` 和 `--sdk-package-version` 以外，所有其他值都會從 .NET Core 2.1.100 SDK 開始進行雜湊。

## <a name="net-clisdk-crash-exception-telemetry-collected"></a>收集的 .NET CLI/SDK 損毀例外狀況遙測

如果 .NET CLI/SDK 損毀，它會收集例外狀況的名稱和 CLI/SDK 程式碼的堆疊追蹤。 收集這項資訊是為了評估問題，並改善 .NET SDK 和 CLI 的品質。 本文提供我們所收集資料的相關資訊。 它也提供使用者如何建立自己的 .NET SDK 版本的秘訣，以避免意外洩漏個人或機密資訊。

### <a name="types-of-collected-data"></a>收集的資料類型

.NET CLI 只會收集 CLI/SDK 例外狀況的資訊，而不會收集您應用程式中的例外狀況。 所收集資料包含例外狀況的名稱和堆疊追蹤。 此堆疊追蹤是 CLI/SDK 程式碼的堆疊追蹤。

下列範例會顯示所收集的資料類型：

```console
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

### <a name="avoid-inadvertent-disclosure-of-information"></a>避免意外洩漏資訊

.NET 參與者和任何其他執行自己所建立之 .NET SDK 版本的人，都應該考慮其 SDK 原始程式碼的路徑。 如果當您使用的 .NET SDK 是自訂的偵錯工具，或使用自訂群組建符號檔進行設定時發生當機，則會在堆疊追蹤中收集來自組建電腦的 SDK 來源檔案路徑，而不會進行雜湊處理。

因此，.NET SDK 的自訂群組建不應位於路徑名稱公開個人或機密資訊的目錄中。

## <a name="see-also"></a>另請參閱

- [.NET CLI 遙測資料](https://dotnet.microsoft.com/platform/telemetry)
- [遙測參考來源 (dotnet/sdk 存放庫) ](https://github.com/dotnet/sdk/tree/master/src/Cli/dotnet/Telemetry)
