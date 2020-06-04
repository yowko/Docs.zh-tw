---
title: 如何：判斷兩個物件是否關聯
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: 30e88a21e737aa57513745899577381ed34151a2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410460"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>如何：判斷兩個物件是否關聯 (Visual Basic)

您可以比較兩個物件來判斷其建立所在的類別之間的關聯性（如果有的話）。 <xref:System.Type.IsInstanceOfType%2A> <xref:System.Type?displayProperty=nameWithType> `True` 如果指定的類別繼承自目前的類別，或如果目前的類型是指定類別所支援的介面，則類別的方法會傳回。

### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>判斷其中一個物件是否繼承自另一個物件的類別或介面

1. 在您認為可能是基底類型的物件上，叫用 <xref:System.Object.GetType%2A> 方法。

2. 在所 <xref:System.Type?displayProperty=nameWithType> 傳回的物件上，叫用 <xref:System.Object.GetType%2A> <xref:System.Type.IsInstanceOfType%2A> 方法。

3. 在的引數清單中 <xref:System.Type.IsInstanceOfType%2A> ，指定您認為可能是衍生類型的物件。

    <xref:System.Type.IsInstanceOfType%2A>`True`如果其引數型別繼承自物件型別，則傳回 <xref:System.Type?displayProperty=nameWithType> 。

## <a name="example"></a>範例
 下列範例會判斷其中一個物件是否代表衍生自另一個物件類別的類別。

```vb
Public Class baseClass
End Class
Public Class derivedClass : Inherits baseClass
End Class
Public Class testTheseClasses
    Public Sub seeIfRelated()
        Dim baseObj As Object = New baseClass()
        Dim derivedObj As Object = New derivedClass()
        Dim related As Boolean
        related = baseObj.GetType().IsInstanceOfType(derivedObj)
        MsgBox(CStr(related))
    End Sub
End Class
```

請注意呼叫中的兩個物件變數未預期的位置 <xref:System.Type.IsInstanceOfType%2A> 。 預期的基底類型是用來產生 <xref:System.Type?displayProperty=nameWithType> 類別，而預期的衍生型別會當做引數傳遞給 <xref:System.Type.IsInstanceOfType%2A> 方法。

## <a name="see-also"></a>另請參閱

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [Object Data Type](../../../language-reference/data-types/object-data-type.md)
- [物件變數](object-variables.md)
- [物件變數值](object-variable-values.md)
- [如何：判斷兩個物件是否相同](how-to-determine-whether-two-objects-are-identical.md)
