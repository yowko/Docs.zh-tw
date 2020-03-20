---
ms.openlocfilehash: 22c4b61b293ac2366cae1dc73e0f6805a4a5fb8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857241"
---
### <a name="chained-popups-with-staysopenfalse"></a>StaysOpen=False 時的鏈結快顯視窗

|   |   |
|---|---|
|詳細資料|當您按一下 StaysOpen=False 快顯視窗的外部時，該快顯視窗應該要關閉。 當兩個或多個這類快顯視窗鏈結在一起 (也就是其中一個包含另一個) 時，會發生許多問題，包括：<ul><li>開啟兩個層級，按一下 P2 外部 (但在 P1 內部)。  不會發生任何情況。</li><li>開啟兩個層級，按一下 P1 外部。  這兩個快顯視窗會關閉。</li><li>開啟及關閉兩個層級。  然後嘗試再次開啟 P2。  不會發生任何情況。</li><li>嘗試開啟三個層級。  您無法開啟。  （要麼不發生任何操作，要麼前兩個級別關閉，具體取決於按一下的位置。這些情況（和其他變體）現在按預期工作。</li></ul>|
|影響範圍|Edge|
|版本|4.7.1|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|
