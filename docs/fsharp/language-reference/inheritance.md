---
title: 繼承
description: "瞭解如何使用 ' inherit ' 關鍵字指定 F # 繼承關聯性。"
ms.date: 05/16/2016
ms.openlocfilehash: 5ab891a93528427a66e4eb8f7bfeccbf6e4d2c7e
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223845"
---
# <a name="inheritance"></a><span data-ttu-id="b3e07-103">繼承</span><span class="sxs-lookup"><span data-stu-id="b3e07-103">Inheritance</span></span>

<span data-ttu-id="b3e07-104">在物件導向程式設計中，會使用繼承來建立「是」關聯性或 subtyping 的模型。</span><span class="sxs-lookup"><span data-stu-id="b3e07-104">Inheritance is used to model the "is-a" relationship, or subtyping, in object-oriented programming.</span></span>

## <a name="specifying-inheritance-relationships"></a><span data-ttu-id="b3e07-105">指定繼承關聯性</span><span class="sxs-lookup"><span data-stu-id="b3e07-105">Specifying Inheritance Relationships</span></span>

<span data-ttu-id="b3e07-106">您可以在類別宣告中使用關鍵字來指定繼承關聯性 `inherit` 。</span><span class="sxs-lookup"><span data-stu-id="b3e07-106">You specify inheritance relationships by using the `inherit` keyword in a class declaration.</span></span> <span data-ttu-id="b3e07-107">下列範例會顯示基本的語法形式。</span><span class="sxs-lookup"><span data-stu-id="b3e07-107">The basic syntactical form is shown in the following example.</span></span>

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

<span data-ttu-id="b3e07-108">一個類別最多隻能有一個直接基類。</span><span class="sxs-lookup"><span data-stu-id="b3e07-108">A class can have at most one direct base class.</span></span> <span data-ttu-id="b3e07-109">如果您沒有使用關鍵字來指定基類 `inherit` ，則類別會隱含地繼承自 `System.Object` 。</span><span class="sxs-lookup"><span data-stu-id="b3e07-109">If you do not specify a base class by using the `inherit` keyword, the class implicitly inherits from `System.Object`.</span></span>

## <a name="inherited-members"></a><span data-ttu-id="b3e07-110">繼承的成員</span><span class="sxs-lookup"><span data-stu-id="b3e07-110">Inherited Members</span></span>

<span data-ttu-id="b3e07-111">如果類別繼承自另一個類別，則衍生類別的使用者可以使用基類的方法和成員，如同它們是衍生類別的直接成員。</span><span class="sxs-lookup"><span data-stu-id="b3e07-111">If a class inherits from another class, the methods and members of the base class are available to users of the derived class as if they were direct members of the derived class.</span></span>

<span data-ttu-id="b3e07-112">任何 let 系結和函式參數都是類別私用的，因此無法從衍生類別存取。</span><span class="sxs-lookup"><span data-stu-id="b3e07-112">Any let bindings and constructor parameters are private to a class and, therefore, cannot be accessed from derived classes.</span></span>

<span data-ttu-id="b3e07-113">關鍵字 `base` 會在衍生類別中提供，並參考基類實例。</span><span class="sxs-lookup"><span data-stu-id="b3e07-113">The keyword `base` is available in derived classes and refers to the base class instance.</span></span> <span data-ttu-id="b3e07-114">它會像自我識別碼一樣使用。</span><span class="sxs-lookup"><span data-stu-id="b3e07-114">It is used like the self-identifier.</span></span>

## <a name="virtual-methods-and-overrides"></a><span data-ttu-id="b3e07-115">虛擬方法和覆寫</span><span class="sxs-lookup"><span data-stu-id="b3e07-115">Virtual Methods and Overrides</span></span>

<span data-ttu-id="b3e07-116">相較于其他 .NET 語言， (和屬性的虛擬方法) 在 F # 中的運作方式稍有不同。</span><span class="sxs-lookup"><span data-stu-id="b3e07-116">Virtual methods (and properties) work somewhat differently in F# as compared to other .NET languages.</span></span> <span data-ttu-id="b3e07-117">若要宣告新的虛擬成員，請使用 `abstract` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="b3e07-117">To declare a new virtual member, you use the `abstract` keyword.</span></span> <span data-ttu-id="b3e07-118">無論您是否提供該方法的預設執行，您都可以這麼做。</span><span class="sxs-lookup"><span data-stu-id="b3e07-118">You do this regardless of whether you provide a default implementation for that method.</span></span> <span data-ttu-id="b3e07-119">因此，基底類別中虛擬方法的完整定義會遵循此模式：</span><span class="sxs-lookup"><span data-stu-id="b3e07-119">Thus a complete definition of a virtual method in a base class follows this pattern:</span></span>

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="b3e07-120">在衍生類別中，此虛擬方法的覆寫會遵循此模式：</span><span class="sxs-lookup"><span data-stu-id="b3e07-120">And in a derived class, an override of this virtual method follows this pattern:</span></span>

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="b3e07-121">如果您省略基類中的預設實值，基類就會變成抽象類別。</span><span class="sxs-lookup"><span data-stu-id="b3e07-121">If you omit the default implementation in the base class, the base class becomes an abstract class.</span></span>

