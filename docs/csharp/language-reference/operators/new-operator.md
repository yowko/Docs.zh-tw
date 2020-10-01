---
description: new 運算子 - C# 參考
title: new 運算子 - C# 參考
ms.date: 10/02/2020
f1_keywords:
- new_CSharpKeyword
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 3125f3d2c694dcfc5682ee482f3f76072ac3726d
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609378"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="515b3-103">new 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="515b3-103">new operator (C# reference)</span></span>

<span data-ttu-id="515b3-104">`new` 運算子會建立型別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="515b3-104">The `new` operator creates a new instance of a type.</span></span>

<span data-ttu-id="515b3-105">您也可以使用 `new` 關鍵字作為[成員宣告修飾詞](../keywords/new-modifier.md)或[泛型型別條件約束](../keywords/new-constraint.md)。</span><span class="sxs-lookup"><span data-stu-id="515b3-105">You can also use the `new` keyword as a [member declaration modifier](../keywords/new-modifier.md) or a [generic type constraint](../keywords/new-constraint.md).</span></span>

## <a name="constructor-invocation"></a><span data-ttu-id="515b3-106">建構函式引動過程</span><span class="sxs-lookup"><span data-stu-id="515b3-106">Constructor invocation</span></span>

<span data-ttu-id="515b3-107">若要建立型別的新執行個體，您通常會使用 `new` 運算子叫用該型別的其中一個[建構函式](../../programming-guide/classes-and-structs/constructors.md)：</span><span class="sxs-lookup"><span data-stu-id="515b3-107">To create a new instance of a type, you typically invoke one of the [constructors](../../programming-guide/classes-and-structs/constructors.md) of that type using the `new` operator:</span></span>

