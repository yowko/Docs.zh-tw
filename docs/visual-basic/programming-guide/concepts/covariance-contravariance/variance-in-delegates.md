---
title: 委派 (Visual Basic) 中的變異數
ms.date: 07/20/2015
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
ms.openlocfilehash: 350f8d6b317f6a82d5b5a718a3d49a4b9ee3e4b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631538"
---
# <a name="variance-in-delegates-visual-basic"></a><span data-ttu-id="8e60c-102">委派 (Visual Basic) 中的變異數</span><span class="sxs-lookup"><span data-stu-id="8e60c-102">Variance in Delegates (Visual Basic)</span></span>
<span data-ttu-id="8e60c-103">.NET framework 3.5 推出差異支援，方法簽章相符的委派型別中的所有委派中使用C#和 Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="8e60c-103">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C# and Visual Basic.</span></span> <span data-ttu-id="8e60c-104">這表示您可以指派給委派的不只是具有相符簽章的方法，也可以是會傳回更多衍生型別 (共變數) 的方法，或接受衍生型別 (反變數) 比委派型別指定少的參數的方法。</span><span class="sxs-lookup"><span data-stu-id="8e60c-104">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="8e60c-105">這包括泛型和非泛型委派。</span><span class="sxs-lookup"><span data-stu-id="8e60c-105">This includes both generic and non-generic delegates.</span></span>  
  
 <span data-ttu-id="8e60c-106">例如，請考慮下列程式碼，有兩個類別和兩個委派︰泛型和非泛型。</span><span class="sxs-lookup"><span data-stu-id="8e60c-106">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>  
  
