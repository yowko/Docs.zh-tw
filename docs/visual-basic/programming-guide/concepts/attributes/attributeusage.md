---
title: "AttributeUsage (Visual Basic) |Microsoft 文件"
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
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
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
ms.openlocfilehash: bf56f40033f9d1547d63fccd25e3c0561bb62cb1
ms.lasthandoff: 03/13/2017

---
# <a name="attributeusage-visual-basic"></a>AttributeUsage (Visual Basic)
決定如何使用自訂屬性類別。 `AttributeUsage`是可以套用自訂屬性定義，來控制如何套用新屬性的屬性。 明確地套用時，預設值看起來像這樣︰  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All,   
                   AllowMultiple:=False,   
                   Inherited:=True)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 在此範例中，`NewAttribute`類別可以套用至任何可屬性的程式碼的實體，但可以一次只能套用至每個實體。 它會由衍生類別，當套用至基底類別繼承。  
  
 `AllowMultiple`和`Inherited`引數是選擇性的因此此程式碼有相同的效果︰  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 第一個`AttributeUsage`引數必須是一個或多個元素的<xref:System.AttributeTargets>列舉型別。</xref:System.AttributeTargets> 多個目標類型可以連結搭配 OR 運算子，就像這樣︰  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>   
Class NewPropertyOrFieldAttribute  
    Inherits Attribute  
End Class  
```  
  
 如果`AllowMultiple`引數設定為`true`，則產生的屬性可以多次套用至單一實體，就像這樣︰  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=True)>   
Class MultiUseAttr  
    Inherits Attribute  
End Class  
  
<MultiUseAttr(), MultiUseAttr()>   
Class Class1  
End Class  
```  
  
 在此情況下`MultiUseAttr`因為可以重複套用`AllowMultiple`設為`true`。 顯示套用多個屬性的兩種格式都有效。  
  
 如果`Inherited`設為`false`，則衍生自類別，其屬性的類別不繼承屬性。 例如:   
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Class, Inherited:=False)>   
Class Attr1  
    Inherits Attribute  
End Class  
  
<Attr1()>   
Class BClass  
  
End Class    
  
Class DClass  
    Inherits BClass  
End Class  
```  
  
 在此情況下`Attr1`不會套用至`DClass`經由繼承。  
  
## <a name="remarks"></a>備註  
 `AttributeUsage`屬性是單次使用屬性-它無法套用一次以上至相同的類別。 `AttributeUsage`<xref:System.AttributeUsageAttribute>.</xref:System.AttributeUsageAttribute>的別名  
  
 如需詳細資訊，請參閱[存取的屬性，使用反映 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)。  
  
## <a name="example"></a>範例  
 下列範例示範的效果`Inherited`和`AllowMultiple`引數`AttributeUsage`屬性及可列舉的自訂屬性套用至類別的方式。  
  
```vb  
Imports System  
```  
  
```vb  
' Create some custom attributes:  
<AttributeUsage(System.AttributeTargets.Class, Inherited:=False)>   
Class A1  
    Inherits System.Attribute  
End Class  
  
<AttributeUsage(System.AttributeTargets.Class)>   
Class A2  
    Inherits System.Attribute  
End Class      
  
<AttributeUsage(System.AttributeTargets.Class, AllowMultiple:=True)>   
Class A3  
    Inherits System.Attribute  
End Class  
  
' Apply custom attributes to classes:  
<A1(), A2()>   
Class BaseClass  
  
End Class  
  
<A3(), A3()>   
Class DerivedClass  
    Inherits BaseClass  
End Class  
  
Public Class TestAttributeUsage  
    Sub Main()  
        Dim b As New BaseClass  
        Dim d As New DerivedClass  
        ' Display custom attributes for each class.  
        Console.WriteLine("Attributes on Base Class:")  
        Dim attrs() As Object = b.GetType().GetCustomAttributes(True)  
  
        For Each attr In attrs  
            Console.WriteLine(attr)  
        Next  
  
        Console.WriteLine("Attributes on Derived Class:")  
        attrs = d.GetType().GetCustomAttributes(True)  
        For Each attr In attrs  
            Console.WriteLine(attr)  
        Next              
    End Sub  
End Class  
```  
  
## <a name="sample-output"></a>範例輸出  
  
```  
Attributes on Base Class:  
A1  
A2  
Attributes on Derived Class:  
A3  
A3  
A2  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Attribute></xref:System.Attribute>   
 <xref:System.Reflection></xref:System.Reflection>   
 [Visual Basic 程式設計指南](../../../../visual-basic/programming-guide/index.md)   
 [屬性](https://msdn.microsoft.com/library/5x6cd29c)   
 [反映 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)   
 [屬性 (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)   
 [建立自訂屬性 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)   
 [使用反映 (Visual Basic) 存取屬性](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
