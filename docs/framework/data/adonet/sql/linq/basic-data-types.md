---
title: 基本資料類型
ms.date: 03/30/2017
ms.assetid: eca2c472-9548-4800-bd31-5d8d9f11752b
ms.openlocfilehash: ae561bad3315977ba12dd0e12abda1da163ca456
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156013"
---
# <a name="basic-data-types"></a>基本資料類型

由於 LINQ to SQL 查詢會先轉譯成 Transact-SQL，然後才能在 Microsoft SQL Server 上執行。 因此，在基本資料型別方面，LINQ to SQL 所支援的許多內建功能都與 SQL Server 相同。  
  
## <a name="casting"></a>轉型  

 如果 SQL Server 內具有與來源 CLR 型別到目標 CLR 型別之隱含或明確轉換 (Cast) 類似的有效轉換，就會啟用這類隱含或明確轉換。 如需有關 CLR 轉換的詳細資訊，請參閱 [CType 函數](../../../../../visual-basic/language-reference/functions/ctype-function.md) (Visual Basic) 和 [類型測試和轉換運算子](../../../../../csharp/language-reference/operators/type-testing-and-cast.md)。 轉換 (Conversion) 之後，轉換 (Cast) 會變更 CLR 運算式上執行的作業行為，使其符合其他會自然對應至目的型別之 CLR 運算式的行為。 在繼承對應的內容中，轉換 (Cast) 也是可以轉譯的。 物件可以轉換 (Cast) 為更特定的實體子型別，因此可以存取物件的子型別特定資料。  
  
## <a name="equality-operators"></a>相等運算子  

 LINQ to SQL 支援針對 LINQ to SQL 查詢內部的基本資料型別使用下列等號比較運算子：  
  
- 等號和不等比較運算子：數值、 <xref:System.Boolean> 、和類型支援等號和不等比較運算子 <xref:System.DateTime> <xref:System.TimeSpan> 。 如需 Visual Basic 運算子和的詳細資訊 `=` `<>` ，請參閱 [比較運算子](../../../../../visual-basic/language-reference/operators/comparison-operators.md)。 如需 c # 比較運算子和的詳細資訊 `==` `!=` ，請參閱 [相等運算子](../../../../../csharp/language-reference/operators/equality-operators.md)。
  
- Is 運算子：使用繼承對應時，`IS` 運算子具有支援的轉譯。 它可以用來判斷物件是否為特定實體型別，而且可以轉譯為鑑別子資料行上的檢查，而不需要直接測試鑑別子資料行。 如需 Visual Basic 的詳細資訊，以及 c # 為運算子，請參閱 [是運算子](../../../../../visual-basic/language-reference/operators/is-operator.md) ，而且 [是](../../../../../csharp/language-reference/operators/type-testing-and-cast.md#is-operator)。  
  
## <a name="see-also"></a>另請參閱

- [SQL-CLR 類型對應](sql-clr-type-mapping.md)
- [資料類型與函式](data-types-and-functions.md)
