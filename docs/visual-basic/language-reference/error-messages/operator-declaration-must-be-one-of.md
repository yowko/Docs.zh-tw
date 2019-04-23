---
title: '運算子宣告必須是其中一個: +、-，*，-、-、 ^， &amp;，喜歡，Mod、 和，Or、 Xor、 不是，<<>>、 =、 <>、 <、 < =、 >、 > =、 CType、 IsTrue、 IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: 4283547109ec312cc4fe07a054bbb8db3bff660f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59299185"
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not--"></a>運算子宣告必須是其中一個: +、-，*，\,/、 ^， &amp;，例如，Mod、，Or、 Xor、 不是， \< \<，>>...
您可以宣告適用於多載的運算子。 下表列出您可以宣告的運算子。  
  
|類型|運算子|  
|----------|---------------|  
|一元|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|二元|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|轉換 (一元)|`CType`|  
  
 請注意， `=` ，二元清單中的運算子為比較運算子，而不是指派運算子。  
  
 **錯誤 ID:** BC33000  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 從一組可多載的運算子中選取運算子。  
  
2. 如果您需要多載無法直接多載之運算子的功能，請建立接受適當參數並傳回適當值的 `Function` 程序。  
  
## <a name="see-also"></a>另請參閱

- [Operator 陳述式](../../../visual-basic/language-reference/statements/operator-statement.md)
- [運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [如何：定義運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [如何：定義轉換運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)
