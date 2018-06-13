---
title: .NET Core CLI 工具遙測
description: 探索收集使用量資訊以進行分析的 .NET Core 工具遙測功能，它會收集哪些資料以及如何停用。
author: richlander
ms.author: mairaw
ms.date: 08/04/2017
ms.openlocfilehash: 4c04867f5db512ef53c23ec41ea66db570a82021
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216079"
---
# <a name="net-core-cli-tools-telemetry"></a>.NET Core CLI 工具遙測

[.NET Core SDK](index.md) 包含收集使用資訊的[遙測功能](https://github.com/dotnet/cli/pull/2145)。 .NET 小組必須了解使用者如何使用這些工具，以便進行改善。 如需詳細資訊，請參閱 [What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/) (我們從 .NET Core SDK 遙測學到什麼)。

所收集的資料是匿名的，而且將會以彙總形式發行，供 Microsoft 和社群工程師根據 [Creative Commons Attribution 授權](https://creativecommons.org/licenses/by/4.0/)使用。 

## <a name="scope"></a>範圍

`dotnet` 命令用來啟動應用程式和 .NET Core CLI。 `dotnet` 命令本身不會收集遙測。 `dotnet` 命令執行的 .NET Core CLI 命令會收集遙測。

使用 `dotnet` 命令本身，沒有任何附加命令時，「不啟用」遙測：

- `dotnet`
- `dotnet [path-to-app]`

使用 [.NET Core CLI 命令](index.md) 時會「啟用」遙測，例如：

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`


## <a name="behavior"></a>行為

預設會啟用 .NET Core CLI 工具遙測功能。 將 `DOTNET_CLI_TELEMETRY_OPTOUT` 環境變數設成 `1` 或 `true`，退出遙測功能。

## <a name="data-points"></a>資料點

這個功能會收集下列資料︰

- 叫用時間戳記&#8224;
- 已叫用的命令 (例如 "build")&#8224;
- 用來判斷地理位置的三個八位元 IP 位址&#8224;
- 命令的 `ExitCode`
- 測試執行器 (用於測試專案)
- 作業系統和版本&#8224;
- 執行階段識別碼是否存在於 "runtimes" 節點中
- .NET Core SDK 版本&#8224;

&#8224;此計量已發行。

從 .NET Core SDK 2.0 開始，收集新的資料點：

- `dotnet` 命令引數和選項：只收集已知的引數和選項 (不是任意字串)。
- SDK 是否正在容器中執行。
- 目標 Framework。
- 雜湊 MAC 位址：機器以密碼編譯 (SHA256) 的匿名和唯一識別碼。 此計量未發行。
- 雜湊的目前工作目錄。

這個功能不收集個人資料，例如使用者名稱或電子郵件地址。 它不會掃描您的程式碼，也不會擷取機密的專案層級資料，例如名稱、存放庫或作者。 資料會使用 [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) 技術安全傳送至 Microsoft 伺服器、保留在限制存取權下，以及以安全的 [Azure 儲存體](https://azure.microsoft.com/services/storage/)系統的嚴格安全性控制項發佈。

我們想要知道您如何使用工具，以及它們是不是好用，而不是您用這些工具建置了什麼。 如果您懷疑遙測收集敏感性資料或我們以不安全或不適當地方式處理資料，請[在 dotnet/cli 存放庫問題中提出問題](https://github.com/dotnet/cli/issues)以進行調查。

## <a name="published-data"></a>發行資料

發行為每季提供，並列於 [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md) (.NET Core SDK 使用方式資料)。 資料檔的資料行包括：
- 時間戳記
- 發生次數&#8224;
- 命令
- 地理位置&#8225;
- OSFamily
- RuntimeID
- OSVersion
- SDKVersion

&#8224;「發生次數」資料行顯示該命令該日用於該資料列計量的彙總計數。 

&#8225;一般而言，「地理位置」資料行會顯示國家/地區的名稱。 在某些情況下，南極大陸會出現在這個資料行，因為研究人員在南極大陸使用 .NET Core 或不正確的位置資料。

### <a name="example"></a>範例

| 時間戳記      | 發生次數 | 命令 | 地理位置 | OSFamily | RuntimeID     | OSVersion | SDKVersion |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| 4/16/2017 0:00 | 8           | 回合     | 烏干達    | 達爾文   | osx.10.12-x64 | 10.12     | 1.0.1      |

### <a name="datasets"></a>資料集

[2016 - Q3](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)  
[2016 - Q4](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)  
[2017 - Q1](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)  
[2017 - Q2](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)

使用標準的 URL 格式張貼額外的資料集。 以年取代 `<YEAR>`，以一年的季取代 `<QUARTER>` (使用 `1`、`2`、`3` 或 `4`)。 這些檔案使用定位字元分隔值 (*TSV*) 格式。 

```
https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv
```

## <a name="license"></a>使用權

Microsoft 的 .NET Core 散發是使用 [MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula) 所授權。 此授權包含 "DATA" 區段以啟用遙測 (如下所示)。

[.NET NuGet 套件](https://www.nuget.org/profiles/dotnetframework)使用相同的授權，但不啟用遙測 (請參閱[範圍](#scope))。

> 2. 資料。 軟體可能會收集和您及您使用軟體之方式有關的資訊，並將該資訊傳送給 Microsoft。 Microsoft 可能會使用此資訊以改善產品與服務。 您可以前往 http://go.microsoft.com/fwlink/?LinkId=528096，以在說明文件及隱私權聲明中深入了解資料收集和使用方式的相關資訊。 使用軟體即代表您同意這些做法。

## <a name="disclosure"></a>公開

.NET Core CLI 工具會在您第一次執行其中一個命令時顯示下列文字 (例如，`dotnet restore`)。 文字可能略有不同，視執行中的 SDK 版本而定。 這個「第一次執行」經驗是 Microsoft 如何通知您有關資料收集。

```console
Welcome to .NET Core!
---------------------
Learn more about .NET Core @ https://aka.ms/dotnet-docs. Use dotnet --help to see available commands or go to https://aka.ms/dotnet-cli-docs.
 
Telemetry
--------------
The .NET Core tools collect usage data in order to improve your experience. The data is anonymous and does not include command-line arguments. The data is collected by Microsoft and shared with the community.
You can opt out of telemetry by setting a DOTNET_CLI_TELEMETRY_OPTOUT environment variable to 1 using your favorite shell.
You can read more about .NET Core tools telemetry @ https://aka.ms/dotnet-cli-telemetry.
```

## <a name="see-also"></a>另請參閱

[What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/) (我們從 .NET Core SDK 遙測學到什麼)  
[Telemetry reference source (dotnet/cli repo; release/2.0.0 branch)](https://github.com/dotnet/cli/tree/release/2.0.0/src/dotnet/Telemetry)  (遙測參考來源 (dotnet/cli 存放庫，版本/2.0.0 分支))  
[.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md) (.NET Core SDK 使用方式資料)
