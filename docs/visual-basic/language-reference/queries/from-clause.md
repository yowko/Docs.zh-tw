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
ms.openlocfilehash: b18ef2f291e20d8a150972a980ba063377b0bc3a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839609"
---
# <a name="from-clause-visual-basic"></a>From 子句 (Visual Basic)
指定一或多個範圍變數和要查詢的集合。  
  
## <a name="syntax"></a>語法  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`element`|必要項。 A*範圍變數*用來逐一查看集合的元素。 範圍變數用來參考的每個成員`collection`逐一查看查詢如`collection`。 必須是可列舉的類型。|  
|`type`|選擇性。 `element` 的類型。 如果沒有`type`指定的型別`element`從推斷而來`collection`。|  
|`collection`|必要項。 是指要查詢的集合。 必須是可列舉的類型。|  
  
## <a name="remarks"></a>備註  
 `From`子句用來識別來源資料查詢及用來參考項目的來源集合的變數。 這些變數稱為*範圍變數*。 `From`子句是必要的查詢，除非`Aggregate`子句用來識別傳回只會彙總結果的查詢。 如需詳細資訊，請參閱 <<c0> [ 彙總子句](../../../visual-basic/language-reference/queries/aggregate-clause.md)。  
  
 您可以指定多個`From`查詢中，以識別要聯結多個集合的子句。 當指定多個集合時，他們會各自獨立地反覆或您可以將它們聯結如果它們相關。 您可以使用隱含聯結集合`Select`子句，或明確地利用`Join`或`Group Join`子句。 或者，您可以指定多個範圍變數和集合在單一`From`子句中，與每個相關的範圍變數和與其他以逗號分隔的集合。 下列程式碼範例顯示這兩種語法選項`From`子句。  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 `From`子句定義的範圍與類似查詢的範圍`For`迴圈。 因此，每個`element`查詢範圍中的範圍變數必須有唯一的名稱。 因為您可以指定多個`From`子句的查詢後續`From`子句可以參考中的範圍變數`From`子句，或它們可以參考範圍變數在過去`From`子句。 例如，下列範例顯示巢狀`From`子句中的第二個子句的集合以第一個子句中的範圍變數的屬性。  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 每個`From`子句後面可以接著以精簡查詢的其他查詢子句的任何組合。 您可以透過下列方式來精簡查詢：  
  
-   使用隱含地結合多個集合`From`並`Select`子句，或明確地利用`Join`或`Group Join`子句。  
  
-   使用`Where`子句來篩選查詢結果。  
  
-   使用排序結果`Order By`子句。  
  
-   分組類似的結果使用`Group By`子句。  
  
-   使用`Aggregate`子句來識別要評估的整個查詢結果的彙總函式。  
  
-   使用`Let`子句來引進反覆運算變數的值取決於而不是集合運算式。  
  
-   使用`Distinct`子句來略過重複的查詢結果。  
  
-   識別要傳回的結果使用的組件`Skip`， `Take`， `Skip While`，和`Take While`子句。  
  
## <a name="example"></a>範例  
 下列查詢的運算式用法`From`子句來宣告範圍變數`cust`每個`Customer`物件中`customers`集合。 `Where`子句來限制輸出給客戶，從指定的區域中使用的範圍變數。 `For Each`迴圈會顯示查詢結果中的每個客戶的公司名稱。  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a>另請參閱

- [查詢](../../../visual-basic/language-reference/queries/index.md)
- [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [For Each...Next 陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)
- [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)
- [Aggregate 子句](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Distinct 子句](../../../visual-basic/language-reference/queries/distinct-clause.md)
- [Join 子句](../../../visual-basic/language-reference/queries/join-clause.md)
- [Group Join 子句](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Let 子句](../../../visual-basic/language-reference/queries/let-clause.md)
- [Skip 子句](../../../visual-basic/language-reference/queries/skip-clause.md)
- [Take 子句](../../../visual-basic/language-reference/queries/take-clause.md)
- [Skip While 子句](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Take While 子句](../../../visual-basic/language-reference/queries/take-while-clause.md)
