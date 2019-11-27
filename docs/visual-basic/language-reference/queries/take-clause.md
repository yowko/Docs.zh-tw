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
ms.openlocfilehash: 3082954ef84560ccb70f7a47cd3532f622829392
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349638"
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
 `Take` 子句會使查詢在結果清單的開頭包含指定數目的連續元素。 要包含的元素數目是由 `count` 參數所指定。  
  
 您可以使用 `Take` 子句搭配 `Skip` 子句，從查詢的任何區段傳回資料範圍。 若要這麼做，請將範圍的第一個元素的索引傳遞至 `Skip` 子句，並將範圍的大小傳遞給 `Take` 子句。 在此情況下，必須在 `Skip` 子句之後指定 `Take` 子句。  
  
 當您在查詢中使用 `Take` 子句時，您可能也需要確保會以可讓 `Take` 子句包含預期結果的順序傳回結果。 如需排序查詢結果的詳細資訊，請參閱[Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md)。  
  
 視提供的條件而定，您可以使用 `TakeWhile` 子句來指定只傳回特定的元素。  
  
## <a name="example"></a>範例  
 下列程式碼範例會搭配使用 `Take` 子句與 `Skip` 子句，以從頁面中的查詢傳回資料。 GetCustomers 函式會使用 `Skip` 子句來略過清單中的客戶，直到提供的起始索引值，並使用 `Take` 子句來傳回從該索引值開始的客戶頁面。  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>請參閱

- [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [查詢](../../../visual-basic/language-reference/queries/index.md)
- [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Take While 子句](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [Skip 子句](../../../visual-basic/language-reference/queries/skip-clause.md)
