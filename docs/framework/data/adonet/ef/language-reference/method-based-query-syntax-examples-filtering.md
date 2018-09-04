---
title: 以方法為基礎的查詢語法範例：篩選
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e40e314c-eb30-4f44-a054-41e511e35832
ms.openlocfilehash: 45000713d0151172762fd797bad7d7736c78a620
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501566"
---
# <a name="method-based-query-syntax-examples-filtering"></a>以方法為基礎的查詢語法範例：篩選
本主題中的範例將示範如何使用`Where`並`Where…Contains`方法來查詢[AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)使用以方法為基礎的查詢語法。 請注意，其中...`Contains` 不能做為一部分[編譯查詢](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md)。  
  
 這些範例中使用的 AdventureWorks Sales Model 是根據 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。  
  
 本主題中的範例使用下列`using` / `Imports`陳述式：  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="where"></a>位置  
  
### <a name="example"></a>範例  
 下列範例會傳回所有線上訂單。  
  
 [!code-csharp[DP L2E Examples#Where1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where1_mq)]
 [!code-vb[DP L2E Examples#Where1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where1_mq)]  
  
### <a name="example"></a>範例  
 下列範例會傳回訂單數量大於 2 而小於 6 的訂單。  
  
 [!code-csharp[DP L2E Examples#Where2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where2_mq)]
 [!code-vb[DP L2E Examples#Where2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where2_mq)]  
  
### <a name="example"></a>範例  
 下列範例會傳回所有紅色的產品。  
  
 [!code-csharp[DP L2E Examples#Where3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where3_mq)]
 [!code-vb[DP L2E Examples#Where3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where3_mq)]  
  
### <a name="example"></a>範例  
 下列範例使用 `Where` 方法尋找在 2003 年 12 月 1 日之後下單的訂單，然後使用 `order.SalesOrderDetail` 導覽屬性取得每筆訂單的詳細資料。  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty_mq)]
 [!code-vb[DP L2E Examples#WhereNavProperty_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty_mq)]  
  
## <a name="wherecontains"></a>Where…Contains  
  
### <a name="example"></a>範例  
 下列範例以陣列為 `Where…Contains` 子句的一部分，尋找 `ProductModelID` 符合陣列中之值的所有產品。  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#3)]
 [!code-vb[DP L2E ArraysAndListsInQueries#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#3)]  
  
> [!NOTE]
>  您可以將 `Where…Contains`、<xref:System.Array> 或實作 <xref:System.Collections.Generic.List%601> 介面的集合 (任何類型) 當作 <xref:System.Collections.Generic.IEnumerable%601> 子句中的部分述詞來使用。 您還可以宣告並初始化 LINQ to Entities 查詢中的集合。 如需詳細資訊，請參閱下一個範例。  
  
### <a name="example"></a>範例  
 下列範例會宣告並初始化 `Where…Contains` 子句中的陣列，以尋找具有 `ProductModelID` 或 `Size` 符合陣列中之值的所有產品。  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#4)]
 [!code-vb[DP L2E ArraysAndListsInQueries#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#4)]  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to Entities 中的查詢](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
