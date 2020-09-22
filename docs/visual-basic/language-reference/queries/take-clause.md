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
ms.openlocfilehash: f2377d8d1635912885a310b2b0429a6a00083b47
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869676"
---
# <a name="take-clause-visual-basic"></a>Take 子句 (Visual Basic)

從集合開頭傳回指定數目的連續項目。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Take count  
```  
  
## <a name="parts"></a>組件  

 `count`  
 必要。 值或運算式，這個值會評估為要傳回之序列的元素數。  
  
## <a name="remarks"></a>備註  

 `Take`子句會讓查詢從結果清單的開頭包含指定數目的連續元素。 要包含的元素數目是由參數所指定 `count` 。  
  
 您可以使用 `Take` 子句搭配 `Skip` 子句，從查詢的任何區段傳回資料範圍。 若要這樣做，請將範圍第一個元素的索引傳遞給子句，並將範圍的大小傳遞給 `Skip` `Take` 子句。 在此情況下， `Take` 子句必須在子句之後指定 `Skip` 。  
  
 當您 `Take` 在查詢中使用子句時，您可能也需要確保結果會以可讓 `Take` 子句包含所需結果的順序傳回。 如需排序查詢結果的詳細資訊，請參閱 [Order By 子句](order-by-clause.md)。  
  
 您可以使用 `TakeWhile` 子句來指定只傳回特定的元素，視提供的條件而定。  
  
## <a name="example"></a>範例  

 下列程式碼範例會將 `Take` 子句和子句一起使用， `Skip` 以從頁面中的查詢傳回資料。 GetCustomers 函式會使用 `Skip` 子句來略過清單中的客戶，直到提供的起始索引值為止，並使用 `Take` 子句傳回從該索引值開始之客戶的頁面。  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [查詢](index.md)
- [Select 子句](select-clause.md)
- [From 子句](from-clause.md)
- [Order By 子句](order-by-clause.md)
- [Take While 子句](take-while-clause.md)
- [Skip 子句](skip-clause.md)
