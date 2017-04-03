---
title: "建立自訂屬性 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b71bf8fe1f4d448bf373fcab4bccd89bca4672b8
ms.lasthandoff: 03/13/2017

---
# <a name="creating-custom-attributes-c"></a>建立自訂屬性 (C#)
您可以建立自己的自訂屬性，方法是定義屬性類別，這是直接或間接衍生自 <xref:System.Attribute> 的類別，它能快速且簡單地在中繼資料中識別屬性定義。 假設您想要用撰寫類型的程式設計人員姓名來標記類型。 您可能會定義自訂的 `Author` 屬性類別：  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct)  
]  
public class Author : System.Attribute  
{  
    private string name;  
    public double version;  
  
    public Author(string name)  
    {  
        this.name = name;  
        version = 1.0;  
    }  
}  
```  
  
 類別名稱是屬性的名稱，亦即 `Author`。 它衍生自 `System.Attribute`，因此它是自訂屬性類別。 建構函式的參數是自訂屬性的位置參數。 在此範例中，`name` 是位置參數。 任何公用讀寫欄位或屬性都是具名參數。 在此情況下，`version` 是唯一的具名參數。 請注意，使用了 `AttributeUsage` 屬性讓 `Author` 屬性只有對類別和 `struct` 宣告有效。  
  
 您可以如下所示使用這個新屬性︰  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 `AttributeUsage` 有一個具名參數 `AllowMultiple`，您可以用它讓自訂屬性僅單次使用或是多次使用。 在下列程式碼範例中，建立了多次使用的屬性。  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 在下列程式碼範例中，相同類型的多個屬性會套用至類別。  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
> [!NOTE]
>  如果您的屬性類別包含屬性，則該屬性必須是讀寫。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Reflection>   
 [C# 程式設計手冊](../../../../csharp/programming-guide/index.md)   
 [撰寫自訂屬性](http://msdn.microsoft.com/library/97216f69-bde8-49fd-ac40-f18c500ef5dc)   
 [反映 (C#)](../../../../csharp/programming-guide/concepts/reflection.md)   
 [屬性 (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)   
 [使用反映存取屬性 (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)   
 [AttributeUsage (C#)](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md)
