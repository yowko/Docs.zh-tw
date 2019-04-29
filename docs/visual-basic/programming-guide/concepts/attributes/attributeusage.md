---
title: AttributeUsage (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
ms.openlocfilehash: 1841171f2f3fc26ba9244c72c69960b765d39807
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789112"
---
# <a name="attributeusage-visual-basic"></a>AttributeUsage (Visual Basic)
決定如何使用自訂屬性類別。 `AttributeUsage` 是一個屬性，可套用至自訂屬性定義來控制如何套用新屬性。 明確套用時，預設設定看起來會像這樣︰  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All,   
                   AllowMultiple:=False,   
                   Inherited:=True)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 在此範例中，`NewAttribute` 類別可以套用至任何可屬性化的程式碼實體，但只能對每個實體套用一次。 當套用至基底類別時，其由衍生類別所繼承。  
  
 `AllowMultiple` 和 `Inherited` 是選擇性引數，因此這個程式碼具有相同的效果︰  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 第一個 `AttributeUsage` 引數必須是 <xref:System.AttributeTargets> 列舉的一或多個元素。 您可以使用 OR 運算子來連結多個目標類型，與下面類似：  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>   
Class NewPropertyOrFieldAttribute  
    Inherits Attribute  
End Class  
```  
  
 如果 `AllowMultiple` 引數設為 `true`，則可以將產生的屬性多次套用至單一實體，與下面類似：  
  
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
  
 在此情況下，因為 `AllowMultiple` 設為 `true`，所以可以重複套用 `MultiUseAttr`。 套用多個屬性所顯示的兩種格式都有效。  
  
 如果 `Inherited` 設為 `false`，則衍生自已屬性化類別的類別不會繼承屬性。 例如:   
  
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
  
 在此情況下，不會透過繼承將 `Attr1` 套用至 `DClass`。  
  
## <a name="remarks"></a>備註  
 `AttributeUsage` 屬性是單次使用的屬性--它無法多次套用至相同的類別。 `AttributeUsage` 是 <xref:System.AttributeUsageAttribute> 的別名。  
  
 如需詳細資訊，請參閱[使用反映存取屬性 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)。  
  
## <a name="example"></a>範例  
 下列範例示範 `AttributeUsage` 屬性的 `Inherited` 和 `AllowMultiple` 引數的效果，以及如何列舉套用至類別的自訂屬性。  
  
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

- <xref:System.Attribute>
- <xref:System.Reflection>
- [Visual Basic 程式設計手冊](../../../../visual-basic/programming-guide/index.md)
- [屬性](../../../../standard/attributes/index.md)
- [反映 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [屬性 (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)
- [建立自訂屬性 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [使用反映存取屬性 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
