---
title: "建立自訂屬性 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7a24553ae4cc2186e805d76ddb37f38c0322aeac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="creating-custom-attributes-visual-basic"></a>建立自訂屬性 (Visual Basic)
您可以建立自己的自訂屬性，方法是定義屬性類別，這是直接或間接衍生自 <xref:System.Attribute> 的類別，它能快速且簡單地在中繼資料中識別屬性定義。 假設您想要用撰寫類型的程式設計人員姓名來標記類型。 您可能會定義自訂的 `Author` 屬性類別：  
  
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
  
 類別名稱是屬性的名稱，亦即 `Author`。 它衍生自 `System.Attribute`，因此它是自訂屬性類別。 建構函式的參數是自訂屬性的位置參數。 在此範例中，`name` 是位置參數。 任何公用讀寫欄位或屬性都是具名參數。 在此情況下，`version` 是唯一的具名參數。 請注意，使用了 `AttributeUsage` 屬性讓 `Author` 屬性只有對類別和 `Structure` 宣告有效。  
  
 您可以如下所示使用這個新屬性︰  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 `AttributeUsage` 有一個具名參數 `AllowMultiple`，您可以用它讓自訂屬性僅單次使用或是多次使用。 在下列程式碼範例中，建立了多次使用的屬性。  
  
```vb  
' multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
```  
  
 在下列程式碼範例中，相同類型的多個屬性會套用至類別。  
  
```vb  
<Author("P. Ackerman", Version:=1.1),   
Author("R. Koch", Version:=1.2)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
    ' R. Koch's code goes here...  
End Class  
```  
  
> [!NOTE]
>  如果您的屬性類別包含屬性，則該屬性必須是讀寫。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Reflection>  
 [Visual Basic 程式設計手冊](../../../../visual-basic/programming-guide/index.md)  
 [撰寫自訂屬性](../../../../standard/attributes/writing-custom-attributes.md)  
 [反映 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [屬性 (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)  
 [使用反映存取屬性 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
 [AttributeUsage (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
