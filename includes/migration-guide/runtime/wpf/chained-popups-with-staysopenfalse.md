---
ms.openlocfilehash: 171b7a3a962f8259e64b88f1ae893e649b5f24bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621107"
---
### <a name="chained-popups-with-staysopenfalse"></a>StaysOpen=False 時的鏈結快顯視窗

#### <a name="details"></a>詳細資料

當您按一下 StaysOpen=False 快顯視窗的外部時，該快顯視窗應該要關閉。 當兩個或多個這類快顯視窗鏈結在一起 (也就是其中一個包含另一個) 時，會發生許多問題，包括：<ul><li>開啟兩個層級，按一下 P2 外部 (但在 P1 內部)。  不會發生任何情況。</li><li>開啟兩個層級，按一下 P1 外部。  這兩個快顯視窗會關閉。</li><li>開啟及關閉兩個層級。  然後嘗試再次開啟 P2。  不會發生任何情況。</li><li>嘗試開啟三個層級。  您無法。  （視您按一下的位置而定，不會發生任何事，或前兩個層級關閉）。這些案例（和其他變異）現在會如預期般運作。</li></ul>

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Edge|
|版本|4.7.1|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|
