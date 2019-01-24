---
title: '運算子宣告必須是其中一個: +、-，*，-、-、 ^， &amp;，喜歡，Mod、 和，Or、 Xor、 沒有，請&lt; &lt;， &gt; &gt;，=， &lt; &gt;， &lt;， &lt;=、 &gt;&gt;=、 CType、 IsTrue、 IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: f32935dd4aaccd3040655b418badc13c1988c1b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622269"
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not-ltlt-gtgt"></a>運算子宣告必須是其中一個: +、-，*，\,/、 ^， &amp;，例如，Mod、，Or、 Xor、 不是， &lt; &lt;， &gt; &gt;...
您可以宣告適用於多載的運算子。 下表列出您可以宣告的運算子。  
  
|類型|運算子|  
|----------|---------------|  
|一元|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|二元|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|轉換 (一元)|`CType`|  
  
 請注意， `=` ，二元清單中的運算子為比較運算子，而不是指派運算子。  
  
 **錯誤 ID:** BC33000  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  從一組可多載的運算子中選取運算子。  
  
2.  如果您需要多載無法直接多載之運算子的功能，請建立接受適當參數並傳回適當值的 `Function` 程序。  
  
## <a name="see-also"></a>另請參閱
- [Operator 陳述式](../../../visual-basic/language-reference/statements/operator-statement.md)
- [運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [如何：定義運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [如何：定義轉換運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)
