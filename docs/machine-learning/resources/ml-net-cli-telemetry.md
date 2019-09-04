---
title: 依 ML.NET CLI 排列的遙測集合
description: 了解 ML.NET CLI 遙測特性，它會收集用於分析、要收集哪些資料，以及如何停用的使用資訊。 此外，尋找 Microsoft GDPR 合規性 .NET 授權合約和相關資訊的連結。
ms.topic: conceptual
ms.date: 09/03/2019
ms.custom: ''
ms.openlocfilehash: e7b3b3d7789f2368ebc4448e73add817986a5906
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254001"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a>依 ML.NET CLI 排列的遙測集合

[ML.NET CLI](https://aka.ms/mlnet-cli) 包含遙測特性，會收集彙總供 Microsoft 使用的匿名使用資料。

## <a name="how-microsoft-uses-the-data"></a>Microsoft 如何使用資料

產品小組會使用 ML.NET CLI 遙測資料協助您了解如何改善工具。 例如，如果客戶不常使用特定的機器學習工作，產品小組會調查原因並使用結果來排定特性開發的優先順序。 ML.NET CLI 遙測也可協助偵錯問題，例如當機和程式碼異常。 

雖然產品小組感激此見解，但我們也知道不是所有人都願意傳送此資料。 [了解如何停用遙測。](#opt-out-of-data-collection)

## <a name="scope"></a>`Scope`

`mlnet` 命令會啟動 ML.NET CLI，但命令本身不會收集遙測。

當您執行 `mlnet` 命令不附加任何其他命令時，「不啟用」遙測。 例如：

- `mlnet`
- `mlnet --help`

當您執行 [ML.NET CLI 命令](../reference/ml-net-cli-reference.md)時，例如 `mlnet auto-train`，會「啟用」遙測。

## <a name="opt-out-of-data-collection"></a>選擇不使用資料收集

預設啟用 ML.NET CLI 遙測特性。

將 `MLDOTNET_CLI_TELEMETRY_OPTOUT` 環境變數設成 `1` 或 `true`，選擇退出遙測功能。 此環境變數會全域套用至 ML.NET CLI 工具。

## <a name="data-points-collected"></a>已收集資料點

這個功能會收集下列資料︰

- 已叫用哪個命令，例如 `auto-train`
- 使用的命令列參數名稱 (也就是「資料集-名稱、標籤-欄名、ml-工作、輸出路徑、最大探索時間、詳細資訊」)
- 雜湊 MAC 位址：機器的密碼編譯 (SHA256) 匿名唯一識別碼
- 叫用的時間戳記
- 僅用來判斷地理位置的三個八位元 IP 位址 (非完整 IP 位址)
- 所有使用的引數/參數名稱。 不是客戶的值，例如字串
- 經雜湊處理的資料集檔案名稱
- 資料集檔案大小貯體
- 作業系統和版本
- --task 參數的值：類別值，例如 `regression`、`binary-classification` 和 `multiclass-classification`
- ML.NET CLI 版本 (也就是 0.3.27703.4)

資料會使用 [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) 技術安全傳送至 Microsoft 伺服器、保留在限制存取權下，並在安全 [Azure 儲存體](https://azure.microsoft.com/services/storage/)系統的嚴格安全性控制項下使用。

### <a name="data-points-not-collected"></a>未收集資料點
遙測特性「不」收集：
- 個人資料，例如使用者姓名
- 資料集檔案名稱
- 來自資料集檔案的資料

如果您懷疑 ML.NET CLI 遙測正在收集敏感性資料，或資料處理的方式不安全或不適當，請在 [ML.NET](https://github.com/dotnet/machinelearning) 存放庫中提出問題以供調查。

## <a name="license"></a>使用權

Microsoft 的 ML.NET CLI 散發由 [Microsoft 軟體授權所授權：Microsoft .NET 程式庫](https://aka.ms/dotnet-core-eula)。 如需資料收集與處理的詳細資訊，請參閱＜資料＞一節。

## <a name="disclosure"></a>公開

當您第一次執行 [ML.NET CLI 命令](../reference/ml-net-cli-reference.md)時，例如 `mlnet auto-train`，ML.NET CLI 工具會顯示揭露文字，告訴您如何選擇退出遙測。 文字可能因您執行的 CLI 版本而略有不同。

## <a name="see-also"></a>另請參閱
- [ML.NET CLI 參考](../reference/ml-net-cli-reference.md)
- [MICROSOFT 軟體授權條款：Microsoft .NET 程式庫](https://aka.ms/dotnet-core-eula)
- [Microsoft 隱私權](https://www.microsoft.com/trustcenter/privacy/)
- [Microsoft 隱私權聲明](https://privacy.microsoft.com/privacystatement)
