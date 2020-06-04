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
ms.openlocfilehash: 63f454064e88bc18f252940f3abd8e59b8900e5b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359744"
---
# <a name="order-by-clause-visual-basic"></a>Order By 子句 (Visual Basic)
指定查詢結果的排序次序。  
  
## <a name="syntax"></a>語法  
  
```vb  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a>組件  
 `orderExp1`  
 必要。 目前查詢結果中的一或多個欄位，可識別如何排序傳回的值。 功能變數名稱必須以逗號（，）分隔。 您可以使用或關鍵字，以遞增或遞減順序將每個欄位識別為排序 `Ascending` `Descending` 。 如果未 `Ascending` `Descending` 指定或關鍵字，則預設排序次序為遞增。 排序次序欄位的優先順序是由左至右。  
  
## <a name="remarks"></a>備註  
 您可以使用 `Order By` 子句來排序查詢的結果。 `Order By`子句只能根據目前範圍的範圍變數來排序結果。 例如， `Select` 子句會在查詢運算式中引進新的範圍，其中包含該範圍的新反復專案變數。 在查詢中的子句之前定義的範圍變數，在 `Select` 子句之後無法使用 `Select` 。 因此，如果您想要依據子句中無法使用的欄位來排序結果 `Select` ，則必須將子句放在 `Order By` `Select` 子句前面。 當您需要執行這項操作的其中一個範例，就是當您想要依欄位排序查詢，而不會在結果中傳回。  
  
 欄位的遞增和遞減順序是由 <xref:System.IComparable> 欄位之資料型別的介面的實作為來決定。 如果資料類型不會執行 <xref:System.IComparable> 介面，則會忽略排序次序。  
  
## <a name="example"></a>範例  
 下列查詢運算式會使用 `From` 子句來宣告集合的範圍變數 `book` `books` 。 子句會依 `Order By` 價格以遞增順序排序查詢結果（預設值）。 具有相同價格的書籍會依標題以遞增順序排序。 `Select`子句會選取 `Title` 和 `Price` 屬性做為查詢所傳回的值。  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a>範例  
 下列查詢運算式會使用 `Order By` 子句，依價格遞減的順序來排序查詢結果。 具有相同價格的書籍會依標題以遞增順序排序。  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a>範例  
 下列查詢運算式會使用 `Select` 子句來選取書籍標題、價格、發行日期和作者。 然後，它會 `Title` 填入 `Price` `PublishDate` 新範圍之範圍變數的、、和 `Author` 欄位。 `Order By`子句會依作者名稱、書名和價格來排序新的範圍變數。 每個資料行都會以預設順序排序（遞增）。  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [查詢](index.md)
- [Select 子句](select-clause.md)
- [From 子句](from-clause.md)
