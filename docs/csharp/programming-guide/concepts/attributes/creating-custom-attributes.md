---
title: 建立自訂屬性 (C#)
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: 3a70b738b376e52482e63f2eb9cc4d7bb62a9b35
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141614"
---
# <a name="creating-custom-attributes-c"></a><span data-ttu-id="84f86-102">建立自訂屬性 (C#)</span><span class="sxs-lookup"><span data-stu-id="84f86-102">Creating Custom Attributes (C#)</span></span>
<span data-ttu-id="84f86-103">您可以建立自己的自訂屬性，方法是定義屬性類別，這是直接或間接衍生自 <xref:System.Attribute> 的類別，它能快速且簡單地在中繼資料中識別屬性定義。</span><span class="sxs-lookup"><span data-stu-id="84f86-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="84f86-104">假設您想要用撰寫類型的程式設計人員姓名來標記類型。</span><span class="sxs-lookup"><span data-stu-id="84f86-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="84f86-105">您可能會定義自訂的 `Author` 屬性類別：</span><span class="sxs-lookup"><span data-stu-id="84f86-105">You might define a custom `Author` attribute class:</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct)  
]  
public class AuthorAttribute : System.Attribute  
{  
    private string name;  
    public double version;  
  
    public AuthorAttribute(string name)  
    {  
        this.name = name;  
        version = 1.0;  
    }  
}  
```  
  
 <span data-ttu-id="84f86-106">類別名稱 `AuthorAttribute` 是屬性的名稱， `Author` 加上 `Attribute` 尾碼。</span><span class="sxs-lookup"><span data-stu-id="84f86-106">The class name `AuthorAttribute` is the attribute's name, `Author`, plus the `Attribute` suffix.</span></span> <span data-ttu-id="84f86-107">它衍生自 `System.Attribute`，因此它是自訂屬性類別。</span><span class="sxs-lookup"><span data-stu-id="84f86-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="84f86-108">建構函式的參數是自訂屬性的位置參數。</span><span class="sxs-lookup"><span data-stu-id="84f86-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="84f86-109">在此範例中，`name` 是位置參數。</span><span class="sxs-lookup"><span data-stu-id="84f86-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="84f86-110">任何公用讀寫欄位或屬性都是具名參數。</span><span class="sxs-lookup"><span data-stu-id="84f86-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="84f86-111">在此情況下，`version` 是唯一的具名參數。</span><span class="sxs-lookup"><span data-stu-id="84f86-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="84f86-112">請注意，使用了 `AttributeUsage` 屬性讓 `Author` 屬性只有對類別和 `struct` 宣告有效。</span><span class="sxs-lookup"><span data-stu-id="84f86-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `struct` declarations.</span></span>  
  
 <span data-ttu-id="84f86-113">您可以如下所示使用這個新屬性︰</span><span class="sxs-lookup"><span data-stu-id="84f86-113">You could use this new attribute as follows:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 <span data-ttu-id="84f86-114">`AttributeUsage` 有一個具名參數 `AllowMultiple`，您可以用它讓自訂屬性僅單次使用或是多次使用。</span><span class="sxs-lookup"><span data-stu-id="84f86-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="84f86-115">在下列程式碼範例中，建立了多次使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="84f86-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class AuthorAttribute : System.Attribute  
```  
  
 <span data-ttu-id="84f86-116">在下列程式碼範例中，相同類型的多個屬性會套用至類別。</span><span class="sxs-lookup"><span data-stu-id="84f86-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="84f86-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84f86-117">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="84f86-118">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="84f86-118">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="84f86-119">撰寫自訂屬性</span><span class="sxs-lookup"><span data-stu-id="84f86-119">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="84f86-120">反映 (C#)</span><span class="sxs-lookup"><span data-stu-id="84f86-120">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="84f86-121">屬性 (C#)</span><span class="sxs-lookup"><span data-stu-id="84f86-121">Attributes (C#)</span></span>](./index.md)
- [<span data-ttu-id="84f86-122">使用反映存取屬性 (C#)</span><span class="sxs-lookup"><span data-stu-id="84f86-122">Accessing Attributes by Using Reflection (C#)</span></span>](./accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="84f86-123">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="84f86-123">AttributeUsage (C#)</span></span>](../../../language-reference/attributes/general.md)
