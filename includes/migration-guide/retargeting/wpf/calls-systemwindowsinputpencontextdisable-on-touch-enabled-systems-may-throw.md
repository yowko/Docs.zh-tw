---
ms.openlocfilehash: a44458484ea09c566defeabc9b604bd55d994e93
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617524"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a>在具有觸控功能的系統上呼叫 System.Windows.Input.PenContext.Disable 可能會擲回 ArgumentException

#### <a name="details"></a>詳細資料

在某些情況下，在具有觸控功能的系統上呼叫內部 **System.Windows.Intput.PenContext.Disable** 方法，可能會擲回由於重新進入而未處理的 `T:System.ArgumentException`。

#### <a name="suggestion"></a>建議

.NET Framework 4.7 中已解決這個問題。 若要避免這個例外狀況，請升級至從 .NET Framework 4.7 開始的 .NET Framework 版本。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Edge        |
| 版本 | 4.6.1       |
| 類型    | 正在重定目標 |
