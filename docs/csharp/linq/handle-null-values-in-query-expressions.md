---
title: 處理查詢運算式中的 Null 值 (C# 中的 LINQ)
description: 了解如何處理 C# 之 LINQ 查詢運算式中的 Null 值。
ms.date: 12/01/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: 3da490b72bd518df7be8c14b34655af8c6f84929
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249301"
---
# <a name="handle-null-values-in-query-expressions"></a>處理查詢運算式中的 Null 值

本例示範如何處理來源集合中可能有的 Null 值。 如 <xref:System.Collections.Generic.IEnumerable%601> 的物件集合，可以包含值為 [null](../language-reference/keywords/null.md) 的元素。 如果來源集合為 Null 或包含值為 Null 的項目，而您的查詢不處理 Null 值，則當您執行查詢時會擲回 <xref:System.NullReferenceException>。

## <a name="example"></a>範例

您可以謹慎撰寫程式碼以避免發生 Null 參考例外狀況，如下例所示︰

[!code-csharp[csProgGuideLINQ#82](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]

在上例中，`where` 子句會篩選掉類別序列中的所有 Null 項目。 這項技術不影響 join 子句中的 Null 檢查。 因為 `Products.CategoryID` 是 `int?` 類型，即 `Nullable<int>` 的速記，所以具有 Null 的條件運算式在本例中可以運作。

## <a name="example"></a>範例

在 join 子句中，如果只有一個比較鍵是空數值型別，則可以將另一個鍵轉換為查詢運算式中的空數值型別。 在下列範例中，假設 `EmployeeID` 是包含 `int?` 類型值的資料行：

[!code-csharp[csProgGuideLINQ#83](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]

## <a name="see-also"></a>另請參閱

- <xref:System.Nullable%601>
- [語言綜合查詢（LINQ）](index.md)
- [可為 Null 的實值類型](../language-reference/builtin-types/nullable-value-types.md)
