---
title: 建立 Variant 泛型介面 (C#)
ms.date: 07/20/2015
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
ms.openlocfilehash: ad82ba27a98d27a18d9cff1e65ab929cd9d711a6
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57673752"
---
# <a name="creating-variant-generic-interfaces-c"></a><span data-ttu-id="3e1a1-102">建立 Variant 泛型介面 (C#)</span><span class="sxs-lookup"><span data-stu-id="3e1a1-102">Creating Variant Generic Interfaces (C#)</span></span>

<span data-ttu-id="3e1a1-103">您可以在介面中將泛型型別參數宣告為 Covariant 或 Contravariant。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-103">You can declare generic type parameters in interfaces as covariant or contravariant.</span></span> <span data-ttu-id="3e1a1-104">「共變數」允許介面方法具有比泛型型別參數衍生程度更大的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-104">*Covariance* allows interface methods to have more derived return types than that defined by the generic type parameters.</span></span> <span data-ttu-id="3e1a1-105">「反變數」允許介面具有比泛型參數所指定引數型別衍生程度更小的引數類型。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-105">*Contravariance* allows interface methods to have argument types that are less derived than that specified by the generic parameters.</span></span> <span data-ttu-id="3e1a1-106">具有 Covariant 或 Contravariant 泛型型別參數的泛型介面稱為「變異」。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-106">A generic interface that has covariant or contravariant generic type parameters is called *variant*.</span></span>

> [!NOTE]
> <span data-ttu-id="3e1a1-107">.NET Framework 4 引入了對於數個現有泛型介面的變異數支援。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-107">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="3e1a1-108">.NET Framework 中的 Variant 介面清單，請參閱[泛型介面中的變異數 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-108">For the list of the variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>

## <a name="declaring-variant-generic-interfaces"></a><span data-ttu-id="3e1a1-109">宣告 Variant 泛型介面</span><span class="sxs-lookup"><span data-stu-id="3e1a1-109">Declaring Variant Generic Interfaces</span></span>

<span data-ttu-id="3e1a1-110">您可以使用泛型型別參數的 `in` 和 `out` 關鍵字宣告 Variant 泛型介面。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-110">You can declare variant generic interfaces by using the `in` and `out` keywords for generic type parameters.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3e1a1-111">C# 中的 `ref`、`in` 及 `out` 參數不可變動。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-111">`ref`, `in`, and `out` parameters in C# cannot be variant.</span></span> <span data-ttu-id="3e1a1-112">實值型別也不支援變異數。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-112">Value types also do not support variance.</span></span>

<span data-ttu-id="3e1a1-113">您可以使用 `out` 關鍵字將泛型型別參數宣告為 Covariant 。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-113">You can declare a generic type parameter covariant by using the `out` keyword.</span></span> <span data-ttu-id="3e1a1-114">Covariant 類型必須滿足下列條件︰</span><span class="sxs-lookup"><span data-stu-id="3e1a1-114">The covariant type must satisfy the following conditions:</span></span>

- <span data-ttu-id="3e1a1-115">類型僅用為介面方法的傳回型別，不用為方法引數的類型。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-115">The type is used only as a return type of interface methods and not used as a type of method arguments.</span></span> <span data-ttu-id="3e1a1-116">這說明於下列範例中，其中 `R` 類型已宣告為 Covariant。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-116">This is illustrated in the following example, in which the type `R` is declared covariant.</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        R GetSomething();
        // The following statement generates a compiler error.
        // void SetSomething(R sampleArg);

    }
    ```

    <span data-ttu-id="3e1a1-117">這個規則只有一個例外。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-117">There is one exception to this rule.</span></span> <span data-ttu-id="3e1a1-118">如果您以 Contravariant 泛型委派作為方法參數，則可將類型用作委派的泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-118">If you have a contravariant generic delegate as a method parameter, you can use the type as a generic type parameter for the delegate.</span></span> <span data-ttu-id="3e1a1-119">以下範例的 `R` 類型說明這種情況：</span><span class="sxs-lookup"><span data-stu-id="3e1a1-119">This is illustrated by the type `R` in the following example.</span></span> <span data-ttu-id="3e1a1-120">如需詳細資訊，請參閱[委派中的變異數 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) 和[針對 Func 與 Action 泛型委派使用變異數](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-120">For more information, see [Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        void DoSomething(Action<R> callback);
    }
    ```

