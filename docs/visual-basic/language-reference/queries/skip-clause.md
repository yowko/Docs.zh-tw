---
title: Skip 子句
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: 40e89160baf663f7d6785e5d3e09ad6cc4eefbde
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866310"
---
# <a name="skip-clause-visual-basic"></a>Skip 子句 (Visual Basic)

略過集合中指定數目的項目，然後傳回其餘項目。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Skip count  
```  
  
## <a name="parts"></a>組件  

 `count`  
 必要。 值或運算式，評估為要跳過之序列的專案數。  
  
## <a name="remarks"></a>備註  

 `Skip`子句會讓查詢略過結果清單開頭的專案，並傳回其餘的元素。 要跳過的元素數目是由參數所識別 `count` 。  
  
 您可以使用 `Skip` 子句搭配 `Take` 子句，從查詢的任何區段傳回資料範圍。 若要這樣做，請將範圍第一個元素的索引傳遞給子句，並將範圍的大小傳遞給 `Skip` `Take` 子句。  
  
 當您 `Skip` 在查詢中使用子句時，您可能也需要確保結果會以可讓 `Skip` 子句略過預期結果的順序傳回。 如需排序查詢結果的詳細資訊，請參閱 [Order By 子句](order-by-clause.md)。  
  
 您可以使用 `SkipWhile` 子句來指定根據提供的條件，只忽略特定的元素。  
  
## <a name="example"></a>範例  

 下列程式碼範例會將 `Skip` 子句和子句一起使用， `Take` 以從頁面中的查詢傳回資料。 `GetCustomers`函數會使用 `Skip` 子句來略過清單中的客戶，直到提供的起始索引值為止，並使用 `Take` 子句傳回從該索引值開始之客戶的頁面。  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [查詢](index.md)
- [Select 子句](select-clause.md)
- [From 子句](from-clause.md)
- [Order By 子句](order-by-clause.md)
- [Skip While 子句](skip-while-clause.md)
- [Take 子句](take-clause.md)
