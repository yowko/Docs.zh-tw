---
title: "委派 (Visual Basic) 中的變異數 |Microsoft 文件"
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
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: cbab7da8c97ca202f8a4d0a1a65b8fa240cca32d
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="variance-in-delegates-visual-basic"></a><span data-ttu-id="2d718-102">委派 (Visual Basic) 中的變異數</span><span class="sxs-lookup"><span data-stu-id="2d718-102">Variance in Delegates (Visual Basic)</span></span>
<span data-ttu-id="2d718-103">.NET framework 3.5 引入變異數支援使用所有的委派，在 C# 和 Visual Basic 中的委派型別比對方法簽章。</span><span class="sxs-lookup"><span data-stu-id="2d718-103">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C# and Visual Basic.</span></span> <span data-ttu-id="2d718-104">這表示您可以指派給委派不只具有相符簽章的方法，也會傳回更多衍生類型 （共變數），或接受具有較少衍生的型別 （反變數） 比指定的委派型別參數的方法。</span><span class="sxs-lookup"><span data-stu-id="2d718-104">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="2d718-105">這包括泛型和非泛型委派。</span><span class="sxs-lookup"><span data-stu-id="2d718-105">This includes both generic and non-generic delegates.</span></span>  
  
 <span data-ttu-id="2d718-106">例如，請考慮下列程式碼，有兩個類別和兩個委派︰ 泛型和非泛型。</span><span class="sxs-lookup"><span data-stu-id="2d718-106">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>  
  
```vb  
Public Class First  
End Class  
  
Public Class Second  
    Inherits First  
End Class  
  
Public Delegate Function SampleDelegate(ByVal a As Second) As First  
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R  
```  
  
 <span data-ttu-id="2d718-107">當您建立的委派`SampleDelegate`或`SampleDelegate(Of A, R)`型別，您可以指派下列方法其中給這些委派。</span><span class="sxs-lookup"><span data-stu-id="2d718-107">When you create delegates of the `SampleDelegate` or `SampleDelegate(Of A, R)` types, you can assign any one of the following methods to those delegates.</span></span>  
  
```vb  
' Matching signature.  
Public Shared Function ASecondRFirst(  
    ByVal second As Second) As First  
    Return New First()  
End Function  
  
' The return type is more derived.  
Public Shared Function ASecondRSecond(  
    ByVal second As Second) As Second  
    Return New Second()  
End Function  
  
' The argument type is less derived.  
Public Shared Function AFirstRFirst(  
    ByVal first As First) As First  
    Return New First()  
End Function  
  
' The return type is more derived   
' and the argument type is less derived.  
Public Shared Function AFirstRSecond(  
    ByVal first As First) As Second  
    Return New Second()  
End Function  
```  
  
 <span data-ttu-id="2d718-108">下列程式碼範例說明的方法簽章與委派型別之間隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="2d718-108">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>  
  
