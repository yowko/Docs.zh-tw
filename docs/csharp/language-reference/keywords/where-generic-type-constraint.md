---
title: where (泛型類型條件約束) - C# 參考
ms.custom: seodec18
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 3982c97bc56b42237700343b2572d1bba930bbbd
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422770"
---
# <a name="where-generic-type-constraint-c-reference"></a><span data-ttu-id="dc3a5-102">where (泛型類型條件約束) (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="dc3a5-102">where (generic type constraint) (C# Reference)</span></span>

<span data-ttu-id="dc3a5-103">泛型定義中的 `where` 子句指定型別上的條件約束，以用來作為泛型型別、方法、委派或本機函式中型別參數的引數。</span><span class="sxs-lookup"><span data-stu-id="dc3a5-103">The `where` clause in a generic definition specifies constraints on the types that are used as arguments for type parameters in a generic type, method, delegate, or local function.</span></span> <span data-ttu-id="dc3a5-104">條件約束可以指定介面、基底類別或需要作為參考、值或非受控型別的泛型型別。</span><span class="sxs-lookup"><span data-stu-id="dc3a5-104">Constraints can specify interfaces, base classes, or require a generic type to be a reference, value or unmanaged type.</span></span> <span data-ttu-id="dc3a5-105">它們會宣告型別引數必須擁有的功能。</span><span class="sxs-lookup"><span data-stu-id="dc3a5-105">They declare capabilities that the type argument must possess.</span></span>