- <span data-ttu-id="3e1a1-121">類型不會用作介面方法的泛型條件約束。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-121">The type is not used as a generic constraint for the interface methods.</span></span> <span data-ttu-id="3e1a1-122">下列程式碼說明此情形。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-122">This is illustrated in the following code.</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        // The following statement generates a compiler error
        // because you can use only contravariant or invariant types
        // in generic constraints.
        // void DoSomething<T>() where T : R;
    }
    ```

<span data-ttu-id="3e1a1-123">您可以使用 `in` 關鍵字將泛型型別參數宣告為 Contravariant 。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-123">You can declare a generic type parameter contravariant by using the `in` keyword.</span></span> <span data-ttu-id="3e1a1-124">Contravariant 類型僅可用作方法引數的類型，而不能用作介面方法的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-124">The contravariant type can be used only as a type of method arguments and not as a return type of interface methods.</span></span> <span data-ttu-id="3e1a1-125">Contravariant 類型也用於泛型條件約束。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-125">The contravariant type can also be used for generic constraints.</span></span> <span data-ttu-id="3e1a1-126">下列程式碼示範如何宣告 Contravariant 介面，並針對其中一個方法使用泛型條件約束。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-126">The following code shows how to declare a contravariant interface and use a generic constraint for one of its methods.</span></span>

```csharp
interface IContravariant<in A>
{
    void SetSomething(A sampleArg);
    void DoSomething<T>() where T : A;
    // The following statement generates a compiler error.
    // A GetSomething();
}
```

<span data-ttu-id="3e1a1-127">也可以在相同介面中同時支援共變數和反變數，但是對於不同的型別參數，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-127">It is also possible to support both covariance and contravariance in the same interface, but for different type parameters, as shown in the following code example.</span></span>

```csharp
interface IVariant<out R, in A>
{
    R GetSomething();
    void SetSomething(A sampleArg);
    R GetSetSomethings(A sampleArg);
}
```

## <a name="implementing-variant-generic-interfaces"></a><span data-ttu-id="3e1a1-128">實作 Variant 泛型介面</span><span class="sxs-lookup"><span data-stu-id="3e1a1-128">Implementing Variant Generic Interfaces</span></span>

<span data-ttu-id="3e1a1-129">您可以使用用於非變異介面的相同語法，在類別中實作 Variant 泛型介面。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-129">You implement variant generic interfaces in classes by using the same syntax that is used for invariant interfaces.</span></span> <span data-ttu-id="3e1a1-130">下列程式碼範例示範如何在泛型類別中實作 Covariant 介面。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-130">The following code example shows how to implement a covariant interface in a generic class.</span></span>

```csharp
interface ICovariant<out R>
{
    R GetSomething();
}
class SampleImplementation<R> : ICovariant<R>
{
    public R GetSomething()
    {
        // Some code.
        return default(R);
    }
}
```

<span data-ttu-id="3e1a1-131">實作 Variant 介面的類別為非變異。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-131">Classes that implement variant interfaces are invariant.</span></span> <span data-ttu-id="3e1a1-132">例如，試想下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-132">For example, consider the following code.</span></span>

```csharp
// The interface is covariant.
ICovariant<Button> ibutton = new SampleImplementation<Button>();
ICovariant<Object> iobj = ibutton;

