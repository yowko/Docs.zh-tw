---
title: "#<a name=\"const-directive\"></a>Const 指示詞"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.#Const
- '#vb.Const'
- '#Const'
helpviewer_keywords:
- '#Const directive'
- conditional compilation [Visual Basic], directives
- Const directive (#Const)
- Visual Basic compiler, compiler directives
- constants [Visual Basic], Const directive
- constants [Visual Basic], declaring
- Const statement [Visual Basic], directive (#Const)
- 'declaring constants [Visual Basic], #const directive'
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6e162b01dc5c99fb7708337d259f9e66ddd6b64
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="const-directive"></a>#Const 指示詞
適用於 Visual Basic 中定義條件式編譯器常數。  
  
## <a name="syntax"></a>語法  
  
```  
#Const constname = expression  
```  
  
## <a name="parts"></a>組件  
 `constname`  
 必要項。 所定義的常數名稱。  
  
 `expression`  
 必要項。 常值、 其他的條件式編譯器常數或包含任何或所有算術或邏輯運算子以外的任何組合`Is`。  
  
## <a name="remarks"></a>備註  
 條件式編譯器常數一定是私用，以它們出現的檔案。 您無法建立使用公用編譯器常數`#Const`指示詞; 您可以只在使用者介面或藉由建立它們`/define`編譯器選項。  
  
 您可以只使用條件式編譯器常數和常值中的`expression`。 使用標準的常數，以定義`Const`會造成錯誤。 相反地，您可以使用常數定義`#Const`條件式編譯的關鍵字。 常數也可以定義，在此情況下，它們的值為`Nothing`。  
  
## <a name="example"></a>範例  
 此範例使用 `#Const` 指示詞。  
  
 [!code-vb[VbVbalrConditionalComp#3](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/const-directive_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)  
 [#If...Then...#Else 指示詞](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)  
 [條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [If...Then...Else 陳述式](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
