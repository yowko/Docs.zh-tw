---
title: Optional (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
ms.openlocfilehash: 3758f17634395236abf2cd7059418bf6f8b6c062
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630929"
---
# <a name="optional-visual-basic"></a>Optional (Visual Basic)

指定在呼叫程式時, 可以省略程式引數。

## <a name="remarks"></a>備註

針對每個選擇性參數, 您必須指定常數運算式做為該參數的預設值。 如果運算式評估為 [[無](../../../visual-basic/language-reference/nothing.md)], 則會使用 value 資料類型的預設值做為參數的預設值。

如果參數清單包含選擇性參數, 則後面的每個參數也必須是選擇性的。

          `Optional` 修飾詞可用於以下內容：

- [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)

- [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)

- [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)

- [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)

> [!NOTE]
> 呼叫含有或不含選擇性參數的程式時, 您可以依位置或名稱傳遞引數。 如需詳細資訊, 請參閱[依位置和名稱傳遞引數](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)。

> [!NOTE]
> 您也可以使用多載來定義具有選擇性參數的程式。 如果您有一個選擇性參數, 您可以定義程式的兩個多載版本, 一個會接受參數, 另一個則不會。 如需詳細資訊，請參閱 [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)。

## <a name="example"></a>範例

下列範例會定義具有選擇性參數的程式。

```vb
Public Function FindMatches(ByRef values As List(Of String),
                            ByVal searchString As String,
                            Optional ByVal matchCase As Boolean = False) As List(Of String)

    Dim results As IEnumerable(Of String)

    If matchCase Then
        results = From v In values
                  Where v.Contains(searchString)
    Else
        results = From v In values
                  Where UCase(v).Contains(UCase(searchString))
    End If

    Return results.ToList()
End Function
```

## <a name="example"></a>範例

下列範例示範如何呼叫具有由位置傳遞的引數, 以及以名稱傳遞之引數的程式。 此程式有兩個選擇性參數。

[!code-vb[VbVbalrKeywords#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class8.vb#21)]

## <a name="see-also"></a>另請參閱

- [參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)
- [選擇性參數](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
