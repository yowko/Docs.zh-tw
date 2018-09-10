---
title: 泛型介面中的差異 (C#)
ms.date: 07/20/2015
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: 11d0c8665412bb513cb68d58203a454b7c97e052
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44200300"
---
# <a name="variance-in-generic-interfaces-c"></a><span data-ttu-id="af875-102">泛型介面中的差異 (C#)</span><span class="sxs-lookup"><span data-stu-id="af875-102">Variance in Generic Interfaces (C#)</span></span>
<span data-ttu-id="af875-103">.NET Framework 4 針對數個現有泛型介面推出了差異支援。</span><span class="sxs-lookup"><span data-stu-id="af875-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="af875-104">差異支援可讓實作這些介面的類別以隱含方式轉換。</span><span class="sxs-lookup"><span data-stu-id="af875-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> <span data-ttu-id="af875-105">下列介面現在都是 Variant︰</span><span class="sxs-lookup"><span data-stu-id="af875-105">The following interfaces are now variant:</span></span>  
  
-   <span data-ttu-id="af875-106"><xref:System.Collections.Generic.IEnumerable%601> (T 是 Covariant)</span><span class="sxs-lookup"><span data-stu-id="af875-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="af875-107"><xref:System.Collections.Generic.IEnumerator%601> (T 是 Covariant)</span><span class="sxs-lookup"><span data-stu-id="af875-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="af875-108"><xref:System.Linq.IQueryable%601> (T 是 Covariant)</span><span class="sxs-lookup"><span data-stu-id="af875-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="af875-109"><xref:System.Linq.IGrouping%602> (`TKey` 和 `TElement` 都是 Covariant)</span><span class="sxs-lookup"><span data-stu-id="af875-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>  
  
-   <span data-ttu-id="af875-110"><xref:System.Collections.Generic.IComparer%601> (T 是 Contravariant)</span><span class="sxs-lookup"><span data-stu-id="af875-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="af875-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T 是 Contravariant)</span><span class="sxs-lookup"><span data-stu-id="af875-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="af875-112"><xref:System.IComparable%601> (T 是 Contravariant)</span><span class="sxs-lookup"><span data-stu-id="af875-112"><xref:System.IComparable%601> (T is contravariant)</span></span>  
  
 <span data-ttu-id="af875-113">共變數允許方法具有比介面泛型型別參數所定義之衍生程度更大的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="af875-113">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="af875-114">若要示範共變數功能，請考慮這些泛型介面︰`IEnumerable<Object>` 和 `IEnumerable<String>`。</span><span class="sxs-lookup"><span data-stu-id="af875-114">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable<Object>` and `IEnumerable<String>`.</span></span> <span data-ttu-id="af875-115">`IEnumerable<String>` 介面不會繼承 `IEnumerable<Object>` 介面。</span><span class="sxs-lookup"><span data-stu-id="af875-115">The `IEnumerable<String>` interface does not inherit the `IEnumerable<Object>` interface.</span></span> <span data-ttu-id="af875-116">不過，`String` 型別確實會繼承`Object` 型別，而且在某些情況下，您可能希望將這些介面的物件指派給彼此。</span><span class="sxs-lookup"><span data-stu-id="af875-116">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="af875-117">這會顯示在以下程式碼範例中。</span><span class="sxs-lookup"><span data-stu-id="af875-117">This is shown in the following code example.</span></span>  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 <span data-ttu-id="af875-118">在舊版的 .NET Framework 中，此程式碼會造成 C# 使用 `Option Strict On` 的編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="af875-118">In earlier versions of the .NET Framework, this code causes a compilation error in C# with `Option Strict On`.</span></span> <span data-ttu-id="af875-119">但現在您可以使用 `strings`，而不使用 `objects`，如上例所示，因為 <xref:System.Collections.Generic.IEnumerable%601> 介面是 Covariant。</span><span class="sxs-lookup"><span data-stu-id="af875-119">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>  
  
 <span data-ttu-id="af875-120">反變數允許方法具有比介面泛型參數所指定之衍生程度更小的引數型別。</span><span class="sxs-lookup"><span data-stu-id="af875-120">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="af875-121">為示範反變數，我們假設您已建立 `BaseComparer` 類別來比較 `BaseClass` 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="af875-121">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="af875-122">`BaseComparer` 類別會實作 `IEqualityComparer<BaseClass>` 介面。</span><span class="sxs-lookup"><span data-stu-id="af875-122">The `BaseComparer` class implements the `IEqualityComparer<BaseClass>` interface.</span></span> <span data-ttu-id="af875-123">因為 <xref:System.Collections.Generic.IEqualityComparer%601> 介面現在是 Contravariant，所以您可以使用 `BaseComparer` 比較繼承了 `BaseClass` 類別的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="af875-123">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="af875-124">這會顯示在以下程式碼範例中。</span><span class="sxs-lookup"><span data-stu-id="af875-124">This is shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="af875-125">如需更多範例，請參閱[針對泛型集合使用介面中的差異 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="af875-125">For more examples, see [Using Variance in Interfaces for Generic Collections (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span></span>  
  
 <span data-ttu-id="af875-126">僅參考型別支援泛型介面的差異。</span><span class="sxs-lookup"><span data-stu-id="af875-126">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="af875-127">實值型別不支援差異。</span><span class="sxs-lookup"><span data-stu-id="af875-127">Value types do not support variance.</span></span> <span data-ttu-id="af875-128">例如，`IEnumerable<int>` 無法以隱含方式轉換成 `IEnumerable<object>`，因為整數是以實值型別表示。</span><span class="sxs-lookup"><span data-stu-id="af875-128">For example, `IEnumerable<int>` cannot be implicitly converted to `IEnumerable<object>`, because integers are represented by a value type.</span></span>  
  
```csharp  
IEnumerable<int> integers = new List<int>();  
// The following statement generates a compiler errror,  
// because int is a value type.  
// IEnumerable<Object> objects = integers;  
```  
  
 <span data-ttu-id="af875-129">請務必牢記，實作 Variant 介面的類別仍然是非變異的。</span><span class="sxs-lookup"><span data-stu-id="af875-129">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="af875-130">例如，雖然 <xref:System.Collections.Generic.List%601> 實作了 Covariant 介面 <xref:System.Collections.Generic.IEnumerable%601>，但您不能以隱含方式將 `List<Object>` 轉換成 `List<String>`。</span><span class="sxs-lookup"><span data-stu-id="af875-130">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List<Object>` to `List<String>`.</span></span> <span data-ttu-id="af875-131">下列程式碼範例說明此情形。</span><span class="sxs-lookup"><span data-stu-id="af875-131">This is illustrated in the following code example.</span></span>  
  
```csharp  
// The following line generates a compiler error  
// because classes are invariant.  
// List<Object> list = new List<String>();  
  
// You can use the interface object instead.  
IEnumerable<Object> listObjects = new List<String>();  
```  
  
## <a name="see-also"></a><span data-ttu-id="af875-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="af875-132">See Also</span></span>

- [<span data-ttu-id="af875-133">針對泛型集合使用介面中的差異 (C#)</span><span class="sxs-lookup"><span data-stu-id="af875-133">Using Variance in Interfaces for Generic Collections (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)  
- [<span data-ttu-id="af875-134">建立 Variant 泛型介面 (C#)</span><span class="sxs-lookup"><span data-stu-id="af875-134">Creating Variant Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)  
- [<span data-ttu-id="af875-135">泛型介面</span><span class="sxs-lookup"><span data-stu-id="af875-135">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)  
- [<span data-ttu-id="af875-136">委派中的差異 (C#)</span><span class="sxs-lookup"><span data-stu-id="af875-136">Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
