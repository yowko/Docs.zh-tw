---
title: 共變數和反變數 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 59224c46-9931-466b-8c6e-3648c3e609c6
ms.openlocfilehash: 241b8f5864b6e9b3e1caddde25d032a24e4d0bb7
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850448"
---
# <a name="covariance-and-contravariance-visual-basic"></a><span data-ttu-id="9d7f1-102">共變數和反變數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d7f1-102">Covariance and Contravariance (Visual Basic)</span></span>
<span data-ttu-id="9d7f1-103">在 Visual Basic 中，共變數和反變數可讓您進行陣列類型、委派類型和泛型型別引數的隱含參考轉換。</span><span class="sxs-lookup"><span data-stu-id="9d7f1-103">In Visual Basic, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="9d7f1-104">共變數會保留指派相容性，而反變數則會將它反轉。</span><span class="sxs-lookup"><span data-stu-id="9d7f1-104">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>  
  
 <span data-ttu-id="9d7f1-105">下列程式碼示範指派相容性、共變數和反變數之間的差異。</span><span class="sxs-lookup"><span data-stu-id="9d7f1-105">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>  
  
```vb  
' Assignment compatibility.   
Dim str As String = "test"  
' An object of a more derived type is assigned to an object of a less derived type.   
Dim obj As Object = str  
  
' Covariance.   
Dim strings As IEnumerable(Of String) = New List(Of String)()  
' An object that is instantiated with a more derived type argument   
' is assigned to an object instantiated with a less derived type argument.   
' Assignment compatibility is preserved.   
Dim objects As IEnumerable(Of Object) = strings  
  
' Contravariance.             
' Assume that there is the following method in the class:   
' Shared Sub SetObject(ByVal o As Object)  
' End Sub  
Dim actObject As Action(Of Object) = AddressOf SetObject  
  
' An object that is instantiated with a less derived type argument   
' is assigned to an object instantiated with a more derived type argument.   
' Assignment compatibility is reversed.   
Dim actString As Action(Of String) = actObject  
```  
  
 <span data-ttu-id="9d7f1-106">陣列的共變數可將衍生程度較大類型的陣列，隱含轉換成衍生程度較小類型的陣列。</span><span class="sxs-lookup"><span data-stu-id="9d7f1-106">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="9d7f1-107">但這項作業不是型別安全的，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="9d7f1-107">But this operation is not type safe, as shown in the following code example.</span></span>  
  
