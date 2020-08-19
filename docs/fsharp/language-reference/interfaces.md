---
title: 介面
description: '瞭解 F # 介面如何指定其他類別所執行的相關成員集合。'
ms.date: 08/15/2020
ms.openlocfilehash: 36272b52fcff83e8e8a54ccc4e6ecd1252a91819
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558123"
---
# <a name="interfaces"></a><span data-ttu-id="4fb2e-103">介面</span><span class="sxs-lookup"><span data-stu-id="4fb2e-103">Interfaces</span></span>

<span data-ttu-id="4fb2e-104">*介面* 會指定其他類別所執行的相關成員集合。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-104">*Interfaces* specify sets of related members that other classes implement.</span></span>

## <a name="syntax"></a><span data-ttu-id="4fb2e-105">語法</span><span class="sxs-lookup"><span data-stu-id="4fb2e-105">Syntax</span></span>

```fsharp
// Interface declaration:
[ attributes ]
type [accessibility-modifier] interface-name =
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

## <a name="remarks"></a><span data-ttu-id="4fb2e-106">備註</span><span class="sxs-lookup"><span data-stu-id="4fb2e-106">Remarks</span></span>

<span data-ttu-id="4fb2e-107">介面宣告類似類別宣告，但不會執行任何成員。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-107">Interface declarations resemble class declarations except that no members are implemented.</span></span> <span data-ttu-id="4fb2e-108">相反地，所有成員都是抽象的，如關鍵字所指示 `abstract` 。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-108">Instead, all the members are abstract, as indicated by the keyword `abstract`.</span></span> <span data-ttu-id="4fb2e-109">您未提供抽象方法的方法主體。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-109">You do not provide a method body for abstract methods.</span></span> <span data-ttu-id="4fb2e-110">不過，您也可以提供預設的執行方式，也就是將個別的成員定義做為方法與 `default` 關鍵字一起使用。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-110">However, you can provide a default implementation by also including a separate definition of the member as a method together with the `default` keyword.</span></span> <span data-ttu-id="4fb2e-111">這麼做相當於在其他 .NET 語言的基類中建立虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-111">Doing so is equivalent to creating a virtual method in a base class in other .NET languages.</span></span> <span data-ttu-id="4fb2e-112">這類虛擬方法可以在執行介面的類別中覆寫。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-112">Such a virtual method can be overridden in classes that implement the interface.</span></span>

<span data-ttu-id="4fb2e-113">介面的預設存取範圍是 `public` 。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-113">The default accessibility for interfaces is `public`.</span></span>

<span data-ttu-id="4fb2e-114">您可以使用一般 F # 語法，選擇性地為每個方法參數指定名稱：</span><span class="sxs-lookup"><span data-stu-id="4fb2e-114">You can optionally give each method parameter a name using normal F# syntax:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

<span data-ttu-id="4fb2e-115">在上述 `ISprintable` 範例中， `Print` 方法具有類型的單一參數，其名稱為 `string` `format` 。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-115">In the above `ISprintable` example, the `Print` method has a single parameter of the type `string` with the name `format`.</span></span>

<span data-ttu-id="4fb2e-116">有兩種方式可以執行介面：使用物件運算式，以及使用類別類型。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-116">There are two ways to implement interfaces: by using object expressions, and by using class types.</span></span> <span data-ttu-id="4fb2e-117">在任一種情況下，類別類型或物件運算式都會提供介面之抽象方法的方法主體。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-117">In either case, the class type or object expression provides method bodies for abstract methods of the interface.</span></span> <span data-ttu-id="4fb2e-118">實作為每個實作為介面的型別。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-118">Implementations are specific to each type that implements the interface.</span></span> <span data-ttu-id="4fb2e-119">因此，不同類型的介面方法可能會彼此不同。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-119">Therefore, interface methods on different types might be different from each other.</span></span>

<span data-ttu-id="4fb2e-120">`interface` `end` 當您使用輕量語法時，關鍵字和（標示定義的開頭和結尾）是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-120">The keywords `interface` and `end`, which mark the start and end of the definition, are optional when you use lightweight syntax.</span></span> <span data-ttu-id="4fb2e-121">如果您未使用這些關鍵字，編譯器會藉由分析您所使用的結構，嘗試推斷型別為類別或介面。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-121">If you do not use these keywords, the compiler attempts to infer whether the type is a class or an interface by analyzing the constructs that you use.</span></span> <span data-ttu-id="4fb2e-122">如果您定義成員或使用其他類別語法，則會將型別解釋為類別。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-122">If you define a member or use other class syntax, the type is interpreted as a class.</span></span>

<span data-ttu-id="4fb2e-123">.NET 程式碼撰寫樣式是以大寫來開始所有的介面 `I` 。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-123">The .NET coding style is to begin all interfaces with a capital `I`.</span></span>

<span data-ttu-id="4fb2e-124">您可以用兩種方式指定多個參數： F # 樣式和。NET 樣式。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-124">You can specify multiple parameters in two ways: F#-style and .NET-style.</span></span> <span data-ttu-id="4fb2e-125">這兩種方法都會針對 .NET 取用者進行編譯，但 F # 樣式會強制 F # 呼叫端使用 F # 樣式參數應用程式和。NET 樣式會強制 F # 呼叫端使用元組引數應用程式。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-125">Both will compile the same way for .NET consumers, but F#-style will force F# callers to use F#-style parameter application and .NET-style will force F# callers to use tupled argument application.</span></span>

```fsharp
type INumeric1 =
    abstract Add: x: int -> y: int -> int

