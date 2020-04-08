---
ms.openlocfilehash: b736ab743a628fdcbc53c5ee51551e5dad986885
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888105"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a>如果顯示工具提示,則不引發單元格格式事件

現在<xref:System.Windows.Forms.DataGridView>,當滑鼠懸停並通過鍵盤選擇時,將顯示單元格的文本和錯誤工具提示。 如果顯示工具提示,則不會引發<xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>該事件。

#### <a name="change-description"></a>變更描述

在 .NET Core<xref:System.Windows.Forms.DataGridView>3.1 之前<xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A>,`true`將屬性設置為 顯示儲存格文本的工具提示,當儲存格被滑鼠懸停時,錯誤。 當通過鍵盤選擇單元格時(例如,通過使用 Tab 鍵、快速鍵或箭頭導航),不會顯示工具提示。 如果使用者編輯了單元格,然後,當<xref:System.Windows.Forms.DataGridView>仍處於編輯模式時,將滑鼠懸停在<xref:System.Windows.Forms.DataGridViewCell.ToolTipText>沒有 屬性集的單元格上,則會引發<xref:System.Windows.Forms.DataGridView.CellFormatting>一個 事件來設置單元格的文本格式,以便顯示在單元格中。

為了滿足輔助功能標準,從 .NET Core<xref:System.Windows.Forms.DataGridView>3.1 開始<xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A>,`true`該屬性設置為 顯示單元格文本的工具提示,不僅在單元格懸停時,而且通過鍵盤選擇時的錯誤。 由於此更改,當在編輯<xref:System.Windows.Forms.DataGridView.CellFormatting>模式下將沒有<xref:System.Windows.Forms.DataGridViewCell.ToolTipText>屬性集的單元格懸停時<xref:System.Windows.Forms.DataGridView>,*不會*引發事件。 不會引發該事件,因為懸停單元格的內容顯示為工具提示,而不是顯示在單元格中。

#### <a name="version-introduced"></a>介紹的版本

3.1

#### <a name="recommended-action"></a>建議的動作

重構任何依賴於<xref:System.Windows.Forms.DataGridView.CellFormatting>事件的代碼<xref:System.Windows.Forms.DataGridView>, 而處於編輯模式。

#### <a name="category"></a>類別

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

None

<!-- 

### Affected APIs

Not detectable via API analysis.

-->
