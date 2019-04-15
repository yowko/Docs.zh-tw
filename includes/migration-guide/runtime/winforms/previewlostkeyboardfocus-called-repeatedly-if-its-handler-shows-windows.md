---
ms.openlocfilehash: addfd55fd01b13e9088e4706ff846fc624aafa68
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235363"
---
### <a name="previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a>如果其處理常式顯示 Windows Forms 訊息方塊，則會重複呼叫 PreviewLostKeyboardFocus

|   |   |
|---|---|
|詳細資料|從 .NET Framework 4.5 開始，從 <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> 處理常式呼叫 <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> 會使處理常式在關閉訊息方塊時重新引發，而可能產生無限的訊息方塊迴圈。|
|建議|此問題有兩個解決方法：<ol><li>藉由呼叫 <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> (而不是 <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>) 來避免此問題。</li><li>藉由從 <xref:System.Windows.UIElement.LostKeyboardFocus?displayProperty=nameWithType> 事件處理常式 (相對於 <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=name> 事件處理常式) 顯示訊息方塊來避免此問題。</li></ol>|
|範圍|Edge|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=nameWithType></li></ul>|
