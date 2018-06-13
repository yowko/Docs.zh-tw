---
title: '#Const 指示詞'
ms.date: 07/20/2015
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
ms.openlocfilehash: a3b3318f6b44f7d1798e08195be5aeb920b61c0c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588063"
---
# <a name="const-directive"></a>#Const 指示詞
適用於 Visual Basic 中定義條件式編譯器常數。  
  
## <a name="syntax"></a>語法  
  
```  
#Const constname = expression  
```  
  
## <a name="parts"></a>組件  
 `constname`  
 必要。 所定義的常數名稱。  
  
 `expression`  
 必要。 常值、 其他的條件式編譯器常數或包含任何或所有算術或邏輯運算子以外的任何組合`Is`。  
  
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
