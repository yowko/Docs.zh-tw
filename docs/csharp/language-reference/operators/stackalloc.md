---
title: 'stackalloc 運算式-c # 參考'
ms.date: 03/13/2020
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc expression [C#]
ms.openlocfilehash: 32ac85f678912cb7e5f506244265b1bf57d0b4aa
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555602"
---
# <a name="stackalloc-expression-c-reference"></a><span data-ttu-id="4dc2f-102">stackalloc expression (c # 參考) </span><span class="sxs-lookup"><span data-stu-id="4dc2f-102">stackalloc expression (C# reference)</span></span>

<span data-ttu-id="4dc2f-103">運算式會配置 `stackalloc` 堆疊上的記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="4dc2f-103">A `stackalloc` expression allocates a block of memory on the stack.</span></span> <span data-ttu-id="4dc2f-104">在方法執行期間建立的堆疊配置的記憶體區塊，會在該方法傳回時自動被捨棄。</span><span class="sxs-lookup"><span data-stu-id="4dc2f-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="4dc2f-105">您無法明確釋放以所配置的記憶體 `stackalloc` 。</span><span class="sxs-lookup"><span data-stu-id="4dc2f-105">You cannot explicitly free the memory allocated with `stackalloc`.</span></span> <span data-ttu-id="4dc2f-106">堆疊配置的記憶體區塊不受[垃圾收集](../../../standard/garbage-collection/index.md)，也不需要使用[ `fixed` 語句](../keywords/fixed-statement.md)來釘選。</span><span class="sxs-lookup"><span data-stu-id="4dc2f-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with a [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="4dc2f-107">您可以將運算式的結果指派 `stackalloc` 給下列其中一種類型的變數：</span><span class="sxs-lookup"><span data-stu-id="4dc2f-107">You can assign the result of a `stackalloc` expression to a variable of one of the following types:</span></span>

- <span data-ttu-id="4dc2f-108">從 c # 7.2、 <xref:System.Span%601?displayProperty=nameWithType> 或開始， <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> 如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="4dc2f-108">Beginning with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](snippets/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="4dc2f-109">當您將堆疊配置的記憶體區塊指派至 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 變數時，您不需要使用 [unsafe](../keywords/unsafe.md) 內容。</span><span class="sxs-lookup"><span data-stu-id="4dc2f-109">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="4dc2f-110">當您處理那些類型時，您可以使用[條件式](conditional-operator.md)或指派運算式中的 `stackalloc` 運算式，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="4dc2f-110">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](snippets/StackallocOperator.cs#AsExpression)]

  <span data-ttu-id="4dc2f-111">從 c # 8.0 開始， `stackalloc` 只要允許或變數，您就可以在其他運算式內使用運算式 <xref:System.Span%601> <xref:System.ReadOnlySpan%601> ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="4dc2f-111">Beginning with C# 8.0, you can use a `stackalloc` expression inside other expressions whenever a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable is allowed, as the following example shows:</span></span>

  [!code-csharp[stackalloc in nested expressions](snippets/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <span data-ttu-id="4dc2f-112">我們建議盡可能使用 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 類型來處理堆疊配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="4dc2f-112">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="4dc2f-113">[指標類型](../../programming-guide/unsafe-code-pointers/pointer-types.md)，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="4dc2f-113">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](snippets/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="4dc2f-114">如先前的範例所示，您在使用指標類型時必須使用 `unsafe` 內容。</span><span class="sxs-lookup"><span data-stu-id="4dc2f-114">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

  <span data-ttu-id="4dc2f-115">在指標類型的情況下，您只能使用 `stackalloc` 區域變數宣告中的運算式來初始化變數。</span><span class="sxs-lookup"><span data-stu-id="4dc2f-115">In the case of pointer types, you can use a `stackalloc` expression only in a local variable declaration to initialize the variable.</span></span>

<span data-ttu-id="4dc2f-116">堆疊上可用的記憶體數量有限。</span><span class="sxs-lookup"><span data-stu-id="4dc2f-116">The amount of memory available on the stack is limited.</span></span> <span data-ttu-id="4dc2f-117">如果您在堆疊上配置太多記憶體， <xref:System.StackOverflowException> 就會擲回。</span><span class="sxs-lookup"><span data-stu-id="4dc2f-117">If you allocate too much memory on the stack, a <xref:System.StackOverflowException> is thrown.</span></span> <span data-ttu-id="4dc2f-118">若要避免這種情況，請遵循下列規則：</span><span class="sxs-lookup"><span data-stu-id="4dc2f-118">To avoid that, follow the rules below:</span></span>

- <span data-ttu-id="4dc2f-119">限制您配置的記憶體數量 `stackalloc` ：</span><span class="sxs-lookup"><span data-stu-id="4dc2f-119">Limit the amount of memory you allocate with `stackalloc`:</span></span>

  [!code-csharp[limit stackalloc](snippets/StackallocOperator.cs#LimitStackalloc)]

  <span data-ttu-id="4dc2f-120">因為堆疊上可用的記憶體數量取決於執行程式碼的環境，所以當您定義實際的限制值時請保守。</span><span class="sxs-lookup"><span data-stu-id="4dc2f-120">Because the amount of memory available on the stack depends on the environment in which the code is executed, be conservative when you define the actual limit value.</span></span>

- <span data-ttu-id="4dc2f-121">避免 `stackalloc` 在迴圈內使用。</span><span class="sxs-lookup"><span data-stu-id="4dc2f-121">Avoid using `stackalloc` inside loops.</span></span> <span data-ttu-id="4dc2f-122">在迴圈外配置記憶體區塊，並在迴圈內重複使用它。</span><span class="sxs-lookup"><span data-stu-id="4dc2f-122">Allocate the memory block outside a loop and reuse it inside the loop.</span></span>

<span data-ttu-id="4dc2f-123">新配置記憶體的內容尚未被定義。</span><span class="sxs-lookup"><span data-stu-id="4dc2f-123">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="4dc2f-124">在使用之前，您應該先將它初始化。</span><span class="sxs-lookup"><span data-stu-id="4dc2f-124">You should initialize it before the use.</span></span> <span data-ttu-id="4dc2f-125">例如，您可以使用 <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> 方法，將所有專案設定為類型的預設值 `T` 。</span><span class="sxs-lookup"><span data-stu-id="4dc2f-125">For example, you can use the <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> method that sets all the items to the default value of type `T`.</span></span>

<span data-ttu-id="4dc2f-126">從 c # 7.3 開始，您可以使用陣列初始化運算式語法來定義新配置之記憶體的內容。</span><span class="sxs-lookup"><span data-stu-id="4dc2f-126">Beginning with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="4dc2f-127">下列範例示範進行該操作的數種方法：</span><span class="sxs-lookup"><span data-stu-id="4dc2f-127">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](snippets/StackallocOperator.cs#StackallocInit)]

<span data-ttu-id="4dc2f-128">在 [運算式] 中 `stackalloc T[E]` ， `T` 必須是[非受控型](../builtin-types/unmanaged-types.md)別，而且 `E` 必須評估為非負[整數](../builtin-types/integral-numeric-types.md)值。</span><span class="sxs-lookup"><span data-stu-id="4dc2f-128">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must evaluate to a non-negative [int](../builtin-types/integral-numeric-types.md) value.</span></span>

## <a name="security"></a><span data-ttu-id="4dc2f-129">安全性</span><span class="sxs-lookup"><span data-stu-id="4dc2f-129">Security</span></span>

<span data-ttu-id="4dc2f-130">使用 `stackalloc` 會自動啟用 Common Language Runtime (CLR) 中的緩衝區滿溢偵測功能。</span><span class="sxs-lookup"><span data-stu-id="4dc2f-130">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="4dc2f-131">如果偵測到緩衝區滿溢，會盡快終止處理序，將執行惡意程式碼的機會降到最低。</span><span class="sxs-lookup"><span data-stu-id="4dc2f-131">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4dc2f-132">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="4dc2f-132">C# language specification</span></span>

<span data-ttu-id="4dc2f-133">如需詳細資訊，請參閱[c # 語言規格](~/_csharplang/spec/introduction.md)的[堆疊配置](~/_csharplang/spec/unsafe-code.md#stack-allocation)一節和在[nested 內容 `stackalloc` 中允許](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md)功能提案。</span><span class="sxs-lookup"><span data-stu-id="4dc2f-133">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the [Permit `stackalloc` in nested contexts](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) feature proposal note.</span></span>

## <a name="see-also"></a><span data-ttu-id="4dc2f-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4dc2f-134">See also</span></span>

- [<span data-ttu-id="4dc2f-135">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="4dc2f-135">C# reference</span></span>](../index.md)
- [<span data-ttu-id="4dc2f-136">C# 運算子與運算式</span><span class="sxs-lookup"><span data-stu-id="4dc2f-136">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="4dc2f-137">指標相關運算子</span><span class="sxs-lookup"><span data-stu-id="4dc2f-137">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="4dc2f-138">指標類型</span><span class="sxs-lookup"><span data-stu-id="4dc2f-138">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="4dc2f-139">記憶體與延伸相關類型</span><span class="sxs-lookup"><span data-stu-id="4dc2f-139">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="4dc2f-140">Stackalloc 的 Dos 和不應事項</span><span class="sxs-lookup"><span data-stu-id="4dc2f-140">Dos and Don'ts of stackalloc</span></span>](https://vcsjones.dev/2020/02/24/stackalloc/)
