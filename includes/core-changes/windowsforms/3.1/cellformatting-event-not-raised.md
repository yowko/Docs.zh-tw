---
ms.openlocfilehash: add3ff8faed2e7fab245e5b6f1b9158b7bdd06f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567354"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a>如果顯示工具提示，則不引發儲存格格式事件

現在<xref:System.Windows.Forms.DataGridView>，當滑鼠懸停並通過鍵盤選擇時，將顯示儲存格的文本和錯誤工具提示。 如果顯示工具提示，則不會引發<xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>該事件。

#### <a name="change-description"></a>變更描述

在 .NET Core 3.1<xref:System.Windows.Forms.DataGridView>之前，<xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A>將屬性設置為`true`顯示儲存格文本的工具提示，當儲存格被滑鼠懸停時，錯誤。 當通過鍵盤選擇儲存格時（例如，通過使用 Tab 鍵、快速鍵或箭頭導航），不會顯示工具提示。 如果使用者編輯了儲存格，然後，當<xref:System.Windows.Forms.DataGridView>仍處於編輯模式時，將滑鼠懸停在沒有<xref:System.Windows.Forms.DataGridViewCell.ToolTipText>屬性集的儲存格上，則會引發一個<xref:System.Windows.Forms.DataGridView.CellFormatting>事件來設置儲存格的文本格式，以便顯示在儲存格中。

為了滿足協助工具標準，從 .NET Core 3.1<xref:System.Windows.Forms.DataGridView>開始，<xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A>該屬性設置為`true`顯示儲存格文本的工具提示，不僅在儲存格懸停時，而且通過鍵盤選擇時的錯誤。 由於此更改，當在 編輯<xref:System.Windows.Forms.DataGridView.CellFormatting>模式下將沒有<xref:System.Windows.Forms.DataGridViewCell.ToolTipText>屬性集的儲存格懸停時，<xref:System.Windows.Forms.DataGridView>*不會*引發事件。 不會引發該事件，因為懸停儲存格的內容顯示為工具提示，而不是顯示在儲存格中。

#### <a name="version-introduced"></a>介紹的版本

3.1

#### <a name="recommended-action"></a>建議的動作

重構任何依賴于<xref:System.Windows.Forms.DataGridView.CellFormatting>事件的代碼，<xref:System.Windows.Forms.DataGridView>而處於編輯模式。

#### <a name="category"></a>類別

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

無法通過 API 分析檢測。

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
