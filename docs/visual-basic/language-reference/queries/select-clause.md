---
title: Select 子句
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySelect
helpviewer_keywords:
- Select statement [Visual Basic]
- Select clause [Visual Basic]
- queries [Visual Basic], Select
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
ms.openlocfilehash: d96423efbee075a7ad257df72471c71e38e09b63
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875747"
---
# <a name="select-clause-visual-basic"></a>Select 子句 (Visual Basic)

定義查詢的結果。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a>組件  

 `var1`  
 選擇性。 別名，可用來參考資料行運算式的結果。  
  
 `fieldName1`  
 必要。 要在查詢結果中傳回之欄位的名稱。  
  
## <a name="remarks"></a>備註  

 您可以使用 `Select` 子句來定義要從查詢傳回的結果。 這可讓您定義查詢所建立之新匿名型別的成員，或以查詢所傳回之命名類型的成員為目標。 `Select`查詢不需要子句。 如果未 `Select` 指定子句，則查詢會根據針對目前範圍所識別之範圍變數的所有成員，傳回型別。 如需詳細資訊，請參閱 [匿名型別](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)。 當查詢建立已命名的型別時，它會傳回類型的結果， <xref:System.Collections.Generic.IEnumerable%601> 其中 `T` 是所建立的型別。  
  
 `Select`子句可以參考目前範圍中的任何變數。 這包括子句中所識別的範圍變數 `From` (或 `From` 子句) 。 它也包含使用、、或子句中的別名建立的任何新變數 `Aggregate` `Let` `Group By` `Group Join` ，或查詢運算式中上一個子句中的變數 `Select` 。 `Select`子句也可以包含靜態值。 例如，下列程式碼範例會顯示查詢運算式，其中子句會將 `Select` 查詢結果定義為具有四個成員的新匿名型別： `ProductName` 、 `Price` 、 `Discount` 和 `DiscountedPrice` 。 `ProductName`和 `Price` 成員值取自在子句中定義的產品範圍變數 `From` 。 `DiscountedPrice`成員值是在子句中計算 `Let` 。 `Discount`成員是靜態值。  
  
 [!code-vb[VbSimpleQuerySamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#27)]  
  
 `Select`子句會為後續的查詢子句引進一組新的範圍變數，而先前的範圍變數不再位於範圍內。 `Select`查詢運算式中的最後一個子句會判斷查詢的傳回值。 例如，下列查詢會傳回總計超過500的每個客戶訂單的公司名稱和訂單識別碼。 第一個 `Select` 子句會識別 `Where` 子句和第二個子句的範圍變數 `Select` 。 第二個子句會將 `Select` 查詢所傳回的值識別為新的匿名型別。  
  
 [!code-vb[VbSimpleQuerySamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#28)]  
  
 如果 `Select` 子句識別要傳回的單一專案，查詢運算式會傳回該單一專案之型別的集合。 如果 `Select` 子句識別要傳回的多個專案，則查詢運算式會根據選取的專案，傳回新匿名型別的集合。 例如，下列兩個查詢會根據子句傳回兩個不同類型的集合 `Select` 。 第一個查詢會以字串形式傳回公司名稱的集合。 第二個查詢會傳回 `Customer` 以公司名稱和位址資訊填入的物件集合。  
  
 [!code-vb[VbSimpleQuerySamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#29)]  
  
## <a name="example"></a>範例  

 下列查詢運算式使用 `From` 子句來宣告集合的範圍變數 `cust` `customers` 。 `Select`子句會選取 [客戶名稱] 和 [識別碼] 值，並填入 `CompanyName` `CustomerID` 新範圍變數的和資料行。 語句會在 `For Each` 每個傳回的物件上進行迴圈，並顯示 `CompanyName` 每一筆記錄的和資料 `CustomerID` 行。  
  
 [!code-vb[VbSimpleQuerySamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#30)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [查詢](index.md)
- [From 子句](from-clause.md)
- [Where 子句](where-clause.md)
- [Order By 子句](order-by-clause.md)
- [匿名類型](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
