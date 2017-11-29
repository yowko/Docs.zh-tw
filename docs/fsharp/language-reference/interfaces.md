---
title: "介面 (F#)"
description: "了解 F # 介面指定集之相關成員的其他類別所實作的方式。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3a082459-17d4-45cf-9153-0b7550a154ec
ms.openlocfilehash: d7c95e5f5cc0bc6c7f6393af990427ac491c5b79
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="interfaces"></a><span data-ttu-id="f793c-104">介面</span><span class="sxs-lookup"><span data-stu-id="f793c-104">Interfaces</span></span>

<span data-ttu-id="f793c-105">*介面*指定集之相關成員的其他類別實作。</span><span class="sxs-lookup"><span data-stu-id="f793c-105">*Interfaces* specify sets of related members that other classes implement.</span></span>

## <a name="syntax"></a><span data-ttu-id="f793c-106">語法</span><span class="sxs-lookup"><span data-stu-id="f793c-106">Syntax</span></span>

```fsharp
// Interface declaration:
[ attributes ]
type interface-name =
    [ interface ]     [ inherit base-interface-name ...]
    abstract member1 : [ argument-types1 -> ] return-type1
    abstract member2 : [ argument-types2 -> ] return-type2
    ...
[ end ]

// Implementing, inside a class type definition:
interface interface-name with
    member self-identifier.member1argument-list = method-body1
    member self-identifier.member2argument-list = method-body2

// Implementing, by using an object expression:
[ attributes ]
let class-name (argument-list) =
    { new interface-name with
        member self-identifier.member1argument-list = method-body1
        member self-identifier.member2argument-list = method-body2
        [ base-interface-definitions ]
    }
    member-list
```

## <a name="remarks"></a><span data-ttu-id="f793c-107">備註</span><span class="sxs-lookup"><span data-stu-id="f793c-107">Remarks</span></span>
<span data-ttu-id="f793c-108">介面宣告類似於類別宣告，不同之處在於會實作任何成員。</span><span class="sxs-lookup"><span data-stu-id="f793c-108">Interface declarations resemble class declarations except that no members are implemented.</span></span> <span data-ttu-id="f793c-109">相反地，所有成員都是抽象的由關鍵字`abstract`。</span><span class="sxs-lookup"><span data-stu-id="f793c-109">Instead, all the members are abstract, as indicated by the keyword `abstract`.</span></span> <span data-ttu-id="f793c-110">您未提供抽象方法的方法主體。</span><span class="sxs-lookup"><span data-stu-id="f793c-110">You do not provide a method body for abstract methods.</span></span> <span data-ttu-id="f793c-111">不過，您可以提供的預設實作，也包含成員的方法，以搭配不同的定義`default`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f793c-111">However, you can provide a default implementation by also including a separate definition of the member as a method together with the `default` keyword.</span></span> <span data-ttu-id="f793c-112">這樣相當於在其他.NET 語言中的基底類別中建立的虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="f793c-112">Doing so is equivalent to creating a virtual method in a base class in other .NET languages.</span></span> <span data-ttu-id="f793c-113">這種虛擬的方法可以實作介面的類別中被覆寫。</span><span class="sxs-lookup"><span data-stu-id="f793c-113">Such a virtual method can be overridden in classes that implement the interface.</span></span>

<span data-ttu-id="f793c-114">您可以選擇性提供每個方法的參數名稱，使用一般的 F # 語法：</span><span class="sxs-lookup"><span data-stu-id="f793c-114">You can optionally give each method parameter a name using normal F# syntax:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

<span data-ttu-id="f793c-115">在以上`ISprintable`範例中，`Print`方法具有單一參數的型別`string`名稱`format`。</span><span class="sxs-lookup"><span data-stu-id="f793c-115">In the above `ISprintable` example, the `Print` method has a single parameter of the type `string` with the name `format`.</span></span>

<span data-ttu-id="f793c-116">有兩種方式來實作介面： 使用物件運算式，以及使用類別類型。</span><span class="sxs-lookup"><span data-stu-id="f793c-116">There are two ways to implement interfaces: by using object expressions, and by using class types.</span></span> <span data-ttu-id="f793c-117">在任一情況下，類別型別或物件運算式會提供介面的抽象方法的方法主體。</span><span class="sxs-lookup"><span data-stu-id="f793c-117">In either case, the class type or object expression provides method bodies for abstract methods of the interface.</span></span> <span data-ttu-id="f793c-118">實作是針對每個實作介面的類型。</span><span class="sxs-lookup"><span data-stu-id="f793c-118">Implementations are specific to each type that implements the interface.</span></span> <span data-ttu-id="f793c-119">因此，在不同的型別上的介面方法可能彼此不同。</span><span class="sxs-lookup"><span data-stu-id="f793c-119">Therefore, interface methods on different types might be different from each other.</span></span>

