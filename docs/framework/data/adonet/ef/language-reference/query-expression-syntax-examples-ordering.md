---
title: 查詢運算式語法範例：排序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bcbc9625-7cf7-476e-85d2-058f12682f54
ms.openlocfilehash: ea9e7cb61facb880a050fbfae3aa9b07c03361fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614167"
---
# <a name="query-expression-syntax-examples-ordering"></a>查詢運算式語法範例：排序
本主題中的範例將示範如何使用`OrderBy`並`OrderByDescending`方法來查詢[AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples)透過查詢運算式語法。 這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。  
  
 本主題中的範例使用下列`using` / `Imports`陳述式：  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="orderby"></a>OrderBy  
  
### <a name="example"></a>範例  
 下列範例會使用 <xref:System.Linq.Enumerable.OrderBy%2A> 來傳回依據姓氏排序的連絡人清單。  
  
 [!code-csharp[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a>範例  
 下列範例會使用 <xref:System.Linq.Enumerable.OrderBy%2A> 來依據姓氏的長度排序連絡人清單。  
  
 [!code-csharp[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a>OrderByDescending  
  
### <a name="example"></a>範例  
 下列範例會使用 `orderby… descending`(Visual Basic 中的 `Order By … Descending`，相當於 <xref:System.Linq.Enumerable.OrderByDescending%2A> 方法)，從最高到最低排序價格清單。  
  
 [!code-csharp[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="thenby"></a>ThenBy  
  
### <a name="example"></a>範例  
 下列範例會使用 <xref:System.Linq.Queryable.OrderBy%2A> 和 <xref:System.Linq.Queryable.ThenBy%2A> 來傳回先依據姓氏再依據名字排序的連絡人清單。  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby)]
 [!code-vb[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby)]  
  
## <a name="thenbydescending"></a>ThenByDescending  
  
### <a name="example"></a>範例  
 下列範例會使用 `OrderBy… Descending` (相當於 <xref:System.Linq.Enumerable.ThenByDescending%2A> 方法) 來排序產品的清單 (先依據名稱，再依據標價，從最高到最低排序)。  
  
 [!code-csharp[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a>另請參閱

- [LINQ to Entities 中的查詢](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
