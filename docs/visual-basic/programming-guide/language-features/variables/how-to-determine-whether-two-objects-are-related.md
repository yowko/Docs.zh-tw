---
title: HOW TO：判斷兩個物件是否關聯 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: 62c0280e3773d2e3ff15bc164d9e0e6cacb7bd4d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544584"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>HOW TO：判斷兩個物件是否關聯 (Visual Basic)
您可以比較來決定關聯性，如果有的話，建立的類別之間的兩個物件。 <xref:System.Type.IsInstanceOfType%2A>方法<xref:System.Type?displayProperty=nameWithType>類別會傳回`True`如果指定的類別繼承自目前的類別，或目前的類型是否支援指定的類別介面。  
  
### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>若要判斷一個物件是否繼承自另一個物件的類別或介面  
  
1.  您認為在物件上可能是基底型別，會叫用<xref:System.Object.GetType%2A>方法。  
  
2.  在 <xref:System.Type?displayProperty=nameWithType>所傳回的物件<xref:System.Object.GetType%2A>，叫用<xref:System.Type.IsInstanceOfType%2A>方法。  
  
3.  中的引數清單<xref:System.Type.IsInstanceOfType%2A>，指定您認為的物件可能是衍生型別。  
  
     <xref:System.Type.IsInstanceOfType%2A> 會傳回`True`如果其引數型別是繼承自<xref:System.Type?displayProperty=nameWithType>物件類型。  
  
## <a name="example"></a>範例  
 下列範例會判斷物件是否代表從另一個物件的類別衍生的類別。  
  
```  
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
  
 請注意兩個物件變數的呼叫中的非預期的放置<xref:System.Type.IsInstanceOfType%2A>。 基底型別應該用來產生<xref:System.Type?displayProperty=nameWithType>類別，而應該衍生的型別傳遞做為引數<xref:System.Type.IsInstanceOfType%2A>方法。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [Object 資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [物件變數值](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [如何：判斷兩個物件是否相同](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
