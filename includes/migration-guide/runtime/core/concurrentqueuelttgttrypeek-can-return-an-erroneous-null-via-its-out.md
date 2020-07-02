---
ms.openlocfilehash: 02a15f6b9c02002b60c568b9e1d871af49744092
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622048"
---
### <a name="concurrentqueuelttgttrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a>ConcurrentQueue&lt;T&gt;.TryPeek 可透過其 out 參數傳回錯誤的 Null

#### <a name="details"></a>詳細資料

在某些多執行緒案例中，<xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=fullName> 可能會傳回 true，但以 Null 值 (而不是查看到的正確值) 填入 out 參數。

#### <a name="suggestion"></a>建議

此問題在 .NET Framework 4.5.1 中已修正。 升級至該 Framework 將會解決問題。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |主要|
|版本|4.5|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType></li></ul>|