<span data-ttu-id="dc3a5-106">例如，您可以宣告泛型類別 `MyGenericClass`，讓型別參數 `T` 實作 <xref:System.IComparable%601> 介面：</span><span class="sxs-lookup"><span data-stu-id="dc3a5-106">For example, you can declare a generic class, `MyGenericClass`, such that the type parameter `T` implements the <xref:System.IComparable%601> interface:</span></span>

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> <span data-ttu-id="dc3a5-107">如需查詢運算式中 where 子句的詳細資訊，請參閱 [where 子句](where-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="dc3a5-107">For more information on the where clause in a query expression, see [where clause](where-clause.md).</span></span>

<span data-ttu-id="dc3a5-108">`where` 子句也可以包含基底類別條件約束。</span><span class="sxs-lookup"><span data-stu-id="dc3a5-108">The `where` clause can also include a base class constraint.</span></span> <span data-ttu-id="dc3a5-109">基底類別條件約束指出要用作該泛型型別之型別引數的型別具有作為基底類別的指定類別 (或是該基底類別)，以用作該泛型型別的型別引數。</span><span class="sxs-lookup"><span data-stu-id="dc3a5-109">The base class constraint states that a type to be used as a type argument for that generic type has the specified class as a base class (or is that base class) to be used as a type argument for that generic type.</span></span> <span data-ttu-id="dc3a5-110">如果使用基底類別條件約束，則它必須出現在該型別參數的任何其他條件約束之前。</span><span class="sxs-lookup"><span data-stu-id="dc3a5-110">If the base class constraint is used, it must appear before any other constraints on that type parameter.</span></span> <span data-ttu-id="dc3a5-111">某些型別不允許作為基底類別條件約束：<xref:System.Object>、<xref:System.Array> 和 <xref:System.ValueType>。</span><span class="sxs-lookup"><span data-stu-id="dc3a5-111">Some types are disallowed as a base class constraint: <xref:System.Object>, <xref:System.Array>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="dc3a5-112">在 C# 7.3 之前，也不允許 <xref:System.Enum>、<xref:System.Delegate> 和 <xref:System.MulticastDelegate> 作為基底類別條件約束。</span><span class="sxs-lookup"><span data-stu-id="dc3a5-112">Prior to C# 7.3, <xref:System.Enum>, <xref:System.Delegate>, and <xref:System.MulticastDelegate> were also disallowed as base class constraints.</span></span> <span data-ttu-id="dc3a5-113">下列範例會顯示現在可以指定為基底類別的型別：</span><span class="sxs-lookup"><span data-stu-id="dc3a5-113">The following example shows the types that can now be specified as a base class:</span></span>

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

<span data-ttu-id="dc3a5-114">`where` 子句可以指定型別是 `class` 或 `struct`。</span><span class="sxs-lookup"><span data-stu-id="dc3a5-114">The `where` clause can specify that the type is a `class` or a `struct`.</span></span> <span data-ttu-id="dc3a5-115">`struct` 條件約束不需要指定 `System.ValueType` 的基底類別條件約束。</span><span class="sxs-lookup"><span data-stu-id="dc3a5-115">The `struct` constraint removes the need to specify a base class constraint of `System.ValueType`.</span></span> <span data-ttu-id="dc3a5-116">`System.ValueType` 型別不能用作基底類別條件約束。</span><span class="sxs-lookup"><span data-stu-id="dc3a5-116">The `System.ValueType` type may not be used as a base class constraint.</span></span> <span data-ttu-id="dc3a5-117">下列範例顯示 `class` 和 `struct` 條件約束：</span><span class="sxs-lookup"><span data-stu-id="dc3a5-117">The following example shows both the `class` and `struct` constraints:</span></span>

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

<span data-ttu-id="dc3a5-118">`where` 子句也可能包含 `unmanaged` 條件約束。</span><span class="sxs-lookup"><span data-stu-id="dc3a5-118">The `where` clause may also include an `unmanaged` constraint.</span></span> <span data-ttu-id="dc3a5-119">`unmanaged` 條件約束會將型別參數限制為稱為「非受控型別」  的型別。</span><span class="sxs-lookup"><span data-stu-id="dc3a5-119">The `unmanaged` constraint limits the type parameter to types known as **unmanaged types**.</span></span> <span data-ttu-id="dc3a5-120">「非受控型別」  是非參考型別的型別，而且未包含任何巢狀層級的參考型別欄位。</span><span class="sxs-lookup"><span data-stu-id="dc3a5-120">An **unmanaged type** is a type that isn't a reference type and doesn't contain reference type fields at any level of nesting.</span></span> <span data-ttu-id="dc3a5-121">`unmanaged` 條件約束可讓您更輕鬆地使用 C# 撰寫低階 Interop 程式碼。</span><span class="sxs-lookup"><span data-stu-id="dc3a5-121">The `unmanaged` constraint makes it easier to write low-level interop code in C#.</span></span> <span data-ttu-id="dc3a5-122">此條件約束會啟用所有非受控型別的可重複使用常式。</span><span class="sxs-lookup"><span data-stu-id="dc3a5-122">This constraint enables reusable routines across all unmanaged types.</span></span> <span data-ttu-id="dc3a5-123">`unmanaged` 條件約束不能與 `class` 或 `struct` 條件約束合併使用。</span><span class="sxs-lookup"><span data-stu-id="dc3a5-123">The `unmanaged` constraint can't be combined with the `class` or `struct` constraint.</span></span> <span data-ttu-id="dc3a5-124">`unmanaged` 條件約束會強制型別必須是 `struct`：</span><span class="sxs-lookup"><span data-stu-id="dc3a5-124">The `unmanaged` constraint enforces that the type must be a `struct`:</span></span>

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

<span data-ttu-id="dc3a5-125">`where` 子句也可能包含建構函式條件約束 `new()`。</span><span class="sxs-lookup"><span data-stu-id="dc3a5-125">The `where` clause may also include a constructor constraint, `new()`.</span></span> <span data-ttu-id="dc3a5-126">該條件約束可讓您使用 `new` 運算子建立型別參數執行個體。</span><span class="sxs-lookup"><span data-stu-id="dc3a5-126">That constraint makes it possible to create an instance of a type parameter using the `new` operator.</span></span> <span data-ttu-id="dc3a5-127">[new() 條件約束](new-constraint.md)可讓編譯器知道提供的任何類型引數都必須有可存取的無參數或預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="dc3a5-127">The [new() Constraint](new-constraint.md) lets the compiler know that any type argument supplied must have an accessible parameterless--or default-- constructor.</span></span> <span data-ttu-id="dc3a5-128">例如：</span><span class="sxs-lookup"><span data-stu-id="dc3a5-128">For example:</span></span>

[!code-csharp[using the new constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

<span data-ttu-id="dc3a5-129">`new()` 條件約束會出現在 `where` 子句中的最後。</span><span class="sxs-lookup"><span data-stu-id="dc3a5-129">The `new()` constraint appears last in the `where` clause.</span></span> <span data-ttu-id="dc3a5-130">`new()` 條件約束不能與 `struct` 或 `unmanaged` 條件約束合併使用。</span><span class="sxs-lookup"><span data-stu-id="dc3a5-130">The `new()` constraint can't be combined with the `struct` or `unmanaged` constraints.</span></span> <span data-ttu-id="dc3a5-131">所有滿足這些條件約束的型別都必須具有可存取的無參數建構函式，讓 `new()` 條件約束成為備援。</span><span class="sxs-lookup"><span data-stu-id="dc3a5-131">All types satisfying those constraints must have an accessible parameterless constructor, making the `new()` constraint redundant.</span></span>

<span data-ttu-id="dc3a5-132">若有多個類型參數，請對每個類型參數使用一個 `where` 子句，例如：</span><span class="sxs-lookup"><span data-stu-id="dc3a5-132">With multiple type parameters, use one `where` clause for each type parameter, for example:</span></span>

[!code-csharp[using multiple where constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

<span data-ttu-id="dc3a5-133">您也可以將條件約束附加至泛型方法的型別參數，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="dc3a5-133">You can also attach constraints to type parameters of generic methods, as shown in the following example:</span></span>

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

<span data-ttu-id="dc3a5-134">請注意，描述委派類型參數條件約束的語法與方法的語法相同︰</span><span class="sxs-lookup"><span data-stu-id="dc3a5-134">Notice that the syntax to describe type parameter constraints on delegates is the same as that of methods:</span></span>

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

<span data-ttu-id="dc3a5-135">如需泛型委派的資訊，請參閱[泛型委派](../../../csharp/programming-guide/generics/generic-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="dc3a5-135">For information on generic delegates, see [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>

<span data-ttu-id="dc3a5-136">如需條件約束語法和用法的詳細資料，請參閱[類型參數的條件約束](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="dc3a5-136">For details on the syntax and use of constraints, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="dc3a5-137">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="dc3a5-137">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="dc3a5-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc3a5-138">See also</span></span>

- [<span data-ttu-id="dc3a5-139">C# 參考</span><span class="sxs-lookup"><span data-stu-id="dc3a5-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="dc3a5-140">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="dc3a5-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="dc3a5-141">泛型簡介</span><span class="sxs-lookup"><span data-stu-id="dc3a5-141">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="dc3a5-142">new 條件約束</span><span class="sxs-lookup"><span data-stu-id="dc3a5-142">new Constraint</span></span>](../../../csharp/language-reference/keywords/new-constraint.md)
- [<span data-ttu-id="dc3a5-143">型別參數的條件約束</span><span class="sxs-lookup"><span data-stu-id="dc3a5-143">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
