---
ms.openlocfilehash: 0e25d5d9b545e5cb400cbf701fb13da572fadf10
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614336"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a>ETW 事件名稱不能只有 "Start" 或 "Stop" 尾碼不同

#### <a name="details"></a>詳細資料

在 .NET Framework 4.6 和4.6.1 中，執行時間會在 <xref:System.ArgumentException> 兩個 Windows 事件追蹤（ETW）事件名稱不同于 "Start" 或 "Stop" 後置詞時擲回（當一個事件名為 `LogUser` 且另一個名為時 `LogUserStart` ）。 在此情況下，執行階段無法建構事件來源，因此無法發出任何記錄。

#### <a name="suggestion"></a>建議

若要避免這個例外狀況，請確定沒有任何兩個事件名稱的差異只在於 "Start" 或 "Stop" 後置詞。從 .NET Framework 4.6.2 開始，會移除這項需求;執行時間可以區分只有 "Start" 和 "Stop" 尾碼不同的事件名稱。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Edge        |
| 版本 | 4.6         |
| 類型    | 正在重定目標 |
