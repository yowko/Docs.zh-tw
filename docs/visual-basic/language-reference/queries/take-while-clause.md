---
title: Take While 子句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 4b6133efdbd9c46ab85201ad454671e5538b6a81
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359576"
---
# <a name="take-while-clause-visual-basic"></a>Take While 子句 (Visual Basic)
只要指定的條件為 `true`，即包含集合中的項目，並略過其餘項目。  
  
## <a name="syntax"></a>語法  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`expression`|必要。 運算式，表示要測試元素的條件。 運算式必須傳回 `Boolean` 值或功能對等用法，例如 `Integer` 要評估為的 `Boolean` 。|  
  
## <a name="remarks"></a>備註  
 `Take While`子句包含查詢結果開頭的專案，直到提供的傳回為止 `expression` `false` 。 傳回之後 `expression` `false` ，查詢將會略過所有剩餘的元素。 `expression`會忽略其餘結果的。  
  
 `Take While`子句與子句不同之處在于 `Where` ， `Where` 子句可以用來包含符合特定條件之查詢中的所有元素。 `Take While`子句只有在第一次未滿足條件時才會包含元素。 `Take While`當您使用已排序的查詢結果時，子句最有用。  
  
## <a name="example"></a>範例  
 下列程式碼範例會使用 `Take While` 子句來抓取結果，直到找不到任何訂單的第一個客戶為止。  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [查詢](index.md)
- [Select 子句](select-clause.md)
- [From 子句](from-clause.md)
- [Take 子句](take-clause.md)
- [Skip While 子句](skip-while-clause.md)
- [Where 子句](where-clause.md)
