---
ms.openlocfilehash: 8b2a01eb6dfdd5bd2bcbef6014d4edeb3ec82ac1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803536"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a>WinForm 的 CheckForOverflowUnderflow 屬性對於 System.Drawing 現在是 true

|   |   |
|---|---|
|詳細資料|System.Drawing.dll 組件的 CheckForOverflowUnderflow 屬性設定為 true。|
|建議|以往發生溢位時，結果會以無訊息模式截斷。 現在則會擲回 <xref:System.OverflowException?displayProperty=name> 例外狀況。|
|範圍|Edge|
|版本|4.5|
|類型|執行階段|
