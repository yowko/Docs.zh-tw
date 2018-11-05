---
title: 元素作業 (C#)
ms.date: 10/03/2018
ms.assetid: 283206c9-3246-4c48-b01a-d9de409a7231
ms.openlocfilehash: dbae8c0b3d98fe9674fbbeb432c1e42763e81026
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48836773"
---
# <a name="element-operations-c"></a>元素作業 (C#)

元素作業會從序列中傳回單一特定的元素。  
  
 下節列出執行元素作業的標準查詢運算子方法。  
  
## <a name="methods"></a>方法  
  
|方法名稱|描述|C# 查詢運算式語法|更多資訊|  
|-----------------|-----------------|---------------------------------|----------------------|  
|ElementAt|傳回位於集合中指定索引處的元素。|不適用。|<xref:System.Linq.Enumerable.ElementAt%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=nameWithType>|  
|ElementAtOrDefault|傳回位於集合中指定索引處的元素；如果索引超出範圍，則傳回預設值。|不適用。|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=nameWithType>|  
|First|傳回集合中的第一個元素或符合條件的第一個元素。|不適用。|<xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.First%2A?displayProperty=nameWithType>|  
|FirstOrDefault|傳回集合中的第一個元素或符合條件的第一個元素。 如果沒有這類元素，則傳回預設值。|不適用。|<xref:System.Linq.Enumerable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%60%601%28System.Linq.IQueryable%7B%60%600%7D%29?displayProperty=nameWithType>|  
|Last|傳回集合中的最後一個元素或符合條件的最後一個元素。|不適用。|<xref:System.Linq.Enumerable.Last%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Last%2A?displayProperty=nameWithType>|  
|LastOrDefault|傳回集合中的最後一個元素或符合條件的最後一個元素。 如果沒有這類元素，則傳回預設值。|不適用。|<xref:System.Linq.Enumerable.LastOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=nameWithType>|  
|Single|傳回集合中的唯一元素或符合條件的唯一元素。 如果沒有元素可傳回，或有多個元素要傳回，則會擲回 <xref:System.InvalidOperationException>。 |不適用。|<xref:System.Linq.Enumerable.Single%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Single%2A?displayProperty=nameWithType>|  
|SingleOrDefault|傳回集合中的唯一元素或符合條件的唯一元素。 如果沒有元素可傳回，會傳回預設值。 如果有多個元素可傳回，會擲回 <xref:System.InvalidOperationException>。 |不適用。|<xref:System.Linq.Enumerable.SingleOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Linq>  
- [標準查詢運算子概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
- [如何：查詢目錄樹狀中的最大檔案 (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
