---
title: Take 子句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: 25dd06905525a96bc1504f033eb4f19af6d454a2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359628"
---
# <a name="take-clause-visual-basic"></a>Take 子句 (Visual Basic)
從集合開頭傳回指定數目的連續項目。  
  
## <a name="syntax"></a>語法  
  
```vb  
Take count  
```  
  
## <a name="parts"></a>組件  
 `count`  
 必要。 值或運算式，評估為要傳回之序列的專案數。  
  
## <a name="remarks"></a>備註  
 `Take`子句會使查詢在結果清單的開頭包含指定數目的連續元素。 要包含的元素數目是由 `count` 參數指定。  
  
 您可以使用 `Take` 子句搭配子句， `Skip` 從查詢的任何區段傳回資料範圍。 若要這麼做，請將範圍的第一個元素的索引傳遞至 `Skip` 子句，並將範圍的大小傳遞給 `Take` 子句。 在此情況下， `Take` 子句必須在子句之後指定 `Skip` 。  
  
 當您 `Take` 在查詢中使用子句時，您可能也需要確保以可讓 `Take` 子句包含預期結果的順序傳回結果。 如需排序查詢結果的詳細資訊，請參閱[Order By 子句](order-by-clause.md)。  
  
 您可以使用 `TakeWhile` 子句來指定只傳回特定元素，視提供的條件而定。  
  
## <a name="example"></a>範例  
 下列程式碼範例會 `Take` 搭配子句使用子句 `Skip` ，以從頁面中的查詢傳回資料。 GetCustomers 函式會使用 `Skip` 子句來略過清單中的客戶，直到提供的起始索引值，並使用 `Take` 子句來傳回從該索引值開始的客戶頁面。  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [查詢](index.md)
- [Select 子句](select-clause.md)
- [From 子句](from-clause.md)
- [Order By 子句](order-by-clause.md)
- [Take While 子句](take-while-clause.md)
- [Skip 子句](skip-clause.md)