<span data-ttu-id="f793c-120">關鍵字`interface`和`end`，當您使用輕量型語法的標記的開始和結束的定義中，為選擇性。</span><span class="sxs-lookup"><span data-stu-id="f793c-120">The keywords `interface` and `end`, which mark the start and end of the definition, are optional when you use lightweight syntax.</span></span> <span data-ttu-id="f793c-121">如果您不使用這些關鍵字，編譯器會嘗試推斷型別是否為類別或介面藉由分析您所使用的建構。</span><span class="sxs-lookup"><span data-stu-id="f793c-121">If you do not use these keywords, the compiler attempts to infer whether the type is a class or an interface by analyzing the constructs that you use.</span></span> <span data-ttu-id="f793c-122">如果您定義的成員，或使用其他類別的語法，則會將類型解譯為類別。</span><span class="sxs-lookup"><span data-stu-id="f793c-122">If you define a member or use other class syntax, the type is interpreted as a class.</span></span>

<span data-ttu-id="f793c-123">開始以大寫的所有介面是.NET 程式碼樣式`I`。</span><span class="sxs-lookup"><span data-stu-id="f793c-123">The .NET coding style is to begin all interfaces with a capital `I`.</span></span>


## <a name="implementing-interfaces-by-using-class-types"></a><span data-ttu-id="f793c-124">使用類別類型來實作介面</span><span class="sxs-lookup"><span data-stu-id="f793c-124">Implementing Interfaces by Using Class Types</span></span>
<span data-ttu-id="f793c-125">您也可以使用類別類型中實作一個或多個介面`interface`關鍵字、 介面、 名稱和`with`關鍵字，後面介面成員的定義，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="f793c-125">You can implement one or more interfaces in a class type by using the `interface` keyword, the name of the interface, and the `with` keyword, followed by the interface member definitions, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

<span data-ttu-id="f793c-126">繼承介面實作，所以不需要任何衍生的類別實作它們。</span><span class="sxs-lookup"><span data-stu-id="f793c-126">Interface implementations are inherited, so any derived classes do not need to reimplement them.</span></span>


## <a name="calling-interface-methods"></a><span data-ttu-id="f793c-127">呼叫介面方法</span><span class="sxs-lookup"><span data-stu-id="f793c-127">Calling Interface Methods</span></span>
<span data-ttu-id="f793c-128">可以呼叫介面方法，只能透過介面，不能透過任何實作介面的型別物件。</span><span class="sxs-lookup"><span data-stu-id="f793c-128">Interface methods can be called only through the interface, not through any object of the type that implements the interface.</span></span> <span data-ttu-id="f793c-129">因此，您可能必須向上轉型為介面型別使用`:>`運算子或`upcast`運算子，才能呼叫這些方法。</span><span class="sxs-lookup"><span data-stu-id="f793c-129">Thus, you might have to upcast to the interface type by using the `:>` operator or the `upcast` operator in order to call these methods.</span></span>

<span data-ttu-id="f793c-130">具有類型的物件時，呼叫介面方法`SomeClass`，您必須向上轉型為介面型別物件，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="f793c-130">To call the interface method when you have an object of type `SomeClass`, you must upcast the object to the interface type, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

<span data-ttu-id="f793c-131">替代是物件上的向上轉型成為宣告的方法，並呼叫介面方法，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="f793c-131">An alternative is to declare a method on the object that upcasts and calls the interface method, as in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]
    
## <a name="implementing-interfaces-by-using-object-expressions"></a><span data-ttu-id="f793c-132">使用物件運算式實作介面</span><span class="sxs-lookup"><span data-stu-id="f793c-132">Implementing Interfaces by Using Object Expressions</span></span>
<span data-ttu-id="f793c-133">物件運算式提供簡短的方式，來實作介面。</span><span class="sxs-lookup"><span data-stu-id="f793c-133">Object expressions provide a short way to implement an interface.</span></span> <span data-ttu-id="f793c-134">當您沒有建立具名的型別，而且您只想支援介面方法，不需要任何其他方法的物件，它們很有用。</span><span class="sxs-lookup"><span data-stu-id="f793c-134">They are useful when you do not have to create a named type, and you just want an object that supports the interface methods, without any additional methods.</span></span> <span data-ttu-id="f793c-135">物件運算式是以下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="f793c-135">An object expression is illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]
    
## <a name="interface-inheritance"></a><span data-ttu-id="f793c-136">介面繼承</span><span class="sxs-lookup"><span data-stu-id="f793c-136">Interface Inheritance</span></span>
<span data-ttu-id="f793c-137">介面可以繼承自一或多個基底介面。</span><span class="sxs-lookup"><span data-stu-id="f793c-137">Interfaces can inherit from one or more base interfaces.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]
    
## <a name="see-also"></a><span data-ttu-id="f793c-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f793c-138">See Also</span></span>
[<span data-ttu-id="f793c-139">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="f793c-139">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="f793c-140">物件運算式</span><span class="sxs-lookup"><span data-stu-id="f793c-140">Object Expressions</span></span>](object-expressions.md)

[<span data-ttu-id="f793c-141">類別</span><span class="sxs-lookup"><span data-stu-id="f793c-141">Classes</span></span>](classes.md)
