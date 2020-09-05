---
ms.openlocfilehash: c4a3d903894027a01d32ca132d1233da9d9c3ee5
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497648"
---
### <a name="previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a>如果其處理常式顯示 Windows Forms 訊息方塊，則會重複呼叫 PreviewLostKeyboardFocus

#### <a name="details"></a>詳細資料

從 .NET Framework 4.5 開始，從 <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> 處理常式呼叫 <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> 會使處理常式在關閉訊息方塊時重新引發，而可能產生無限的訊息方塊迴圈。

#### <a name="suggestion"></a>建議

此問題有兩個解決方法：<ol><li>藉由呼叫 <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> (而不是 <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>) 來避免此問題。</li><li>藉由從 <xref:System.Windows.UIElement.LostKeyboardFocus> 事件處理常式 (相對於 <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName> 事件處理常式) 顯示訊息方塊來避免此問題。</li></ol>

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Edge|
|版本|4.5|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=nameWithType>
- <xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=nameWithType>
- <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=nameWithType>
- <xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=nameWithType>

<!--

#### Affected APIs

- `E:System.Windows.ContentElement.PreviewLostKeyboardFocus`
- `E:System.Windows.IInputElement.PreviewLostKeyboardFocus`
- `E:System.Windows.UIElement.PreviewLostKeyboardFocus`
- `E:System.Windows.UIElement3D.PreviewLostKeyboardFocus`

-->
