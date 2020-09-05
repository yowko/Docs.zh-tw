---
ms.openlocfilehash: 14581b193fc000c7f805a0602e191cad688c014a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496941"
---
### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a>波斯曆現在會使用回教陽曆演算法

#### <a name="details"></a>詳細資料

從 .NET Framework 4.6 開始，<xref:System.Globalization.PersianCalendar?displayProperty=fullName> 類別會使用回教陽曆演算法。 從 .NET Framework 4.6 開始，針對 1800 年以前的日期或 2023 年以後的日期 (西曆)，在 <xref:System.Globalization.PersianCalendar?displayProperty=fullName> 與其他日曆之間轉換這些日期可能會產生稍微不同的結果。此外，<xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> 現在是 <code>March 22, 0622</code>，而不是 <code>March 21, 0622</code>。

#### <a name="suggestion"></a>建議

請注意，在 .NET Framework 4.6 中使用 PersianCalendar 時，某些較早或較晚的日期可能會稍微不同。 此外，在不同 .NET Framework 版本上執行的處理序之間序列化日期，不會將日期儲存為 PersianCalendar 日期字串 (因為這些值可能不同)。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Minor|
|版本|4.6|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Globalization.PersianCalendar?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Globalization.PersianCalendar`

-->
