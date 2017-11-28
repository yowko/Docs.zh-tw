---
title: "泛型介面中的差異 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cc3fe009e89d5d8f6619b406c8c08f47620a881d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="variance-in-generic-interfaces-c"></a><span data-ttu-id="5f473-102">泛型介面中的差異 (C#)</span><span class="sxs-lookup"><span data-stu-id="5f473-102">Variance in Generic Interfaces (C#)</span></span>
<span data-ttu-id="5f473-103">.NET Framework 4 針對數個現有泛型介面推出了差異支援。</span><span class="sxs-lookup"><span data-stu-id="5f473-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="5f473-104">差異支援可讓實作這些介面的類別以隱含方式轉換。</span><span class="sxs-lookup"><span data-stu-id="5f473-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> <span data-ttu-id="5f473-105">下列介面現在都是 Variant︰</span><span class="sxs-lookup"><span data-stu-id="5f473-105">The following interfaces are now variant:</span></span>  
  
-   <span data-ttu-id="5f473-106"><xref:System.Collections.Generic.IEnumerable%601> (T 是 Covariant)</span><span class="sxs-lookup"><span data-stu-id="5f473-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="5f473-107"><xref:System.Collections.Generic.IEnumerator%601> (T 是 Covariant)</span><span class="sxs-lookup"><span data-stu-id="5f473-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="5f473-108"><xref:System.Linq.IQueryable%601> (T 是 Covariant)</span><span class="sxs-lookup"><span data-stu-id="5f473-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="5f473-109"><xref:System.Linq.IGrouping%602> (`TKey` 和 `TElement` 都是 Covariant)</span><span class="sxs-lookup"><span data-stu-id="5f473-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>  
  
-   <span data-ttu-id="5f473-110"><xref:System.Collections.Generic.IComparer%601> (T 是 Contravariant)</span><span class="sxs-lookup"><span data-stu-id="5f473-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="5f473-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T 是 Contravariant)</span><span class="sxs-lookup"><span data-stu-id="5f473-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="5f473-112"><xref:System.IComparable%601> (T 是 Contravariant)</span><span class="sxs-lookup"><span data-stu-id="5f473-112"><xref:System.IComparable%601> (T is contravariant)</span></span>  
  
 <span data-ttu-id="5f473-113">共變數允許方法具有比介面泛型型別參數所定義之衍生程度更大的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="5f473-113">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="5f473-114">若要示範共變數功能，請考慮這些泛型介面︰`IEnumerable<Object>` 和 `IEnumerable<String>`。</span><span class="sxs-lookup"><span data-stu-id="5f473-114">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable<Object>` and `IEnumerable<String>`.</span></span> <span data-ttu-id="5f473-115">`IEnumerable<String>` 介面不會繼承 `IEnumerable<Object>` 介面。</span><span class="sxs-lookup"><span data-stu-id="5f473-115">The `IEnumerable<String>` interface does not inherit the `IEnumerable<Object>` interface.</span></span> <span data-ttu-id="5f473-116">不過，`String` 型別確實會繼承`Object` 型別，而且在某些情況下，您可能希望將這些介面的物件指派給彼此。</span><span class="sxs-lookup"><span data-stu-id="5f473-116">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="5f473-117">這會顯示在以下程式碼範例中。</span><span class="sxs-lookup"><span data-stu-id="5f473-117">This is shown in the following code example.</span></span>  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 <span data-ttu-id="5f473-118">在舊版的 .NET Framework 中，此程式碼會造成 C# 使用 `Option Strict On` 的編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="5f473-118">In earlier versions of the .NET Framework, this code causes a compilation error in C# with `Option Strict On`.</span></span> <span data-ttu-id="5f473-119">但現在您可以使用 `strings`，而不使用 `objects`，如上例所示，因為 <xref:System.Collections.Generic.IEnumerable%601> 介面是 Covariant。</span><span class="sxs-lookup"><span data-stu-id="5f473-119">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>  
  
 <span data-ttu-id="5f473-120">反變數允許方法具有比介面泛型參數所指定之衍生程度更小的引數型別。</span><span class="sxs-lookup"><span data-stu-id="5f473-120">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="5f473-121">為示範反變數，我們假設您已建立 `BaseComparer` 類別來比較 `BaseClass` 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5f473-121">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="5f473-122">`BaseComparer` 類別會實作 `IEqualityComparer<BaseClass>` 介面。</span><span class="sxs-lookup"><span data-stu-id="5f473-122">The `BaseComparer` class implements the `IEqualityComparer<BaseClass>` interface.</span></span> <span data-ttu-id="5f473-123">因為 <xref:System.Collections.Generic.IEqualityComparer%601> 介面現在是 Contravariant，所以您可以使用 `BaseComparer` 比較繼承了 `BaseClass` 類別的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="5f473-123">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="5f473-124">這會顯示在以下程式碼範例中。</span><span class="sxs-lookup"><span data-stu-id="5f473-124">This is shown in the following code example.</span></span>  
  
```csharp  
// Simple hierarchy of classes.  
class BaseClass { }  
class DerivedClass : BaseClass { }  
  
