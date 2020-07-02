---
ms.openlocfilehash: 4cd06fd02fadbaa9f74e40f850e688ee883454ed
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620091"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a>WinForm 的 CheckForOverflowUnderflow 屬性對於 System.Drawing 現在是 true

#### <a name="details"></a>詳細資料

System.Drawing.dll 組件的 CheckForOverflowUnderflow 屬性設定為 true。

#### <a name="suggestion"></a>建議

以往發生溢位時，結果會以無訊息模式截斷。 現在則會擲回 <xref:System.OverflowException?displayProperty=fullName> 例外狀況。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Edge|
|版本|4.5|
|類型|執行階段|
