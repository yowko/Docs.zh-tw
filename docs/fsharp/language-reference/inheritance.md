---
title: 繼承
description: 瞭解如何使用"繼承"關鍵字指定 F# 繼承關係。
ms.date: 05/16/2016
ms.openlocfilehash: 5ab891a93528427a66e4eb8f7bfeccbf6e4d2c7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400285"
---
# <a name="inheritance"></a><span data-ttu-id="63ae4-103">繼承</span><span class="sxs-lookup"><span data-stu-id="63ae4-103">Inheritance</span></span>

<span data-ttu-id="63ae4-104">繼承用於在物件導向的程式設計中對"is-a"關係或子類型化建模。</span><span class="sxs-lookup"><span data-stu-id="63ae4-104">Inheritance is used to model the "is-a" relationship, or subtyping, in object-oriented programming.</span></span>

## <a name="specifying-inheritance-relationships"></a><span data-ttu-id="63ae4-105">指定繼承關係</span><span class="sxs-lookup"><span data-stu-id="63ae4-105">Specifying Inheritance Relationships</span></span>

<span data-ttu-id="63ae4-106">通過在類聲明中使用 關鍵字`inherit`指定繼承關係。</span><span class="sxs-lookup"><span data-stu-id="63ae4-106">You specify inheritance relationships by using the `inherit` keyword in a class declaration.</span></span> <span data-ttu-id="63ae4-107">基本語法形式如下例所示。</span><span class="sxs-lookup"><span data-stu-id="63ae4-107">The basic syntactical form is shown in the following example.</span></span>

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

<span data-ttu-id="63ae4-108">類最多隻能有一個直接基類。</span><span class="sxs-lookup"><span data-stu-id="63ae4-108">A class can have at most one direct base class.</span></span> <span data-ttu-id="63ae4-109">如果不使用`inherit`關鍵字指定基類，則類隱式繼承從`System.Object`。</span><span class="sxs-lookup"><span data-stu-id="63ae4-109">If you do not specify a base class by using the `inherit` keyword, the class implicitly inherits from `System.Object`.</span></span>

## <a name="inherited-members"></a><span data-ttu-id="63ae4-110">繼承的成員</span><span class="sxs-lookup"><span data-stu-id="63ae4-110">Inherited Members</span></span>

<span data-ttu-id="63ae4-111">如果類從其他類繼承，則派生類的使用者可以使用基類的方法和成員，就像它們是派生類的直接成員一樣。</span><span class="sxs-lookup"><span data-stu-id="63ae4-111">If a class inherits from another class, the methods and members of the base class are available to users of the derived class as if they were direct members of the derived class.</span></span>

<span data-ttu-id="63ae4-112">任何 let 綁定和建構函式參數都是類的私有參數，因此無法從派生類訪問。</span><span class="sxs-lookup"><span data-stu-id="63ae4-112">Any let bindings and constructor parameters are private to a class and, therefore, cannot be accessed from derived classes.</span></span>

<span data-ttu-id="63ae4-113">關鍵字`base`在派生類中可用，並引用基類實例。</span><span class="sxs-lookup"><span data-stu-id="63ae4-113">The keyword `base` is available in derived classes and refers to the base class instance.</span></span> <span data-ttu-id="63ae4-114">它像自識別碼一樣使用。</span><span class="sxs-lookup"><span data-stu-id="63ae4-114">It is used like the self-identifier.</span></span>

## <a name="virtual-methods-and-overrides"></a><span data-ttu-id="63ae4-115">虛擬方法和重寫</span><span class="sxs-lookup"><span data-stu-id="63ae4-115">Virtual Methods and Overrides</span></span>

<span data-ttu-id="63ae4-116">與其他 .NET 語言相比，虛擬方法（和屬性）在 F# 中的工作方式略有不同。</span><span class="sxs-lookup"><span data-stu-id="63ae4-116">Virtual methods (and properties) work somewhat differently in F# as compared to other .NET languages.</span></span> <span data-ttu-id="63ae4-117">要聲明新的虛擬成員，請使用 關鍵字`abstract`。</span><span class="sxs-lookup"><span data-stu-id="63ae4-117">To declare a new virtual member, you use the `abstract` keyword.</span></span> <span data-ttu-id="63ae4-118">無論是否為該方法提供預設實現，都可以執行此操作。</span><span class="sxs-lookup"><span data-stu-id="63ae4-118">You do this regardless of whether you provide a default implementation for that method.</span></span> <span data-ttu-id="63ae4-119">因此，基類中虛擬方法的完整定義遵循此模式：</span><span class="sxs-lookup"><span data-stu-id="63ae4-119">Thus a complete definition of a virtual method in a base class follows this pattern:</span></span>

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="63ae4-120">在派生類中，此虛擬方法的重寫遵循此模式：</span><span class="sxs-lookup"><span data-stu-id="63ae4-120">And in a derived class, an override of this virtual method follows this pattern:</span></span>

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="63ae4-121">如果在基類中省略預設實現，則基類將成為抽象類別。</span><span class="sxs-lookup"><span data-stu-id="63ae4-121">If you omit the default implementation in the base class, the base class becomes an abstract class.</span></span>

