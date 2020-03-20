---
ms.openlocfilehash: 946096cb9510ca12bbd2cecd00099142308b072a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "67856966"
---
### <a name="keytips-behavior-improved-in-wpf"></a>已改進 WPF 中的按鍵提示行為

|   |   |
|---|---|
|詳細資料|按鍵提示行為已經過修改，讓 Microsoft Word 與 Windows 檔案總管之間的行為趨於一致。 WPF 會藉由查看是否已啟用按鍵提示狀態，或是並非按下 <xref:System.Windows.Input.KeyEventArgs.SystemKey> (特別是 <xref:System.Windows.Input.Key> 或 <xref:System.Windows.Input.Key.F11>) 的情況，正確地處理按鍵提示的按鍵。 現在即使滑鼠已開啟了按鍵提示，其仍會關閉功能表。|
|建議|N/A|
|影響範圍|Edge|
|版本|4.7.2|
|類型|執行階段|
