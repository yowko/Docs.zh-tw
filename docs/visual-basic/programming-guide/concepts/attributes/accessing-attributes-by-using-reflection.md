---
title: "使用反映 (Visual Basic) 存取屬性 |Microsoft 文件"
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
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4763eccc5d1a6bdf3e89c1c4d825d5ff5c6caa3e
ms.lasthandoff: 03/13/2017

---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a>使用反映 (Visual Basic) 存取屬性
您可以用來定義自訂屬性，並將它們放在原始程式碼中的事實是價值擷取資訊並加以執行的方法不大。 使用反映，您可以擷取的已定義的自訂屬性的資訊。 重要的方法是`GetCustomAttributes`，它會傳回所對應之來源的程式碼屬性的執行階段物件的陣列。 這個方法有數個多載的版本。 如需詳細資訊，請參閱<xref:System.Attribute>。</xref:System.Attribute>  
  
 屬性規格，例如︰  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 在概念上等同於此︰  
  
```vb  
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")  
anonymousAuthorObject.version = 1.1  
```  
  
 不過，程式碼將會等到執行`SampleClass`查詢的屬性。 呼叫`GetCustomAttributes`上`SampleClass`造成`Author`物件建構和初始化與以上所述。 如果類別有其他屬性，其他屬性的物件是類似的方式建構。 `GetCustomAttributes`然後傳回`Author`物件和陣列中的其他屬性物件。 然後您可以逐一查看陣列、 判斷哪些屬性已套用的每個陣列項目類型和從屬性物件擷取資訊。  
  
## <a name="example"></a>範例  
 以下是完整的範例。 定義、 套用至數個項目，並經由反映來擷取自訂屬性。  
  
```vb  
' Multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
    Private name As String  
    Public version As Double  
    Sub New(ByVal authorName As String)  
        name = authorName  
  
        ' Default value  
        version = 1.0  
    End Sub  
  
    Function GetName() As String  
        Return name  
    End Function          
End Class  
  
' Class with the Author attribute  
<Author("P. Ackerman")>   
Public Class FirstClass  
End Class  
  
' Class without the Author attribute  
Public Class SecondClass  
End Class  
  
' Class with multiple Author attributes.  
<Author("P. Ackerman"), Author("R. Koch", Version:=2.0)>   
Public Class ThirdClass  
End Class  
  
Class TestAuthorAttribute  
    Sub Main()  
        PrintAuthorInfo(GetType(FirstClass))  
        PrintAuthorInfo(GetType(SecondClass))  
        PrintAuthorInfo(GetType(ThirdClass))  
    End Sub  
  
    Private Shared Sub PrintAuthorInfo(ByVal t As System.Type)  
        System.Console.WriteLine("Author information for {0}", t)  
  
        ' Using reflection  
        Dim attrs() As System.Attribute = System.Attribute.GetCustomAttributes(t)  
  
        ' Displaying output  
        For Each attr In attrs  
            Dim a As Author = CType(attr, Author)  
            System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version)  
        Next              
    End Sub  
  
    ' Output:  
    '   Author information for FirstClass  
    '     P. Ackerman, version 1.00  
    ' Author information for SecondClass  
    ' Author information for ThirdClass  
    '  R. Koch, version 2.00  
    '  P. Ackerman, version 1.00  
  
End Class  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Reflection></xref:System.Reflection>   
 <xref:System.Attribute></xref:System.Attribute>   
 [Visual Basic 程式設計指南](../../../../visual-basic/programming-guide/index.md)   
 [擷取儲存於屬性中的資訊](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c)   
 [反映 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)   
 [屬性 (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)   
 [建立自訂屬性 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
