---
ms.openlocfilehash: 2aa6603e2ed77ffa94fbc6325cd5db50985bda6a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620079"
---
### <a name="previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a>如果其處理常式顯示 Windows Forms 訊息方塊，則會重複呼叫 PreviewLostKeyboardFocus

#### <a name="details"></a>詳細資料

從 .NET Framework 4.5 開始，從 <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> 處理常式呼叫 <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> 會使處理常式在關閉訊息方塊時重新引發，而可能產生無限的訊息方塊迴圈。

#### <a name="suggestion"></a>建議

此問題有兩個解決方法：<ol><li>藉由呼叫 <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> (而不是 <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>) 來避免此問題。</li><li>藉由從 <xref:System.Windows.UIElement.LostKeyboardFocus> 事件處理常式 (相對於 <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName> 事件處理常式) 顯示訊息方塊來避免此問題。</li></ol>

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Edge|
|版本|4.5|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=nameWithType></li></ul>|
