---
ms.openlocfilehash: de79182e326082786c1e0691f8888e30cd410f5d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235120"
---
### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a>WPF TextBox 的預設復原限制為 100

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.5 中，WPF TextBox 的預設復原限制為 100 (在 .NET Framework 4.0 中則沒有限制)|
|建議|如果 100 的復原限制太低，此限制可以明確設定 (使用 <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit>|
|範圍|Edge|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