// Comparer class.  
class BaseComparer : IEqualityComparer<BaseClass>   
{  
    public int GetHashCode(BaseClass baseInstance)  
    {  
        return baseInstance.GetHashCode();  
    }  
    public bool Equals(BaseClass x, BaseClass y)  
    {  
        return x == y;  
    }  
}  
class Program  
{  
    static void Test()  
    {  
        IEqualityComparer<BaseClass> baseComparer = new BaseComparer();  
  
        // Implicit conversion of IEqualityComparer<BaseClass> to   
        // IEqualityComparer<DerivedClass>.  
        IEqualityComparer<DerivedClass> childComparer = baseComparer;  
    }  
}  
```  
  
 <span data-ttu-id="5f473-125">如需更多範例，請參閱[針對泛型集合使用介面中的差異 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="5f473-125">For more examples, see [Using Variance in Interfaces for Generic Collections (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span></span>  
  
 <span data-ttu-id="5f473-126">僅參考型別支援泛型介面的差異。</span><span class="sxs-lookup"><span data-stu-id="5f473-126">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="5f473-127">實值型別不支援差異。</span><span class="sxs-lookup"><span data-stu-id="5f473-127">Value types do not support variance.</span></span> <span data-ttu-id="5f473-128">例如，`IEnumerable<int>` 無法以隱含方式轉換成 `IEnumerable<object>`，因為整數是以實值型別表示。</span><span class="sxs-lookup"><span data-stu-id="5f473-128">For example, `IEnumerable<int>` cannot be implicitly converted to `IEnumerable<object>`, because integers are represented by a value type.</span></span>  
  
```csharp  
IEnumerable<int> integers = new List<int>();  
// The following statement generates a compiler errror,  
// because int is a value type.  
// IEnumerable<Object> objects = integers;  
```  
  
 <span data-ttu-id="5f473-129">請務必牢記，實作 Variant 介面的類別仍然是非變異的。</span><span class="sxs-lookup"><span data-stu-id="5f473-129">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="5f473-130">例如，雖然 <xref:System.Collections.Generic.List%601> 實作了 Covariant 介面 <xref:System.Collections.Generic.IEnumerable%601>，但您不能以隱含方式將 `List<Object>` 轉換成 `List<String>`。</span><span class="sxs-lookup"><span data-stu-id="5f473-130">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List<Object>` to `List<String>`.</span></span> <span data-ttu-id="5f473-131">下列程式碼範例說明此情形。</span><span class="sxs-lookup"><span data-stu-id="5f473-131">This is illustrated in the following code example.</span></span>  
  
```csharp  
// The following line generates a compiler error  
// because classes are invariant.  
// List<Object> list = new List<String>();  
  
// You can use the interface object instead.  
IEnumerable<Object> listObjects = new List<String>();  
```  
  
## <a name="see-also"></a><span data-ttu-id="5f473-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f473-132">See Also</span></span>  
 [<span data-ttu-id="5f473-133">針對泛型集合使用介面中的差異 (C#)</span><span class="sxs-lookup"><span data-stu-id="5f473-133">Using Variance in Interfaces for Generic Collections (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)  
 [<span data-ttu-id="5f473-134">建立 Variant 泛型介面 (C#)</span><span class="sxs-lookup"><span data-stu-id="5f473-134">Creating Variant Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)  
 [<span data-ttu-id="5f473-135">泛型介面</span><span class="sxs-lookup"><span data-stu-id="5f473-135">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)  
 [<span data-ttu-id="5f473-136">委派中的差異 (C#)</span><span class="sxs-lookup"><span data-stu-id="5f473-136">Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
