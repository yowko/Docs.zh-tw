---
ms.openlocfilehash: 51ac10e6b4cc9c757cb7f68d7d665982bcb57d4e
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497545"
---
### <a name="systemactivities-is-now-aptca"></a>System.Activities 現在是 APTCA

#### <a name="details"></a>詳細資料

組件會以 <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> 屬性標記。

#### <a name="suggestion"></a>建議

衍生類別無法以 <xref:System.Security.SecurityCriticalAttribute?displayProperty=fullName> 標記。 以往衍生類型必須以 <xref:System.Security.SecurityCriticalAttribute?displayProperty=fullName> 標記。 不過，這項變更應該不會產生實際影響。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Edge|
|版本|4.5|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

無法透過 API 分析偵測。

<!--

#### Affected APIs

Not detectable via API analysis.

-->
