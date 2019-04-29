---
title: 繼承
description: 了解如何指定F#使用 'inherit' 關鍵字的繼承關聯性。
ms.date: 05/16/2016
ms.openlocfilehash: 775ee52039caf4c4ab65f82fa21d4e536135a12a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937458"
---
# <a name="inheritance"></a><span data-ttu-id="190c9-103">繼承</span><span class="sxs-lookup"><span data-stu-id="190c9-103">Inheritance</span></span>

<span data-ttu-id="190c9-104">使用繼承來建立模型的 「 是 」 關聯性，或子型別，在物件導向程式設計中。</span><span class="sxs-lookup"><span data-stu-id="190c9-104">Inheritance is used to model the "is-a" relationship, or subtyping, in object-oriented programming.</span></span>

## <a name="specifying-inheritance-relationships"></a><span data-ttu-id="190c9-105">指定的繼承關聯性</span><span class="sxs-lookup"><span data-stu-id="190c9-105">Specifying Inheritance Relationships</span></span>

<span data-ttu-id="190c9-106">使用指定繼承關聯性`inherit`類別宣告中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="190c9-106">You specify inheritance relationships by using the `inherit` keyword in a class declaration.</span></span> <span data-ttu-id="190c9-107">基本的語法形式是由下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="190c9-107">The basic syntactical form is shown in the following example.</span></span>

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

<span data-ttu-id="190c9-108">一個類別可以有最多一個基底類別。</span><span class="sxs-lookup"><span data-stu-id="190c9-108">A class can have at most one direct base class.</span></span> <span data-ttu-id="190c9-109">如果您未指定基底類別使用`inherit`關鍵字，類別會隱含地繼承自`System.Object`。</span><span class="sxs-lookup"><span data-stu-id="190c9-109">If you do not specify a base class by using the `inherit` keyword, the class implicitly inherits from `System.Object`.</span></span>

## <a name="inherited-members"></a><span data-ttu-id="190c9-110">繼承的成員</span><span class="sxs-lookup"><span data-stu-id="190c9-110">Inherited Members</span></span>

<span data-ttu-id="190c9-111">如果類別繼承自另一個類別，方法和基底類別成員可用於衍生類別的使用者，就像是在衍生類別的直接成員一樣。</span><span class="sxs-lookup"><span data-stu-id="190c9-111">If a class inherits from another class, the methods and members of the base class are available to users of the derived class as if they were direct members of the derived class.</span></span>

<span data-ttu-id="190c9-112">任何的 let 繫結和建構函式參數都是私用的類別，因此，無法從衍生類別存取。</span><span class="sxs-lookup"><span data-stu-id="190c9-112">Any let bindings and constructor parameters are private to a class and, therefore, cannot be accessed from derived classes.</span></span>

<span data-ttu-id="190c9-113">關鍵字`base`隨附在衍生類別中，參考的基底類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="190c9-113">The keyword `base` is available in derived classes and refers to the base class instance.</span></span> <span data-ttu-id="190c9-114">它當成自我識別項。</span><span class="sxs-lookup"><span data-stu-id="190c9-114">It is used like the self-identifier.</span></span>

## <a name="virtual-methods-and-overrides"></a><span data-ttu-id="190c9-115">虛擬方法和覆寫</span><span class="sxs-lookup"><span data-stu-id="190c9-115">Virtual Methods and Overrides</span></span>

<span data-ttu-id="190c9-116">虛擬方法 （和屬性） 運作方式稍有不同的F#相較於其他.NET 語言。</span><span class="sxs-lookup"><span data-stu-id="190c9-116">Virtual methods (and properties) work somewhat differently in F# as compared to other .NET languages.</span></span> <span data-ttu-id="190c9-117">若要宣告新的虛擬成員，您使用`abstract`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="190c9-117">To declare a new virtual member, you use the `abstract` keyword.</span></span> <span data-ttu-id="190c9-118">要這麼做，不論您是否提供該方法的預設實作。</span><span class="sxs-lookup"><span data-stu-id="190c9-118">You do this regardless of whether you provide a default implementation for that method.</span></span> <span data-ttu-id="190c9-119">因此基底類別中的虛擬方法的完整定義會遵循下列模式：</span><span class="sxs-lookup"><span data-stu-id="190c9-119">Thus a complete definition of a virtual method in a base class follows this pattern:</span></span>

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="190c9-120">然後，在衍生類別中，此虛擬方法的覆寫會遵循此模式：</span><span class="sxs-lookup"><span data-stu-id="190c9-120">And in a derived class, an override of this virtual method follows this pattern:</span></span>

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="190c9-121">如果您省略基底類別中的預設實作，基底類別變成抽象類別。</span><span class="sxs-lookup"><span data-stu-id="190c9-121">If you omit the default implementation in the base class, the base class becomes an abstract class.</span></span>

