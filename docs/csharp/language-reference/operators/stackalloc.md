---
description: 'stackalloc 運算式-c # 參考'
title: 'stackalloc 運算式-c # 參考'
ms.date: 03/13/2020
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc expression [C#]
ms.openlocfilehash: 72d91cf9aa67957ed8e1cad5b2c4a1f3b6382c1f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136846"
---
# <a name="stackalloc-expression-c-reference"></a><span data-ttu-id="fce73-103">stackalloc 運算式 (c # 參考) </span><span class="sxs-lookup"><span data-stu-id="fce73-103">stackalloc expression (C# reference)</span></span>

<span data-ttu-id="fce73-104">運算式會配置 `stackalloc` 堆疊上的記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="fce73-104">A `stackalloc` expression allocates a block of memory on the stack.</span></span> <span data-ttu-id="fce73-105">在方法執行期間建立的堆疊配置的記憶體區塊，會在該方法傳回時自動被捨棄。</span><span class="sxs-lookup"><span data-stu-id="fce73-105">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="fce73-106">您無法明確釋放配置給的記憶體 `stackalloc` 。</span><span class="sxs-lookup"><span data-stu-id="fce73-106">You cannot explicitly free the memory allocated with `stackalloc`.</span></span> <span data-ttu-id="fce73-107">堆疊配置的記憶體區塊不受[垃圾收集](../../../standard/garbage-collection/index.md)的制約，也不需要使用[ `fixed` 語句](../keywords/fixed-statement.md)釘選。</span><span class="sxs-lookup"><span data-stu-id="fce73-107">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with a [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="fce73-108">您可以將運算式的結果指派 `stackalloc` 給下列其中一種類型的變數：</span><span class="sxs-lookup"><span data-stu-id="fce73-108">You can assign the result of a `stackalloc` expression to a variable of one of the following types:</span></span>

- <span data-ttu-id="fce73-109">從 c # 7.2 開始， <xref:System.Span%601?displayProperty=nameWithType> 或 <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="fce73-109">Beginning with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](snippets/shared/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="fce73-110">當您將堆疊配置的記憶體區塊指派至 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 變數時，您不需要使用 [unsafe](../keywords/unsafe.md) 內容。</span><span class="sxs-lookup"><span data-stu-id="fce73-110">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="fce73-111">當您處理那些類型時，您可以使用[條件式](conditional-operator.md)或指派運算式中的 `stackalloc` 運算式，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="fce73-111">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](snippets/shared/StackallocOperator.cs#AsExpression)]

  <span data-ttu-id="fce73-112">從 c # 8.0 開始， `stackalloc` 只要允許或變數，您就可以在其他運算式內使用運算式 <xref:System.Span%601> <xref:System.ReadOnlySpan%601> ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="fce73-112">Beginning with C# 8.0, you can use a `stackalloc` expression inside other expressions whenever a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable is allowed, as the following example shows:</span></span>

  [!code-csharp[stackalloc in nested expressions](snippets/shared/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <span data-ttu-id="fce73-113">我們建議盡可能使用 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 類型來處理堆疊配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="fce73-113">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="fce73-114">[指標類型](../../programming-guide/unsafe-code-pointers/pointer-types.md)，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="fce73-114">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](snippets/shared/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="fce73-115">如先前的範例所示，您在使用指標類型時必須使用 `unsafe` 內容。</span><span class="sxs-lookup"><span data-stu-id="fce73-115">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

  <span data-ttu-id="fce73-116">在指標類型的案例中，您只能 `stackalloc` 在本機變數宣告中使用運算式來初始化變數。</span><span class="sxs-lookup"><span data-stu-id="fce73-116">In the case of pointer types, you can use a `stackalloc` expression only in a local variable declaration to initialize the variable.</span></span>

<span data-ttu-id="fce73-117">堆疊上的可用記憶體數量有限。</span><span class="sxs-lookup"><span data-stu-id="fce73-117">The amount of memory available on the stack is limited.</span></span> <span data-ttu-id="fce73-118">如果您在堆疊上配置過多的記憶體， <xref:System.StackOverflowException> 就會擲回。</span><span class="sxs-lookup"><span data-stu-id="fce73-118">If you allocate too much memory on the stack, a <xref:System.StackOverflowException> is thrown.</span></span> <span data-ttu-id="fce73-119">若要避免這種情況，請遵循下列規則：</span><span class="sxs-lookup"><span data-stu-id="fce73-119">To avoid that, follow the rules below:</span></span>

- <span data-ttu-id="fce73-120">限制您配置的記憶體數量 `stackalloc` ：</span><span class="sxs-lookup"><span data-stu-id="fce73-120">Limit the amount of memory you allocate with `stackalloc`:</span></span>

  [!code-csharp[limit stackalloc](snippets/shared/StackallocOperator.cs#LimitStackalloc)]

  <span data-ttu-id="fce73-121">由於堆疊上可用的記憶體數量取決於執行程式碼的環境，因此當您定義實際的限制值時，請務必保守。</span><span class="sxs-lookup"><span data-stu-id="fce73-121">Because the amount of memory available on the stack depends on the environment in which the code is executed, be conservative when you define the actual limit value.</span></span>

- <span data-ttu-id="fce73-122">避免 `stackalloc` 在迴圈中使用。</span><span class="sxs-lookup"><span data-stu-id="fce73-122">Avoid using `stackalloc` inside loops.</span></span> <span data-ttu-id="fce73-123">在迴圈之外配置記憶體區塊，並在迴圈內重複使用它。</span><span class="sxs-lookup"><span data-stu-id="fce73-123">Allocate the memory block outside a loop and reuse it inside the loop.</span></span>

<span data-ttu-id="fce73-124">新配置記憶體的內容尚未被定義。</span><span class="sxs-lookup"><span data-stu-id="fce73-124">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="fce73-125">您應該在使用之前將它初始化。</span><span class="sxs-lookup"><span data-stu-id="fce73-125">You should initialize it before the use.</span></span> <span data-ttu-id="fce73-126">例如，您可以使用 <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> 方法，將所有專案設定為型別的預設值 `T` 。</span><span class="sxs-lookup"><span data-stu-id="fce73-126">For example, you can use the <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> method that sets all the items to the default value of type `T`.</span></span>

<span data-ttu-id="fce73-127">從 c # 7.3 開始，您可以使用陣列初始化運算式語法來定義新配置記憶體的內容。</span><span class="sxs-lookup"><span data-stu-id="fce73-127">Beginning with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="fce73-128">下列範例示範進行該操作的數種方法：</span><span class="sxs-lookup"><span data-stu-id="fce73-128">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](snippets/shared/StackallocOperator.cs#StackallocInit)]

<span data-ttu-id="fce73-129">在 expression 中 `stackalloc T[E]` ， `T` 必須是 [非受控型](../builtin-types/unmanaged-types.md) 別，而且 `E` 必須評估為非負 [整數](../builtin-types/integral-numeric-types.md) 值。</span><span class="sxs-lookup"><span data-stu-id="fce73-129">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must evaluate to a non-negative [int](../builtin-types/integral-numeric-types.md) value.</span></span>

## <a name="security"></a><span data-ttu-id="fce73-130">安全性</span><span class="sxs-lookup"><span data-stu-id="fce73-130">Security</span></span>

<span data-ttu-id="fce73-131">使用 `stackalloc` 會自動啟用 Common Language Runtime (CLR) 中的緩衝區滿溢偵測功能。</span><span class="sxs-lookup"><span data-stu-id="fce73-131">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="fce73-132">如果偵測到緩衝區滿溢，會盡快終止處理序，將執行惡意程式碼的機會降到最低。</span><span class="sxs-lookup"><span data-stu-id="fce73-132">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="fce73-133">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="fce73-133">C# language specification</span></span>

<span data-ttu-id="fce73-134">如需詳細資訊，請參閱[c # 語言規格](~/_csharplang/spec/introduction.md)的[堆疊配置](~/_csharplang/spec/unsafe-code.md#stack-allocation)一節和在[嵌套內容 `stackalloc` 中允許](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md)的建議附注。</span><span class="sxs-lookup"><span data-stu-id="fce73-134">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the [Permit `stackalloc` in nested contexts](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) feature proposal note.</span></span>

## <a name="see-also"></a><span data-ttu-id="fce73-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fce73-135">See also</span></span>

- [<span data-ttu-id="fce73-136">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="fce73-136">C# reference</span></span>](../index.md)
- [<span data-ttu-id="fce73-137">C# 運算子與運算式</span><span class="sxs-lookup"><span data-stu-id="fce73-137">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="fce73-138">指標相關運算子</span><span class="sxs-lookup"><span data-stu-id="fce73-138">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="fce73-139">指標類型</span><span class="sxs-lookup"><span data-stu-id="fce73-139">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="fce73-140">記憶體與延伸相關類型</span><span class="sxs-lookup"><span data-stu-id="fce73-140">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="fce73-141">Stackalloc 的 Dos 和不注意事項</span><span class="sxs-lookup"><span data-stu-id="fce73-141">Dos and Don'ts of stackalloc</span></span>](https://vcsjones.dev/2020/02/24/stackalloc/)
