---
ms.openlocfilehash: 395463225e3c1f1d168dd019ea75966ad54e5a8a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621108"
---
### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a>變更 TextBlock 控制項之父代的 IsEnabled 屬性會影響任何子控制項

#### <a name="details"></a>詳細資料

從 .NET Framework 4.6.2 開始，變更 <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 控制項之父代的 <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> 屬性，會影響 <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 控制項的任何子控制項 (例如超連結和按鈕)。在 .NET Framework 4.6.1 和舊版中，<xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 內的控制項不一定會反映 <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 父代的 <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> 屬性狀態。

#### <a name="suggestion"></a>建議

無。 這項變更符合 <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 控制項內的之控制項的預期行為。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Minor|
|版本|4.6.2|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType></li></ul>|
