---
title: Take While 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: fe6ee470698504bc0434930cc9aa6de712e04254
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004682"
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
|`expression`|必要項。 運算式，表示要測試元素的條件。 運算式必須傳回 `Boolean` 值或函式對等用法，例如要評估為 `Boolean` 的 `Integer`。|  
  
## <a name="remarks"></a>備註  
 @No__t-0 子句包含查詢結果開頭的元素，直到提供的 `expression` 傳回 `false` 為止。 在 `expression` 傳回 `false` 之後，查詢將會略過所有剩餘的元素。 針對其餘的結果，會忽略 `expression`。  
  
 @No__t-0 子句與 `Where` 子句不同之處在于，@no__t 2 子句可以用來包含符合特定條件之查詢中的所有元素。 只有在第一次未滿足條件時，@no__t 0 子句才會包含元素。 當您使用已排序的查詢結果時，`Take While` 子句最有用。  
  
## <a name="example"></a>範例  
 下列程式碼範例會使用 `Take While` 子句來抓取結果，直到找不到任何訂單的第一個客戶為止。  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [查詢](../../../visual-basic/language-reference/queries/index.md)
- [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Take 子句](../../../visual-basic/language-reference/queries/take-clause.md)
- [Skip While 子句](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)
