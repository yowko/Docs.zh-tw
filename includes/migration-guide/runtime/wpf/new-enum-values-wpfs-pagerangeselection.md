---
ms.openlocfilehash: 61749f59f9379a6d18bb013b2612a07cb7822b3a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496895"
---
### <a name="new-enum-values-in-wpfs-pagerangeselection"></a>WPF PageRangeSelection 中的新列舉值

#### <a name="details"></a>詳細資料

兩個新成員 (<xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=fullName> 和 <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=fullName>) 已新增至 <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> 列舉。

#### <a name="suggestion"></a>建議

在大多數情況下，這些變更不會影響使用者程式碼。 不過，您應該修改與 <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> 型別的 <xref:System.Enum.GetNames(System.Type)> 或 <xref:System.Enum.GetValues(System.Type)> 呼叫中現有的特定項目數目相依的程式碼。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Edge|
|版本|4.5|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Controls.PageRangeSelection?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Windows.Controls.PageRangeSelection`

-->
