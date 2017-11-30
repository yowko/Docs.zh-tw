---
title: "如何：判斷兩個物件是否關聯 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7824742459fca355c0043ad8ed20a26330402c05
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>如何：判斷兩個物件是否關聯 (Visual Basic)
您可以比較來決定關聯性，如果建立的類別之間的任何兩個物件。 <xref:System.Type.IsInstanceOfType%2A>方法<xref:System.Type?displayProperty=nameWithType>類別會傳回`True`如果指定的類別繼承自目前的類別，或如果目前的類型是指定類別所支援的介面。  
  
### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>若要判斷某個物件是否繼承自另一個物件的類別或介面  
  
1.  您認為在物件上可能是基底型別，會叫用<xref:System.Object.GetType%2A>方法。  
  
2.  在<xref:System.Type?displayProperty=nameWithType>所傳回物件<xref:System.Object.GetType%2A>，叫用<xref:System.Type.IsInstanceOfType%2A>方法。  
  
3.  引數清單中<xref:System.Type.IsInstanceOfType%2A>，指定您認為的物件可能的衍生型別。  
  
     <xref:System.Type.IsInstanceOfType%2A>傳回`True`如果其引數型別繼承自<xref:System.Type?displayProperty=nameWithType>物件類型。  
  
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
  
 請注意預期的呼叫中的兩個物件變數的位置<xref:System.Type.IsInstanceOfType%2A>。 正確的基底類型用來產生<xref:System.Type?displayProperty=nameWithType>類別，而應該衍生型別做為引數傳遞<xref:System.Type.IsInstanceOfType%2A>方法。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Object.GetType%2A>  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Type.IsInstanceOfType%2A>  
 [Object 資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [物件變數值](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [如何：判斷兩個物件是否相同](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
