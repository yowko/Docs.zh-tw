---
title: "AttributeUsage (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c91f2686a03d2590e1aaf166d27c49744bb13c9b
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="attributeusage-visual-basic"></a><span data-ttu-id="3c886-102">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c886-102">AttributeUsage (Visual Basic)</span></span>
<span data-ttu-id="3c886-103">決定如何使用自訂屬性類別。</span><span class="sxs-lookup"><span data-stu-id="3c886-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="3c886-104">`AttributeUsage`是可以套用自訂屬性定義，來控制如何套用新屬性的屬性。</span><span class="sxs-lookup"><span data-stu-id="3c886-104">`AttributeUsage` is an attribute that can be applied to custom attribute definitions to control how the new attribute can be applied.</span></span> <span data-ttu-id="3c886-105">明確地套用時，預設值看起來像這樣︰</span><span class="sxs-lookup"><span data-stu-id="3c886-105">The default settings look like this when applied explicitly:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All,   
                   AllowMultiple:=False,   
                   Inherited:=True)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 <span data-ttu-id="3c886-106">在此範例中，`NewAttribute`類別可以套用至任何可屬性的程式碼的實體，但可以一次只能套用至每個實體。</span><span class="sxs-lookup"><span data-stu-id="3c886-106">In this example, the `NewAttribute` class can be applied to any attribute-able code entity, but can be applied only once to each entity.</span></span> <span data-ttu-id="3c886-107">它會由衍生類別，當套用至基底類別繼承。</span><span class="sxs-lookup"><span data-stu-id="3c886-107">It is inherited by derived classes when applied to a base class.</span></span>  
  
 <span data-ttu-id="3c886-108">`AllowMultiple`和`Inherited`引數是選擇性的因此此程式碼有相同的效果︰</span><span class="sxs-lookup"><span data-stu-id="3c886-108">The `AllowMultiple` and `Inherited` arguments are optional, so this code has the same effect:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 <span data-ttu-id="3c886-109">第一個`AttributeUsage`引數必須是一個或多個元素的<xref:System.AttributeTargets>列舉型別。</xref:System.AttributeTargets></span><span class="sxs-lookup"><span data-stu-id="3c886-109">The first `AttributeUsage` argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="3c886-110">多個目標類型可以連結搭配 OR 運算子，就像這樣︰</span><span class="sxs-lookup"><span data-stu-id="3c886-110">Multiple target types can be linked together with the OR operator, like this:</span></span>  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>   
Class NewPropertyOrFieldAttribute  
    Inherits Attribute  
End Class  
```  
  
 <span data-ttu-id="3c886-111">如果`AllowMultiple`引數設定為`true`，則產生的屬性可以多次套用至單一實體，就像這樣︰</span><span class="sxs-lookup"><span data-stu-id="3c886-111">If the `AllowMultiple` argument is set to `true`, then the resulting attribute can be applied more than once to a single entity, like this:</span></span>  
  
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
  
 <span data-ttu-id="3c886-112">在此情況下`MultiUseAttr`因為可以重複套用`AllowMultiple`設為`true`。</span><span class="sxs-lookup"><span data-stu-id="3c886-112">In this case `MultiUseAttr` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="3c886-113">顯示套用多個屬性的兩種格式都有效。</span><span class="sxs-lookup"><span data-stu-id="3c886-113">Both formats shown for applying multiple attributes are valid.</span></span>  
  
 <span data-ttu-id="3c886-114">如果`Inherited`設為`false`，則衍生自類別，其屬性的類別不繼承屬性。</span><span class="sxs-lookup"><span data-stu-id="3c886-114">If `Inherited` is set to `false`, then the attribute is not inherited by classes that are derived from a class that is attributed.</span></span> <span data-ttu-id="3c886-115">例如: </span><span class="sxs-lookup"><span data-stu-id="3c886-115">For example:</span></span>  
  
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
  
 <span data-ttu-id="3c886-116">在此情況下`Attr1`不會套用至`DClass`經由繼承。</span><span class="sxs-lookup"><span data-stu-id="3c886-116">In this case `Attr1` is not applied to `DClass` via inheritance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c886-117">備註</span><span class="sxs-lookup"><span data-stu-id="3c886-117">Remarks</span></span>  
 <span data-ttu-id="3c886-118">`AttributeUsage`屬性是單次使用屬性-它無法套用一次以上至相同的類別。</span><span class="sxs-lookup"><span data-stu-id="3c886-118">The `AttributeUsage` attribute is a single-use attribute--it cannot be applied more than once to the same class.</span></span> <span data-ttu-id="3c886-119">`AttributeUsage`<xref:System.AttributeUsageAttribute>.</xref:System.AttributeUsageAttribute>的別名</span><span class="sxs-lookup"><span data-stu-id="3c886-119">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="3c886-120">如需詳細資訊，請參閱[存取的屬性，使用反映 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)。</span><span class="sxs-lookup"><span data-stu-id="3c886-120">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c886-121">範例</span><span class="sxs-lookup"><span data-stu-id="3c886-121">Example</span></span>  
 <span data-ttu-id="3c886-122">下列範例示範的效果`Inherited`和`AllowMultiple`引數`AttributeUsage`屬性及可列舉的自訂屬性套用至類別的方式。</span><span class="sxs-lookup"><span data-stu-id="3c886-122">The following example demonstrates the effect of the `Inherited` and `AllowMultiple` arguments to the `AttributeUsage` attribute, and how the custom attributes applied to a class can be enumerated.</span></span>  
  
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
  
## <a name="sample-output"></a><span data-ttu-id="3c886-123">範例輸出</span><span class="sxs-lookup"><span data-stu-id="3c886-123">Sample Output</span></span>  
  
```  
Attributes on Base Class:  
A1  
A2  
Attributes on Derived Class:  
A3  
A3  
A2  
```  
  
## <a name="see-also"></a><span data-ttu-id="3c886-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c886-124">See Also</span></span>  
 <span data-ttu-id="3c886-125"><xref:System.Attribute></xref:System.Attribute></span><span class="sxs-lookup"><span data-stu-id="3c886-125"><xref:System.Attribute></span></span>   
 <span data-ttu-id="3c886-126"><xref:System.Reflection></xref:System.Reflection></span><span class="sxs-lookup"><span data-stu-id="3c886-126"><xref:System.Reflection></span></span>   
<span data-ttu-id="3c886-127"> [Visual Basic 程式設計指南](../../../../visual-basic/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="3c886-127"> [Visual Basic Programming Guide](../../../../visual-basic/programming-guide/index.md) </span></span>  
<span data-ttu-id="3c886-128"> [屬性](https://msdn.microsoft.com/library/5x6cd29c) </span><span class="sxs-lookup"><span data-stu-id="3c886-128"> [Attributes](https://msdn.microsoft.com/library/5x6cd29c) </span></span>  
<span data-ttu-id="3c886-129"> [反映 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="3c886-129"> [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span></span>  
<span data-ttu-id="3c886-130"> [屬性 (Visual Basic)](../../../../visual-basic/language-reference/attributes.md) </span><span class="sxs-lookup"><span data-stu-id="3c886-130"> [Attributes (Visual Basic)](../../../../visual-basic/language-reference/attributes.md) </span></span>  
<span data-ttu-id="3c886-131"> [建立自訂屬性 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="3c886-131"> [Creating Custom Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md) </span></span>  
<span data-ttu-id="3c886-132"> [使用反映 (Visual Basic) 存取屬性](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="3c886-132"> [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)</span></span>
