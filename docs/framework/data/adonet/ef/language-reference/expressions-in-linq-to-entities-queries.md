---
title: LINQ to Entities 查詢中的運算式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: 0b77fc4c2a7c7df6efc9f4d8ce4001c39250ab94
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539907"
---
# <a name="expressions-in-linq-to-entities-queries"></a>LINQ to Entities 查詢中的運算式
運算式是可以評估為單一值、物件、方法或命名空間的程式碼片段。 運算式可以包含常值、方法呼叫、運算子及其運算元，或是簡單名稱。 簡單名稱可以是變數、型別成員、方法參數、命名空間或型別的名稱。 運算式可以使用運算子 (後者又可能使用其他運算式當做參數) 或方法呼叫 (它的參數又可能是其他方法呼叫)。 因此，運算式可以很簡單，也可以非常複雜。  
  
 在 LINQ to Entities 查詢中，運算式可以包含內類型所允許的任何項目<xref:System.Linq.Expressions>命名空間，包括 lambda 運算式。 可以用於 LINQ to Entities 查詢運算式都可以使用的運算式的超集來查詢[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]。  運算式所產生的查詢部分[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]所支援的作業僅限於`ObjectQuery<T>`和基礎資料來源。  
  
 在以下範例中，`Where` 子句中的比較就是個運算式：  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
>  指定語言建構，例如C# `unchecked`，LINQ to Entities 中不具任何意義。  
  
## <a name="in-this-section"></a>本節內容  
 [常數運算式](../../../../../../docs/framework/data/adonet/ef/language-reference/constant-expressions.md)  
  
 [比較運算式](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-expressions.md)  
  
 [Null 比較](../../../../../../docs/framework/data/adonet/ef/language-reference/null-comparisons.md)  
  
 [初始化運算式](../../../../../../docs/framework/data/adonet/ef/language-reference/initialization-expressions.md)  
  
 [關聯性、 導覽屬性和外部索引鍵](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)
