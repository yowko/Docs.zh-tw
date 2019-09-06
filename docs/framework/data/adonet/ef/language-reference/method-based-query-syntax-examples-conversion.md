---
title: 以方法為基礎的查詢語法範例：轉換
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 19f66872-d5ab-49f8-969f-e53f9632a13d
ms.openlocfilehash: 5506c37ea4f313599f666014fd305a79f5cc7ffb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250240"
---
# <a name="method-based-query-syntax-examples-conversion"></a>以方法為基礎的查詢語法範例：轉換
本主題中的範例將<xref:System.Linq.Enumerable.ToArray%2A>示範如何使用、和<xref:System.Linq.Enumerable.ToDictionary%2A> <xref:System.Linq.Enumerable.ToList%2A>方法，利用以方法為基礎的查詢語法來查詢[AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) 。 這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。  
  
 本主題中的範例會使用下列`using` / `Imports`語句：  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="toarray"></a>ToArray  
  
### <a name="example"></a>範例  
 以下範例使用 <xref:System.Linq.Enumerable.ToArray%2A> 方法將序列立即評估為陣列。  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a>ToDictionary  
  
### <a name="example"></a>範例  
 下列範例會使用 <xref:System.Linq.Enumerable.ToDictionary%2A> 方法，立即將序列和相關的索引鍵運算式評估為字典。  
  
 [!code-csharp[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a>ToList  
  
### <a name="example"></a>範例  
 下列範例會使用 <xref:System.Linq.Enumerable.ToList%2A> 方法，立即將序列評估為 <xref:System.Collections.Generic.List%601>，其中 `T` 的型別為 <xref:System.Data.DataRow>。  
  
 [!code-csharp[DP L2E Examples#ToList](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#tolist)]
 [!code-vb[DP L2E Examples#ToList](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a>另請參閱

- [LINQ to Entities 中的查詢](queries-in-linq-to-entities.md)
