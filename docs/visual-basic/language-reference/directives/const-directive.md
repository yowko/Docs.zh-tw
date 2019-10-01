---
title: '#Const 指示詞（Visual Basic）'
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
ms.openlocfilehash: 9b8d2da2158a8244b4533eb6ef49049949417216
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696859"
---
# <a name="const-directive"></a>#Const 指示詞
定義 Visual Basic 的條件式編譯器常數。  
  
## <a name="syntax"></a>語法  
  
```vb  
#Const constname = expression  
```  
  
## <a name="parts"></a>組件  
 `constname`  
 必要項。 所定義之常數的名稱。  
  
 `expression`  
 必要項。 常值、其他條件式編譯器常數，或包含任何或所有算術或邏輯運算子的任何組合，`Is` 除外。  
  
## <a name="remarks"></a>備註  
 條件式編譯器常數一律為其出現所在檔案的私用。 您無法使用 `#Const` 指示詞來建立公用編譯器常數;您只能在使用者介面中，或使用 `/define` 編譯器選項來建立它們。  
  
 您只能在 `expression` 中使用條件式編譯器常數和常值。 使用以 `Const` 定義的標準常數會造成錯誤。 相反地，您只能使用以 `#Const` 關鍵字定義的常數來進行條件式編譯。 常數也可以是未定義的，在此情況下，它們的值為 `Nothing`。  
  
## <a name="example"></a>範例  
 此範例使用 `#Const` 指示詞。  
  
 [!code-vb[VbVbalrConditionalComp#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>另請參閱

- [/define （Visual Basic）](../../../visual-basic/reference/command-line-compiler/define.md)
- [#If...Then...#Else 指示詞](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)
- [條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [If...Then...Else 陳述式](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
