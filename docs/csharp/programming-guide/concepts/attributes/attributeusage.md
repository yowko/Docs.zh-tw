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
# <a name="attributeusage-c"></a><span data-ttu-id="f7fdc-102">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="f7fdc-102">AttributeUsage (C#)</span></span>
<span data-ttu-id="f7fdc-103">決定如何使用自訂屬性類別。</span><span class="sxs-lookup"><span data-stu-id="f7fdc-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="f7fdc-104">`AttributeUsage` 是一個屬性，可套用至自訂屬性定義來控制如何套用新屬性。</span><span class="sxs-lookup"><span data-stu-id="f7fdc-104">`AttributeUsage` is an attribute that can be applied to custom attribute definitions to control how the new attribute can be applied.</span></span> <span data-ttu-id="f7fdc-105">明確套用時，預設設定看起來會像這樣︰</span><span class="sxs-lookup"><span data-stu-id="f7fdc-105">The default settings look like this when applied explicitly:</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.All,  
                   AllowMultiple = false,  
                   Inherited = true)]  
class NewAttribute : System.Attribute { }  
```  
  
 <span data-ttu-id="f7fdc-106">在此範例中，`NewAttribute` 類別可以套用至任何可屬性化的程式碼實體，但只能對每個實體套用一次。</span><span class="sxs-lookup"><span data-stu-id="f7fdc-106">In this example, the `NewAttribute` class can be applied to any attribute-able code entity, but can be applied only once to each entity.</span></span> <span data-ttu-id="f7fdc-107">當套用至基底類別時，其由衍生類別所繼承。</span><span class="sxs-lookup"><span data-stu-id="f7fdc-107">It is inherited by derived classes when applied to a base class.</span></span>  
  
 <span data-ttu-id="f7fdc-108">`AllowMultiple` 和 `Inherited` 是選擇性引數，因此這個程式碼具有相同的效果︰</span><span class="sxs-lookup"><span data-stu-id="f7fdc-108">The `AllowMultiple` and `Inherited` arguments are optional, so this code has the same effect:</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.All)]  
class NewAttribute : System.Attribute { }  
```  
  
 <span data-ttu-id="f7fdc-109">第一個 `AttributeUsage` 引數必須是 <xref:System.AttributeTargets> 列舉的一或多個元素。</span><span class="sxs-lookup"><span data-stu-id="f7fdc-109">The first `AttributeUsage` argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="f7fdc-110">您可以使用 OR 運算子來連結多個目標類型，與下面類似：</span><span class="sxs-lookup"><span data-stu-id="f7fdc-110">Multiple target types can be linked together with the OR operator, like this:</span></span>  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Property | AttributeTargets.Field)]  
class NewPropertyOrFieldAttribute : Attribute { }  
```  
  
 <span data-ttu-id="f7fdc-111">如果 `AllowMultiple` 引數設為 `true`，則可以將產生的屬性多次套用至單一實體，與下面類似：</span><span class="sxs-lookup"><span data-stu-id="f7fdc-111">If the `AllowMultiple` argument is set to `true`, then the resulting attribute can be applied more than once to a single entity, like this:</span></span>  
  
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
  
 <span data-ttu-id="f7fdc-112">在此情況下，因為 `AllowMultiple` 設為 `true`，所以可以重複套用 `MultiUseAttr`。</span><span class="sxs-lookup"><span data-stu-id="f7fdc-112">In this case `MultiUseAttr` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="f7fdc-113">套用多個屬性所顯示的兩種格式都有效。</span><span class="sxs-lookup"><span data-stu-id="f7fdc-113">Both formats shown for applying multiple attributes are valid.</span></span>  
  
 <span data-ttu-id="f7fdc-114">如果 `Inherited` 設為 `false`，則衍生自已屬性化類別的類別不會繼承屬性。</span><span class="sxs-lookup"><span data-stu-id="f7fdc-114">If `Inherited` is set to `false`, then the attribute is not inherited by classes that are derived from a class that is attributed.</span></span> <span data-ttu-id="f7fdc-115">例如: </span><span class="sxs-lookup"><span data-stu-id="f7fdc-115">For example:</span></span>  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Class, Inherited = false)]  
class Attr1 : Attribute { }  
  
[Attr1]  
class BClass { }  
  
class DClass : BClass { }  
```  
  
 <span data-ttu-id="f7fdc-116">在此情況下，不會透過繼承將 `Attr1` 套用至 `DClass`。</span><span class="sxs-lookup"><span data-stu-id="f7fdc-116">In this case `Attr1` is not applied to `DClass` via inheritance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7fdc-117">備註</span><span class="sxs-lookup"><span data-stu-id="f7fdc-117">Remarks</span></span>  
 <span data-ttu-id="f7fdc-118">`AttributeUsage` 屬性是單次使用的屬性--它無法多次套用至相同的類別。</span><span class="sxs-lookup"><span data-stu-id="f7fdc-118">The `AttributeUsage` attribute is a single-use attribute--it cannot be applied more than once to the same class.</span></span> <span data-ttu-id="f7fdc-119">`AttributeUsage` 是 <xref:System.AttributeUsageAttribute> 的別名。</span><span class="sxs-lookup"><span data-stu-id="f7fdc-119">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="f7fdc-120">如需詳細資訊，請參閱[使用反映存取屬性 (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)。</span><span class="sxs-lookup"><span data-stu-id="f7fdc-120">For more information, see [Accessing Attributes by Using Reflection (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7fdc-121">範例</span><span class="sxs-lookup"><span data-stu-id="f7fdc-121">Example</span></span>  
 <span data-ttu-id="f7fdc-122">下列範例示範 `AttributeUsage` 屬性的 `Inherited` 和 `AllowMultiple` 引數的效果，以及如何列舉套用至類別的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="f7fdc-122">The following example demonstrates the effect of the `Inherited` and `AllowMultiple` arguments to the `AttributeUsage` attribute, and how the custom attributes applied to a class can be enumerated.</span></span>  
  
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
  
## <a name="sample-output"></a><span data-ttu-id="f7fdc-123">範例輸出</span><span class="sxs-lookup"><span data-stu-id="f7fdc-123">Sample Output</span></span>  
  
```  
Attributes on Base Class:  
A1  
A2  
Attributes on Derived Class:  
A3  
A3  
A2  
```  
  
## <a name="see-also"></a><span data-ttu-id="f7fdc-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7fdc-124">See Also</span></span>  
 <xref:System.Attribute>  
 <xref:System.Reflection>  
 [<span data-ttu-id="f7fdc-125">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f7fdc-125">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f7fdc-126">屬性</span><span class="sxs-lookup"><span data-stu-id="f7fdc-126">Attributes</span></span>](https://msdn.microsoft.com/library/5x6cd29c)  
 [<span data-ttu-id="f7fdc-127">反映 (C#)</span><span class="sxs-lookup"><span data-stu-id="f7fdc-127">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="f7fdc-128">屬性</span><span class="sxs-lookup"><span data-stu-id="f7fdc-128">Attributes</span></span>](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="f7fdc-129">建立自訂屬性 (C#)</span><span class="sxs-lookup"><span data-stu-id="f7fdc-129">Creating Custom Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [<span data-ttu-id="f7fdc-130">使用反射存取屬性 (C#)</span><span class="sxs-lookup"><span data-stu-id="f7fdc-130">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
