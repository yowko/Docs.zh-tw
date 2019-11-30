---
ms.openlocfilehash: add3ff8faed2e7fab245e5b6f1b9158b7bdd06f5
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567354"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a>如果顯示工具提示，則不會引發 CellFormatting 事件

<xref:System.Windows.Forms.DataGridView> 現在會在滑鼠停留時顯示儲存格的文字和錯誤工具提示，並透過鍵盤選取。 如果顯示工具提示，則不會引發 <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> 事件。

#### <a name="change-description"></a>變更描述

在 .NET Core 3.1 之前，<xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> 屬性設定為 `true` 的 <xref:System.Windows.Forms.DataGridView> 會在滑鼠游標停留時，顯示儲存格文字和錯誤的工具提示。 透過鍵盤選取資料格時，不會顯示工具提示（例如，使用 Tab 鍵、快速鍵或箭號導覽）。 如果使用者編輯了資料格，而當 <xref:System.Windows.Forms.DataGridView> 仍處於編輯模式時，將滑鼠停留在未設定 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> 屬性的資料格上，就會引發 <xref:System.Windows.Forms.DataGridView.CellFormatting> 事件來格式化儲存格的文字，以便顯示在資料格中。

為了符合協助工具標準，從 .NET Core 3.1 開始，<xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> 屬性設定為 `true` 的 <xref:System.Windows.Forms.DataGridView> 會顯示儲存格文字的工具提示，而不只是在資料格停留時，也會在透過鍵盤選取時的錯誤。 由於這項變更的結果，當 <xref:System.Windows.Forms.DataGridView> 處於編輯模式時，如果未設定 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> 屬性集的儲存格，就*不*會引發 <xref:System.Windows.Forms.DataGridView.CellFormatting> 事件。 事件不會引發，因為暫留的資料格內容會顯示為工具提示，而不會顯示在資料格中。

#### <a name="version-introduced"></a>引進的版本

3.1

#### <a name="recommended-action"></a>建議的動作

當 <xref:System.Windows.Forms.DataGridView> 處於編輯模式時，重構相依于 <xref:System.Windows.Forms.DataGridView.CellFormatting> 事件的任何程式碼。

#### <a name="category"></a>Category

Windows 表單

#### <a name="affected-apis"></a>受影響的 API

無法透過 API 分析來偵測。

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
