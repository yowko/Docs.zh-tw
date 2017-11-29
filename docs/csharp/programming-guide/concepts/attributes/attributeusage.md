---
title: AttributeUsage (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 22c45568-9a6a-4c2f-8480-f38c1caa0a99
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 81e7440279a2d7dfa801394ee0e9af6181da3c13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="attributeusage-c"></a>AttributeUsage (C#)
決定如何使用自訂屬性類別。 `AttributeUsage` 是一個屬性，可套用至自訂屬性定義來控制如何套用新屬性。 明確套用時，預設設定看起來會像這樣︰  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.All,  
                   AllowMultiple = false,  
                   Inherited = true)]  
class NewAttribute : System.Attribute { }  
```  
  
 在此範例中，`NewAttribute` 類別可以套用至任何可屬性化的程式碼實體，但只能對每個實體套用一次。 當套用至基底類別時，其由衍生類別所繼承。  
  
 `AllowMultiple` 和 `Inherited` 是選擇性引數，因此這個程式碼具有相同的效果︰  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.All)]  
class NewAttribute : System.Attribute { }  
```  
  
 第一個 `AttributeUsage` 引數必須是 <xref:System.AttributeTargets> 列舉的一或多個元素。 您可以使用 OR 運算子來連結多個目標類型，與下面類似：  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Property | AttributeTargets.Field)]  
class NewPropertyOrFieldAttribute : Attribute { }  
```  
  
 如果 `AllowMultiple` 引數設為 `true`，則可以將產生的屬性多次套用至單一實體，與下面類似：  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Class, AllowMultiple = true)]  
class MultiUseAttr : Attribute { }  
  
[MultiUseAttr]  
[MultiUseAttr]  
class Class1 { }  
  
[MultiUseAttr, MultiUseAttr]  
class Class2 { }  
```  
  
 在此情況下，因為 `AllowMultiple` 設為 `true`，所以可以重複套用 `MultiUseAttr`。 套用多個屬性所顯示的兩種格式都有效。  
  
 如果 `Inherited` 設為 `false`，則衍生自已屬性化類別的類別不會繼承屬性。 例如:   
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Class, Inherited = false)]  
class Attr1 : Attribute { }  
  
[Attr1]  
class BClass { }  
  
class DClass : BClass { }  
```  
  
 在此情況下，不會透過繼承將 `Attr1` 套用至 `DClass`。  
  
## <a name="remarks"></a>備註  
 `AttributeUsage` 屬性是單次使用的屬性--它無法多次套用至相同的類別。 `AttributeUsage` 是 <xref:System.AttributeUsageAttribute> 的別名。  
  
 如需詳細資訊，請參閱[使用反映存取屬性 (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)。  
  
## <a name="example"></a>範例  
 下列範例示範 `AttributeUsage` 屬性的 `Inherited` 和 `AllowMultiple` 引數的效果，以及如何列舉套用至類別的自訂屬性。  
  
```csharp  
using System;  

// Create some custom attributes:  
[AttributeUsage(System.AttributeTargets.Class, Inherited = false)]  
class A1 : System.Attribute { }  
  
[AttributeUsage(System.AttributeTargets.Class)]  
class A2 : System.Attribute { }  
  
[AttributeUsage(System.AttributeTargets.Class, AllowMultiple = true)]  
class A3 : System.Attribute { }  
  
// Apply custom attributes to classes:  
[A1, A2]  
class BaseClass { }  
  
[A3, A3]  
class DerivedClass : BaseClass { }  
  
public class TestAttributeUsage  
{  
    static void Main()  
    {  
        BaseClass b = new BaseClass();  
        DerivedClass d = new DerivedClass();  
  
        // Display custom attributes for each class.  
        Console.WriteLine("Attributes on Base Class:");  
        object[] attrs = b.GetType().GetCustomAttributes(true);  
        foreach (Attribute attr in attrs)  
        {  
            Console.WriteLine(attr);  
        }  
  
        Console.WriteLine("Attributes on Derived Class:");  
        attrs = d.GetType().GetCustomAttributes(true);  
        foreach (Attribute attr in attrs)  
        {  
            Console.WriteLine(attr);  
        }  
    }  
}  
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
 <xref:System.Attribute>  
 <xref:System.Reflection>  
 [C# 程式設計指南](../../../../csharp/programming-guide/index.md)  
 [屬性](https://msdn.microsoft.com/library/5x6cd29c)  
 [反映 (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
 [屬性](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [建立自訂屬性 (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [使用反射存取屬性 (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
