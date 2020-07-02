---
ms.openlocfilehash: 75f176133697056bab9349ba1d18d7a0e1aa7da2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619814"
---
### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a>Items.Clear 不會從 SelectedItems 移除重複項目

#### <a name="details"></a>詳細資料

假設選取器 (啟用了多個選取項目) 在其 <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> 集合中有重複項目 - 相同的項目出現一次以上。  從資料來源移除這些項目 (例如，藉由呼叫 Items.Clear) 無法從 <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> 中加以移除；只會移除第一個執行個體。 此外，後續使用 <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> (例如 SelectedItems.Clear()) 可能會發生像是 <xref:System.ArgumentException?displayProperty=fullName> 的問題，因為 <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> 包含已不在資料來源中的項目。

#### <a name="suggestion"></a>建議

如有可能，請升級至 .NET Framework 4.6.2。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Minor|
|版本|4.5|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType></li></ul>|
