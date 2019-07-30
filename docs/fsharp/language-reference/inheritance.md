---
title: 繼承
description: 瞭解如何使用 ' F# inherit ' 關鍵字來指定繼承關聯性。
ms.date: 05/16/2016
ms.openlocfilehash: 5ab891a93528427a66e4eb8f7bfeccbf6e4d2c7e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627660"
---
# <a name="inheritance"></a><span data-ttu-id="d8ee1-103">繼承</span><span class="sxs-lookup"><span data-stu-id="d8ee1-103">Inheritance</span></span>

<span data-ttu-id="d8ee1-104">繼承是用來建立物件導向程式設計中的「is-a」關聯性或 subtyping 模型。</span><span class="sxs-lookup"><span data-stu-id="d8ee1-104">Inheritance is used to model the "is-a" relationship, or subtyping, in object-oriented programming.</span></span>

## <a name="specifying-inheritance-relationships"></a><span data-ttu-id="d8ee1-105">指定繼承關聯性</span><span class="sxs-lookup"><span data-stu-id="d8ee1-105">Specifying Inheritance Relationships</span></span>

<span data-ttu-id="d8ee1-106">您可以使用類別宣告中的`inherit`關鍵字來指定繼承關聯性。</span><span class="sxs-lookup"><span data-stu-id="d8ee1-106">You specify inheritance relationships by using the `inherit` keyword in a class declaration.</span></span> <span data-ttu-id="d8ee1-107">基本的語法形式如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d8ee1-107">The basic syntactical form is shown in the following example.</span></span>

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

<span data-ttu-id="d8ee1-108">一個類別最多隻能有一個直接基類。</span><span class="sxs-lookup"><span data-stu-id="d8ee1-108">A class can have at most one direct base class.</span></span> <span data-ttu-id="d8ee1-109">如果您未使用`inherit`關鍵字指定基類, 類別會隱含繼承自。 `System.Object`</span><span class="sxs-lookup"><span data-stu-id="d8ee1-109">If you do not specify a base class by using the `inherit` keyword, the class implicitly inherits from `System.Object`.</span></span>

## <a name="inherited-members"></a><span data-ttu-id="d8ee1-110">繼承的成員</span><span class="sxs-lookup"><span data-stu-id="d8ee1-110">Inherited Members</span></span>

<span data-ttu-id="d8ee1-111">如果類別繼承自另一個類別, 則衍生類別的使用者可以使用基類的方法和成員, 就如同它們是衍生類別的直接成員一樣。</span><span class="sxs-lookup"><span data-stu-id="d8ee1-111">If a class inherits from another class, the methods and members of the base class are available to users of the derived class as if they were direct members of the derived class.</span></span>

<span data-ttu-id="d8ee1-112">任何 let 系結和函式參數都是類別的私用, 因此無法從衍生類別存取。</span><span class="sxs-lookup"><span data-stu-id="d8ee1-112">Any let bindings and constructor parameters are private to a class and, therefore, cannot be accessed from derived classes.</span></span>

<span data-ttu-id="d8ee1-113">關鍵字`base`可在衍生類別中使用, 並參考基類實例。</span><span class="sxs-lookup"><span data-stu-id="d8ee1-113">The keyword `base` is available in derived classes and refers to the base class instance.</span></span> <span data-ttu-id="d8ee1-114">其使用方式與自我識別碼類似。</span><span class="sxs-lookup"><span data-stu-id="d8ee1-114">It is used like the self-identifier.</span></span>

## <a name="virtual-methods-and-overrides"></a><span data-ttu-id="d8ee1-115">虛擬方法和覆寫</span><span class="sxs-lookup"><span data-stu-id="d8ee1-115">Virtual Methods and Overrides</span></span>

