---
title: HOW TO：判斷兩個物件是否相關 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: 2b17be4ef5a7dabfc4779ab6f5675cc2baec9c3c
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626563"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>作法：判斷兩個物件是否相關 (Visual Basic)

您可以比較兩個物件來判斷其建立所在的類別之間的關聯性 (如果有的話)。 如果指定的類別<xref:System.Type?displayProperty=nameWithType>繼承自目前的類別, 或如果目前的類型是指定類別所支援的介面, 則類別<xref:System.Type.IsInstanceOfType%2A>的方法`True`會傳回。

### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>判斷其中一個物件是否繼承自另一個物件的類別或介面

1. 在您認為可能是基底類型的物件上, <xref:System.Object.GetType%2A>叫用方法。

2. 在所<xref:System.Type?displayProperty=nameWithType>傳回的物件<xref:System.Object.GetType%2A>上, <xref:System.Type.IsInstanceOfType%2A>叫用方法。

3. 在的引數清單<xref:System.Type.IsInstanceOfType%2A>中, 指定您認為可能是衍生類型的物件。

    <xref:System.Type.IsInstanceOfType%2A>如果其引數型別繼承自<xref:System.Type?displayProperty=nameWithType>物件型別, 則傳回。 `True`

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

請注意呼叫<xref:System.Type.IsInstanceOfType%2A>中的兩個物件變數未預期的位置。 預期的基底類型是用來產生<xref:System.Type?displayProperty=nameWithType>類別, 而預期的衍生型別會當做引數傳遞<xref:System.Type.IsInstanceOfType%2A>給方法。

## <a name="see-also"></a>另請參閱

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [Object 資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [物件變數值](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [如何：判斷兩個物件是否相同](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
