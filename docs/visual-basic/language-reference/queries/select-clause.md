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
ms.openlocfilehash: 087472c51d203be083fea0d39ade6f12066cfcb4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004744"
---
# <a name="select-clause-visual-basic"></a>Select 子句 (Visual Basic)
定義查詢的結果。  
  
## <a name="syntax"></a>語法  
  
```vb  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a>組件  
 `var1`  
 選擇性。 可以用來參考資料行運算式結果的別名。  
  
 `fieldName1`  
 必要項。 要在查詢結果中傳回之欄位的名稱。  
  
## <a name="remarks"></a>備註  
 您可以使用 `Select` 子句來定義要從查詢傳回的結果。 這可讓您定義由查詢所建立之新匿名型別的成員，或是以查詢所傳回之命名型別的成員為目標。 查詢不需要 `Select` 子句。 如果未指定任何 `Select` 子句，則查詢會根據目前範圍所識別之範圍變數的所有成員，傳回型別。 如需詳細資訊，請參閱[匿名型別](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。 當查詢建立名為的型別時，它會傳回型別為 <xref:System.Collections.Generic.IEnumerable%601> 的結果，其中 `T` 是所建立的型別。  
  
 @No__t-0 子句可以參考目前範圍中的任何變數。 這包括在 `From` 子句（或 `From` 子句）中識別的範圍變數。 它也包含以 `Aggregate`、`Let`、`Group By` 或 `Group Join` 子句的別名建立的新變數，或查詢運算式中先前 `Select` 子句的變數。 @No__t-0 子句也可以包含靜態值。 例如，下列程式碼範例顯示一個查詢運算式，其中 `Select` 子句會將查詢結果定義為具有四個成員的新匿名型別： `ProductName`、`Price`、`Discount` 和 `DiscountedPrice`。 @No__t-0 和 @no__t 1 成員值取自在 `From` 子句中定義的產品範圍變數。 在 `Let` 子句中，會計算 @no__t 0 的成員值。 @No__t 0 成員是靜態值。  
  
 [!code-vb[VbSimpleQuerySamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#27)]  
  
 @No__t-0 子句為後續的查詢子句導入了一組新的範圍變數，而先前的範圍變數已不再在範圍內。 查詢運算式中的最後一個 `Select` 子句會決定查詢的傳回值。 例如，下列查詢會傳回總計超過500的每個客戶訂單的公司名稱和訂單識別碼。 第一個 `Select` 子句會識別 `Where` 子句和第二個 `Select` 子句的範圍變數。 第二個 `Select` 子句會將查詢所傳回的值識別為新的匿名型別。  
  
 [!code-vb[VbSimpleQuerySamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#28)]  
  
 如果 `Select` 子句識別要傳回的單一專案，則查詢運算式會傳回該單一專案之類型的集合。 如果 `Select` 子句識別要傳回的多個專案，則查詢運算式會根據選取的專案，傳回新匿名型別的集合。 例如，下列兩個查詢會根據 `Select` 子句傳回兩個不同類型的集合。 第一個查詢會以字串形式傳回公司名稱的集合。 第二個查詢會傳回以公司名稱和位址資訊填入之 @no__t 0 物件的集合。  
  
 [!code-vb[VbSimpleQuerySamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#29)]  
  
## <a name="example"></a>範例  
 下列查詢運算式會使用 `From` 子句，針對 @no__t 2 集合宣告範圍變數 `cust`。 @No__t-0 子句會選取 [客戶名稱] 和 [識別碼] 值，並填入新範圍變數的 `CompanyName` 和 @no__t 2 資料行。 @No__t-0 語句會在每個傳回的物件上迴圈，並顯示每一筆記錄的 `CompanyName` 和 @no__t 2 資料行。  
  
 [!code-vb[VbSimpleQuerySamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#30)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [查詢](../../../visual-basic/language-reference/queries/index.md)
- [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)
- [Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
