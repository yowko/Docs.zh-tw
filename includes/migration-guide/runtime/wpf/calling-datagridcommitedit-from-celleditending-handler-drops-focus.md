---
ms.openlocfilehash: c78122a2fe69c78625d6cb7fa9ddf41c49c2e737
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496659"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a>從 CellEditEnding 處理常式呼叫 DataGrid.CommitEdit 會卸除焦點

#### <a name="details"></a>詳細資料

從其中一個 <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> 的 <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=fullName> 事件處理常式呼叫 <xref:System.Windows.Controls.DataGrid.CommitEdit> 會導致 <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> 失去焦點。

#### <a name="suggestion"></a>建議

此錯誤 (bug) 在 .NET Framework 4.5.2 中已修正，因此可藉由升級 .NET Framework 來避免。 或者，您也可以在呼叫 <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName> 之後明確重新選取 <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>，來避免此 Bug。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Edge|
|版本|4.5|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType>
- <xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Controls.DataGrid.CommitEdit`
- `M:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)`

-->
