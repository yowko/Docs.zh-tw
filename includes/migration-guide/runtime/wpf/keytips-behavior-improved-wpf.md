---
ms.openlocfilehash: 9659068304eb208fd6a0a753273453bc669fbc56
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621114"
---
### <a name="keytips-behavior-improved-in-wpf"></a>已改進 WPF 中的按鍵提示行為

#### <a name="details"></a>詳細資料

按鍵提示行為已經過修改，讓 Microsoft Word 與 Windows 檔案總管之間的行為趨於一致。 WPF 會藉由查看是否已啟用按鍵提示狀態，或是並非按下 <xref:System.Windows.Input.KeyEventArgs.SystemKey> (特別是 <xref:System.Windows.Input.Key> 或 <xref:System.Windows.Input.Key.F11>) 的情況，正確地處理按鍵提示的按鍵。 現在即使滑鼠已開啟了按鍵提示，其仍會關閉功能表。

#### <a name="suggestion"></a>建議

N/A

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Edge|
|版本|4.7.2|
|類型|執行階段|
