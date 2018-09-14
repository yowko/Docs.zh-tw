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
ms.openlocfilehash: d4abb5f0b75ae4069c1dbe695a5c810b1f7aa6e1
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45558008"
---
# <a name="order-by-clause-visual-basic"></a>Order By 子句 (Visual Basic)
指定查詢結果的排序次序。  
  
## <a name="syntax"></a>語法  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a>組件  
 `orderExp1`  
 必要。 一或多個欄位從目前的查詢結果，找出如何排序傳回的值。 欄位名稱必須以逗號 （，） 分隔。 您可以識別每個欄位，因為依照遞增或遞減順序，使用`Ascending`或`Descending`關鍵字。 如果沒有`Ascending`或`Descending`關鍵字指定，則預設排序順序為遞增。 排序次序欄位可以從左到右的優先順序。  
  
## <a name="remarks"></a>備註  
 您可以使用`Order By`子句來排序查詢的結果。 `Order By`子句只能排序結果，根據目前的範圍的範圍變數。 比方說，`Select`子句會導入該範圍與新的反覆項目變數的查詢運算式中的新範圍。 範圍之前定義的變數`Select`查詢中的子句之後沒有`Select`子句。 因此，如果您想要排序的欄位，不適用於您結果`Select`子句中，您必須在放置`Order By`子句之前`Select`子句。 一個您想要排序您的查詢不會傳回為結果一部分的欄位時，當您必須執行這項操作的範例。  
  
 遞增和遞減順序，欄位是由決定藉由實作<xref:System.IComparable>欄位的資料類型的介面。 如果資料類型未實作<xref:System.IComparable>介面，排序次序會被忽略。  
  
## <a name="example"></a>範例  
 下列查詢的運算式用法`From`子句來宣告範圍變數`book`如`books`集合。 `Order By`子句排序查詢結果，以遞增順序 （預設值） 的定價。 活頁簿相同的價格會依標題，依遞增順序排序。 `Select`子句選取`Title`和`Price`查詢所傳回的值的屬性。  
  
 [!code-vb[VbSimpleQuerySamples#24](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_1.vb)]  
  
## <a name="example"></a>範例  
 下列查詢運算式使用`Order By`子句來排序查詢結果以遞減順序的價格。 活頁簿相同的價格會依標題，依遞增順序排序。  
  
 [!code-vb[VbSimpleQuerySamples#25](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_2.vb)]  
  
## <a name="example"></a>範例  
 下列查詢運算式使用`Select`選取的書籍標題、 價格、 發行日期，以及撰寫的子句。 它接著會填入`Title`， `Price`， `PublishDate`，和`Author`新範圍的範圍變數的欄位。 `Order By`子句排序新的範圍變數的作者名稱、 書名和價格。 每個資料行排序 （遞增） 的預設順序。  
  
 [!code-vb[VbSimpleQuerySamples#26](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_3.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [查詢](../../../visual-basic/language-reference/queries/index.md)  
 [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
