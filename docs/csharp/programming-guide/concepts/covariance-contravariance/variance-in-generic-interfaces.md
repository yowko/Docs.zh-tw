---
title: 泛型介面中的差異 (C#)
ms.date: 04/10/2019
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: 5874a39a57f85695bedc3d1ffa61adf19fcdbe37
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/11/2019
ms.locfileid: "59480777"
---
# <a name="variance-in-generic-interfaces-c"></a><span data-ttu-id="c6a6c-102">泛型介面中的差異 (C#)</span><span class="sxs-lookup"><span data-stu-id="c6a6c-102">Variance in Generic Interfaces (C#)</span></span>

<span data-ttu-id="c6a6c-103">.NET Framework 4 針對數個現有泛型介面推出了差異支援。</span><span class="sxs-lookup"><span data-stu-id="c6a6c-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="c6a6c-104">差異支援可讓實作這些介面的類別以隱含方式轉換。</span><span class="sxs-lookup"><span data-stu-id="c6a6c-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> 

<span data-ttu-id="c6a6c-105">開始使用 .NET Framework 4，下列介面是變數：</span><span class="sxs-lookup"><span data-stu-id="c6a6c-105">Staring with .NET Framework 4, the following interfaces are variant:</span></span>

- <xref:System.Collections.Generic.IEnumerable%601> <span data-ttu-id="c6a6c-106">(T 是 Covariant)</span><span class="sxs-lookup"><span data-stu-id="c6a6c-106">(T is covariant)</span></span>

- <xref:System.Collections.Generic.IEnumerator%601> <span data-ttu-id="c6a6c-107">(T 是 Covariant)</span><span class="sxs-lookup"><span data-stu-id="c6a6c-107">(T is covariant)</span></span>

- <xref:System.Linq.IQueryable%601> <span data-ttu-id="c6a6c-108">(T 是 Covariant)</span><span class="sxs-lookup"><span data-stu-id="c6a6c-108">(T is covariant)</span></span>

- <xref:System.Linq.IGrouping%602> <span data-ttu-id="c6a6c-109">(`TKey` 和 `TElement` 都是 Covariant)</span><span class="sxs-lookup"><span data-stu-id="c6a6c-109">(`TKey` and `TElement` are covariant)</span></span>

- <xref:System.Collections.Generic.IComparer%601> <span data-ttu-id="c6a6c-110">(T 是 Contravariant)</span><span class="sxs-lookup"><span data-stu-id="c6a6c-110">(T is contravariant)</span></span>

- <xref:System.Collections.Generic.IEqualityComparer%601> <span data-ttu-id="c6a6c-111">(T 是 Contravariant)</span><span class="sxs-lookup"><span data-stu-id="c6a6c-111">(T is contravariant)</span></span>

- <xref:System.IComparable%601> <span data-ttu-id="c6a6c-112">(T 是 Contravariant)</span><span class="sxs-lookup"><span data-stu-id="c6a6c-112">(T is contravariant)</span></span>

<span data-ttu-id="c6a6c-113">開始使用 .NET Framework 4.5，下列介面是變數：</span><span class="sxs-lookup"><span data-stu-id="c6a6c-113">Starting with .NET Framework 4.5, the following interfaces are variant:</span></span>

- <xref:System.Collections.Generic.IReadOnlyList%601> <span data-ttu-id="c6a6c-114">(T 是 Contravariant)</span><span class="sxs-lookup"><span data-stu-id="c6a6c-114">(T is contravariant)</span></span>

- <xref:System.Collections.Generic.IReadOnlyCollection%601> <span data-ttu-id="c6a6c-115">(T 是 Contravariant)</span><span class="sxs-lookup"><span data-stu-id="c6a6c-115">(T is contravariant)</span></span>

<span data-ttu-id="c6a6c-116">共變數允許方法具有比介面泛型型別參數所定義之衍生程度更大的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="c6a6c-116">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="c6a6c-117">若要示範共變數功能，請考慮這些泛型介面︰`IEnumerable<Object>` 和 `IEnumerable<String>`。</span><span class="sxs-lookup"><span data-stu-id="c6a6c-117">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable<Object>` and `IEnumerable<String>`.</span></span> <span data-ttu-id="c6a6c-118">`IEnumerable<String>` 介面不會繼承 `IEnumerable<Object>` 介面。</span><span class="sxs-lookup"><span data-stu-id="c6a6c-118">The `IEnumerable<String>` interface does not inherit the `IEnumerable<Object>` interface.</span></span> <span data-ttu-id="c6a6c-119">不過，`String` 型別確實會繼承`Object` 型別，而且在某些情況下，您可能希望將這些介面的物件指派給彼此。</span><span class="sxs-lookup"><span data-stu-id="c6a6c-119">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="c6a6c-120">這會顯示在以下程式碼範例中。</span><span class="sxs-lookup"><span data-stu-id="c6a6c-120">This is shown in the following code example.</span></span>

```csharp
IEnumerable<String> strings = new List<String>();
IEnumerable<Object> objects = strings;
```

<span data-ttu-id="c6a6c-121">在舊版的 .NET Framework 中，此程式碼會造成 C# 和 Visual Basic (如果開啟 `Option Strict`) 中的編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="c6a6c-121">In earlier versions of the .NET Framework, this code causes a compilation error in C# and, if `Option Strict` is on, in Visual Basic.</span></span> <span data-ttu-id="c6a6c-122">但現在您可以使用 `strings`，而不使用 `objects`，如上例所示，因為 <xref:System.Collections.Generic.IEnumerable%601> 介面是 Covariant。</span><span class="sxs-lookup"><span data-stu-id="c6a6c-122">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>

<span data-ttu-id="c6a6c-123">反變數允許方法具有比介面泛型參數所指定之衍生程度更小的引數型別。</span><span class="sxs-lookup"><span data-stu-id="c6a6c-123">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="c6a6c-124">為示範反變數，我們假設您已建立 `BaseComparer` 類別來比較 `BaseClass` 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c6a6c-124">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="c6a6c-125">`BaseComparer` 類別會實作 `IEqualityComparer<BaseClass>` 介面。</span><span class="sxs-lookup"><span data-stu-id="c6a6c-125">The `BaseComparer` class implements the `IEqualityComparer<BaseClass>` interface.</span></span> <span data-ttu-id="c6a6c-126">因為 <xref:System.Collections.Generic.IEqualityComparer%601> 介面現在是 Contravariant，所以您可以使用 `BaseComparer` 比較繼承了 `BaseClass` 類別的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="c6a6c-126">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="c6a6c-127">這會顯示在以下程式碼範例中。</span><span class="sxs-lookup"><span data-stu-id="c6a6c-127">This is shown in the following code example.</span></span>

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

<span data-ttu-id="c6a6c-128">如需更多範例，請參閱[針對泛型集合使用介面中的差異 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="c6a6c-128">For more examples, see [Using Variance in Interfaces for Generic Collections (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span></span>

<span data-ttu-id="c6a6c-129">僅參考型別支援泛型介面的差異。</span><span class="sxs-lookup"><span data-stu-id="c6a6c-129">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="c6a6c-130">實值型別不支援差異。</span><span class="sxs-lookup"><span data-stu-id="c6a6c-130">Value types do not support variance.</span></span> <span data-ttu-id="c6a6c-131">例如，`IEnumerable<int>` 無法以隱含方式轉換成 `IEnumerable<object>`，因為整數是以實值型別表示。</span><span class="sxs-lookup"><span data-stu-id="c6a6c-131">For example, `IEnumerable<int>` cannot be implicitly converted to `IEnumerable<object>`, because integers are represented by a value type.</span></span>

```csharp
IEnumerable<int> integers = new List<int>();
// The following statement generates a compiler error,
// because int is a value type.
// IEnumerable<Object> objects = integers;
```

<span data-ttu-id="c6a6c-132">請務必牢記，實作 Variant 介面的類別仍然是非變異的。</span><span class="sxs-lookup"><span data-stu-id="c6a6c-132">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="c6a6c-133">例如，雖然 <xref:System.Collections.Generic.List%601> 實作了 Covariant 介面 <xref:System.Collections.Generic.IEnumerable%601>，但您不能以隱含方式將 `List<Object>` 轉換成 `List<String>`。</span><span class="sxs-lookup"><span data-stu-id="c6a6c-133">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List<Object>` to `List<String>`.</span></span> <span data-ttu-id="c6a6c-134">下列程式碼範例說明此情形。</span><span class="sxs-lookup"><span data-stu-id="c6a6c-134">This is illustrated in the following code example.</span></span>

```csharp
// The following line generates a compiler error
// because classes are invariant.
// List<Object> list = new List<String>();

// You can use the interface object instead.
IEnumerable<Object> listObjects = new List<String>();
```

## <a name="see-also"></a><span data-ttu-id="c6a6c-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6a6c-135">See also</span></span>

- [<span data-ttu-id="c6a6c-136">針對泛型集合使用介面中的變異數 (C#)</span><span class="sxs-lookup"><span data-stu-id="c6a6c-136">Using Variance in Interfaces for Generic Collections (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)
- [<span data-ttu-id="c6a6c-137">建立 Variant 泛型介面 (C#)</span><span class="sxs-lookup"><span data-stu-id="c6a6c-137">Creating Variant Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)
- [<span data-ttu-id="c6a6c-138">泛型介面</span><span class="sxs-lookup"><span data-stu-id="c6a6c-138">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)
- [<span data-ttu-id="c6a6c-139">委派中的差異 (C#)</span><span class="sxs-lookup"><span data-stu-id="c6a6c-139">Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
