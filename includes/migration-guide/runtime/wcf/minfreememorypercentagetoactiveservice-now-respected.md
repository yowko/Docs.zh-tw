---
ms.openlocfilehash: f8e5dee9e97956cea78b7c8ec999af1afe9ac66b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620049"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a>現在會遵守 MinFreeMemoryPercentageToActiveService

#### <a name="details"></a>詳細資料

此設定建立伺服器上必須提供才能啟動 WCF 服務的最小記憶體。 其設計目的是為了防止發生 <xref:System.OutOfMemoryException?displayProperty=fullName> 例外狀況。 在 .NET Framework 4.5 中，此設定不會造成影響。 在 .NET Framework 4.5.1 中，會遵守此設定。

#### <a name="suggestion"></a>建議

如果 Ｗeb 伺服器上可用的記憶體小於此組態設定所定義的百分比，則會發生例外狀況。 某些成功啟動並在有限記憶體環境下執行的 WCF 服務現在可能會失敗。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Minor|
|版本|4.5.1|
|類型|執行階段|