```vb  
Dim array() As Object = New String(10) {}  
' The following statement produces a run-time exception.  
' array(0) = 10  
```  
  
 <span data-ttu-id="9d7f1-108">共變數和反變數的方法群組支援可讓您比對方法簽章和委派類型。</span><span class="sxs-lookup"><span data-stu-id="9d7f1-108">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="9d7f1-109">這可讓您指派方法給委派，不只是具有相符簽章的方法，也可以是會傳回衍生程度較大類型 (共變數) 的方法，或接受衍生程度比委派類型所指定更小類型 (反變數) 的方法。</span><span class="sxs-lookup"><span data-stu-id="9d7f1-109">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="9d7f1-110">如需詳細資訊，請參閱[委派中的變異數 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) 和[在委派中使用變異數 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="9d7f1-110">For more information, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="9d7f1-111">下列程式碼範例示範共變數和反變數的方法群組支援。</span><span class="sxs-lookup"><span data-stu-id="9d7f1-111">The following code example shows covariance and contravariance support for method groups.</span></span>  
  
```vb  
Shared Function GetObject() As Object  
    Return Nothing  
End Function  
  
Shared Sub SetObject(ByVal obj As Object)  
End Sub  
  
Shared Function GetString() As String  
    Return ""  
End Function  
  
Shared Sub SetString(ByVal str As String)  
  
End Sub  
  
Shared Sub Test()  
    ' Covariance. A delegate specifies a return type as object,  
    ' but you can assign a method that returns a string.  
    Dim del As Func(Of Object) = AddressOf GetString  
  
    ' Contravariance. A delegate specifies a parameter type as string,  
    ' but you can assign a method that takes an object.  
    Dim del2 As Action(Of String) = AddressOf SetObject  
End Sub  
```  
  
 <span data-ttu-id="9d7f1-112">在.NET Framework 4 或更新版本，Visual Basic 支援泛型介面及委派中的共變性與逆變性，並允許泛型類型參數的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="9d7f1-112">In .NET Framework 4 or later, Visual Basic supports covariance and contravariance in generic interfaces and delegates and allows for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="9d7f1-113">如需詳細資訊，請參閱[泛型介面中的變異數 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) 和[委派中的變異數 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="9d7f1-113">For more information, see [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="9d7f1-114">下列程式碼範例示範泛型介面的隱含參考轉換。</span><span class="sxs-lookup"><span data-stu-id="9d7f1-114">The following code example shows implicit reference conversion for generic interfaces.</span></span>  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 <span data-ttu-id="9d7f1-115">如果泛型介面或委派的泛型參數宣告為共變數或反變數，此泛型介面或委派稱為 *variant*。</span><span class="sxs-lookup"><span data-stu-id="9d7f1-115">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="9d7f1-116">Visual Basic 可讓您建立自己的 Variant 介面和委派。</span><span class="sxs-lookup"><span data-stu-id="9d7f1-116">Visual Basic enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="9d7f1-117">如需詳細資訊，請參閱[建立 Variant 泛型介面 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) 和[委派中的變異數 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="9d7f1-117">For more information, see [Creating Variant Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="9d7f1-118">相關主題</span><span class="sxs-lookup"><span data-stu-id="9d7f1-118">Related Topics</span></span>  
  
|<span data-ttu-id="9d7f1-119">標題</span><span class="sxs-lookup"><span data-stu-id="9d7f1-119">Title</span></span>|<span data-ttu-id="9d7f1-120">描述</span><span class="sxs-lookup"><span data-stu-id="9d7f1-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="9d7f1-121">泛型介面中的變異數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d7f1-121">Variance in Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|<span data-ttu-id="9d7f1-122">討論泛型介面中的共變性與逆變性，並提供.NET Framework 中的 Variant 泛型介面清單。</span><span class="sxs-lookup"><span data-stu-id="9d7f1-122">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|  
|[<span data-ttu-id="9d7f1-123">建立 Variant 泛型介面 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d7f1-123">Creating Variant Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|<span data-ttu-id="9d7f1-124">示範如何建立自訂 Variant 介面。</span><span class="sxs-lookup"><span data-stu-id="9d7f1-124">Shows how to create custom variant interfaces.</span></span>|  
|[<span data-ttu-id="9d7f1-125">使用泛型集合介面中的變異數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d7f1-125">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="9d7f1-126">示範 <xref:System.Collections.Generic.IEnumerable%601> 和 <xref:System.IComparable%601> 介面中的共變數和反變數支援如何協助您重複使用程式碼。</span><span class="sxs-lookup"><span data-stu-id="9d7f1-126">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|  
|[<span data-ttu-id="9d7f1-127">委派中的變異數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d7f1-127">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|<span data-ttu-id="9d7f1-128">討論泛型和非泛型委派中的共變性和反變數，並提供 .NET Framework 中的 Variant 泛型委派清單。</span><span class="sxs-lookup"><span data-stu-id="9d7f1-128">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|  
|[<span data-ttu-id="9d7f1-129">使用委派中的變異數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d7f1-129">Using Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|<span data-ttu-id="9d7f1-130">示範如何在非泛型委派中使用共變數和反變數支援，以比對方法簽章和委派類型。</span><span class="sxs-lookup"><span data-stu-id="9d7f1-130">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|  
|[<span data-ttu-id="9d7f1-131">針對 Func 與 Action 泛型委派使用變異數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d7f1-131">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="9d7f1-132">示範 `Func` 和 `Action` 委派中的共變數和反變數支援如何協助您重複使用程式碼。</span><span class="sxs-lookup"><span data-stu-id="9d7f1-132">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
