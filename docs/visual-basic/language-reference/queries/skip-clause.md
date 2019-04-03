---
title: Skip 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: db2d79596895505ddaa7778e831082a94c7ad44e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821097"
---
# <a name="skip-clause-visual-basic"></a>Skip 子句 (Visual Basic)
略過集合中指定數目的項目，然後傳回其餘項目。  
  
## <a name="syntax"></a>語法  
  
```  
Skip count  
```  
  
## <a name="parts"></a>組件  
 `count`  
 必要項。 值或評估運算式，以略過序列的項目數目。  
  
## <a name="remarks"></a>備註  
 `Skip`子句會使查詢，以略過的結果清單開頭的項目，並傳回其餘項目。 略過的項目數由`count`參數。  
  
 您可以使用`Skip`子句搭配`Take`子句傳回的資料範圍查詢的任何區段。 若要這樣做，請將傳遞到的範圍內的第一個元素的索引`Skip`子句和範圍的大小`Take`子句。  
  
 當您使用`Skip`查詢中的子句，您可能也需要確定結果傳回的順序，將會啟用`Skip`子句來略過所要的結果。 如需有關如何排序查詢結果的詳細資訊，請參閱 < [Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md)。  
  
 您可以使用`SkipWhile`子句來指定特定項目會忽略，根據提供的條件。  
  
## <a name="example"></a>範例  
 下列程式碼範例會使用`Skip`子句搭配`Take`子句，以從查詢頁面中傳回資料。 `GetCustomers`函式會使用`Skip`子句來略過清單中的客戶，直到提供開始索引值，並使用`Take`子句傳回的客戶，從該索引值開始的頁面。  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [查詢](../../../visual-basic/language-reference/queries/index.md)
- [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Skip While 子句](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Take 子句](../../../visual-basic/language-reference/queries/take-clause.md)
