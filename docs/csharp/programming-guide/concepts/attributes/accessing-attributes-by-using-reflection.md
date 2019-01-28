---
title: 使用反射存取屬性 (C#)
ms.date: 07/20/2015
ms.assetid: dce3a696-4ceb-489a-b5e4-322a83052f18
ms.openlocfilehash: f7c7b89be13022471f4e17bcb6ed9a90bcbc1c54
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660407"
---
# <a name="accessing-attributes-by-using-reflection-c"></a><span data-ttu-id="53c45-102">使用反射存取屬性 (C#)</span><span class="sxs-lookup"><span data-stu-id="53c45-102">Accessing Attributes by Using Reflection (C#)</span></span>
<span data-ttu-id="53c45-103">您可以定義自訂屬性並將它們放在原始程式碼的事實，對於擷取並處理該項資訊並沒有什麼幫助。</span><span class="sxs-lookup"><span data-stu-id="53c45-103">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="53c45-104">使用反射，即可擷取已使用自訂屬性所定義的資訊。</span><span class="sxs-lookup"><span data-stu-id="53c45-104">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="53c45-105">重要方法是 `GetCustomAttributes`，這會傳回為來源程式碼屬性的執行階段對等項目的物件陣列。</span><span class="sxs-lookup"><span data-stu-id="53c45-105">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="53c45-106">這個方法有數個多載的版本。</span><span class="sxs-lookup"><span data-stu-id="53c45-106">This method has several overloaded versions.</span></span> <span data-ttu-id="53c45-107">如需詳細資訊，請參閱<xref:System.Attribute>。</span><span class="sxs-lookup"><span data-stu-id="53c45-107">For more information, see <xref:System.Attribute>.</span></span>  
  
 <span data-ttu-id="53c45-108">屬性規格，例如︰</span><span class="sxs-lookup"><span data-stu-id="53c45-108">An attribute specification such as:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 <span data-ttu-id="53c45-109">概念上相當於這個：</span><span class="sxs-lookup"><span data-stu-id="53c45-109">is conceptually equivalent to this:</span></span>  
  
```csharp  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 <span data-ttu-id="53c45-110">不過，程式碼會等到查詢 `SampleClass` 的屬性才會執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="53c45-110">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="53c45-111">在 `SampleClass` 上呼叫 `GetCustomAttributes`，會如上建構和初始化 `Author` 物件。</span><span class="sxs-lookup"><span data-stu-id="53c45-111">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="53c45-112">如果類別有其他屬性，則以類似的方式建構其他屬性物件。</span><span class="sxs-lookup"><span data-stu-id="53c45-112">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="53c45-113">`GetCustomAttributes` 接著會傳回 `Author` 物件以及陣列中的任何其他屬性物件。</span><span class="sxs-lookup"><span data-stu-id="53c45-113">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="53c45-114">您接著可以逐一查看這個陣列、根據每個陣列項目的類型來決定已套用的屬性，以及從屬性物件擷取資訊。</span><span class="sxs-lookup"><span data-stu-id="53c45-114">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53c45-115">範例</span><span class="sxs-lookup"><span data-stu-id="53c45-115">Example</span></span>  
 <span data-ttu-id="53c45-116">以下是完整範例。</span><span class="sxs-lookup"><span data-stu-id="53c45-116">Here is a complete example.</span></span> <span data-ttu-id="53c45-117">定義、套用至數個實體並透過反射來擷取自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="53c45-117">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="53c45-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53c45-118">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="53c45-119">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="53c45-119">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="53c45-120">擷取儲存於屬性中的資訊</span><span class="sxs-lookup"><span data-stu-id="53c45-120">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="53c45-121">反映 (C#)</span><span class="sxs-lookup"><span data-stu-id="53c45-121">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="53c45-122">屬性 (C#)</span><span class="sxs-lookup"><span data-stu-id="53c45-122">Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="53c45-123">建立自訂屬性 (C#)</span><span class="sxs-lookup"><span data-stu-id="53c45-123">Creating Custom Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)
