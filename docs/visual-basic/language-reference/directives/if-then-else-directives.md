---
title: '#如果......#Else 指示詞'
ms.date: 04/11/2018
f1_keywords:
- vb.#EndIf
- '#End If'
- '#Then'
- '#ElseIf'
- vb.#ElseIf
- vb.#Else
- vb.#If
helpviewer_keywords:
- Visual Basic code, compiling
- '#If directive [Visual Basic]'
- conditional compilation [Visual Basic], directives
- '#End if directive [Visual Basic]'
- selective compiling
- else directive (#else)
- '#Else directive [Visual Basic]'
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69ce56d770de5f004f204b1764fd51d948ba92c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ifthenelse-directives"></a>#If...Then...#Else 指示詞
有條件地編譯選取的 Visual Basic 程式碼區塊。  
  
## <a name="syntax"></a>語法  
  
```  
#If expression Then  
   statements  
[ #ElseIf expression Then  
   [ statements ]  
...  
#ElseIf expression Then  
   [ statements ] ]  
[ #Else  
   [ statements ] ]  
#End If  
```  
  
## <a name="parts"></a>組件  
 `expression`  
 所需的`#If`和`#ElseIf`陳述式，指定其他位置。 任何運算式，以獨佔方式組成一或多個條件式編譯器常數、 常值和運算子，評估為`True`或`False`。  
  
 `statements`  
 所需的`#If`陳述式區塊，選擇性其他位置。 Visual Basic 程式行或如果相關聯的運算式評估為編譯的編譯器指示詞`True`。  
  
 `#End If`  
 終止`#If`陳述式區塊。  
  
## <a name="remarks"></a>備註  
 在介面中，行為`#If...Then...#Else`指示詞會出現相同的`If...Then...Else`陳述式。 不過，`#If...Then...#Else`指示詞評估由編譯器所編譯的功能而`If...Then...Else`陳述式在執行階段評估的條件。  
  
 條件式編譯通常用來編譯為不同平台相同的程式。 它也會用來防止偵錯的可執行檔中出現的程式碼。 條件式編譯期間排除的程式碼完全中會省略最後的可執行檔，所以其大小或效能上的沒有作用。  
  
 不論任何評估結果，評估所有運算式都使用`Option Compare Binary`。 `Option Compare`陳述式不會影響運算式中的`#If`和`#ElseIf`陳述式。  
  
> [!NOTE]
>  任何單一線條形式的`#If`， `#Else`， `#ElseIf`，和`#End If`存在指示詞。 沒有其他程式碼可以出現在任何指示詞的同一行。 

條件式編譯區塊內的陳述式必須是完整的邏輯陳述式。 例如，您不能有條件地編譯函式的屬性，但您可以有條件地宣告的函式，以及它的屬性：

```vb
   #If DEBUG Then
   <WebMethod()>
   Public Function SomeFunction() As String
   #Else
   <WebMethod(CacheDuration:=86400)>
   Public Function SomeFunction() As String
   #End If
```

## <a name="example"></a>範例
 這個範例會使用`#If...Then...#Else`建構函式來判斷是否要編譯某些陳述式。  
  
 [!code-vb[VbVbalrConditionalComp#1](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/if-then-else-directives_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
[#Const 指示詞](../../../visual-basic/language-reference/directives/const-directive.md)  
[If...Then...Else 陳述式](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
[條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
<xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>   