<span data-ttu-id="d8ee1-116">相較于其他 .NET 語言, 虛擬方法 ( F#和屬性) 在中的工作方式稍有不同。</span><span class="sxs-lookup"><span data-stu-id="d8ee1-116">Virtual methods (and properties) work somewhat differently in F# as compared to other .NET languages.</span></span> <span data-ttu-id="d8ee1-117">若要宣告新的虛擬成員, 請使用`abstract`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d8ee1-117">To declare a new virtual member, you use the `abstract` keyword.</span></span> <span data-ttu-id="d8ee1-118">無論您是否為該方法提供預設的實作為, 都可以執行此動作。</span><span class="sxs-lookup"><span data-stu-id="d8ee1-118">You do this regardless of whether you provide a default implementation for that method.</span></span> <span data-ttu-id="d8ee1-119">因此, 基底類別中虛擬方法的完整定義會遵循此模式:</span><span class="sxs-lookup"><span data-stu-id="d8ee1-119">Thus a complete definition of a virtual method in a base class follows this pattern:</span></span>

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="d8ee1-120">而在衍生類別中, 此虛擬方法的覆寫會遵循此模式:</span><span class="sxs-lookup"><span data-stu-id="d8ee1-120">And in a derived class, an override of this virtual method follows this pattern:</span></span>

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="d8ee1-121">如果您省略基類中的預設實作為, 基底類別會變成抽象類別。</span><span class="sxs-lookup"><span data-stu-id="d8ee1-121">If you omit the default implementation in the base class, the base class becomes an abstract class.</span></span>

<span data-ttu-id="d8ee1-122">下列程式碼範例說明如何在基類中宣告新的`function1`虛擬方法, 以及如何在衍生類別中覆寫它。</span><span class="sxs-lookup"><span data-stu-id="d8ee1-122">The following code example illustrates the declaration of a new virtual method `function1` in a base class and how to override it in a derived class.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a><span data-ttu-id="d8ee1-123">建構函式和繼承</span><span class="sxs-lookup"><span data-stu-id="d8ee1-123">Constructors and Inheritance</span></span>

<span data-ttu-id="d8ee1-124">基類的函式必須在衍生類別中呼叫。</span><span class="sxs-lookup"><span data-stu-id="d8ee1-124">The constructor for the base class must be called in the derived class.</span></span> <span data-ttu-id="d8ee1-125">基類的引數會出現在`inherit`子句的引數清單中。</span><span class="sxs-lookup"><span data-stu-id="d8ee1-125">The arguments for the base class constructor appear in the argument list in the `inherit` clause.</span></span> <span data-ttu-id="d8ee1-126">所使用的值必須從提供給衍生類別的引數來判斷。</span><span class="sxs-lookup"><span data-stu-id="d8ee1-126">The values that are used must be determined from the arguments supplied to the derived class constructor.</span></span>

<span data-ttu-id="d8ee1-127">下列程式碼顯示基類和衍生類別, 其中衍生的類別會在繼承子句中呼叫基類的函式:</span><span class="sxs-lookup"><span data-stu-id="d8ee1-127">The following code shows a base class and a derived class, where the derived class calls the base class constructor in the inherit clause:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

<span data-ttu-id="d8ee1-128">在多個函式的情況下, 可以使用下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="d8ee1-128">In the case of multiple constructors, the following code can be used.</span></span> <span data-ttu-id="d8ee1-129">衍生類別的第一行程式碼是`inherit`子句, 而欄位則是以`val`關鍵字宣告的明確欄位來顯示。</span><span class="sxs-lookup"><span data-stu-id="d8ee1-129">The first line of the derived class constructors is the `inherit` clause, and the fields appear as explicit fields that are declared with the `val` keyword.</span></span> <span data-ttu-id="d8ee1-130">如需詳細資訊, [請參閱明確欄位:`val`關鍵字。](./members/explicit-fields-the-val-keyword.md)</span><span class="sxs-lookup"><span data-stu-id="d8ee1-130">For more information, see [Explicit Fields: The `val` Keyword](./members/explicit-fields-the-val-keyword.md).</span></span>

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

## <a name="alternatives-to-inheritance"></a><span data-ttu-id="d8ee1-131">繼承的替代專案</span><span class="sxs-lookup"><span data-stu-id="d8ee1-131">Alternatives to Inheritance</span></span>

<span data-ttu-id="d8ee1-132">在需要稍微修改類型的情況下, 請考慮使用物件運算式做為繼承的替代方法。</span><span class="sxs-lookup"><span data-stu-id="d8ee1-132">In cases where a minor modification of a type is required, consider using an object expression as an alternative to inheritance.</span></span> <span data-ttu-id="d8ee1-133">下列範例說明如何使用物件運算式, 做為建立新衍生型別的替代方法:</span><span class="sxs-lookup"><span data-stu-id="d8ee1-133">The following example illustrates the use of an object expression as an alternative to creating a new derived type:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

<span data-ttu-id="d8ee1-134">如需物件運算式的詳細資訊, 請參閱[物件運算式](object-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="d8ee1-134">For more information about object expressions, see [Object Expressions](object-expressions.md).</span></span>

<span data-ttu-id="d8ee1-135">當您建立物件階層時, 請考慮使用區分聯集, 而不是繼承。</span><span class="sxs-lookup"><span data-stu-id="d8ee1-135">When you are creating object hierarchies, consider using a discriminated union instead of inheritance.</span></span> <span data-ttu-id="d8ee1-136">相異聯集也可以針對共用一般類型的不同物件, 建立各種不同的行為模型。</span><span class="sxs-lookup"><span data-stu-id="d8ee1-136">Discriminated unions can also model varied behavior of different objects that share a common overall type.</span></span> <span data-ttu-id="d8ee1-137">單一差異聯集通常不需要多個不同的衍生類別, 而是彼此的次要變化。</span><span class="sxs-lookup"><span data-stu-id="d8ee1-137">A single discriminated union can often eliminate the need for a number of derived classes that are minor variations of each other.</span></span> <span data-ttu-id="d8ee1-138">如需區分等位的詳細資訊, 請參閱[區分](discriminated-unions.md)等位。</span><span class="sxs-lookup"><span data-stu-id="d8ee1-138">For information about discriminated unions, see [Discriminated Unions](discriminated-unions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d8ee1-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8ee1-139">See also</span></span>

- [<span data-ttu-id="d8ee1-140">物件運算式</span><span class="sxs-lookup"><span data-stu-id="d8ee1-140">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="d8ee1-141">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="d8ee1-141">F# Language Reference</span></span>](index.md)
