---
ms.openlocfilehash: d0de1a262d57c67dd4dfb258d5ac013af5d8783d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617144"
---
### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a>WPF TextBox.Text 可能與資料繫結不同步

#### <a name="details"></a>詳細資料

在某些情況下，如果屬性在資料繫結寫入作業期間經過修改，<xref:System.Windows.Controls.TextBox.Text> 屬性會反映資料繫結屬性值先前的值。

#### <a name="suggestion"></a>建議

這應該不會產生負面影響。 不過，您可以藉由將 <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> 屬性設為 `false` 還原舊有行為。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Edge        |
| 版本 | 4.5         |
|類型|正在重定目標

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType>
