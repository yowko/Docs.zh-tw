---
title: 以方法為基礎的查詢語法範例：項目運算子
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8438b995-bd07-4223-b22d-13adadef33fb
ms.openlocfilehash: 7add62a2792a0fc82346851b7dd835aad5082742
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397454"
---
# <a name="method-based-query-syntax-examples-element-operators"></a>以方法為基礎的查詢語法範例：項目運算子
本主題中的範例將示範如何使用<xref:System.Linq.Enumerable.First%2A>方法，利用以方法為基礎的查詢語法來查詢[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) 。 這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。  
  
 本主題中的範例會使用下列`using` / `Imports`語句：  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a>第一個  
  
### <a name="example"></a>範例  
 下列範例會使用<xref:System.Linq.Enumerable.First%2A>方法來尋找以 ' caroline ' 開頭的第一個電子郵件地址。  
  
 [!code-csharp[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstcondition_mq)]
 [!code-vb[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstcondition_mq)]  
  
## <a name="see-also"></a>另請參閱

- [LINQ to Entities 中的查詢](queries-in-linq-to-entities.md)
