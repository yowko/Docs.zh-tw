---
title: Select 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySelect
helpviewer_keywords:
- Select statement [Visual Basic]
- Select clause [Visual Basic]
- queries [Visual Basic], Select
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
ms.openlocfilehash: 367d810c2358963bfe2f092a390443eccdc66941
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945258"
---
# <a name="select-clause-visual-basic"></a>Select 子句 (Visual Basic)
定義查詢的結果。  
  
## <a name="syntax"></a>語法  
  
```  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a>組件  
 `var1`  
 選擇性。 可用來參考的資料行運算式結果的別名。  
  
 `fieldName1`  
 必要項。 要傳回查詢結果中的欄位名稱。  
  
## <a name="remarks"></a>備註  
 您可以使用`Select`子句來定義要從查詢傳回的結果。 這可讓您定義的查詢所建立的新匿名類型成員，或目標查詢所傳回的具名型別的成員。 `Select`子句並不需要查詢。 如果沒有`Select`指定子句，查詢會傳回根據識別目前範圍的範圍變數的所有成員的類型。 如需詳細資訊，請參閱[匿名型別](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。 當查詢建立具名型別時，它會傳回類型的結果<xref:System.Collections.Generic.IEnumerable%601>其中`T`已建立的類型。  
  
 `Select`子句可以參考目前範圍中的任何變數。 這包括在中所識別的範圍變數`From`子句 (或`From`子句)。 它也包含與別名所建立的任何新變數`Aggregate`， `Let`， `Group By`，或`Group Join`子句或將舊版的變數`Select`查詢運算式中的子句。 `Select`子句也可以包含靜態值。 比方說，下列程式碼範例顯示在其中的查詢運算式`Select`子句會定義查詢結果為四個成員的新匿名類型： `ProductName`， `Price`， `Discount`，和`DiscountedPrice`。 `ProductName`並`Price`成員值會從定義於產品範圍變數`From`子句。 `DiscountedPrice`成員值會計算在`Let`子句。 `Discount`成員是靜態的值。  
  
 [!code-vb[VbSimpleQuerySamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#27)]  
  
 `Select`子句會導入一組新的範圍變數，如後續的查詢子句和前一個範圍變數已不在範圍中。 最後一個`Select`中查詢運算式子句會決定查詢的傳回值。 例如，下列查詢會傳回公司名稱和訂單總計超過 500 的每個客戶訂單識別碼。 第一個`Select`子句會識別的範圍變數`Where`子句和第二個`Select`子句。 第二個`Select`子句會識別為新的匿名型別查詢所傳回的值。  
  
 [!code-vb[VbSimpleQuerySamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#28)]  
  
 如果`Select`子句會識別要傳回的單一項目、 查詢運算式會傳回該單一項目之型別的集合。 如果`Select`子句會識別要傳回的多個項目、 查詢運算式會傳回新的匿名類型，根據選取的項目集合。 例如，下列兩個查詢會傳回為基礎的兩種不同類型的集合`Select`子句。 第一個查詢會傳回字串形式的公司名稱集合。 第二個查詢傳回的集合`Customer`填入的公司名稱和位址資訊的物件。  
  
 [!code-vb[VbSimpleQuerySamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#29)]  
  
## <a name="example"></a>範例  
 下列查詢的運算式用法`From`子句來宣告範圍變數`cust`如`customers`集合。 `Select`子句選取的客戶名稱和識別碼值，並於其中填入`CompanyName`和`CustomerID`新範圍變數的資料行。 `For Each`陳述式傳回的每個物件執行迴圈，並顯示`CompanyName`和`CustomerID`每一筆記錄的資料行。  
  
 [!code-vb[VbSimpleQuerySamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#30)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [查詢](../../../visual-basic/language-reference/queries/index.md)
- [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)
- [Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