<span data-ttu-id="b3e07-122">下列程式碼範例說明如何在基類中宣告新的虛擬方法 `function1` ，以及如何在衍生類別中覆寫它。</span><span class="sxs-lookup"><span data-stu-id="b3e07-122">The following code example illustrates the declaration of a new virtual method `function1` in a base class and how to override it in a derived class.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a><span data-ttu-id="b3e07-123">建構函式和繼承</span><span class="sxs-lookup"><span data-stu-id="b3e07-123">Constructors and Inheritance</span></span>

<span data-ttu-id="b3e07-124">基類的函式必須在衍生類別中呼叫。</span><span class="sxs-lookup"><span data-stu-id="b3e07-124">The constructor for the base class must be called in the derived class.</span></span> <span data-ttu-id="b3e07-125">基類（base class）的引數會出現在子句的引數清單中 `inherit` 。</span><span class="sxs-lookup"><span data-stu-id="b3e07-125">The arguments for the base class constructor appear in the argument list in the `inherit` clause.</span></span> <span data-ttu-id="b3e07-126">使用的值必須取決於提供給衍生類別的引數。</span><span class="sxs-lookup"><span data-stu-id="b3e07-126">The values that are used must be determined from the arguments supplied to the derived class constructor.</span></span>

<span data-ttu-id="b3e07-127">下列程式碼顯示基類和衍生類別，其中衍生類別會在繼承子句中呼叫基類的函式：</span><span class="sxs-lookup"><span data-stu-id="b3e07-127">The following code shows a base class and a derived class, where the derived class calls the base class constructor in the inherit clause:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

<span data-ttu-id="b3e07-128">在多個函式的情況下，可以使用下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="b3e07-128">In the case of multiple constructors, the following code can be used.</span></span> <span data-ttu-id="b3e07-129">衍生類別的第一行是 `inherit` 子句，而這些欄位會顯示為使用關鍵字宣告的明確欄位 `val` 。</span><span class="sxs-lookup"><span data-stu-id="b3e07-129">The first line of the derived class constructors is the `inherit` clause, and the fields appear as explicit fields that are declared with the `val` keyword.</span></span> <span data-ttu-id="b3e07-130">如需詳細資訊，請參閱 [明確欄位： `val` 關鍵字](./members/explicit-fields-the-val-keyword.md)。</span><span class="sxs-lookup"><span data-stu-id="b3e07-130">For more information, see [Explicit Fields: The `val` Keyword](./members/explicit-fields-the-val-keyword.md).</span></span>

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

## <a name="alternatives-to-inheritance"></a><span data-ttu-id="b3e07-131">繼承的替代方案</span><span class="sxs-lookup"><span data-stu-id="b3e07-131">Alternatives to Inheritance</span></span>

<span data-ttu-id="b3e07-132">在需要稍微修改類型的情況下，請考慮使用物件運算式作為繼承的替代方法。</span><span class="sxs-lookup"><span data-stu-id="b3e07-132">In cases where a minor modification of a type is required, consider using an object expression as an alternative to inheritance.</span></span> <span data-ttu-id="b3e07-133">下列範例說明如何使用物件運算式做為建立新衍生型別的替代方法：</span><span class="sxs-lookup"><span data-stu-id="b3e07-133">The following example illustrates the use of an object expression as an alternative to creating a new derived type:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

<span data-ttu-id="b3e07-134">如需物件運算式的詳細資訊，請參閱 [物件運算式](object-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="b3e07-134">For more information about object expressions, see [Object Expressions](object-expressions.md).</span></span>

<span data-ttu-id="b3e07-135">當您建立物件階層時，請考慮使用差異聯集，而不是繼承。</span><span class="sxs-lookup"><span data-stu-id="b3e07-135">When you are creating object hierarchies, consider using a discriminated union instead of inheritance.</span></span> <span data-ttu-id="b3e07-136">差異聯集也可以針對共用通用整體類型的不同物件，建立各種不同的行為模型。</span><span class="sxs-lookup"><span data-stu-id="b3e07-136">Discriminated unions can also model varied behavior of different objects that share a common overall type.</span></span> <span data-ttu-id="b3e07-137">單一差異聯集通常可以免除一些不同的衍生類別需求。</span><span class="sxs-lookup"><span data-stu-id="b3e07-137">A single discriminated union can often eliminate the need for a number of derived classes that are minor variations of each other.</span></span> <span data-ttu-id="b3e07-138">如需差異聯集的詳細資訊，請參閱 [區分](discriminated-unions.md)聯集。</span><span class="sxs-lookup"><span data-stu-id="b3e07-138">For information about discriminated unions, see [Discriminated Unions](discriminated-unions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b3e07-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3e07-139">See also</span></span>

- [<span data-ttu-id="b3e07-140">物件運算式</span><span class="sxs-lookup"><span data-stu-id="b3e07-140">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="b3e07-141">F # 語言參考</span><span class="sxs-lookup"><span data-stu-id="b3e07-141">F# Language Reference</span></span>](index.md)
