---
title: AttributeUsage (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
ms.openlocfilehash: 0e88c57b2a18afb7f9f7d567f355d38a78892b2f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648137"
---
# <a name="attributeusage-visual-basic"></a><span data-ttu-id="01a50-102">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01a50-102">AttributeUsage (Visual Basic)</span></span>
<span data-ttu-id="01a50-103">決定如何使用自訂屬性類別。</span><span class="sxs-lookup"><span data-stu-id="01a50-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="01a50-104">`AttributeUsage` 是一個屬性，可套用至自訂屬性定義來控制如何套用新屬性。</span><span class="sxs-lookup"><span data-stu-id="01a50-104">`AttributeUsage` is an attribute that can be applied to custom attribute definitions to control how the new attribute can be applied.</span></span> <span data-ttu-id="01a50-105">明確套用時，預設設定看起來會像這樣︰</span><span class="sxs-lookup"><span data-stu-id="01a50-105">The default settings look like this when applied explicitly:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All,   
                   AllowMultiple:=False,   
                   Inherited:=True)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 <span data-ttu-id="01a50-106">在此範例中，`NewAttribute` 類別可以套用至任何可屬性化的程式碼實體，但只能對每個實體套用一次。</span><span class="sxs-lookup"><span data-stu-id="01a50-106">In this example, the `NewAttribute` class can be applied to any attribute-able code entity, but can be applied only once to each entity.</span></span> <span data-ttu-id="01a50-107">當套用至基底類別時，其由衍生類別所繼承。</span><span class="sxs-lookup"><span data-stu-id="01a50-107">It is inherited by derived classes when applied to a base class.</span></span>  
  
 <span data-ttu-id="01a50-108">`AllowMultiple` 和 `Inherited` 是選擇性引數，因此這個程式碼具有相同的效果︰</span><span class="sxs-lookup"><span data-stu-id="01a50-108">The `AllowMultiple` and `Inherited` arguments are optional, so this code has the same effect:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 <span data-ttu-id="01a50-109">第一個 `AttributeUsage` 引數必須是 <xref:System.AttributeTargets> 列舉的一或多個元素。</span><span class="sxs-lookup"><span data-stu-id="01a50-109">The first `AttributeUsage` argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="01a50-110">您可以使用 OR 運算子來連結多個目標類型，與下面類似：</span><span class="sxs-lookup"><span data-stu-id="01a50-110">Multiple target types can be linked together with the OR operator, like this:</span></span>  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>   
Class NewPropertyOrFieldAttribute  
    Inherits Attribute  
End Class  
```  
  
 <span data-ttu-id="01a50-111">如果 `AllowMultiple` 引數設為 `true`，則可以將產生的屬性多次套用至單一實體，與下面類似：</span><span class="sxs-lookup"><span data-stu-id="01a50-111">If the `AllowMultiple` argument is set to `true`, then the resulting attribute can be applied more than once to a single entity, like this:</span></span>  
  
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
  
 <span data-ttu-id="01a50-112">在此情況下，因為 `AllowMultiple` 設為 `true`，所以可以重複套用 `MultiUseAttr`。</span><span class="sxs-lookup"><span data-stu-id="01a50-112">In this case `MultiUseAttr` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="01a50-113">套用多個屬性所顯示的兩種格式都有效。</span><span class="sxs-lookup"><span data-stu-id="01a50-113">Both formats shown for applying multiple attributes are valid.</span></span>  
  
 <span data-ttu-id="01a50-114">如果 `Inherited` 設為 `false`，則衍生自已屬性化類別的類別不會繼承屬性。</span><span class="sxs-lookup"><span data-stu-id="01a50-114">If `Inherited` is set to `false`, then the attribute is not inherited by classes that are derived from a class that is attributed.</span></span> <span data-ttu-id="01a50-115">例如: </span><span class="sxs-lookup"><span data-stu-id="01a50-115">For example:</span></span>  
  
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
  
 <span data-ttu-id="01a50-116">在此情況下，不會透過繼承將 `Attr1` 套用至 `DClass`。</span><span class="sxs-lookup"><span data-stu-id="01a50-116">In this case `Attr1` is not applied to `DClass` via inheritance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01a50-117">備註</span><span class="sxs-lookup"><span data-stu-id="01a50-117">Remarks</span></span>  
 <span data-ttu-id="01a50-118">`AttributeUsage` 屬性是單次使用的屬性--它無法多次套用至相同的類別。</span><span class="sxs-lookup"><span data-stu-id="01a50-118">The `AttributeUsage` attribute is a single-use attribute--it cannot be applied more than once to the same class.</span></span> <span data-ttu-id="01a50-119">`AttributeUsage` 是 <xref:System.AttributeUsageAttribute> 的別名。</span><span class="sxs-lookup"><span data-stu-id="01a50-119">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="01a50-120">如需詳細資訊，請參閱[使用反映存取屬性 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)。</span><span class="sxs-lookup"><span data-stu-id="01a50-120">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="01a50-121">範例</span><span class="sxs-lookup"><span data-stu-id="01a50-121">Example</span></span>  
 <span data-ttu-id="01a50-122">下列範例示範 `AttributeUsage` 屬性的 `Inherited` 和 `AllowMultiple` 引數的效果，以及如何列舉套用至類別的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="01a50-122">The following example demonstrates the effect of the `Inherited` and `AllowMultiple` arguments to the `AttributeUsage` attribute, and how the custom attributes applied to a class can be enumerated.</span></span>  
  
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
  
## <a name="sample-output"></a><span data-ttu-id="01a50-123">範例輸出</span><span class="sxs-lookup"><span data-stu-id="01a50-123">Sample Output</span></span>  
  
```  
Attributes on Base Class:  
A1  
A2  
Attributes on Derived Class:  
A3  
A3  
A2  
```  
  
## <a name="see-also"></a><span data-ttu-id="01a50-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01a50-124">See also</span></span>
- <xref:System.Attribute>
- <xref:System.Reflection>
- [<span data-ttu-id="01a50-125">Visual Basic 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="01a50-125">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="01a50-126">屬性</span><span class="sxs-lookup"><span data-stu-id="01a50-126">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="01a50-127">反映 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01a50-127">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="01a50-128">屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01a50-128">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="01a50-129">建立自訂屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01a50-129">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="01a50-130">使用反映存取屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01a50-130">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