<span data-ttu-id="63ae4-122">以下代碼示例演示了基類中新虛擬方法`function1`的聲明以及如何在派生類中重寫它。</span><span class="sxs-lookup"><span data-stu-id="63ae4-122">The following code example illustrates the declaration of a new virtual method `function1` in a base class and how to override it in a derived class.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a><span data-ttu-id="63ae4-123">建構函式和繼承</span><span class="sxs-lookup"><span data-stu-id="63ae4-123">Constructors and Inheritance</span></span>

<span data-ttu-id="63ae4-124">基類的建構函式必須在派生類中調用。</span><span class="sxs-lookup"><span data-stu-id="63ae4-124">The constructor for the base class must be called in the derived class.</span></span> <span data-ttu-id="63ae4-125">基類建構函式的參數出現在`inherit`子句中的參數清單中。</span><span class="sxs-lookup"><span data-stu-id="63ae4-125">The arguments for the base class constructor appear in the argument list in the `inherit` clause.</span></span> <span data-ttu-id="63ae4-126">使用的值必須根據提供給派生類建構函式的參數確定。</span><span class="sxs-lookup"><span data-stu-id="63ae4-126">The values that are used must be determined from the arguments supplied to the derived class constructor.</span></span>

<span data-ttu-id="63ae4-127">以下代碼顯示基類和派生類，其中派生類調用繼承子句中的基類建構函式：</span><span class="sxs-lookup"><span data-stu-id="63ae4-127">The following code shows a base class and a derived class, where the derived class calls the base class constructor in the inherit clause:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

<span data-ttu-id="63ae4-128">在多個建構函式的情況下，可以使用以下代碼。</span><span class="sxs-lookup"><span data-stu-id="63ae4-128">In the case of multiple constructors, the following code can be used.</span></span> <span data-ttu-id="63ae4-129">派生類建構函式的第一行是`inherit`子句，欄位顯示為使用 關鍵字聲明的`val`顯式欄位。</span><span class="sxs-lookup"><span data-stu-id="63ae4-129">The first line of the derived class constructors is the `inherit` clause, and the fields appear as explicit fields that are declared with the `val` keyword.</span></span> <span data-ttu-id="63ae4-130">有關詳細資訊，請參閱[顯式欄位：`val`關鍵字](./members/explicit-fields-the-val-keyword.md)。</span><span class="sxs-lookup"><span data-stu-id="63ae4-130">For more information, see [Explicit Fields: The `val` Keyword](./members/explicit-fields-the-val-keyword.md).</span></span>

```fsharp
type BaseClass =
    val string1 : string
    new (str) = { string1 = str }
    new () = { string1 = "" }

type DerivedClass =
    inherit BaseClass

    val string2 : string
    new (str1, str2) = { inherit BaseClass(str1); string2 = str2 }
    new (str2) = { inherit BaseClass(); string2 = str2 }

let obj1 = DerivedClass("A", "B")
let obj2 = DerivedClass("A")
```

## <a name="alternatives-to-inheritance"></a><span data-ttu-id="63ae4-131">繼承的替代方法</span><span class="sxs-lookup"><span data-stu-id="63ae4-131">Alternatives to Inheritance</span></span>

<span data-ttu-id="63ae4-132">如果需要對類型進行細微修改，請考慮使用物件運算式作為繼承的替代方法。</span><span class="sxs-lookup"><span data-stu-id="63ae4-132">In cases where a minor modification of a type is required, consider using an object expression as an alternative to inheritance.</span></span> <span data-ttu-id="63ae4-133">以下示例說明了使用物件運算式作為創建新派生類型的替代方法：</span><span class="sxs-lookup"><span data-stu-id="63ae4-133">The following example illustrates the use of an object expression as an alternative to creating a new derived type:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

<span data-ttu-id="63ae4-134">有關物件運算式的詳細資訊，請參閱[物件運算式](object-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="63ae4-134">For more information about object expressions, see [Object Expressions](object-expressions.md).</span></span>

<span data-ttu-id="63ae4-135">創建物件層次結構時，請考慮使用受歧視的聯合而不是繼承。</span><span class="sxs-lookup"><span data-stu-id="63ae4-135">When you are creating object hierarchies, consider using a discriminated union instead of inheritance.</span></span> <span data-ttu-id="63ae4-136">受歧視的聯合還可以對共用公共整體類型的不同物件的不同行為建模。</span><span class="sxs-lookup"><span data-stu-id="63ae4-136">Discriminated unions can also model varied behavior of different objects that share a common overall type.</span></span> <span data-ttu-id="63ae4-137">單個受歧視的聯合通常可以消除對一些派生類的需求，這些類彼此的微小變化。</span><span class="sxs-lookup"><span data-stu-id="63ae4-137">A single discriminated union can often eliminate the need for a number of derived classes that are minor variations of each other.</span></span> <span data-ttu-id="63ae4-138">有關受歧視工會的資訊，請參閱[歧視工會](discriminated-unions.md)。</span><span class="sxs-lookup"><span data-stu-id="63ae4-138">For information about discriminated unions, see [Discriminated Unions](discriminated-unions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="63ae4-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63ae4-139">See also</span></span>

- [<span data-ttu-id="63ae4-140">物件運算式</span><span class="sxs-lookup"><span data-stu-id="63ae4-140">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="63ae4-141">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="63ae4-141">F# Language Reference</span></span>](index.md)
