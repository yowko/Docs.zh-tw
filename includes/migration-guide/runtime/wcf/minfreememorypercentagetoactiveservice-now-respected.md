---
ms.openlocfilehash: b23182ad1da8208a69b78fc7bc872780d386a59a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496878"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a>現在會遵守 MinFreeMemoryPercentageToActiveService

#### <a name="details"></a>詳細資料

此設定建立伺服器上必須提供才能啟動 WCF 服務的最小記憶體。 其設計目的是為了防止發生 <xref:System.OutOfMemoryException?displayProperty=fullName> 例外狀況。 在 .NET Framework 4.5 中，此設定不會造成影響。 在 .NET Framework 4.5.1 中，會遵守此設定。

#### <a name="suggestion"></a>建議

如果 Ｗeb 伺服器上可用的記憶體小於此組態設定所定義的百分比，則會發生例外狀況。 某些成功啟動並在有限記憶體環境下執行的 WCF 服務現在可能會失敗。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Minor|
|版本|4.5.1|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

無法透過 API 分析偵測。

<!--

#### Affected APIs

Not detectable via API analysis.

-->
