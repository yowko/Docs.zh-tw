---
title: 介面
description: 瞭解介面F#如何指定其他類別所要執行的相關成員集合。
ms.date: 05/16/2016
ms.openlocfilehash: 8f054a668ad0fbc2453a45883e8052471280eca3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627644"
---
# <a name="interfaces"></a><span data-ttu-id="44e7d-103">介面</span><span class="sxs-lookup"><span data-stu-id="44e7d-103">Interfaces</span></span>

<span data-ttu-id="44e7d-104">*介面*會指定其他類別所要執行的相關成員集合。</span><span class="sxs-lookup"><span data-stu-id="44e7d-104">*Interfaces* specify sets of related members that other classes implement.</span></span>

## <a name="syntax"></a><span data-ttu-id="44e7d-105">語法</span><span class="sxs-lookup"><span data-stu-id="44e7d-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="44e7d-106">備註</span><span class="sxs-lookup"><span data-stu-id="44e7d-106">Remarks</span></span>

<span data-ttu-id="44e7d-107">介面宣告類似于類別宣告, 不同之處在于不會執行任何成員。</span><span class="sxs-lookup"><span data-stu-id="44e7d-107">Interface declarations resemble class declarations except that no members are implemented.</span></span> <span data-ttu-id="44e7d-108">相反地, 所有成員都是抽象的, 如關鍵字`abstract`所指示。</span><span class="sxs-lookup"><span data-stu-id="44e7d-108">Instead, all the members are abstract, as indicated by the keyword `abstract`.</span></span> <span data-ttu-id="44e7d-109">您未提供抽象方法的方法主體。</span><span class="sxs-lookup"><span data-stu-id="44e7d-109">You do not provide a method body for abstract methods.</span></span> <span data-ttu-id="44e7d-110">不過, 您也可以提供預設的執行方式, 方法是同時包含成員的個別定義做為方法, `default`並搭配關鍵字。</span><span class="sxs-lookup"><span data-stu-id="44e7d-110">However, you can provide a default implementation by also including a separate definition of the member as a method together with the `default` keyword.</span></span> <span data-ttu-id="44e7d-111">這麼做相當於在其他 .NET 語言的基類中建立虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="44e7d-111">Doing so is equivalent to creating a virtual method in a base class in other .NET languages.</span></span> <span data-ttu-id="44e7d-112">這類虛擬方法可以在實介面的類別中覆寫。</span><span class="sxs-lookup"><span data-stu-id="44e7d-112">Such a virtual method can be overridden in classes that implement the interface.</span></span>

<span data-ttu-id="44e7d-113">介面的預設存取範圍是`public`。</span><span class="sxs-lookup"><span data-stu-id="44e7d-113">The default accessibility for interfaces is `public`.</span></span>

<span data-ttu-id="44e7d-114">您可以使用一般F#語法, 選擇性地提供每個方法參數的名稱:</span><span class="sxs-lookup"><span data-stu-id="44e7d-114">You can optionally give each method parameter a name using normal F# syntax:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

<span data-ttu-id="44e7d-115">在上述`ISprintable`範例中`Print` , 方法具有名稱`format`為之類型`string`的單一參數。</span><span class="sxs-lookup"><span data-stu-id="44e7d-115">In the above `ISprintable` example, the `Print` method has a single parameter of the type `string` with the name `format`.</span></span>

<span data-ttu-id="44e7d-116">有兩種方式可以執行介面: 藉由使用物件運算式, 以及使用類別類型。</span><span class="sxs-lookup"><span data-stu-id="44e7d-116">There are two ways to implement interfaces: by using object expressions, and by using class types.</span></span> <span data-ttu-id="44e7d-117">在任一情況下, 類別類型或物件運算式都會針對介面的抽象方法提供方法主體。</span><span class="sxs-lookup"><span data-stu-id="44e7d-117">In either case, the class type or object expression provides method bodies for abstract methods of the interface.</span></span> <span data-ttu-id="44e7d-118">針對每個實作為介面的型別, 都是專用的。</span><span class="sxs-lookup"><span data-stu-id="44e7d-118">Implementations are specific to each type that implements the interface.</span></span> <span data-ttu-id="44e7d-119">因此, 不同類型上的介面方法可能會彼此不同。</span><span class="sxs-lookup"><span data-stu-id="44e7d-119">Therefore, interface methods on different types might be different from each other.</span></span>

