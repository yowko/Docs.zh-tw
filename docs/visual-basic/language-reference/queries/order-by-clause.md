---
title: Order By 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryOrderBy
- vb.QueryAscending
- vb.QueryDescending
helpviewer_keywords:
- queries [Visual Basic], Order By
- Order By clause [Visual Basic]
- Order By statement [Visual Basic]
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
ms.openlocfilehash: 7c60156ee81618530b42d5f61dbcac6f59c4f675
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604116"
---
# <a name="order-by-clause-visual-basic"></a>Order By 子句 (Visual Basic)
指定查詢結果的排序次序。  
  
## <a name="syntax"></a>語法  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a>組件  
 `orderExp1`  
 必要。 一或多個從目前的查詢結果識別欄位如何排序傳回的值。 欄位名稱必須以逗號 （，） 分隔。 您可以識別每個欄位，為已排序，以遞增或遞減順序，使用`Ascending`或`Descending`關鍵字。 如果沒有`Ascending`或`Descending`關鍵字已指定，預設排序次序為遞增。 排序次序欄位可以從左到右的優先順序。  
  
## <a name="remarks"></a>備註  
 您可以使用`Order By`子句來排序查詢的結果。 `Order By`子句只能排序結果，根據目前範圍的範圍變數。 例如，`Select`子句會導入新範圍與新的反覆項目變數的查詢運算式中針對該領域。 範圍變數之前定義`Select`在查詢中的子句之後沒有`Select`子句。 因此，如果您想要排序您的結果來依欄位中都沒有`Select`子句，您必須將`Order By`子句之前`Select`子句。 一個範例說明時，您就必須執行這項操作，當您想要排序查詢不會傳回結果的一部分的欄位。  
  
 遞增和遞減順序的欄位取決於實作<xref:System.IComparable>欄位的資料類型的介面。 如果資料類型未實作<xref:System.IComparable>介面，在排序次序會被忽略。  
  
## <a name="example"></a>範例  
 下列查詢運算式使用`From`子句來宣告範圍變數`book`如`books`集合。 `Order By`子句依照依遞增順序 （預設值） 的價格排序查詢結果。 使用相同的價格會依標題以遞增順序排序。 `Select`子句選取`Title`和`Price`屬性作為查詢所傳回的值。  
  
 [!code-vb[VbSimpleQuerySamples#24](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_1.vb)]  
  
## <a name="example"></a>範例  
 下列查詢運算式使用`Order By`子句來排序查詢結果以遞減順序的價格。 使用相同的價格會依標題以遞增順序排序。  
  
 [!code-vb[VbSimpleQuerySamples#25](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_2.vb)]  
  
## <a name="example"></a>範例  
 下列查詢運算式使用`Select`子句來選取書名、 price、 發行日期，以及撰寫。 然後填入`Title`， `Price`， `PublishDate`，和`Author`新範圍的範圍變數的欄位。 `Order By`子句排序新的範圍變數的作者名稱、 書籍標題和價格。 每個資料行排序 （遞增） 的預設順序。  
  
 [!code-vb[VbSimpleQuerySamples#26](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_3.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [查詢](../../../visual-basic/language-reference/queries/queries.md)  
 [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
