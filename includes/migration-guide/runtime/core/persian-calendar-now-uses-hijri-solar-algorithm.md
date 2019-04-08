---
ms.openlocfilehash: 130c26b7d135db232eb40a2c466aa3bdb2481ace
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761316"
---
### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a>波斯曆現在會使用回教陽曆演算法

|   |   |
|---|---|
|詳細資料|從 .NET Framework 4.6 開始，<xref:System.Globalization.PersianCalendar?displayProperty=name> 類別會使用回教陽曆演算法。 從 .NET Framework 4.6 開始，針對 1800 年以前的日期或 2023 年以後的日期 (西曆)，在 <xref:System.Globalization.PersianCalendar?displayProperty=name> 與其他日曆之間轉換這些日期可能會產生稍微不同的結果。此外，<xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> 現在是 <code>March 22, 0622</code>，而不是 <code>March 21, 0622</code>。|
|建議|請注意，在 .NET Framework 4.6 中使用 PersianCalendar 時，某些較早或較晚的日期可能會稍微不同。 此外，在不同 .NET Framework 版本上執行的處理序之間序列化日期，不會將日期儲存為 PersianCalendar 日期字串 (因為這些值可能不同)。|
|範圍|次要|
|版本|4.6|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Globalization.PersianCalendar?displayProperty=nameWithType></li></ul>|

