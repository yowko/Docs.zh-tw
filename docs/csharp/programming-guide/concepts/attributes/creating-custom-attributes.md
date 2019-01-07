---
title: 建立自訂屬性 (C#)
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: 0a27924623cc462f6d3339149718a1b29999ac1d
ms.sourcegitcommit: deb9225a55485a5a6e6c7914deb30ccfceb69d3f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2019
ms.locfileid: "54058265"
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
  
## <a name="see-also"></a>請參閱

- <xref:System.Reflection>  
- [C# 程式設計指南](../../../../csharp/programming-guide/index.md)  
- [撰寫自訂屬性](../../../../standard/attributes/writing-custom-attributes.md)  
- [反映 (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
- [屬性 (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)  
- [使用反射存取屬性 (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
- [AttributeUsage (C#)](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md)