```vb  
' Assigning a method with a matching signature   
' to a non-generic delegate. No conversion is necessary.  
Dim dNonGeneric As SampleDelegate = AddressOf ASecondRFirst  
' Assigning a method with a more derived return type   
' and less derived argument type to a non-generic delegate.  
' The implicit conversion is used.  
Dim dNonGenericConversion As SampleDelegate = AddressOf AFirstRSecond  
  
' Assigning a method with a matching signature to a generic delegate.  
' No conversion is necessary.  
Dim dGeneric As SampleGenericDelegate(Of Second, First) = AddressOf ASecondRFirst  
' Assigning a method with a more derived return type   
' and less derived argument type to a generic delegate.  
' The implicit conversion is used.  
Dim dGenericConversion As SampleGenericDelegate(Of Second, First) = AddressOf AFirstRSecond  
```  
  
 <span data-ttu-id="2d718-109">如需詳細資訊，請參閱[使用委派 (Visual Basic) 中的變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)和[Func 與 Action 委派 (Visual Basic) 使用變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="2d718-109">For more examples, see [Using Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="2d718-110">泛型型別參數中的變異數</span><span class="sxs-lookup"><span data-stu-id="2d718-110">Variance in Generic Type Parameters</span></span>  
 <span data-ttu-id="2d718-111">在.NET Framework 4 和更新版本可以啟用委派之間的隱含轉換，因此可以有不同類型的泛型型別參數所指定的泛型委派指派給彼此，如果型別繼承自其他所需的變異數。</span><span class="sxs-lookup"><span data-stu-id="2d718-111">In .NET Framework 4 and later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>  
  
 <span data-ttu-id="2d718-112">若要啟用的隱含轉換，您必須明確宣告泛用參數中的委派做為 covariant 或 contravariant 使用`in`或`out`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="2d718-112">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>  
  
 <span data-ttu-id="2d718-113">下列程式碼範例示範如何建立具有共變性泛型型別參數的委派。</span><span class="sxs-lookup"><span data-stu-id="2d718-113">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>  
  
```vb  
' Type T is declared covariant by using the out keyword.  
Public Delegate Function SampleGenericDelegate(Of Out T)() As T  
Sub Test()  
    Dim dString As SampleGenericDelegate(Of String) = Function() " "  
    ' You can assign delegates to each other,  
    ' because the type T is declared covariant.  
    Dim dObject As SampleGenericDelegate(Of Object) = dString  
End Sub  
```  
  
 <span data-ttu-id="2d718-114">如果您使用唯一的差異支援比對方法簽章與委派型別，並且不要使用`in`和`out`關鍵字，您可能會發現有時候執行個體化使用相同的 lambda 運算式或方法的委派，但您無法將一個委派指派給另一個。</span><span class="sxs-lookup"><span data-stu-id="2d718-114">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>  
  
 <span data-ttu-id="2d718-115">在下列程式碼範例中，`SampleGenericDelegate(Of String)`無法明確地轉換成`SampleGenericDelegate(Of Object)`，不過`String`繼承`Object`。</span><span class="sxs-lookup"><span data-stu-id="2d718-115">In the following code example, `SampleGenericDelegate(Of String)` can't be explicitly converted to `SampleGenericDelegate(Of Object)`, although `String` inherits `Object`.</span></span> <span data-ttu-id="2d718-116">您可以修正這個問題，是將泛型參數標記`T`與`out`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="2d718-116">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>  
  
```vb  
Public Delegate Function SampleGenericDelegate(Of T)() As T  
Sub Test()  
    Dim dString As SampleGenericDelegate(Of String) = Function() " "  
  
    ' You can assign the dObject delegate  
    ' to the same lambda expression as dString delegate  
    ' because of the variance support for   
    ' matching method signatures with delegate types.  
    Dim dObject As SampleGenericDelegate(Of Object) = Function() " "  
  
    ' The following statement generates a compiler error  
    ' because the generic type T is not marked as covariant.  
    ' Dim dObject As SampleGenericDelegate(Of Object) = dString  
  
End Sub  
```  
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a><span data-ttu-id="2d718-117">在具有變異的泛型委派在.NET Framework 型別參數</span><span class="sxs-lookup"><span data-stu-id="2d718-117">Generic Delegates That Have Variant Type Parameters in the .NET Framework</span></span>  
 <span data-ttu-id="2d718-118">.NET framework 4 引入變異數支援數個現有的泛型委派中的泛型型別參數︰</span><span class="sxs-lookup"><span data-stu-id="2d718-118">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>  
  
-   <span data-ttu-id="2d718-119">`Action`從委派<xref:System>命名空間，例如<xref:System.Action%601>和<xref:System.Action%602></xref:System.Action%602></xref:System.Action%601></xref:System></span><span class="sxs-lookup"><span data-stu-id="2d718-119">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>  
  
-   <span data-ttu-id="2d718-120">`Func`從委派<xref:System>命名空間，例如<xref:System.Func%601>和<xref:System.Func%602></xref:System.Func%602></xref:System.Func%601></xref:System></span><span class="sxs-lookup"><span data-stu-id="2d718-120">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>  
  
-   <span data-ttu-id="2d718-121"><xref:System.Predicate%601>委派</xref:System.Predicate%601></span><span class="sxs-lookup"><span data-stu-id="2d718-121">The <xref:System.Predicate%601> delegate</span></span>  
  
-   <span data-ttu-id="2d718-122"><xref:System.Comparison%601>委派</xref:System.Comparison%601></span><span class="sxs-lookup"><span data-stu-id="2d718-122">The <xref:System.Comparison%601> delegate</span></span>  
  
-   <span data-ttu-id="2d718-123"><xref:System.Converter%602>委派</xref:System.Converter%602></span><span class="sxs-lookup"><span data-stu-id="2d718-123">The <xref:System.Converter%602> delegate</span></span>  
  
 <span data-ttu-id="2d718-124">如需詳細資訊和範例，請參閱[Func 與 Action 委派 (Visual Basic) 使用變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="2d718-124">For more information and examples, see [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="2d718-125">宣告泛型委派中的 Variant 類型參數</span><span class="sxs-lookup"><span data-stu-id="2d718-125">Declaring Variant Type Parameters in Generic Delegates</span></span>  
 <span data-ttu-id="2d718-126">如果泛型委派具有 covariant 或 contravariant 的泛型型別參數，它可以稱為*variant 泛型委派*。</span><span class="sxs-lookup"><span data-stu-id="2d718-126">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>  
  
 <span data-ttu-id="2d718-127">您可以宣告泛型型別參數中的泛型委派的共變數使用`out`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="2d718-127">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="2d718-128">可以使用 covariant 類型，只要方法的傳回型別，而不是一種方法引數。</span><span class="sxs-lookup"><span data-stu-id="2d718-128">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="2d718-129">下列程式碼範例示範如何宣告共變性泛型委派。</span><span class="sxs-lookup"><span data-stu-id="2d718-129">The following code example shows how to declare a covariant generic delegate.</span></span>  
  
<span data-ttu-id="2d718-130"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="2d718-130"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="2d718-131">您可以使用宣告中的泛型委派的泛型型別參數 contravariant`in`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="2d718-131">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="2d718-132">可以使用 contravariant 類型，只為方法引數的型別，而不是方法的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="2d718-132">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="2d718-133">下列程式碼範例示範如何宣告 contravariant 的泛型委派。</span><span class="sxs-lookup"><span data-stu-id="2d718-133">The following code example shows how to declare a contravariant generic delegate.</span></span>  
  
<span data-ttu-id="2d718-134"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="2d718-134"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span></span>  
> [!IMPORTANT]
> <span data-ttu-id="2d718-135"> `ByRef`在 Visual Basic 中的參數不能標示為 variant。</span><span class="sxs-lookup"><span data-stu-id="2d718-135"> `ByRef` parameters in Visual Basic can't be marked as variant.</span></span>  
  
 <span data-ttu-id="2d718-136">此外，也可以在相同的委派，但不同的型別參數支援共變數和變異數。</span><span class="sxs-lookup"><span data-stu-id="2d718-136">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="2d718-137">這在下列範例中顯示。</span><span class="sxs-lookup"><span data-stu-id="2d718-137">This is shown in the following example.</span></span>  
  
<span data-ttu-id="2d718-138"><CodeContentPlaceHolder>7</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="2d718-138"><CodeContentPlaceHolder>7</CodeContentPlaceHolder></span></span>  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="2d718-139">具現化，並叫用 Variant 泛型委派</span><span class="sxs-lookup"><span data-stu-id="2d718-139">Instantiating and Invoking Variant Generic Delegates</span></span>  
 <span data-ttu-id="2d718-140">您可以具現化，並叫用 variant 的委派，就像您具現化，並叫用委派而異。</span><span class="sxs-lookup"><span data-stu-id="2d718-140">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="2d718-141">在下列範例中，委派是 lambda 運算式所具現化。</span><span class="sxs-lookup"><span data-stu-id="2d718-141">In the following example, the delegate is instantiated by a lambda expression.</span></span>  
  
<span data-ttu-id="2d718-142"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="2d718-142"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span></span>  
### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="2d718-143">結合 Variant 泛型委派</span><span class="sxs-lookup"><span data-stu-id="2d718-143">Combining Variant Generic Delegates</span></span>  
 <span data-ttu-id="2d718-144">您不應該結合 variant 的委派。</span><span class="sxs-lookup"><span data-stu-id="2d718-144">You should not combine variant delegates.</span></span> <span data-ttu-id="2d718-145"><xref:System.Delegate.Combine%2A>方法不支援 variant 委派轉換，而且必須是相同類型的委派。</xref:System.Delegate.Combine%2A></span><span class="sxs-lookup"><span data-stu-id="2d718-145">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="2d718-146">這可能會導致執行階段例外狀況時結合使用委派<xref:System.Delegate.Combine%2A>方法 （在 C# 和 Visual Basic） 或使用`+`運算子 （C# 中），如下列程式碼範例所示。</xref:System.Delegate.Combine%2A></span><span class="sxs-lookup"><span data-stu-id="2d718-146">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method (in C# and Visual Basic) or by using the `+` operator (in C#), as shown in the following code example.</span></span>  
  
<span data-ttu-id="2d718-147"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="2d718-147"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span></span>  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="2d718-148">泛型型別參數的值和參考類型的變異數</span><span class="sxs-lookup"><span data-stu-id="2d718-148">Variance in Generic Type Parameters for Value and Reference Types</span></span>  
 <span data-ttu-id="2d718-149">參考型別只支援泛型型別參數的變異數。</span><span class="sxs-lookup"><span data-stu-id="2d718-149">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="2d718-150">例如，`DVariant(Of Int)`無法隱含地轉換成`DVariant(Of Object)`或`DVariant(Of Long)`，因為整數是實值型別。</span><span class="sxs-lookup"><span data-stu-id="2d718-150">For example, `DVariant(Of Int)`can't be implicitly converted to `DVariant(Of Object)` or `DVariant(Of Long)`, because integer is a value type.</span></span>  
  
 <span data-ttu-id="2d718-151">下列範例示範的變異數的泛型型別參數不支援實值型別。</span><span class="sxs-lookup"><span data-stu-id="2d718-151">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>  
  
```vb  
' The type T is covariant.  
Public Delegate Function DVariant(Of Out T)() As T  
' The type T is invariant.  
Public Delegate Function DInvariant(Of T)() As T  
Sub Test()  
    Dim i As Integer = 0  
    Dim dInt As DInvariant(Of Integer) = Function() i  
    Dim dVaraintInt As DVariant(Of Integer) = Function() i  
  
    ' All of the following statements generate a compiler error  
    ' because type variance in generic parameters is not supported  
    ' for value types, even if generic type parameters are declared variant.  
    ' Dim dObject As DInvariant(Of Object) = dInt  
    ' Dim dLong As DInvariant(Of Long) = dInt  
    ' Dim dVaraintObject As DInvariant(Of Object) = dInt  
    ' Dim dVaraintLong As DInvariant(Of Long) = dInt  
End Sub  
```  
  
## <a name="relaxed-delegate-conversion-in-visual-basic"></a><span data-ttu-id="2d718-152">在 Visual Basic 中寬鬆的委派轉換</span><span class="sxs-lookup"><span data-stu-id="2d718-152">Relaxed Delegate Conversion in Visual Basic</span></span>  
 <span data-ttu-id="2d718-153">寬鬆的委派轉換可讓您更靈活地使用委派型別比對方法簽章。</span><span class="sxs-lookup"><span data-stu-id="2d718-153">Relaxed delegate conversion enables more flexibility in matching method signatures with delegate types.</span></span> <span data-ttu-id="2d718-154">比方說，它可讓您省略參數規格，並省略函式傳回值，當您指派給委派的方法。</span><span class="sxs-lookup"><span data-stu-id="2d718-154">For example, it lets you omit parameter specifications and omit function return values when you assign a method to a delegate.</span></span> <span data-ttu-id="2d718-155">如需詳細資訊，請參閱[寬鬆委派轉換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。</span><span class="sxs-lookup"><span data-stu-id="2d718-155">For more information, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d718-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d718-156">See Also</span></span>  
 <span data-ttu-id="2d718-157">[泛型](https://msdn.microsoft.com/library/ms172192) </span><span class="sxs-lookup"><span data-stu-id="2d718-157">[Generics](https://msdn.microsoft.com/library/ms172192) </span></span>  
<span data-ttu-id="2d718-158"> [針對 Func 與 Action 委派 (Visual Basic) 中使用變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)</span><span class="sxs-lookup"><span data-stu-id="2d718-158"> [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)</span></span>
