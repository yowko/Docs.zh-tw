---
title: new 運算子 - C# 參考
ms.custom: seodec18
ms.date: 06/25/2019
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 3d64c4805abe38c80301748ffa6b35fc87563b60
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2019
ms.locfileid: "67403966"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="12abf-102">new 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="12abf-102">new operator (C# reference)</span></span>

<span data-ttu-id="12abf-103">`new` 運算子會建立型別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="12abf-103">The `new` operator creates a new instance of a type.</span></span>

<span data-ttu-id="12abf-104">您也可以使用 `new` 關鍵字作為[成員宣告修飾詞](../keywords/new-modifier.md)或[泛型型別條件約束](../keywords/new-constraint.md)。</span><span class="sxs-lookup"><span data-stu-id="12abf-104">You can also use the `new` keyword as a [member declaration modifier](../keywords/new-modifier.md) or a [generic type constraint](../keywords/new-constraint.md).</span></span>

## <a name="constructor-invocation"></a><span data-ttu-id="12abf-105">建構函式引動過程</span><span class="sxs-lookup"><span data-stu-id="12abf-105">Constructor invocation</span></span>

<span data-ttu-id="12abf-106">若要建立型別的新執行個體，您通常會使用 `new` 運算子叫用該型別的其中一個[建構函式](../../programming-guide/classes-and-structs/constructors.md)：</span><span class="sxs-lookup"><span data-stu-id="12abf-106">To create a new instance of a type, you typically invoke one of the [constructors](../../programming-guide/classes-and-structs/constructors.md) of that type using the `new` operator:</span></span>

[!code-csharp-interactive[invoke constructor](~/samples/csharp/language-reference/operators/NewOperator.cs#Constructor)]

<span data-ttu-id="12abf-107">您可以搭配 `new` 運算子使用[物件或集合初始設定式](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)，來在單一陳述式中具現化和初始化物件，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="12abf-107">You can use an [object or collection initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) with the `new` operator to instantiate and initialize an object in one statement, as the following example shows:</span></span>

[!code-csharp-interactive[constructor with initializer](~/samples/csharp/language-reference/operators/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a><span data-ttu-id="12abf-108">建立陣列</span><span class="sxs-lookup"><span data-stu-id="12abf-108">Array creation</span></span>

<span data-ttu-id="12abf-109">您也可以使用 `new` 運算子建立陣列執行個體，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="12abf-109">You also use the `new` operator to create an array instance, as the following example shows:</span></span>

[!code-csharp-interactive[create array](~/samples/csharp/language-reference/operators/NewOperator.cs#Array)]

<span data-ttu-id="12abf-110">在單一陳述式中使用陣列初始化語法建立陣列執行個體，並使用項目。</span><span class="sxs-lookup"><span data-stu-id="12abf-110">Use array initialization syntax to create an array instance and populate it with elements in one statement.</span></span> <span data-ttu-id="12abf-111">下列範例會示範執行該操作的各種方式：</span><span class="sxs-lookup"><span data-stu-id="12abf-111">The following example shows various ways how you can do that:</span></span>

[!code-csharp-interactive[initialize array](~/samples/csharp/language-reference/operators/NewOperator.cs#ArrayInitialization)]

<span data-ttu-id="12abf-112">如需陣列的詳細資訊，請參閱[陣列](../../programming-guide/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="12abf-112">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

## <a name="instantiation-of-anonymous-types"></a><span data-ttu-id="12abf-113">匿名型別的具現化</span><span class="sxs-lookup"><span data-stu-id="12abf-113">Instantiation of anonymous types</span></span>

<span data-ttu-id="12abf-114">若要建立[匿名型別](../../programming-guide/classes-and-structs/anonymous-types.md)的執行個體，請使用 `new` 運算子及物件初始設定式語法：</span><span class="sxs-lookup"><span data-stu-id="12abf-114">To create an instance of an [anonymous type](../../programming-guide/classes-and-structs/anonymous-types.md), use the `new` operator and object initializer syntax:</span></span>

[!code-csharp-interactive[anonymous type](~/samples/csharp/language-reference/operators/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a><span data-ttu-id="12abf-115">型別執行個體的解構</span><span class="sxs-lookup"><span data-stu-id="12abf-115">Destruction of type instances</span></span>

<span data-ttu-id="12abf-116">您不需要終結先前建立的型別執行個體。</span><span class="sxs-lookup"><span data-stu-id="12abf-116">You don't have to destroy earlier created type instances.</span></span> <span data-ttu-id="12abf-117">參考和實值型別的執行個體都會自動終結。</span><span class="sxs-lookup"><span data-stu-id="12abf-117">Instances of both reference and value types are destroyed automatically.</span></span> <span data-ttu-id="12abf-118">實值型別的執行個體會在內容包含它們時立即終結。</span><span class="sxs-lookup"><span data-stu-id="12abf-118">Instances of value types are destroyed as soon as the context that contains them is destroyed.</span></span> <span data-ttu-id="12abf-119">參考型別的執行個體則會由[記憶體回收行程](../../../standard/garbage-collection/index.md)在移除執行個體的最後一個參考後，於未指定的時間終結。</span><span class="sxs-lookup"><span data-stu-id="12abf-119">Instances of reference types are destroyed by the [garbage collector](../../../standard/garbage-collection/index.md) at unspecified time after the last reference to them is removed.</span></span>

<span data-ttu-id="12abf-120">針對包含非受控資源的型別 (例如檔案控制代碼)，建議採用具決定性清理以確保其包含的資源會盡快釋出。</span><span class="sxs-lookup"><span data-stu-id="12abf-120">For types that contain unmanaged resources, for example, a file handle, it's recommended to employ deterministic clean-up to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="12abf-121">如需詳細資訊，請參閱 <xref:System.IDisposable?displayProperty=nameWithType> API 參考和 [using 陳述式](../keywords/using-statement.md)一文。</span><span class="sxs-lookup"><span data-stu-id="12abf-121">For more information, see the <xref:System.IDisposable?displayProperty=nameWithType> API reference and the [using statement](../keywords/using-statement.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="12abf-122">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="12abf-122">Operator overloadability</span></span>

<span data-ttu-id="12abf-123">使用者定義型別不可多載 `new` 運算子。</span><span class="sxs-lookup"><span data-stu-id="12abf-123">A user-defined type cannot overload the `new` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="12abf-124">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="12abf-124">C# language specification</span></span>

<span data-ttu-id="12abf-125">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的 [new 運算子](~/_csharplang/spec/expressions.md#the-new-operator)一節。</span><span class="sxs-lookup"><span data-stu-id="12abf-125">For more information, see [The new operator](~/_csharplang/spec/expressions.md#the-new-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="12abf-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12abf-126">See also</span></span>

- [<span data-ttu-id="12abf-127">C# 參考</span><span class="sxs-lookup"><span data-stu-id="12abf-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="12abf-128">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="12abf-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="12abf-129">物件和集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="12abf-129">Object and collection initializers</span></span>](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
