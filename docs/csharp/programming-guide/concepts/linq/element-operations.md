---
title: "項目作業 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 283206c9-3246-4c48-b01a-d9de409a7231
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 0cada4f5dae6eab5511870395133c2ef67ca796e
ms.lasthandoff: 03/13/2017

---
# <a name="element-operations-c"></a>項目作業 (C#)
項目作業會從序列中傳回單一特定的項目。  
  
 下節列出執行項目作業的標準查詢運算子方法。  
  
## <a name="methods"></a>方法  
  
|方法名稱|描述|C# 查詢運算式語法|更多資訊|  
|-----------------|-----------------|---------------------------------|----------------------|  
|ElementAt|傳回位於集合中指定索引處的項目。|不適用。|<xref:System.Linq.Enumerable.ElementAt%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=fullName>|  
|ElementAtOrDefault|傳回位於集合中指定索引處的項目；如果索引超出範圍，則傳回預設值。|不適用。|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=fullName>|  
|First|傳回集合中的第一個項目或符合條件的第一個項目。|不適用。|<xref:System.Linq.Enumerable.First%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.First%2A?displayProperty=fullName>|  
|FirstOrDefault|傳回集合中的第一個項目或符合條件的第一個項目。 如果沒有這類項目，則傳回預設值。|不適用。|<xref:System.Linq.Enumerable.FirstOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%60%601%28System.Linq.IQueryable%7B%60%600%7D%29?displayProperty=fullName>|  
|最後一筆|傳回集合中的最後一個項目或符合條件的最後一個項目。|不適用。|<xref:System.Linq.Enumerable.Last%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Last%2A?displayProperty=fullName>|  
|LastOrDefault|傳回集合中的最後一個項目或符合條件的最後一個項目。 如果沒有這類項目，則傳回預設值。|不適用。|<xref:System.Linq.Enumerable.LastOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=fullName>|  
|Single|傳回集合中的唯一項目或符合條件的唯一項目。|不適用。|<xref:System.Linq.Enumerable.Single%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Single%2A?displayProperty=fullName>|  
|SingleOrDefault|傳回集合中的唯一項目或符合條件的唯一項目。 如果沒有這類項目或集合不僅僅包含一個項目，則傳回預設值。|不適用。|<xref:System.Linq.Enumerable.SingleOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=fullName>|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Linq>   
 [標準查詢運算子概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [如何：查詢目錄樹狀中的最大檔案 (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
