---
ms.openlocfilehash: 8b0617d8f021a9534289fd7ae8539cd054684862
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774317"
---
### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a>WPF TextBox.Text 可能與資料繫結不同步

|   |   |
|---|---|
|詳細資料|在某些情況下，如果屬性在資料繫結寫入作業期間經過修改，<xref:System.Windows.Controls.TextBox.Text> 屬性會反映資料繫結屬性值先前的值。|
|建議|這應該不會產生負面影響。 不過，您可以藉由將 <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> 屬性設為 <code>false</code> 還原舊有行為。|
|範圍|Edge|
|版本|4.5|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType></li></ul>|
