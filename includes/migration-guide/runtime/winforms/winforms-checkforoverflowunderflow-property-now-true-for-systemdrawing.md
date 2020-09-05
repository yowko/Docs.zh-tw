---
ms.openlocfilehash: 68b0c4bb032b9744ef585eaef3d68e31afebee24
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496414"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a>WinForm 的 CheckForOverflowUnderflow 屬性對於 System.Drawing 現在是 true

#### <a name="details"></a>詳細資料

System.Drawing.dll 組件的 CheckForOverflowUnderflow 屬性設定為 true。

#### <a name="suggestion"></a>建議

以往發生溢位時，結果會以無訊息模式截斷。 現在則會擲回 <xref:System.OverflowException?displayProperty=fullName> 例外狀況。

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
