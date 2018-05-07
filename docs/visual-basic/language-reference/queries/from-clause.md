---
title: From 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
ms.openlocfilehash: 1f113444efae83de7d299db330593937c7800bb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="from-clause-visual-basic"></a>From 子句 (Visual Basic)
指定一或多個範圍變數以及要查詢的集合。  
  
## <a name="syntax"></a>語法  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`element`|必要。 A*範圍變數*用來逐一查看集合的元素。 範圍變數用來參考的每個成員`collection`如逐一查看查詢`collection`。 必須是可列舉的類型。|  
|`type`|選擇性。 `element` 的類型。 如果沒有`type`指定的型別`element`推斷從`collection`。|  
|`collection`|必要。 是指要查詢的集合。 必須是可列舉的類型。|  
  
## <a name="remarks"></a>備註  
 `From`子句用來識別來源資料查詢，包括用來參考項目的來源集合的變數。 這些變數稱為*範圍變數*。 `From`子句是必要的查詢，除非`Aggregate`子句用來識別傳回只會彙總結果的查詢。 如需詳細資訊，請參閱[Aggregate 子句](../../../visual-basic/language-reference/queries/aggregate-clause.md)。  
  
 您可以指定多個`From`查詢中，以識別要加入多個集合的子句。 當指定多個集合時，它們各自獨立地重複處理，或您可以將其聯結如果它們相關。 使用隱含聯結集合`Select`子句，或明確地使用`Join`或`Group Join`子句。 或者，您可以指定多個範圍變數和集合中單一`From`子句，具有每個相關的範圍變數以及與其他以逗號分隔的集合。 下列程式碼範例顯示兩個語法選項`From`子句。  
  
 [!code-vb[VbSimpleQuerySamples#21](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_1.vb)]  
  
 `From`子句定義的範圍內的類似查詢的範圍`For`迴圈。 因此，每個`element`查詢範圍中的範圍變數必須有唯一的名稱。 因為您可以指定多個`From`子句的查詢時，後續`From`子句可以參考中的範圍變數`From`子句，或者也可以參考的範圍變數中前一個`From`子句。 例如，下列範例顯示巢狀`From`子句，其中第二個子句中的集合根據第一個子句中的範圍變數的屬性。  
  
 [!code-vb[VbSimpleQuerySamples#22](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_2.vb)]  
  
 每個`From`子句後面可以接著以精簡查詢的其他查詢子句的任何組合。 您可以下列方式來縮小查詢：  
  
-   使用隱含結合多個集合`From`和`Select`子句，或明確地使用`Join`或`Group Join`子句。  
  
-   使用`Where`子句來篩選查詢結果。  
  
-   使用排序結果`Order By`子句。  
  
-   利用群組類似的結果`Group By`子句。  
  
-   使用`Aggregate`子句，以識別要評估的整個查詢結果的彙總函式。  
  
-   使用`Let`引入反覆運算變數的值取決於運算式而不是集合的子句。  
  
-   使用`Distinct`子句來略過重複的查詢結果。  
  
-   使用傳回的結果的部分識別為`Skip`， `Take`， `Skip While`，和`Take While`子句。  
  
## <a name="example"></a>範例  
 下列查詢運算式使用`From`子句來宣告範圍變數`cust`每個`Customer`物件存放至`customers`集合。 `Where`子句來限制輸出給客戶，從指定的地區中使用的範圍變數。 `For Each`迴圈會顯示查詢結果中的每個客戶的公司名稱。  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_3.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [查詢](../../../visual-basic/language-reference/queries/queries.md)  
 [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [For Each...Next 陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)  
 [Aggregate 子句](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Distinct 子句](../../../visual-basic/language-reference/queries/distinct-clause.md)  
 [Join 子句](../../../visual-basic/language-reference/queries/join-clause.md)  
 [Group Join 子句](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Let 子句](../../../visual-basic/language-reference/queries/let-clause.md)  
 [Skip 子句](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [Take 子句](../../../visual-basic/language-reference/queries/take-clause.md)  
 [Skip While 子句](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Take While 子句](../../../visual-basic/language-reference/queries/take-while-clause.md)
