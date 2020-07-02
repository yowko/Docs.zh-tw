---
ms.openlocfilehash: cd59818fe674e10a206725bea8a74c4aceed99b1
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620099"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a>WPF TextBox 選取文字在文字方塊非作用中時，會以不同的色彩來顯示

#### <a name="details"></a>詳細資料

在 .NET Framework 4.5 中，當 WPF 文字方塊控制項非作用中時 (沒有焦點)，方塊內的選取文字會以不同於控制項作用中的色彩來顯示。

#### <a name="suggestion"></a>建議

將 <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> 屬性設為 <code>false</code> 可以還原舊有 (.NET Framework 4.0) 行為。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Edge|
|版本|4.5|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