```vb  
Public Class First  
End Class  
  
Public Class Second  
    Inherits First  
End Class  
  
Public Delegate Function SampleDelegate(ByVal a As Second) As First  
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R  
```  
  
 <span data-ttu-id="8e60c-107">當您建立 `SampleDelegate` 或 `SampleDelegate(Of A, R)` 型別的委派時，您可以指派下列任一方法給這些委派。</span><span class="sxs-lookup"><span data-stu-id="8e60c-107">When you create delegates of the `SampleDelegate` or `SampleDelegate(Of A, R)` types, you can assign any one of the following methods to those delegates.</span></span>  
  
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
  
 <span data-ttu-id="8e60c-108">下列程式碼範例會示範方法簽章與委派型別之間的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="8e60c-108">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>  
  
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
  
 <span data-ttu-id="8e60c-109">如需其他範例，請參閱 <<c0> [ 使用委派 (Visual Basic) 中的變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)並[針對 Func 與 Action 泛型委派 (Visual Basic) 使用差異](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="8e60c-109">For more examples, see [Using Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="8e60c-110">泛型型別參數中的差異</span><span class="sxs-lookup"><span data-stu-id="8e60c-110">Variance in Generic Type Parameters</span></span>  
 <span data-ttu-id="8e60c-111">在.NET Framework 4 和更新版本，以便具有泛型型別參數所指定的不同類型的泛型委派可以指派給彼此，如果所需的類型繼承自彼此，您可以啟用委派之間的隱含轉換變異數。</span><span class="sxs-lookup"><span data-stu-id="8e60c-111">In .NET Framework 4 and later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>  
  
 <span data-ttu-id="8e60c-112">若要啟用隱含轉換，您必須使用 `in` 或 `out` 關鍵字，明確宣告委派中的泛型參數為 Covariant 或 Contravariant。</span><span class="sxs-lookup"><span data-stu-id="8e60c-112">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>  
  
 <span data-ttu-id="8e60c-113">下列程式碼範例示範如何建立具有 Covariant 泛型型別參數的委派。</span><span class="sxs-lookup"><span data-stu-id="8e60c-113">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>  
  
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
  
 <span data-ttu-id="8e60c-114">如果您使用唯一的差異支援來比對方法簽章與委派型別，請不要使用 `in` 和 `out` 關鍵字，因為您會發現，有時候您會使用相同的 lambda 運算式或方法具現化委派，但無法將一個委派指派給另一個。</span><span class="sxs-lookup"><span data-stu-id="8e60c-114">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>  
  
 <span data-ttu-id="8e60c-115">在下列程式碼範例中，`SampleGenericDelegate(Of String)`無法明確地轉換成`SampleGenericDelegate(Of Object)`，雖然`String`繼承`Object`。</span><span class="sxs-lookup"><span data-stu-id="8e60c-115">In the following code example, `SampleGenericDelegate(Of String)` can't be explicitly converted to `SampleGenericDelegate(Of Object)`, although `String` inherits `Object`.</span></span> <span data-ttu-id="8e60c-116">您可以使用 `out` 關鍵字標記泛型參數 `T`，修正這個問題。</span><span class="sxs-lookup"><span data-stu-id="8e60c-116">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a><span data-ttu-id="8e60c-117">.NET Framework 中具有 Variant 型別參數的泛型委派</span><span class="sxs-lookup"><span data-stu-id="8e60c-117">Generic Delegates That Have Variant Type Parameters in the .NET Framework</span></span>  
 <span data-ttu-id="8e60c-118">.NET Framework 4 推出差異支援，適用於數個現有泛型委派中的泛型型別參數：</span><span class="sxs-lookup"><span data-stu-id="8e60c-118">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>  
  
-   <span data-ttu-id="8e60c-119"><xref:System> 命名空間中的 `Action` 委派，例如 <xref:System.Action%601> 和 <xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="8e60c-119">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>  
  
-   <span data-ttu-id="8e60c-120"><xref:System> 命名空間中的 `Func` 委派，例如 <xref:System.Func%601> 和 <xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="8e60c-120">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>  
  
-   <span data-ttu-id="8e60c-121"><xref:System.Predicate%601> 委派</span><span class="sxs-lookup"><span data-stu-id="8e60c-121">The <xref:System.Predicate%601> delegate</span></span>  
  
-   <span data-ttu-id="8e60c-122"><xref:System.Comparison%601> 委派</span><span class="sxs-lookup"><span data-stu-id="8e60c-122">The <xref:System.Comparison%601> delegate</span></span>  
  
-   <span data-ttu-id="8e60c-123"><xref:System.Converter%602> 委派</span><span class="sxs-lookup"><span data-stu-id="8e60c-123">The <xref:System.Converter%602> delegate</span></span>  
  
 <span data-ttu-id="8e60c-124">如需詳細資訊和範例，請參閱 <<c0> [ 針對 Func 與 Action 泛型委派 (Visual Basic) 使用差異](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="8e60c-124">For more information and examples, see [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="8e60c-125">宣告泛型委派中的 Variant 型別參數</span><span class="sxs-lookup"><span data-stu-id="8e60c-125">Declaring Variant Type Parameters in Generic Delegates</span></span>  
 <span data-ttu-id="8e60c-126">如果泛型委派具有 Covariant 或 Contravariant 泛型型別參數，它可以稱之為「Variant 泛型委派」。</span><span class="sxs-lookup"><span data-stu-id="8e60c-126">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>  
  
 <span data-ttu-id="8e60c-127">您可以使用 `out` 關鍵字將泛型委派中的泛型型別參數宣告為 Covariant。</span><span class="sxs-lookup"><span data-stu-id="8e60c-127">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="8e60c-128">Covariant 型別僅可用為方法傳回型別，不能用為方法引數的型別。</span><span class="sxs-lookup"><span data-stu-id="8e60c-128">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="8e60c-129">以下程式碼範例會示範如何宣告 Covariant 泛型委派。</span><span class="sxs-lookup"><span data-stu-id="8e60c-129">The following code example shows how to declare a covariant generic delegate.</span></span>  
  
```vb  
Public Delegate Function DCovariant(Of Out R)() As R  
```  
  
 <span data-ttu-id="8e60c-130">您可以使用 `in` 關鍵字將泛型委派中的泛型型別參數宣告為 Contravariant。</span><span class="sxs-lookup"><span data-stu-id="8e60c-130">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="8e60c-131">Contravariant 型別僅可用為方法引數的型別，不能用為方法傳回型別。</span><span class="sxs-lookup"><span data-stu-id="8e60c-131">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="8e60c-132">以下程式碼範例會示範如何宣告 Contravariant 泛型委派。</span><span class="sxs-lookup"><span data-stu-id="8e60c-132">The following code example shows how to declare a contravariant generic delegate.</span></span>  
  
```vb  
Public Delegate Sub DContravariant(Of In A)(ByVal a As A)  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="8e60c-133">`ByRef` 在 Visual Basic 中的參數不能標示為 variant。</span><span class="sxs-lookup"><span data-stu-id="8e60c-133">`ByRef` parameters in Visual Basic can't be marked as variant.</span></span>  
  
 <span data-ttu-id="8e60c-134">您也可以支援相同委派中不同型別參數的差異和共變數。</span><span class="sxs-lookup"><span data-stu-id="8e60c-134">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="8e60c-135">這在下列範例中顯示。</span><span class="sxs-lookup"><span data-stu-id="8e60c-135">This is shown in the following example.</span></span>  
  
```vb  
Public Delegate Function DVariant(Of In A, Out R)(ByVal a As A) As R  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="8e60c-136">具現化及叫用 Variant 泛型委派</span><span class="sxs-lookup"><span data-stu-id="8e60c-136">Instantiating and Invoking Variant Generic Delegates</span></span>  
 <span data-ttu-id="8e60c-137">您可以具現化及叫用 Variant 委派，一如您具現化及叫用非變異委派。</span><span class="sxs-lookup"><span data-stu-id="8e60c-137">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="8e60c-138">在下例中，委派是由 lambda 運算式具現化。</span><span class="sxs-lookup"><span data-stu-id="8e60c-138">In the following example, the delegate is instantiated by a lambda expression.</span></span>  
  
```vb  
Dim dvariant As DVariant(Of String, String) = Function(str) str + " "  
dvariant("test")  
```  
  
### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="8e60c-139">結合 Variant 泛型委派</span><span class="sxs-lookup"><span data-stu-id="8e60c-139">Combining Variant Generic Delegates</span></span>  
 <span data-ttu-id="8e60c-140">您不應該組合 Variant 委派。</span><span class="sxs-lookup"><span data-stu-id="8e60c-140">You should not combine variant delegates.</span></span> <span data-ttu-id="8e60c-141"><xref:System.Delegate.Combine%2A> 方法不支援 Variant 委派轉換，且委派的類型必須完全一致。</span><span class="sxs-lookup"><span data-stu-id="8e60c-141">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="8e60c-142">這會導致執行階段例外狀況時結合使用的委派<xref:System.Delegate.Combine%2A>方法 (在C#和 Visual Basic) 或使用`+`運算子 (在C#)，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="8e60c-142">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method (in C# and Visual Basic) or by using the `+` operator (in C#), as shown in the following code example.</span></span>  
  
```vb  
Dim actObj As Action(Of Object) = Sub(x) Console.WriteLine("object: {0}", x)  
Dim actStr As Action(Of String) = Sub(x) Console.WriteLine("string: {0}", x)  
  
' The following statement throws an exception at run time.  
' Dim actCombine = [Delegate].Combine(actStr, actObj)  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="8e60c-143">實值型別和參考型別的泛型型別參數中的差異</span><span class="sxs-lookup"><span data-stu-id="8e60c-143">Variance in Generic Type Parameters for Value and Reference Types</span></span>  
 <span data-ttu-id="8e60c-144">僅參考型別支援泛型型別參數的差異。</span><span class="sxs-lookup"><span data-stu-id="8e60c-144">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="8e60c-145">例如，`DVariant(Of Int)`無法隱含地轉換成`DVariant(Of Object)`或`DVariant(Of Long)`，因為整數是實值型別。</span><span class="sxs-lookup"><span data-stu-id="8e60c-145">For example, `DVariant(Of Int)`can't be implicitly converted to `DVariant(Of Object)` or `DVariant(Of Long)`, because integer is a value type.</span></span>  
  
 <span data-ttu-id="8e60c-146">下例示範實值型別不支援的泛型型別參數的差異。</span><span class="sxs-lookup"><span data-stu-id="8e60c-146">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>  
  
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
  
## <a name="relaxed-delegate-conversion-in-visual-basic"></a><span data-ttu-id="8e60c-147">在 Visual Basic 中的寬鬆的委派轉換</span><span class="sxs-lookup"><span data-stu-id="8e60c-147">Relaxed Delegate Conversion in Visual Basic</span></span>  
 <span data-ttu-id="8e60c-148">寬鬆的委派轉換可讓更多的彈性，在方法簽章與委派類型相符。</span><span class="sxs-lookup"><span data-stu-id="8e60c-148">Relaxed delegate conversion enables more flexibility in matching method signatures with delegate types.</span></span> <span data-ttu-id="8e60c-149">比方說，它可讓您省略參數規格，並省略函式傳回值，當您指派給委派的方法。</span><span class="sxs-lookup"><span data-stu-id="8e60c-149">For example, it lets you omit parameter specifications and omit function return values when you assign a method to a delegate.</span></span> <span data-ttu-id="8e60c-150">如需詳細資訊，請參閱 <<c0> [ 寬鬆委派轉換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。</span><span class="sxs-lookup"><span data-stu-id="8e60c-150">For more information, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e60c-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e60c-151">See also</span></span>
- [<span data-ttu-id="8e60c-152">泛型</span><span class="sxs-lookup"><span data-stu-id="8e60c-152">Generics</span></span>](~/docs/standard/generics/index.md)
- [<span data-ttu-id="8e60c-153">針對 Func 與 Action 泛型委派使用變異數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e60c-153">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