<span data-ttu-id="44e7d-120">當您`interface`使用`end`輕量語法時, 關鍵字和 (用來標示定義的開始和結束) 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="44e7d-120">The keywords `interface` and `end`, which mark the start and end of the definition, are optional when you use lightweight syntax.</span></span> <span data-ttu-id="44e7d-121">如果您未使用這些關鍵字, 編譯器會藉由分析您所使用的結構, 嘗試推斷該類型是類別或介面。</span><span class="sxs-lookup"><span data-stu-id="44e7d-121">If you do not use these keywords, the compiler attempts to infer whether the type is a class or an interface by analyzing the constructs that you use.</span></span> <span data-ttu-id="44e7d-122">如果您定義成員或使用其他類別語法, 則會將類型視為類別。</span><span class="sxs-lookup"><span data-stu-id="44e7d-122">If you define a member or use other class syntax, the type is interpreted as a class.</span></span>

<span data-ttu-id="44e7d-123">.NET 程式碼樣式是用來開始所有具有資本`I`的介面。</span><span class="sxs-lookup"><span data-stu-id="44e7d-123">The .NET coding style is to begin all interfaces with a capital `I`.</span></span>

## <a name="implementing-interfaces-by-using-class-types"></a><span data-ttu-id="44e7d-124">使用類別類型來執行介面</span><span class="sxs-lookup"><span data-stu-id="44e7d-124">Implementing Interfaces by Using Class Types</span></span>

<span data-ttu-id="44e7d-125">您可以使用`interface`關鍵字、介面的名稱`with`和關鍵字 (後面接著介面成員定義) 來執行類別類型中的一或多個介面, 如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="44e7d-125">You can implement one or more interfaces in a class type by using the `interface` keyword, the name of the interface, and the `with` keyword, followed by the interface member definitions, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

<span data-ttu-id="44e7d-126">系統會繼承介面實作為, 因此任何衍生的類別都不需要加以重新執行。</span><span class="sxs-lookup"><span data-stu-id="44e7d-126">Interface implementations are inherited, so any derived classes do not need to reimplement them.</span></span>

## <a name="calling-interface-methods"></a><span data-ttu-id="44e7d-127">呼叫介面方法</span><span class="sxs-lookup"><span data-stu-id="44e7d-127">Calling Interface Methods</span></span>

<span data-ttu-id="44e7d-128">介面方法只能透過介面呼叫, 而不能透過實作為介面之型別的任何物件。</span><span class="sxs-lookup"><span data-stu-id="44e7d-128">Interface methods can be called only through the interface, not through any object of the type that implements the interface.</span></span> <span data-ttu-id="44e7d-129">因此, 您可能必須使用`:>`運算子`upcast`或運算子來向上轉換成介面類別型, 才能呼叫這些方法。</span><span class="sxs-lookup"><span data-stu-id="44e7d-129">Thus, you might have to upcast to the interface type by using the `:>` operator or the `upcast` operator in order to call these methods.</span></span>

<span data-ttu-id="44e7d-130">若要在具有類型`SomeClass`的物件時呼叫介面方法, 您必須將物件向上轉型為介面類別型, 如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="44e7d-130">To call the interface method when you have an object of type `SomeClass`, you must upcast the object to the interface type, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

<span data-ttu-id="44e7d-131">另一個替代方式是在 upcasts 和呼叫介面方法的物件上宣告方法, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="44e7d-131">An alternative is to declare a method on the object that upcasts and calls the interface method, as in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a><span data-ttu-id="44e7d-132">使用物件運算式來執行介面</span><span class="sxs-lookup"><span data-stu-id="44e7d-132">Implementing Interfaces by Using Object Expressions</span></span>

<span data-ttu-id="44e7d-133">物件運算式提供了簡單的方法來執行介面。</span><span class="sxs-lookup"><span data-stu-id="44e7d-133">Object expressions provide a short way to implement an interface.</span></span> <span data-ttu-id="44e7d-134">當您不需要建立命名類型, 而且只想要支援介面方法的物件, 而不需要任何其他方法時, 它們會很有用。</span><span class="sxs-lookup"><span data-stu-id="44e7d-134">They are useful when you do not have to create a named type, and you just want an object that supports the interface methods, without any additional methods.</span></span> <span data-ttu-id="44e7d-135">下列程式碼說明物件運算式。</span><span class="sxs-lookup"><span data-stu-id="44e7d-135">An object expression is illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a><span data-ttu-id="44e7d-136">介面繼承</span><span class="sxs-lookup"><span data-stu-id="44e7d-136">Interface Inheritance</span></span>

<span data-ttu-id="44e7d-137">介面可以繼承自一或多個基底介面。</span><span class="sxs-lookup"><span data-stu-id="44e7d-137">Interfaces can inherit from one or more base interfaces.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="see-also"></a><span data-ttu-id="44e7d-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44e7d-138">See also</span></span>

- [<span data-ttu-id="44e7d-139">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="44e7d-139">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="44e7d-140">物件運算式</span><span class="sxs-lookup"><span data-stu-id="44e7d-140">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="44e7d-141">類別</span><span class="sxs-lookup"><span data-stu-id="44e7d-141">Classes</span></span>](classes.md)
