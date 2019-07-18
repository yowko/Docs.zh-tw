---
ms.openlocfilehash: 01bbc49cb0febc5a29dafc7c311b848387a4094a
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803492"
---
### <a name="add-selectiontextbrush-public-property-to-textboxpasswordbox-non-adorner-selection"></a>將 SelectionTextBrush 公用屬性新增至 TextBox/PasswordBox 非提示選取項目

|   |   |
|---|---|
|詳細資料|在針對 <xref:System.Windows.Controls.TextBox> 和 <xref:System.Windows.Controls.PasswordBox> 使用[非提示型文字選取項目](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md)的 WPF 應用程式中，開發人員現在可以設定新增的 SelectionTextBrush 屬性，以變更所選文字的轉譯。  根據預設，此色彩會隨著 <xref:System.Windows.SystemColors.HighlightTextBrushKey> 而變更。  如果未啟用非提示型文字選取範圍，則會忽略這個屬性。|
|建議|啟用非提示型文字選取範圍後，您可以使用 <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> 和 <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> 屬性變更所選文字的外觀。 此操作可以使用 XAML 完成：<pre><code class="lang-xaml">&lt;TextBox SelectionBrush=&quot;Red&quot; SelectionTextBrush=&quot;White&quot;  SelectionOpacity=&quot;0.5&quot;&#13;&#10;Foreground=&quot;Blue&quot; CaretBrush=&quot;Blue&quot;&gt;&#13;&#10;This is some text.&#13;&#10;&lt;/TextBox&gt;&#13;&#10;</code></pre>|
|範圍|主要|
|版本|4.8|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrushProperty?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush?displayProperty=nameWithType></li><li>[System.Windows.Controls.TextBox](xref:System.Windows.Controls.TextBox)</li><li>[System.Windows.Controls.PasswordBox](xref:System.Windows.Controls.PasswordBox)</li></ul>|

