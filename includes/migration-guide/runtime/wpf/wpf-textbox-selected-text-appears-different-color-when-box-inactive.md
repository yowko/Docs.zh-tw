---
ms.openlocfilehash: 74ce1bbc9a887aee3a33eaf05084e8c2000967c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379561"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a>WPF TextBox 選取文字在文字方塊非作用中時，會以不同的色彩來顯示

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.5 中，當 WPF 文字方塊控制項非作用中時 (沒有焦點)，方塊內的選取文字會以不同於控制項作用中的色彩來顯示。|
|建議|將 <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> 屬性設為 <code>false</code> 可以還原舊有 (.NET Framework 4.0) 行為。|
|範圍|Edge|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
