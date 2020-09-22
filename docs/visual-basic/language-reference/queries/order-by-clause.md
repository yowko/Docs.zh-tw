---
title: Order By 子句
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
ms.openlocfilehash: 05fa720237f4b0185b5c07217362c99b5dbf4303
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869785"
---
# <a name="order-by-clause-visual-basic"></a>Order By 子句 (Visual Basic)

指定查詢結果的排序次序。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a>組件  

 `orderExp1`  
 必要。 目前查詢結果中的一或多個欄位，可識別如何排序傳回值。 功能變數名稱必須以逗號分隔 (，) 。 您可以使用或關鍵字，以遞增或遞減順序來識別每個 `Ascending` 欄位 `Descending` 。 如果未 `Ascending` `Descending` 指定或關鍵字，則預設排序次序為遞增。 排序次序欄位的優先順序是由左至右。  
  
## <a name="remarks"></a>備註  

 您可以使用 `Order By` 子句來排序查詢的結果。 `Order By`子句只能根據目前範圍的範圍變數來排序結果。 例如， `Select` 子句會在查詢運算式中引入新的範圍，並在該範圍內加入新的反覆運算變數。 在查詢中的子句之前定義的範圍變數 `Select` 無法在子句之後使用 `Select` 。 因此，如果您想要依子句中不提供的欄位來排序結果 `Select` ，則必須將子句放在 `Order By` `Select` 子句之前。 當您想要依未傳回為結果一部分的欄位來排序查詢時，其中一個範例就是。  
  
 欄位的遞增和遞減順序是由 <xref:System.IComparable> 欄位資料類型的介面實作為決定。 如果資料類型不會執行 <xref:System.IComparable> 介面，則會忽略排序次序。  
  
## <a name="example"></a>範例  

 下列查詢運算式使用 `From` 子句來宣告集合的範圍變數 `book` `books` 。 子句會將 `Order By` 查詢結果依價格以遞增順序排序 (預設) 。 具有相同價格的書籍會依標題以遞增順序排序。 `Select`子句會選取 `Title` 和 `Price` 屬性做為查詢所傳回的值。  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a>範例  

 下列查詢運算式會使用 `Order By` 子句，依價格的遞減順序來排序查詢結果。 具有相同價格的書籍會依標題以遞增順序排序。  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a>範例  

 下列查詢運算式使用 `Select` 子句來選取書籍標題、價格、發行日期和作者。 然後，它會 `Title` `Price` `PublishDate` `Author` 針對新的範圍填入範圍變數的、、和欄位。 `Order By`子句會依作者名稱、書籍標題和價格來排序新的範圍變數。 每個資料行都會依照預設順序排序 (遞增) 。  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [查詢](index.md)
- [Select 子句](select-clause.md)
- [From 子句](from-clause.md)
