---
ms.openlocfilehash: 9d960774161fc44810f90ca30f56eb98f98de3ff
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496181"
---
### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a>WPF TextBox 的預設復原限制為 100

#### <a name="details"></a>詳細資料

在 .NET Framework 4.5 中，WPF TextBox 的預設復原限制為 100 (在 .NET Framework 4.0 中則沒有限制)

#### <a name="suggestion"></a>建議

如果 100 的復原限制太低，可以使用 <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit> 明確設定此限制

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Edge|
|版本|4.5|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Windows.Controls.TextBox`

-->
