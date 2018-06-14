---
title: LINQ to Entities 查詢中的運算式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: f9230e9b5ac0c906652c03111b82df5147267143
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760761"
---
# <a name="expressions-in-linq-to-entities-queries"></a>LINQ to Entities 查詢中的運算式
運算式是可以評估為單一值、物件、方法或命名空間的程式碼片段。 運算式可以包含常值、方法呼叫、運算子及其運算元，或是簡單名稱。 簡單名稱可以是變數、型別成員、方法參數、命名空間或型別的名稱。 運算式可以使用運算子 (後者又可能使用其他運算式當做參數) 或方法呼叫 (它的參數又可能是其他方法呼叫)。 因此，運算式可以很簡單，也可以非常複雜。  
  
 在[!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]查詢運算式可包含任何項目內類型所允許<xref:System.Linq.Expressions>命名空間，包括 lambda 運算式。 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查詢中可以使用的運算式是可用於查詢 [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] 之運算式的超集。  針對查詢運算式[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]僅限於所支援的作業`ObjectQuery<T>`和基礎資料來源。  
  
 在以下範例中，`Where` 子句中的比較就是個運算式：  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
>  指定語言建構 (例如 C# `unchecked`) 在 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 中沒有意義。  
  
## <a name="in-this-section"></a>本節內容  
 [常數運算式](../../../../../../docs/framework/data/adonet/ef/language-reference/constant-expressions.md)  
  
 [比較運算式](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-expressions.md)  
  
 [Null 比較](../../../../../../docs/framework/data/adonet/ef/language-reference/null-comparisons.md)  
  
 [初始化運算式](../../../../../../docs/framework/data/adonet/ef/language-reference/initialization-expressions.md)  
  
 [導覽屬性](http://msdn.microsoft.com/library/41e1e6b9-8a57-467d-99d9-1857d2ca2ea5)  
  
## <a name="see-also"></a>另請參閱  
 [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)
