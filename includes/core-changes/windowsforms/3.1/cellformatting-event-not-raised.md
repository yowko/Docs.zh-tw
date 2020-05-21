---
ms.openlocfilehash: 4a34a64eba72ea24c1d830566565ce4fbee8e5b7
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721060"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a>如果顯示工具提示，則不會引發 CellFormatting 事件

A <xref:System.Windows.Forms.DataGridView> 現在會在滑鼠停留時顯示儲存格的文字和錯誤工具提示，並透過鍵盤選取。 如果顯示工具提示，則 <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> 不會引發事件。

#### <a name="change-description"></a>變更描述

在 .NET Core 3.1 之前， <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> 已將屬性設定為的會在 `true` 滑鼠游標停留時，顯示儲存格文字和錯誤的工具提示。 透過鍵盤選取資料格時，不會顯示工具提示（例如，使用 Tab 鍵、快速鍵或箭號導覽）。 如果使用者編輯了資料格，而當 <xref:System.Windows.Forms.DataGridView> 仍然處於編輯模式時，將滑鼠停留在未設定屬性的資料格上，就會 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> <xref:System.Windows.Forms.DataGridView.CellFormatting> 引發事件來格式化儲存格的文字，以便顯示在資料格中。

為了符合協助工具標準，從 .NET Core 3.1 開始，將 <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> 屬性設定為的會 `true` 顯示資料格文字的工具提示，而不只是在資料格已暫留時，也會在透過鍵盤選取時出現的錯誤。 由於這項變更的結果， <xref:System.Windows.Forms.DataGridView.CellFormatting> 當*not* <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> <xref:System.Windows.Forms.DataGridView> 處於編輯模式時，不會引發未設定屬性的資料格時，就不會引發事件。 事件不會引發，因為暫留的資料格內容會顯示為工具提示，而不會顯示在資料格中。

#### <a name="version-introduced"></a>引進的版本

3.1

#### <a name="recommended-action"></a>建議的動作

<xref:System.Windows.Forms.DataGridView.CellFormatting>當處於編輯模式時，重構相依于事件的任何程式碼 <xref:System.Windows.Forms.DataGridView> 。

#### <a name="category"></a>類別

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

無

<!-- 

#### Affected APIs

Not detectable via API analysis.

-->
