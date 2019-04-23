---
ms.openlocfilehash: a93fbbd787aa50f080337a6170cf8f56d0d24e31
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236693"
---
### <a name="concurrentqueuettrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a>ConcurrentQueue\<T>.TryPeek 可透過其 out 參數傳回錯誤的 Null

|   |   |
|---|---|
|詳細資料|在某些多執行緒案例中，<xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=name> 可能會傳回 true，但以 Null 值 (而不是查看到的正確值) 填入 out 參數。|
|建議|此問題在 .NET Framework 4.5.1 中已修正。 升級至該 Framework 將會解決問題。|
|範圍|主要|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType></li></ul>|