// The class is invariant.
SampleImplementation<Button> button = new SampleImplementation<Button>();
// The following statement generates a compiler error
// because classes are invariant.
// SampleImplementation<Object> obj = button;
```

## <a name="extending-variant-generic-interfaces"></a><span data-ttu-id="3e1a1-133">擴充 Variant 泛型介面</span><span class="sxs-lookup"><span data-stu-id="3e1a1-133">Extending Variant Generic Interfaces</span></span>

<span data-ttu-id="3e1a1-134">當您擴充 Variant 泛型介面時，必須使用 `in` 和 `out` 關鍵字明確指定衍生的介面是否支援變異數。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-134">When you extend a variant generic interface, you have to use the `in` and `out` keywords to explicitly specify whether the derived interface supports variance.</span></span> <span data-ttu-id="3e1a1-135">編譯器不會從要擴充的介面推斷變異數。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-135">The compiler does not infer the variance from the interface that is being extended.</span></span> <span data-ttu-id="3e1a1-136">例如，請參考下列介面。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-136">For example, consider the following interfaces.</span></span>

```csharp
interface ICovariant<out T> { }
interface IInvariant<T> : ICovariant<T> { }
interface IExtCovariant<out T> : ICovariant<T> { }
```

<span data-ttu-id="3e1a1-137">在 `IInvariant<T>` 介面中，`T` 泛型型別參數為非變異，而在 `IExtCovariant<out T>` 中，型別參數是 Covariant，雖然這兩個介面都擴充相同的介面。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-137">In the `IInvariant<T>` interface, the generic type parameter `T` is invariant, whereas in `IExtCovariant<out T>` the type parameter is covariant, although both interfaces extend the same interface.</span></span> <span data-ttu-id="3e1a1-138">相同的規則也套用至 Contravariant 泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-138">The same rule is applied to contravariant generic type parameters.</span></span>

<span data-ttu-id="3e1a1-139">您可以建立介面，以便擴充 `T` 泛型型別參數為 Covariant 的介面，以及如果在擴充介面中， `T` 泛型型別參數為非變異的情況下，擴充其為 Contravariant 的介面。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-139">You can create an interface that extends both the interface where the generic type parameter `T` is covariant and the interface where it is contravariant if in the extending interface the generic type parameter `T` is invariant.</span></span> <span data-ttu-id="3e1a1-140">下列程式碼範例說明此情形。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-140">This is illustrated in the following code example.</span></span>

```csharp
interface ICovariant<out T> { }
interface IContravariant<in T> { }
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }
```

<span data-ttu-id="3e1a1-141">不過，如果 `T` 泛型型別參數在一個介面中宣告為 Covariant，則無法在擴充的介面中將它宣告為 Contravariant，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-141">However, if a generic type parameter `T` is declared covariant in one interface, you cannot declare it contravariant in the extending interface, or vice versa.</span></span> <span data-ttu-id="3e1a1-142">下列程式碼範例說明此情形。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-142">This is illustrated in the following code example.</span></span>

```csharp
interface ICovariant<out T> { }
// The following statement generates a compiler error.
// interface ICoContraVariant<in T> : ICovariant<T> { }
```

### <a name="avoiding-ambiguity"></a><span data-ttu-id="3e1a1-143">避免語意模糊</span><span class="sxs-lookup"><span data-stu-id="3e1a1-143">Avoiding Ambiguity</span></span>

<span data-ttu-id="3e1a1-144">當您實作 Variant 泛型介面時，變異數有時會導致語意模糊。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-144">When you implement variant generic interfaces, variance can sometimes lead to ambiguity.</span></span> <span data-ttu-id="3e1a1-145">對此應該要設法避免。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-145">This should be avoided.</span></span>

<span data-ttu-id="3e1a1-146">例如，如果您在一個類別中，明確地實作相同 Variant 泛型介面與不同泛型型別參數，它可能會造成語意模糊。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-146">For example, if you explicitly implement the same variant generic interface with different generic type parameters in one class, it can create ambiguity.</span></span> <span data-ttu-id="3e1a1-147">在此情況下，編譯器不會產生錯誤，但未指定在執行階段將選擇哪個介面實作。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-147">The compiler does not produce an error in this case, but it is not specified which interface implementation will be chosen at runtime.</span></span> <span data-ttu-id="3e1a1-148">這可能會導致您的程式碼中有細微錯誤。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-148">This could lead to subtle bugs in your code.</span></span> <span data-ttu-id="3e1a1-149">請參考下列程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-149">Consider the following code example.</span></span>

```csharp
// Simple class hierarchy.
class Animal { }
class Cat : Animal { }
class Dog : Animal { }

// This class introduces ambiguity
// because IEnumerable<out T> is covariant.
class Pets : IEnumerable<Cat>, IEnumerable<Dog>
{
    IEnumerator<Cat> IEnumerable<Cat>.GetEnumerator()
    {
        Console.WriteLine("Cat");
        // Some code.
        return null;
    }

    IEnumerator IEnumerable.GetEnumerator()
    {
        // Some code.
        return null;
    }

    IEnumerator<Dog> IEnumerable<Dog>.GetEnumerator()
    {
        Console.WriteLine("Dog");
        // Some code.
        return null;
    }
}
class Program
{
    public static void Test()
    {
        IEnumerable<Animal> pets = new Pets();
        pets.GetEnumerator();
    }
}
```

<span data-ttu-id="3e1a1-150">在此範例中，並未指定 `pets.GetEnumerator` 方法如何在 `Cat` 和 `Dog` 之間選擇。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-150">In this example, it is unspecified how the `pets.GetEnumerator` method chooses between `Cat` and `Dog`.</span></span> <span data-ttu-id="3e1a1-151">這可能會在程式碼中造成問題。</span><span class="sxs-lookup"><span data-stu-id="3e1a1-151">This could cause problems in your code.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e1a1-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e1a1-152">See also</span></span>

- [<span data-ttu-id="3e1a1-153">泛型介面中的變異數 (C#)</span><span class="sxs-lookup"><span data-stu-id="3e1a1-153">Variance in Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="3e1a1-154">針對 Func 與 Action 泛型委派使用變異數 (C#)</span><span class="sxs-lookup"><span data-stu-id="3e1a1-154">Using Variance for Func and Action Generic Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