<span data-ttu-id="190c9-122">下列程式碼範例說明新的虛擬方法的宣告`function1`基底類別，以及如何在衍生類別中覆寫它。</span><span class="sxs-lookup"><span data-stu-id="190c9-122">The following code example illustrates the declaration of a new virtual method `function1` in a base class and how to override it in a derived class.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a><span data-ttu-id="190c9-123">建構函式和繼承</span><span class="sxs-lookup"><span data-stu-id="190c9-123">Constructors and Inheritance</span></span>

<span data-ttu-id="190c9-124">在衍生類別中，就必須呼叫基底類別的建構函式。</span><span class="sxs-lookup"><span data-stu-id="190c9-124">The constructor for the base class must be called in the derived class.</span></span> <span data-ttu-id="190c9-125">基底類別建構函式的引數出現在引數清單中`inherit`子句。</span><span class="sxs-lookup"><span data-stu-id="190c9-125">The arguments for the base class constructor appear in the argument list in the `inherit` clause.</span></span> <span data-ttu-id="190c9-126">從衍生的類別建構函式所提供的引數，必須決定所使用的值。</span><span class="sxs-lookup"><span data-stu-id="190c9-126">The values that are used must be determined from the arguments supplied to the derived class constructor.</span></span>

<span data-ttu-id="190c9-127">下列程式碼顯示基底類別和衍生的類別，衍生的類別繼承子句中呼叫基底類別建構函式的位置：</span><span class="sxs-lookup"><span data-stu-id="190c9-127">The following code shows a base class and a derived class, where the derived class calls the base class constructor in the inherit clause:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

<span data-ttu-id="190c9-128">在多個建構函式的情況下可以使用下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="190c9-128">In the case of multiple constructors, the following code can be used.</span></span> <span data-ttu-id="190c9-129">在衍生的類別建構函式的第一行會`inherit`子句和欄位會顯示為使用宣告的明確欄位`val`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="190c9-129">The first line of the derived class constructors is the `inherit` clause, and the fields appear as explicit fields that are declared with the `val` keyword.</span></span> <span data-ttu-id="190c9-130">如需詳細資訊，請參閱[明確欄位：`val`關鍵字](members/explicit-fields-the-val-keyword.md)。</span><span class="sxs-lookup"><span data-stu-id="190c9-130">For more information, see [Explicit Fields: The `val` Keyword](members/explicit-fields-the-val-keyword.md).</span></span>

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

## <a name="alternatives-to-inheritance"></a><span data-ttu-id="190c9-131">繼承的替代方案</span><span class="sxs-lookup"><span data-stu-id="190c9-131">Alternatives to Inheritance</span></span>

<span data-ttu-id="190c9-132">在需要稍微修改的型別所在的情況下，請考慮使用替代繼承的物件運算式。</span><span class="sxs-lookup"><span data-stu-id="190c9-132">In cases where a minor modification of a type is required, consider using an object expression as an alternative to inheritance.</span></span> <span data-ttu-id="190c9-133">下列範例說明如何使用的物件運算式，以建立新的衍生的類型的替代方案：</span><span class="sxs-lookup"><span data-stu-id="190c9-133">The following example illustrates the use of an object expression as an alternative to creating a new derived type:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

<span data-ttu-id="190c9-134">如需有關物件運算式的詳細資訊，請參閱[物件運算式](object-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="190c9-134">For more information about object expressions, see [Object Expressions](object-expressions.md).</span></span>

<span data-ttu-id="190c9-135">當您建立的物件階層架構時，請考慮使用已區分的聯集而非繼承。</span><span class="sxs-lookup"><span data-stu-id="190c9-135">When you are creating object hierarchies, consider using a discriminated union instead of inheritance.</span></span> <span data-ttu-id="190c9-136">差別等位也各不相同的模型行為的不同共用常見的整體類型的物件。</span><span class="sxs-lookup"><span data-stu-id="190c9-136">Discriminated unions can also model varied behavior of different objects that share a common overall type.</span></span> <span data-ttu-id="190c9-137">單一的已區分聯集可以通常不需要是彼此的微小差異的衍生類別的數字。</span><span class="sxs-lookup"><span data-stu-id="190c9-137">A single discriminated union can often eliminate the need for a number of derived classes that are minor variations of each other.</span></span> <span data-ttu-id="190c9-138">差別聯集的相關資訊，請參閱[差別聯集](discriminated-unions.md)。</span><span class="sxs-lookup"><span data-stu-id="190c9-138">For information about discriminated unions, see [Discriminated Unions](discriminated-unions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="190c9-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="190c9-139">See also</span></span>

- [<span data-ttu-id="190c9-140">物件運算式</span><span class="sxs-lookup"><span data-stu-id="190c9-140">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="190c9-141">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="190c9-141">F# Language Reference</span></span>](index.md)