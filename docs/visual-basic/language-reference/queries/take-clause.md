---
title: Take 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: bdd12340c5a0bd522c09a22e74c7b4f487cc5821
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626728"
---
# <a name="take-clause-visual-basic"></a>Take 子句 (Visual Basic)
從集合開頭傳回指定數目的連續項目。  
  
## <a name="syntax"></a>語法  
  
```  
Take count  
```  
  
## <a name="parts"></a>組件  
 `count`  
 必要項。 值或運算式評估為要傳回之序列的項目數。  
  
## <a name="remarks"></a>備註  
 `Take`子句會使查詢包含指定的數目的連續項目，從結果清單的開頭。 指定要包含的項目數`count`參數。  
  
 您可以使用`Take`子句搭配`Skip`子句傳回的資料範圍查詢的任何區段。 若要這樣做，請將傳遞到的範圍內的第一個元素的索引`Skip`子句和範圍的大小`Take`子句。 在此情況下，`Take`之後，必須指定子句`Skip`子句。  
  
 當您使用`Take`查詢中的子句，您可能也需要確定結果傳回的順序，將會啟用`Take`子句，以包含所要的結果。 如需有關如何排序查詢結果的詳細資訊，請參閱 < [Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md)。  
  
 您可以使用`TakeWhile`子句來指定傳回特定項目，根據提供的條件。  
  
## <a name="example"></a>範例  
 下列程式碼範例會使用`Take`子句搭配`Skip`子句，以從查詢頁面中傳回資料。 GetCustomers 函式會使用`Skip`子句來略過清單中的客戶，直到提供開始索引值，並使用`Take`子句傳回的客戶，從該索引值開始的頁面。  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-clause_1.vb)]  
  
## <a name="see-also"></a>另請參閱
- [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [查詢](../../../visual-basic/language-reference/queries/index.md)
- [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Take While 子句](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [Skip 子句](../../../visual-basic/language-reference/queries/skip-clause.md)
