---
title: 堆疊aoc運算式 - C# 引用
ms.date: 03/13/2020
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc expression [C#]
ms.openlocfilehash: 2e99ce8b1e44dfa040c1acac799a3a55b375bd91
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546597"
---
# <a name="stackalloc-expression-c-reference"></a><span data-ttu-id="e7415-102">堆疊aoc運算式（C# 引用）</span><span class="sxs-lookup"><span data-stu-id="e7415-102">stackalloc expression (C# reference)</span></span>

<span data-ttu-id="e7415-103">運算式`stackalloc`在堆疊上分配區塊。</span><span class="sxs-lookup"><span data-stu-id="e7415-103">A `stackalloc` expression allocates a block of memory on the stack.</span></span> <span data-ttu-id="e7415-104">在方法執行期間建立的堆疊配置的記憶體區塊，會在該方法傳回時自動被捨棄。</span><span class="sxs-lookup"><span data-stu-id="e7415-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="e7415-105">不能顯式釋放分配的`stackalloc`記憶體。</span><span class="sxs-lookup"><span data-stu-id="e7415-105">You cannot explicitly free the memory allocated with `stackalloc`.</span></span> <span data-ttu-id="e7415-106">堆疊分配的區塊不受[垃圾回收](../../../standard/garbage-collection/index.md)，也不必用[`fixed`語句](../keywords/fixed-statement.md)固定。</span><span class="sxs-lookup"><span data-stu-id="e7415-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with a [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="e7415-107">可以將`stackalloc`運算式的結果分配給以下類型之一的變數：</span><span class="sxs-lookup"><span data-stu-id="e7415-107">You can assign the result of a `stackalloc` expression to a variable of one of the following types:</span></span>

- <span data-ttu-id="e7415-108">從 C# 7.2 <xref:System.Span%601?displayProperty=nameWithType> <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>或 開始，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="e7415-108">Beginning with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](snippets/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="e7415-109">當您將堆疊配置的記憶體區塊指派至 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 變數時，您不需要使用 [unsafe](../keywords/unsafe.md) 內容。</span><span class="sxs-lookup"><span data-stu-id="e7415-109">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="e7415-110">當您處理那些類型時，您可以使用[條件式](conditional-operator.md)或指派運算式中的 `stackalloc` 運算式，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="e7415-110">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](snippets/StackallocOperator.cs#AsExpression)]

  <span data-ttu-id="e7415-111">從 C# 8.0 開始，只要`stackalloc`允許 或<xref:System.Span%601><xref:System.ReadOnlySpan%601>變數，都可以在其他運算式中使用運算式，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="e7415-111">Beginning with C# 8.0, you can use a `stackalloc` expression inside other expressions whenever a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable is allowed, as the following example shows:</span></span>

  [!code-csharp[stackalloc in nested expressions](snippets/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <span data-ttu-id="e7415-112">我們建議盡可能使用 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 類型來處理堆疊配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="e7415-112">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="e7415-113">[指標類型](../../programming-guide/unsafe-code-pointers/pointer-types.md)，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="e7415-113">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](snippets/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="e7415-114">如先前的範例所示，您在使用指標類型時必須使用 `unsafe` 內容。</span><span class="sxs-lookup"><span data-stu-id="e7415-114">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

  <span data-ttu-id="e7415-115">在指標類型中，只能在區域變數聲明中使用`stackalloc`運算式來初始化變數。</span><span class="sxs-lookup"><span data-stu-id="e7415-115">In the case of pointer types, you can use a `stackalloc` expression only in a local variable declaration to initialize the variable.</span></span>

<span data-ttu-id="e7415-116">堆疊上的可用記憶體量是有限的。</span><span class="sxs-lookup"><span data-stu-id="e7415-116">The amount of memory available on the stack is limited.</span></span> <span data-ttu-id="e7415-117">如果在堆疊上分配了過多的記憶體，則引發<xref:System.StackOverflowException>。</span><span class="sxs-lookup"><span data-stu-id="e7415-117">If you allocate too much memory on the stack, a <xref:System.StackOverflowException> is thrown.</span></span> <span data-ttu-id="e7415-118">為此，請遵循以下規則：</span><span class="sxs-lookup"><span data-stu-id="e7415-118">To avoid that, follow the rules below:</span></span>

- <span data-ttu-id="e7415-119">限制使用 分配的`stackalloc`記憶體量：</span><span class="sxs-lookup"><span data-stu-id="e7415-119">Limit the amount of memory you allocate with `stackalloc`:</span></span>

  [!code-csharp[limit stackalloc](snippets/StackallocOperator.cs#LimitStackalloc)]

  <span data-ttu-id="e7415-120">由於堆疊上的可用記憶體量取決於執行代碼的環境，因此在定義實際限制值時要保守。</span><span class="sxs-lookup"><span data-stu-id="e7415-120">Because the amount of memory available on the stack depends on the environment in which the code is executed, be conservative when you define the actual limit value.</span></span>

- <span data-ttu-id="e7415-121">避免使用`stackalloc`內部迴圈。</span><span class="sxs-lookup"><span data-stu-id="e7415-121">Avoid using `stackalloc` inside loops.</span></span> <span data-ttu-id="e7415-122">將區塊分配到迴圈之外，並在迴圈中重用它。</span><span class="sxs-lookup"><span data-stu-id="e7415-122">Allocate the memory block outside a loop and reuse it inside the loop.</span></span>

<span data-ttu-id="e7415-123">新配置記憶體的內容尚未被定義。</span><span class="sxs-lookup"><span data-stu-id="e7415-123">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="e7415-124">應在使用前初始化它。</span><span class="sxs-lookup"><span data-stu-id="e7415-124">You should initialize it before the use.</span></span> <span data-ttu-id="e7415-125">例如，可以使用將<xref:System.Span%601.Clear%2A?displayProperty=nameWithType>所有項都設置為 類型的`T`預設值的方法。</span><span class="sxs-lookup"><span data-stu-id="e7415-125">For example, you can use the <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> method that sets all the items to the default value of type `T`.</span></span>

<span data-ttu-id="e7415-126">從 C# 7.3 開始，可以使用陣列初始化器語法來定義新分配的記憶體的內容。</span><span class="sxs-lookup"><span data-stu-id="e7415-126">Beginning with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="e7415-127">下列範例示範進行該操作的數種方法：</span><span class="sxs-lookup"><span data-stu-id="e7415-127">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](snippets/StackallocOperator.cs#StackallocInit)]

<span data-ttu-id="e7415-128">在運算式`stackalloc T[E]`中`T`，必須是[非託管類型](../builtin-types/unmanaged-types.md)，並且必須`E`計算為非負[int](../builtin-types/integral-numeric-types.md)值。</span><span class="sxs-lookup"><span data-stu-id="e7415-128">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must evaluate to a non-negative [int](../builtin-types/integral-numeric-types.md) value.</span></span>

## <a name="security"></a><span data-ttu-id="e7415-129">安全性</span><span class="sxs-lookup"><span data-stu-id="e7415-129">Security</span></span>

<span data-ttu-id="e7415-130">使用 `stackalloc` 會自動啟用 Common Language Runtime (CLR) 中的緩衝區滿溢偵測功能。</span><span class="sxs-lookup"><span data-stu-id="e7415-130">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="e7415-131">如果偵測到緩衝區滿溢，會盡快終止處理序，將執行惡意程式碼的機會降到最低。</span><span class="sxs-lookup"><span data-stu-id="e7415-131">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e7415-132">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="e7415-132">C# language specification</span></span>

<span data-ttu-id="e7415-133">有關詳細資訊，請參閱[C# 語言規範](~/_csharplang/spec/introduction.md)的[堆疊分配](~/_csharplang/spec/unsafe-code.md#stack-allocation)部分和[嵌套上下文中的`stackalloc`"許可](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md)"功能建議說明。</span><span class="sxs-lookup"><span data-stu-id="e7415-133">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the [Permit `stackalloc` in nested contexts](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) feature proposal note.</span></span>

## <a name="see-also"></a><span data-ttu-id="e7415-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7415-134">See also</span></span>

- [<span data-ttu-id="e7415-135">C# 參考</span><span class="sxs-lookup"><span data-stu-id="e7415-135">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e7415-136">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="e7415-136">C# operators</span></span>](index.md)
- [<span data-ttu-id="e7415-137">指標相關運算子</span><span class="sxs-lookup"><span data-stu-id="e7415-137">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="e7415-138">指標類型</span><span class="sxs-lookup"><span data-stu-id="e7415-138">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="e7415-139">記憶體與延伸相關類型</span><span class="sxs-lookup"><span data-stu-id="e7415-139">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="e7415-140">堆疊的做和不做</span><span class="sxs-lookup"><span data-stu-id="e7415-140">Dos and Don'ts of stackalloc</span></span>](https://vcsjones.dev/2020/02/24/stackalloc/)
