---
title: "泛型介面 (Visual Basic) 中的變異數 |Microsoft 文件"
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
ms.assetid: cf4096d0-4bb3-45a9-9a6b-f01e29a60333
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
ms.openlocfilehash: c53c27bdb085213046553fc4b08f11336880a7c2
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="variance-in-generic-interfaces-visual-basic"></a><span data-ttu-id="3174a-102">泛型介面 (Visual Basic) 中的變異數</span><span class="sxs-lookup"><span data-stu-id="3174a-102">Variance in Generic Interfaces (Visual Basic)</span></span>
<span data-ttu-id="3174a-103">.NET framework 4 引入變異數支援數個現有的泛型介面。</span><span class="sxs-lookup"><span data-stu-id="3174a-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="3174a-104">變異數支援可讓實作這些介面的類別的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="3174a-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> <span data-ttu-id="3174a-105">下列介面是現在變異︰</span><span class="sxs-lookup"><span data-stu-id="3174a-105">The following interfaces are now variant:</span></span>  
  
-   <span data-ttu-id="3174a-106"><xref:System.Collections.Generic.IEnumerable%601>（T 是共變數）</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="3174a-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="3174a-107"><xref:System.Collections.Generic.IEnumerator%601>（T 是共變數）</xref:System.Collections.Generic.IEnumerator%601></span><span class="sxs-lookup"><span data-stu-id="3174a-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="3174a-108"><xref:System.Linq.IQueryable%601>（T 是共變數）</xref:System.Linq.IQueryable%601></span><span class="sxs-lookup"><span data-stu-id="3174a-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="3174a-109"><xref:System.Linq.IGrouping%602>(`TKey`和`TElement`都是共變數)</xref:System.Linq.IGrouping%602></span><span class="sxs-lookup"><span data-stu-id="3174a-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>  
  
