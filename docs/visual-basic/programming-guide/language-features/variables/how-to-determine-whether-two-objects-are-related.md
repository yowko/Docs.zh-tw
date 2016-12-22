---
title: "How to: Determine Whether Two Objects Are Related (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "inheritance, Visual Basic objects"
  - "objects [Visual Basic], inheritance"
  - "object variables, determining relation"
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Determine Whether Two Objects Are Related (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

如果類別之間有關聯性 \(Relationship\)，您可以比較兩個物件來判斷建立物件之類別的關聯性。  如果指定的類別 \(Class\) 繼承自目前類別，或如果目前型別是指定類別支援的介面，則 <xref:System.Type?displayProperty=fullName> 類別的 <xref:System.Type.IsInstanceOfType%2A> 方法會傳回 `True`。  
  
### 若要判斷物件是否繼承自其他物件之類別或介面  
  
1.  對於您認為可能是基底型別 \(Base Type\) 的物件，請叫用 \(Invoke\) <xref:System.Object.GetType%2A> 方法。  
  
2.  對於由 <xref:System.Object.GetType%2A> 傳回的 <xref:System.Type?displayProperty=fullName> 物件，請叫用 <xref:System.Type.IsInstanceOfType%2A> 方法。  
  
3.  於 <xref:System.Type.IsInstanceOfType%2A> 的引數清單中，指定您認為可能是衍生型別 \(Derived Type\) 的物件。  
  
     <xref:System.Type.IsInstanceOfType%2A> 會傳回 `True`，前提是它的引數型別繼承自 <xref:System.Type?displayProperty=fullName> 物件型別。  
  
## 範例  
 下列範例判斷物件是否代表洐生自其他物件類別的類別：  
  
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
  
 請注意，在 <xref:System.Type.IsInstanceOfType%2A> 呼叫中，兩個物件變數的非預期位置。  假設的基底型別是用來產生 <xref:System.Type?displayProperty=fullName> 類別，而假設的衍生型別會以引數形式傳遞至 <xref:System.Type.IsInstanceOfType%2A> 方法。  
  
## 請參閱  
 <xref:System.Object.GetType%2A>   
 <xref:System.Type?displayProperty=fullName>   
 <xref:System.Type.IsInstanceOfType%2A>   
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [How to: Determine Whether Two Objects Are Identical](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)