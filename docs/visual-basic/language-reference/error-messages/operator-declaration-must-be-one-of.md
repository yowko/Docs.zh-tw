---
title: '運算子宣告必須為其中一個: +、-，*，-、-^， &amp;，Like、 Mod、 和，Or、 Xor、 Not、 &lt; &lt;， &gt; &gt;，=， &lt; &gt;， &lt;， &lt;=、 &gt;&gt;=、 CType、 IsTrue、 IsFalse'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 80c8358dd13105c18e73e94735a51b02d5bd22c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not-ltlt-gtgt"></a>運算子宣告必須為其中一個: +、-，*，\,/、 ^， &amp;，Like、 Mod、，Or、 Xor、 Not、 &lt; &lt;， &gt; &gt;...
您可以宣告適用於多載的運算子。 下表列出您可以宣告的運算子。  
  
|類型|運算子|  
|----------|---------------|  
|一元|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|二元|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|轉換 (一元)|`CType`|  
  
 請注意，`=`二元清單中的運算子是比較運算子，而不是指派運算子。  
  
 **錯誤 ID:** BC33000  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  從一組可多載的運算子中選取運算子。  
  
2.  如果您需要多載無法直接多載之運算子的功能，請建立接受適當參數並傳回適當值的 `Function` 程序。  
  
## <a name="see-also"></a>另請參閱  
 [Operator 陳述式](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [如何：定義運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [如何：定義轉換運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)