type INumeric2 =
    abstract Add: x: int * y: int -> int
```

## <a name="implementing-interfaces-by-using-class-types"></a><span data-ttu-id="4fb2e-126">使用類別類型來執行介面</span><span class="sxs-lookup"><span data-stu-id="4fb2e-126">Implementing Interfaces by Using Class Types</span></span>

<span data-ttu-id="4fb2e-127">您可以使用 `interface` 關鍵字、介面名稱和關鍵字，然後使用介面成員定義，在類別型別中執行一個或多個介面， `with` 如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-127">You can implement one or more interfaces in a class type by using the `interface` keyword, the name of the interface, and the `with` keyword, followed by the interface member definitions, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

<span data-ttu-id="4fb2e-128">介面會被繼承，因此任何衍生的類別都不需要重新執行它們。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-128">Interface implementations are inherited, so any derived classes do not need to reimplement them.</span></span>

## <a name="calling-interface-methods"></a><span data-ttu-id="4fb2e-129">呼叫介面方法</span><span class="sxs-lookup"><span data-stu-id="4fb2e-129">Calling Interface Methods</span></span>

<span data-ttu-id="4fb2e-130">介面方法只能透過介面呼叫，而不能透過任何實介面型別的物件來呼叫。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-130">Interface methods can be called only through the interface, not through any object of the type that implements the interface.</span></span> <span data-ttu-id="4fb2e-131">因此，您可能必須使用運算子或運算子來向上轉型為介面型別，才能 `:>` `upcast` 呼叫這些方法。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-131">Thus, you might have to upcast to the interface type by using the `:>` operator or the `upcast` operator in order to call these methods.</span></span>

<span data-ttu-id="4fb2e-132">當您擁有類型的物件時，若要呼叫介面方法 `SomeClass` ，您必須將物件向上轉型為介面類別型，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-132">To call the interface method when you have an object of type `SomeClass`, you must upcast the object to the interface type, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

<span data-ttu-id="4fb2e-133">替代方法是在將和呼叫介面方法的物件上宣告方法，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-133">An alternative is to declare a method on the object that upcasts and calls the interface method, as in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a><span data-ttu-id="4fb2e-134">使用物件運算式來執行介面</span><span class="sxs-lookup"><span data-stu-id="4fb2e-134">Implementing Interfaces by Using Object Expressions</span></span>

<span data-ttu-id="4fb2e-135">物件運算式提供簡單的方法來執行介面。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-135">Object expressions provide a short way to implement an interface.</span></span> <span data-ttu-id="4fb2e-136">當您不需要建立已命名的型別，而且您只想要支援介面方法的物件，而不需要任何其他方法時，它們就很有用。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-136">They are useful when you do not have to create a named type, and you just want an object that supports the interface methods, without any additional methods.</span></span> <span data-ttu-id="4fb2e-137">下列程式碼說明物件運算式。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-137">An object expression is illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a><span data-ttu-id="4fb2e-138">介面繼承</span><span class="sxs-lookup"><span data-stu-id="4fb2e-138">Interface Inheritance</span></span>

<span data-ttu-id="4fb2e-139">介面可以繼承自一或多個基底介面。</span><span class="sxs-lookup"><span data-stu-id="4fb2e-139">Interfaces can inherit from one or more base interfaces.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="see-also"></a><span data-ttu-id="4fb2e-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fb2e-140">See also</span></span>

- [<span data-ttu-id="4fb2e-141">F # 語言參考</span><span class="sxs-lookup"><span data-stu-id="4fb2e-141">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="4fb2e-142">物件運算式</span><span class="sxs-lookup"><span data-stu-id="4fb2e-142">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="4fb2e-143">類別</span><span class="sxs-lookup"><span data-stu-id="4fb2e-143">Classes</span></span>](classes.md)
