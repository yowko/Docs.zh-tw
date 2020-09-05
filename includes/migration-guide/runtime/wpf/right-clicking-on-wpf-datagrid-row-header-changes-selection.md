---
ms.openlocfilehash: e1faee846627b22b88eb888d6241d47d8ea6ea06
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497859"
---
### <a name="right-clicking-on-a-wpf-datagrid-row-header-changes-the-datagrid-selection"></a>以滑鼠右鍵按一下 WPF DataGrid 資料列標頭會變更 DataGrid 選取項目

#### <a name="details"></a>詳細資料

選取多個資料列時，若以滑鼠右鍵按一下選取的 <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> 資料列標頭，會導致 <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> 的選取項目變更為只有該資料列。

#### <a name="suggestion"></a>建議

此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Edge|
|版本|4.5|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Controls.DataGrid.%23ctor>

<!--

#### Affected APIs

- `M:System.Windows.Controls.DataGrid.#ctor`

-->
