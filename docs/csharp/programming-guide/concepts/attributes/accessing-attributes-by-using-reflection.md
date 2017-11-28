---
title: "使用反射存取屬性 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: dce3a696-4ceb-489a-b5e4-322a83052f18
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 162bdd6b968def391a2f3413596ee8c2a8b01cc3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="accessing-attributes-by-using-reflection-c"></a>使用反射存取屬性 (C#)
您可以定義自訂屬性並將它們放在原始程式碼的事實，對於擷取並處理該項資訊並沒有什麼幫助。 使用反射，即可擷取已使用自訂屬性所定義的資訊。 重要方法是 `GetCustomAttributes`，這會傳回為來源程式碼屬性的執行階段對等項目的物件陣列。 這個方法有數個多載的版本。 如需詳細資訊，請參閱<xref:System.Attribute>。  
  
 屬性規格，例如︰  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 概念上相當於這個：  
  
```csharp  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 不過，程式碼會等到查詢 `SampleClass` 的屬性才會執行程式碼。 在 `SampleClass` 上呼叫 `GetCustomAttributes`，會如上建構和初始化 `Author` 物件。 如果類別有其他屬性，則以類似的方式建構其他屬性物件。 `GetCustomAttributes` 接著會傳回 `Author` 物件以及陣列中的任何其他屬性物件。 您接著可以逐一查看這個陣列、根據每個陣列項目的類型來決定已套用的屬性，以及從屬性物件擷取資訊。  
  
## <a name="example"></a>範例  
 以下是完整範例。 定義、套用至數個實體並透過反射來擷取自訂屬性。  
  
```csharp  
// Multiuse attribute.  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // Multiuse attribute.  
]  
public class Author : System.Attribute  
{  
    string name;  
    public double version;  
  
    public Author(string name)  
    {  
        this.name = name;  
  
        // Default value.  
        version = 1.0;  
    }  
  
    public string GetName()  
    {  
        return name;  
    }  
}  
  
// Class with the Author attribute.  
[Author("P. Ackerman")]  
public class FirstClass  
{  
    // ...  
}  
  
// Class without the Author attribute.  
public class SecondClass  
{  
    // ...  
}  
  
// Class with multiple Author attributes.  
[Author("P. Ackerman"), Author("R. Koch", version = 2.0)]  
public class ThirdClass  
{  
    // ...  
}  
  
class TestAuthorAttribute  
{  
    static void Test()  
    {  
        PrintAuthorInfo(typeof(FirstClass));  
        PrintAuthorInfo(typeof(SecondClass));  
        PrintAuthorInfo(typeof(ThirdClass));  
    }  
  
    private static void PrintAuthorInfo(System.Type t)  
    {  
        System.Console.WriteLine("Author information for {0}", t);  
  
        // Using reflection.  
        System.Attribute[] attrs = System.Attribute.GetCustomAttributes(t);  // Reflection.  
  
        // Displaying output.  
        foreach (System.Attribute attr in attrs)  
        {  
            if (attr is Author)  
            {  
                Author a = (Author)attr;  
                System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version);  
            }  
        }  
    }  
}  
/* Output:  
    Author information for FirstClass  
       P. Ackerman, version 1.00  
    Author information for SecondClass  
    Author information for ThirdClass  
       R. Koch, version 2.00  
       P. Ackerman, version 1.00  
*/  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [C# 程式設計指南](../../../../csharp/programming-guide/index.md)  
 [擷取儲存於屬性中的資訊](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
 [反映 (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
 [屬性 (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [建立自訂屬性 (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)