-   <span data-ttu-id="3174a-110"><xref:System.Collections.Generic.IComparer%601>（T 是 contravariant）</xref:System.Collections.Generic.IComparer%601></span><span class="sxs-lookup"><span data-stu-id="3174a-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="3174a-111"><xref:System.Collections.Generic.IEqualityComparer%601>（T 是 contravariant）</xref:System.Collections.Generic.IEqualityComparer%601></span><span class="sxs-lookup"><span data-stu-id="3174a-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="3174a-112"><xref:System.IComparable%601>（T 是 contravariant）</xref:System.IComparable%601></span><span class="sxs-lookup"><span data-stu-id="3174a-112"><xref:System.IComparable%601> (T is contravariant)</span></span>  
  
 <span data-ttu-id="3174a-113">共變數允許具有衍生程度較大的傳回型別比介面的泛型型別參數所定義的方法。</span><span class="sxs-lookup"><span data-stu-id="3174a-113">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="3174a-114">若要說明共變異數項功能，請考慮下列這些泛型介面︰`IEnumerable(Of Object)`和`IEnumerable(Of String)`。</span><span class="sxs-lookup"><span data-stu-id="3174a-114">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable(Of Object)` and `IEnumerable(Of String)`.</span></span> <span data-ttu-id="3174a-115">`IEnumerable(Of String)`介面不會繼承`IEnumerable(Of Object)`介面。</span><span class="sxs-lookup"><span data-stu-id="3174a-115">The `IEnumerable(Of String)` interface does not inherit the `IEnumerable(Of Object)` interface.</span></span> <span data-ttu-id="3174a-116">不過，`String`型別會繼承`Object`型別，在某些情況下，您可以將這些介面的物件指派給彼此。</span><span class="sxs-lookup"><span data-stu-id="3174a-116">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="3174a-117">這都是以下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="3174a-117">This is shown in the following code example.</span></span>  
  
<span data-ttu-id="3174a-118"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="3174a-118"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="3174a-119">在舊版的.NET Framework 中，此程式碼會造成編譯錯誤，在 Visual Basic `Option Strict On`。</span><span class="sxs-lookup"><span data-stu-id="3174a-119">In earlier versions of the .NET Framework, this code causes a compilation error in Visual Basic with `Option Strict On`.</span></span> <span data-ttu-id="3174a-120">但現在您可以使用`strings`而不是`objects`如上述範例中，因為<xref:System.Collections.Generic.IEnumerable%601>介面是 covariant。</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="3174a-120">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>  
  
 <span data-ttu-id="3174a-121">反變數允許擁有較少衍生的介面的泛型參數所指定的引數型別方法。</span><span class="sxs-lookup"><span data-stu-id="3174a-121">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="3174a-122">為了說明反變數，我們假設您已建立`BaseComparer`類別的執行個體的比較`BaseClass`類別。</span><span class="sxs-lookup"><span data-stu-id="3174a-122">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="3174a-123">`BaseComparer` 類別會實作 `IEqualityComparer(Of BaseClass)` 介面。</span><span class="sxs-lookup"><span data-stu-id="3174a-123">The `BaseComparer` class implements the `IEqualityComparer(Of BaseClass)` interface.</span></span> <span data-ttu-id="3174a-124">因為<xref:System.Collections.Generic.IEqualityComparer%601>介面現在是反變數，您可以使用`BaseComparer`比較繼承的類別的執行個體`BaseClass`類別</xref:System.Collections.Generic.IEqualityComparer%601></span><span class="sxs-lookup"><span data-stu-id="3174a-124">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="3174a-125">這都是以下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="3174a-125">This is shown in the following code example.</span></span>  
  
<span data-ttu-id="3174a-126"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="3174a-126"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="3174a-127">如需詳細資訊，請參閱[使用泛型集合 (Visual Basic) 的介面中的變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="3174a-127">For more examples, see [Using Variance in Interfaces for Generic Collections (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span></span>  
  
 <span data-ttu-id="3174a-128">參考型別只支援泛型介面中的變異數。</span><span class="sxs-lookup"><span data-stu-id="3174a-128">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="3174a-129">實值型別不支援變異數。</span><span class="sxs-lookup"><span data-stu-id="3174a-129">Value types do not support variance.</span></span> <span data-ttu-id="3174a-130">例如，`IEnumerable(Of Integer)`無法隱含地轉換成`IEnumerable(Of Object)`，因為整數都由實值型別。</span><span class="sxs-lookup"><span data-stu-id="3174a-130">For example, `IEnumerable(Of Integer)` cannot be implicitly converted to `IEnumerable(Of Object)`, because integers are represented by a value type.</span></span>  
  
<span data-ttu-id="3174a-131"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="3174a-131"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="3174a-132">它也是一定要記住，實作 variant 介面的類別仍然是不變。</span><span class="sxs-lookup"><span data-stu-id="3174a-132">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="3174a-133">例如，雖然<xref:System.Collections.Generic.List%601>實作 covariant 介面<xref:System.Collections.Generic.IEnumerable%601>，不能隱含轉換`List(Of Object)`到`List(Of String)`。</xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.Generic.List%601></span><span class="sxs-lookup"><span data-stu-id="3174a-133">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List(Of Object)` to `List(Of String)`.</span></span> <span data-ttu-id="3174a-134">下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="3174a-134">This is illustrated in the following code example.</span></span>  
  
```vb  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim list As List(Of Object) = New List(Of String)  
  
' You can use the interface object instead.  
Dim listObjects As IEnumerable(Of Object) = New List(Of String)  
```  
  
## <a name="see-also"></a><span data-ttu-id="3174a-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3174a-135">See Also</span></span>  
 <span data-ttu-id="3174a-136">[在介面中使用變異數的泛型集合 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md) </span><span class="sxs-lookup"><span data-stu-id="3174a-136">[Using Variance in Interfaces for Generic Collections (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md) </span></span>  
<span data-ttu-id="3174a-137"> [建立 Variant 泛型介面 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) </span><span class="sxs-lookup"><span data-stu-id="3174a-137"> [Creating Variant Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) </span></span>  
<span data-ttu-id="3174a-138"> [泛型介面](http://msdn.microsoft.com/library/88bf5b04-d371-4edb-ba38-01ec7cabaacf) </span><span class="sxs-lookup"><span data-stu-id="3174a-138"> [Generic Interfaces](http://msdn.microsoft.com/library/88bf5b04-d371-4edb-ba38-01ec7cabaacf) </span></span>  
<span data-ttu-id="3174a-139"> [委派 (Visual Basic) 中的變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)</span><span class="sxs-lookup"><span data-stu-id="3174a-139"> [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)</span></span>
