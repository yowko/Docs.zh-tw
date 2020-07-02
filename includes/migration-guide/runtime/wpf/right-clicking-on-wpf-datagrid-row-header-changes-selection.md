---
ms.openlocfilehash: 6d804dd335cb18d5febc2ca5f794af92963bece1
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620107"
---
### <a name="right-clicking-on-a-wpf-datagrid-row-header-changes-the-datagrid-selection"></a>以滑鼠右鍵按一下 WPF DataGrid 資料列標頭會變更 DataGrid 選取項目

#### <a name="details"></a>詳細資料

選取多個資料列時，若以滑鼠右鍵按一下選取的 <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> 資料列標頭，會導致 <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> 的選取項目變更為只有該資料列。

#### <a name="suggestion"></a>建議

此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Edge|
|版本|4.5|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Windows.Controls.DataGrid.%23ctor></li></ul>|
