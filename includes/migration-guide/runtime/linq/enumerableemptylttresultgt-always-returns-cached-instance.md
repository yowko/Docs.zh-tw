---
ms.openlocfilehash: 9131c91b34f4c24653dea37ea39af6be6e072287
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620031"
---
### <a name="enumerableemptylttresultgt-always-returns-cached-instance"></a>Enumerable.Empty&lt;TResult&gt; 一律會傳回快取的執行個體

#### <a name="details"></a>詳細資料

從 .NET Framework 4.5 開始，<xref:System.Linq.Enumerable.Empty%60%601> 一律會傳回快取的內部執行個體 <xref:System.Collections.Generic.IEnumerable%601>。之前，<xref:System.Linq.Enumerable.Empty%60%601> 會在呼叫 API 時快取空的 <xref:System.Collections.Generic.IEnumerable%601>，也就是說，在快速且同時呼叫 <xref:System.Linq.Enumerable.Empty%60%601> 的某些情況下，可能會針對不同的 API 呼叫傳回不同的類型執行個體。

#### <a name="suggestion"></a>建議

由於舊版行為不具決定性，因此程式碼不太可能取決於此行為。 不過，在罕見的情況下，如果空的可列舉值經比較有時必須不相等，則應該建立明確的空陣列 (<code>new T[0]</code>)，而不是使用 <xref:System.Linq.Enumerable.Empty%60%601>。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Edge|
|版本|4.5|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType></li></ul>|
