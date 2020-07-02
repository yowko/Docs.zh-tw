---
ms.openlocfilehash: beaac7b14535335a665add4fa056a60793879753
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620073"
---
### <a name="systemactivities-is-now-aptca"></a>System.Activities 現在是 APTCA

#### <a name="details"></a>詳細資料

組件會以 <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> 屬性標記。

#### <a name="suggestion"></a>建議

衍生類別無法以 <xref:System.Security.SecurityCriticalAttribute?displayProperty=fullName> 標記。 以往衍生類型必須以 <xref:System.Security.SecurityCriticalAttribute?displayProperty=fullName> 標記。 不過，這項變更應該不會產生實際影響。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Edge|
|版本|4.5|
|類型|執行階段|
