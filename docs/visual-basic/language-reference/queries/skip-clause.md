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
ms.openlocfilehash: e52de186e1475bfabd02821a0cd2384d8350eed3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004774"
---
# <a name="skip-clause-visual-basic"></a>Skip 子句 (Visual Basic)
略過集合中指定數目的項目，然後傳回其餘項目。  
  
## <a name="syntax"></a>語法  
  
```vb  
Skip count  
```  
  
## <a name="parts"></a>組件  
 `count`  
 必要項。 值或運算式，評估為要略過的序列元素數目。  
  
## <a name="remarks"></a>備註  
 @No__t 0 子句會使查詢略過結果清單開頭的專案，並傳回剩餘的元素。 要略過的元素數目是由 `count` 參數所識別。  
  
 您可以使用 `Skip` 子句搭配 `Take` 子句，從查詢的任何區段傳回資料範圍。 若要這麼做，請將範圍的第一個元素的索引傳遞至 `Skip` 子句，並將範圍的大小傳遞給 `Take` 子句。  
  
 當您在查詢中使用 `Skip` 子句時，您可能也需要確保會以可讓 @no__t 1 子句略過預期結果的順序傳回結果。 如需排序查詢結果的詳細資訊，請參閱[Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md)。  
  
 視提供的條件而定，您可以使用 `SkipWhile` 子句來指定只忽略特定元素。  
  
## <a name="example"></a>範例  
 下列程式碼範例會使用 `Skip` 子句搭配 `Take` 子句，以從頁面中的查詢傳回資料。 @No__t-0 函式會使用 `Skip` 子句來略過清單中的客戶，直到提供的起始索引值，並使用 `Take` 子句來傳回從該索引值開始的客戶頁面。  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [查詢](../../../visual-basic/language-reference/queries/index.md)
- [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Skip While 子句](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Take 子句](../../../visual-basic/language-reference/queries/take-clause.md)
