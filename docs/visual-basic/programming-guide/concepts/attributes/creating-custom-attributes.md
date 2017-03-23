---
title: "建立自訂屬性 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1aa97a591fdbdfab931a8b5e4f70ec3c00762332
ms.lasthandoff: 03/13/2017

---
# <a name="creating-custom-attributes-visual-basic"></a>建立自訂屬性 (Visual Basic)
您可以建立您自己的自訂屬性定義的屬性類別，而是直接或間接衍生自類別<xref:System.Attribute>，因此可以快速又簡單的中繼資料中的屬性定義用來識別。</xref:System.Attribute> 假設您想要撰寫此類型的程式設計人員的名稱的標記類型。 您可以定義自訂`Author`屬性類別︰  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct)>   
Public Class Author  
    Inherits System.Attribute  
    Private name As String  
    Public version As Double  
    Sub New(ByVal authorName As String)  
        name = authorName  
        version = 1.0  
    End Sub  
End Class  
```  
  
 類別名稱是屬性的名稱， `Author`。 它衍生自`System.Attribute`，因此它是自訂屬性類別。 建構函式的參數是位置參數的自訂屬性。 在此範例中，`name`是位置參數。 任何公用讀寫欄位或屬性都被具名參數。 在此情況下，`version`唯一具名參數。 請注意使用`AttributeUsage`屬性，讓`Author`屬性只有在類別上有效和`Structure`宣告。  
  
 您可以使用這個新屬性，如下所示︰  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 `AttributeUsage`具有具名的參數， `AllowMultiple`，這可以讓自訂屬性單次使用或多重與。 在下列程式碼範例中，建立多重的屬性。  
  
```vb  
' multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
```  
  
 在下列程式碼範例中，相同型別的多個屬性會套用至類別。  
  
```vb  
<Author("P. Ackerman", Version:=1.1),   
Author("R. Koch", Version:=1.2)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
    ' R. Koch's code goes here...  
End Class  
```  
  
> [!NOTE]
>  如果屬性類別包含屬性，該屬性必須是讀寫。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Reflection></xref:System.Reflection>   
 [Visual Basic 程式設計指南](../../../../visual-basic/programming-guide/index.md)   
 [撰寫自訂屬性](http://msdn.microsoft.com/library/97216f69-bde8-49fd-ac40-f18c500ef5dc)   
 [反映 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)   
 [屬性 (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)   
 [使用反映 (Visual Basic) 存取屬性](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)   
 [AttributeUsage (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
