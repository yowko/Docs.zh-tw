---
title: "處理查詢運算式中的 Null 值"
description: "如何處理查詢運算式中的 Null 值。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: d16256e31b073a599504ffef6501ed34430a7694
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="handle-null-values-in-query-expressions"></a>處理查詢運算式中的 Null 值

本例示範如何處理來源集合中可能有的 Null 值。 如 <xref:System.Collections.Generic.IEnumerable%601> 的物件集合，可以包含值為 [null](../language-reference/keywords/null.md) 的元素。 如果來源集合為 Null 或包含值為 Null 的項目，而您的查詢不處理 Null 值，則當您執行查詢時會擲回 <xref:System.NullReferenceException>。  
  
## <a name="example"></a>範例

 您可以謹慎撰寫程式碼以避免發生 Null 參考例外狀況，如下例所示︰  
  
 [!code-csharp[csProgGuideLINQ#82](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]  
  
 在上例中，`where` 子句會篩選掉類別序列中的所有 Null 項目。 這項技術不影響 join 子句中的 Null 檢查。 因為 `Products.CategoryID` 是 `int?` 類型，即 `Nullable<int>` 的速記，所以具有 Null 的條件運算式在本例中可以運作。  
  
## <a name="example"></a>範例

 在 join 子句中，如果僅有一個比較索引鍵是可為 Null 的實值型別，則可以在查詢運算式中將其他的轉換成可為 Null 的型別。 在下列範例中，假設 `EmployeeID` 是包含 `int?` 類型值的資料行：  
  
 [!code-csharp[csProgGuideLINQ#83](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Nullable%601>  
 [LINQ 查詢運算式](index.md)  
 [可為 Null 的型別](../programming-guide/nullable-types/index.md)
