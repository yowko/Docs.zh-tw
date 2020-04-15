---
title: 建立自訂屬性 (C#)
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: ec959723c339a13a40fd62388421ceacb736dfca
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389550"
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
  
## <a name="see-also"></a>另請參閱

- <xref:System.Reflection>
- [C# 編程指南](../../index.md)
- [撰寫自訂屬性](../../../../standard/attributes/writing-custom-attributes.md)
- [反映 (C#)](../reflection.md)
- [屬性 (C#)](./index.md)
- [使用反映存取屬性 (C#)](./accessing-attributes-by-using-reflection.md)
- [AttributeUsage (C#)](../../../language-reference/attributes/general.md)
