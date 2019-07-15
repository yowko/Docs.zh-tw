---
ms.openlocfilehash: 2f94ec58e6fdb56cfc5147e74b6ffd6bb657228d
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857608"
---
### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a>Items.Clear 不會從 SelectedItems 移除重複項目

|   |   |
|---|---|
|詳細資料|假設選取器 (啟用了多個選取項目) 在其 <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> 集合中有重複項目 - 相同的項目出現一次以上。  從資料來源移除這些項目 (例如，藉由呼叫 Items.Clear) 無法從 <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> 中加以移除；只會移除第一個執行個體。 此外，後續使用 <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> (例如 SelectedItems.Clear()) 可能會發生像是 <xref:System.ArgumentException?displayProperty=name> 的問題，因為 <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> 包含已不在資料來源中的項目。|
|建議|如有可能，請升級至 .NET Framework 4.6.2。|
|範圍|次要|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType></li></ul>|