[!code-csharp-interactive[invoke constructor](snippets/shared/NewOperator.cs#Constructor)]

<span data-ttu-id="515b3-108">您可以搭配 `new` 運算子使用[物件或集合初始設定式](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)，來在單一陳述式中具現化和初始化物件，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="515b3-108">You can use an [object or collection initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) with the `new` operator to instantiate and initialize an object in one statement, as the following example shows:</span></span>

[!code-csharp-interactive[constructor with initializer](snippets/shared/NewOperator.cs#ConstructorWithInitializer)]

<span data-ttu-id="515b3-109">從 c # 9.0 開始，函式調用運算式是目標型別。</span><span class="sxs-lookup"><span data-stu-id="515b3-109">Beginning with C# 9.0, constructor invocation expressions are target-typed.</span></span> <span data-ttu-id="515b3-110">也就是說，如果已知運算式的目標型別，您可以省略型別名稱，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="515b3-110">That is, if a target type of an expression is known, you can omit a type name, as the following example shows:</span></span>

:::code language="csharp" source="snippets/shared/NewOperator.cs" id="SnippetTargetTyped":::

<span data-ttu-id="515b3-111">如先前的範例所示，您一律使用目標型別運算式中的括弧 `new` 。</span><span class="sxs-lookup"><span data-stu-id="515b3-111">As the preceding example shows, you always use parentheses in a target-typed `new` expression.</span></span>

<span data-ttu-id="515b3-112">如果運算式的目標型別 `new` 未知 (例如，當您使用 [`var`](../keywords/var.md) 關鍵字) 時，必須指定型別名稱。</span><span class="sxs-lookup"><span data-stu-id="515b3-112">If a target type of a `new` expression is unknown (for example, when you use the [`var`](../keywords/var.md) keyword), you must specify a type name.</span></span>

## <a name="array-creation"></a><span data-ttu-id="515b3-113">建立陣列</span><span class="sxs-lookup"><span data-stu-id="515b3-113">Array creation</span></span>

<span data-ttu-id="515b3-114">您也可以使用 `new` 運算子建立陣列執行個體，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="515b3-114">You also use the `new` operator to create an array instance, as the following example shows:</span></span>

[!code-csharp-interactive[create array](snippets/shared/NewOperator.cs#Array)]

<span data-ttu-id="515b3-115">在單一陳述式中使用陣列初始化語法建立陣列執行個體，並使用項目。</span><span class="sxs-lookup"><span data-stu-id="515b3-115">Use array initialization syntax to create an array instance and populate it with elements in one statement.</span></span> <span data-ttu-id="515b3-116">下列範例會示範執行該操作的各種方式：</span><span class="sxs-lookup"><span data-stu-id="515b3-116">The following example shows various ways how you can do that:</span></span>

[!code-csharp-interactive[initialize array](snippets/shared/NewOperator.cs#ArrayInitialization)]

<span data-ttu-id="515b3-117">如需陣列的詳細資訊，請參閱[陣列](../../programming-guide/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="515b3-117">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

## <a name="instantiation-of-anonymous-types"></a><span data-ttu-id="515b3-118">匿名型別的具現化</span><span class="sxs-lookup"><span data-stu-id="515b3-118">Instantiation of anonymous types</span></span>

<span data-ttu-id="515b3-119">若要建立[匿名型別](../../programming-guide/classes-and-structs/anonymous-types.md)的執行個體，請使用 `new` 運算子及物件初始設定式語法：</span><span class="sxs-lookup"><span data-stu-id="515b3-119">To create an instance of an [anonymous type](../../programming-guide/classes-and-structs/anonymous-types.md), use the `new` operator and object initializer syntax:</span></span>

[!code-csharp-interactive[anonymous type](snippets/shared/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a><span data-ttu-id="515b3-120">型別執行個體的解構</span><span class="sxs-lookup"><span data-stu-id="515b3-120">Destruction of type instances</span></span>

<span data-ttu-id="515b3-121">您不需要終結先前建立的型別執行個體。</span><span class="sxs-lookup"><span data-stu-id="515b3-121">You don't have to destroy earlier created type instances.</span></span> <span data-ttu-id="515b3-122">參考和實值型別的執行個體都會自動終結。</span><span class="sxs-lookup"><span data-stu-id="515b3-122">Instances of both reference and value types are destroyed automatically.</span></span> <span data-ttu-id="515b3-123">實值型別的執行個體會在內容包含它們時立即終結。</span><span class="sxs-lookup"><span data-stu-id="515b3-123">Instances of value types are destroyed as soon as the context that contains them is destroyed.</span></span> <span data-ttu-id="515b3-124">在移除參考型別的最後一個參考之後，垃圾收集行程會將這些實例被 [垃圾收集](../../../standard/garbage-collection/index.md) 行程終結。</span><span class="sxs-lookup"><span data-stu-id="515b3-124">Instances of reference types are destroyed by the [garbage collector](../../../standard/garbage-collection/index.md) at some unspecified time after the last reference to them is removed.</span></span>

<span data-ttu-id="515b3-125">針對包含非受控資源的類型實例（例如，檔案控制代碼），建議採用具決定性的清除，以確保其所包含的資源會儘快釋出。</span><span class="sxs-lookup"><span data-stu-id="515b3-125">For type instances that contain unmanaged resources, for example, a file handle, it's recommended to employ deterministic clean-up to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="515b3-126">如需詳細資訊，請參閱 <xref:System.IDisposable?displayProperty=nameWithType> API 參考和 [using 陳述式](../keywords/using-statement.md)一文。</span><span class="sxs-lookup"><span data-stu-id="515b3-126">For more information, see the <xref:System.IDisposable?displayProperty=nameWithType> API reference and the [using statement](../keywords/using-statement.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="515b3-127">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="515b3-127">Operator overloadability</span></span>

<span data-ttu-id="515b3-128">使用者定義型別不可多載 `new` 運算子。</span><span class="sxs-lookup"><span data-stu-id="515b3-128">A user-defined type cannot overload the `new` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="515b3-129">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="515b3-129">C# language specification</span></span>

<span data-ttu-id="515b3-130">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的 [new 運算子](~/_csharplang/spec/expressions.md#the-new-operator)一節。</span><span class="sxs-lookup"><span data-stu-id="515b3-130">For more information, see [The new operator](~/_csharplang/spec/expressions.md#the-new-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="515b3-131">如需目標型別運算式的詳細資訊 `new` ，請參閱 [功能提案注意事項](~/_csharplang/proposals/csharp-9.0/target-typed-new.md)。</span><span class="sxs-lookup"><span data-stu-id="515b3-131">For more information about a target-typed `new` expression, see the [feature proposal note](~/_csharplang/proposals/csharp-9.0/target-typed-new.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="515b3-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="515b3-132">See also</span></span>

- [<span data-ttu-id="515b3-133">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="515b3-133">C# reference</span></span>](../index.md)
- [<span data-ttu-id="515b3-134">C# 運算子與運算式</span><span class="sxs-lookup"><span data-stu-id="515b3-134">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="515b3-135">物件和集合初始化運算式</span><span class="sxs-lookup"><span data-stu-id="515b3-135">Object and collection initializers</span></span>](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
