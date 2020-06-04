---
title: '#If...Then...#Else 指示詞'
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
ms.openlocfilehash: 7054a6ada4583c5d89e020437eb622a59d3eb17a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410006"
---
# <a name="ifthenelse-directives"></a>#If...Then...#Else 指示詞

有條件地編譯選取的 Visual Basic 程式碼區塊。

## <a name="syntax"></a>語法

```vb
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
`#If`和語句的必要 `#ElseIf` ，其他地方則為選擇性。 由評估為或的一個或多個條件式編譯器常數、常值和運算子所組成的任何運算式 `True` `False` 。

`statements`  
`#If`語句區塊的必要參數，其他地方則為選擇性。 當相關聯的運算式評估為時，Visual Basic 編譯的程式列或編譯器指示詞 `True` 。

`#End If`  
終止 `#If` 語句區塊。

## <a name="remarks"></a>備註

在介面上，指示詞的行為 `#If...Then...#Else` 會與 `If...Then...Else` 語句相同。 不過，指示詞 `#If...Then...#Else` 會評估編譯器所編譯的內容，而 `If...Then...Else` 語句會在執行時間評估條件。

條件式編譯通常用來針對不同的平臺編譯相同的程式。 它也可用來防止程式碼在可執行檔中出現。 在條件式編譯期間排除的程式碼會完全從最終可執行檔中省略，因此它不會影響大小或效能。

不論任何評估的結果為何，都會使用來評估所有運算式 `Option Compare Binary` 。 `Option Compare`語句不會影響和語句中的運算式 `#If` `#ElseIf` 。

> [!NOTE]
> 沒有、、和指示詞的單行形式 `#If` `#Else` `#ElseIf` `#End If` 存在。 任何其他程式碼都無法出現在與任何指示詞相同的行上。

條件式編譯區塊內的語句必須是完整的邏輯語句。 例如，您不能有條件地只編譯函式的屬性，但您可以有條件地宣告函式及其屬性：

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

這個範例會使用 `#If...Then...#Else` 結構來判斷是否要編譯特定語句。

[!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]

## <a name="see-also"></a>另請參閱

- [#Const 指示詞](const-directive.md)
- [If...Then...Else 陳述式](../statements/if-then-else-statement.md)
- [條件式編譯](../../programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
