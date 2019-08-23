---
title: '#如果 .。。Then ... #Else 指示詞 (Visual Basic)'
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
ms.openlocfilehash: 697521276e2d5a8d0a4aaae38789a21b7aa87fcb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940764"
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
 `#If` 和`#ElseIf`語句的必要, 其他地方則為選擇性。 由評估為`True`或`False`的一個或多個條件式編譯器常數、常值和運算子所組成的任何運算式。  
  
 `statements`  
 語句區塊`#If`的必要參數, 其他地方則為選擇性。 當相關聯的運算式評估為`True`時, Visual Basic 編譯的程式列或編譯器指示詞。  
  
 `#End If`  
 `#If`終止語句區塊。  
  
## <a name="remarks"></a>備註  
 在介面上, 指示`#If...Then...#Else` `If...Then...Else`詞的行為會與語句相同。 不過, `#If...Then...#Else`指示詞會評估編譯器所編譯的內容, `If...Then...Else`而語句會在執行時間評估條件。  
  
 條件式編譯通常用來針對不同的平臺編譯相同的程式。 它也可用來防止程式碼在可執行檔中出現。 在條件式編譯期間排除的程式碼會完全從最終可執行檔中省略, 因此它不會影響大小或效能。  
  
 不論任何評估的結果為何, 都會使用`Option Compare Binary`來評估所有運算式。 語句不會影響和`#ElseIf`語句中`#If`的運算式。 `Option Compare`  
  
> [!NOTE]
> 沒有`#If`、 `#Else`、 `#ElseIf`和指示詞的單行形式存在。`#End If` 任何其他程式碼都無法出現在與任何指示詞相同的行上。 

條件式編譯區塊內的語句必須是完整的邏輯語句。 例如, 您不能有條件地只編譯函式的屬性, 但您可以有條件地宣告函式及其屬性:

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
 這個範例會使用`#If...Then...#Else`結構來判斷是否要編譯特定語句。  
  
 [!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [#Const 指示詞](../../../visual-basic/language-reference/directives/const-directive.md)
- [If...Then...Else 陳述式](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
