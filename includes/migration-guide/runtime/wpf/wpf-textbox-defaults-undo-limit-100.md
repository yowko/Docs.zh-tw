---
ms.openlocfilehash: 13d3799aeede86b01aa81ce1cd69b3c4c22311ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620103"
---
### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a>WPF TextBox 的預設復原限制為 100

#### <a name="details"></a>詳細資料

在 .NET Framework 4.5 中，WPF TextBox 的預設復原限制為 100 (在 .NET Framework 4.0 中則沒有限制)

#### <a name="suggestion"></a>建議

如果 100 的復原限制太低，可以使用 <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit> 明確設定此限制

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Edge|
|版本|4.5|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
