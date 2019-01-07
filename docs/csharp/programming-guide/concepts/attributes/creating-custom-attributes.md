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
# <a name="creating-custom-attributes-c"></a><span data-ttu-id="3249f-102">建立自訂屬性 (C#)</span><span class="sxs-lookup"><span data-stu-id="3249f-102">Creating Custom Attributes (C#)</span></span>
<span data-ttu-id="3249f-103">您可以建立自己的自訂屬性，方法是定義屬性類別，這是直接或間接衍生自 <xref:System.Attribute> 的類別，它能快速且簡單地在中繼資料中識別屬性定義。</span><span class="sxs-lookup"><span data-stu-id="3249f-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="3249f-104">假設您想要用撰寫類型的程式設計人員姓名來標記類型。</span><span class="sxs-lookup"><span data-stu-id="3249f-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="3249f-105">您可能會定義自訂的 `Author` 屬性類別：</span><span class="sxs-lookup"><span data-stu-id="3249f-105">You might define a custom `Author` attribute class:</span></span>  
  
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
  
 <span data-ttu-id="3249f-106">類別名稱是屬性的名稱，亦即 `Author`。</span><span class="sxs-lookup"><span data-stu-id="3249f-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="3249f-107">它衍生自 `System.Attribute`，因此它是自訂屬性類別。</span><span class="sxs-lookup"><span data-stu-id="3249f-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="3249f-108">建構函式的參數是自訂屬性的位置參數。</span><span class="sxs-lookup"><span data-stu-id="3249f-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="3249f-109">在此範例中，`name` 是位置參數。</span><span class="sxs-lookup"><span data-stu-id="3249f-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="3249f-110">任何公用讀寫欄位或屬性都是具名參數。</span><span class="sxs-lookup"><span data-stu-id="3249f-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="3249f-111">在此情況下，`version` 是唯一的具名參數。</span><span class="sxs-lookup"><span data-stu-id="3249f-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="3249f-112">請注意，使用了 `AttributeUsage` 屬性讓 `Author` 屬性只有對類別和 `struct` 宣告有效。</span><span class="sxs-lookup"><span data-stu-id="3249f-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `struct` declarations.</span></span>  
  
 <span data-ttu-id="3249f-113">您可以如下所示使用這個新屬性︰</span><span class="sxs-lookup"><span data-stu-id="3249f-113">You could use this new attribute as follows:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 <span data-ttu-id="3249f-114">`AttributeUsage` 有一個具名參數 `AllowMultiple`，您可以用它讓自訂屬性僅單次使用或是多次使用。</span><span class="sxs-lookup"><span data-stu-id="3249f-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="3249f-115">在下列程式碼範例中，建立了多次使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="3249f-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 <span data-ttu-id="3249f-116">在下列程式碼範例中，相同類型的多個屬性會套用至類別。</span><span class="sxs-lookup"><span data-stu-id="3249f-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="3249f-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="3249f-117">See Also</span></span>

- <xref:System.Reflection>  
- [<span data-ttu-id="3249f-118">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="3249f-118">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="3249f-119">撰寫自訂屬性</span><span class="sxs-lookup"><span data-stu-id="3249f-119">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)  
- [<span data-ttu-id="3249f-120">反映 (C#)</span><span class="sxs-lookup"><span data-stu-id="3249f-120">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)  
- [<span data-ttu-id="3249f-121">屬性 (C#)</span><span class="sxs-lookup"><span data-stu-id="3249f-121">Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/index.md)  
- [<span data-ttu-id="3249f-122">使用反射存取屬性 (C#)</span><span class="sxs-lookup"><span data-stu-id="3249f-122">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
- [<span data-ttu-id="3249f-123">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="3249f-123">AttributeUsage (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md)
