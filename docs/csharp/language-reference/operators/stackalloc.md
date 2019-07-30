---
title: stackalloc 運算子 - C# 參考
ms.custom: seodec18
ms.date: 06/10/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: f211acaa8c47ab42a1f7f06cff6c35570cd22b75
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433833"
---
# <a name="stackalloc-operator-c-reference"></a><span data-ttu-id="db151-102">stackalloc 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="db151-102">stackalloc operator (C# reference)</span></span>

<span data-ttu-id="db151-103">`stackalloc` 運算子會在堆疊上配置記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="db151-103">The `stackalloc` operator allocates a block of memory on the stack.</span></span> <span data-ttu-id="db151-104">在方法執行期間建立的堆疊配置的記憶體區塊，會在該方法傳回時自動被捨棄。</span><span class="sxs-lookup"><span data-stu-id="db151-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="db151-105">您無法明確釋放搭配 `stackalloc` 運算子配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="db151-105">You cannot explicitly free memory allocated with the `stackalloc` operator.</span></span> <span data-ttu-id="db151-106">堆疊配置的記憶體區塊不會被[記憶體回收](../../../standard/garbage-collection/index.md)，且不需要以 [`fixed` 陳述式](../keywords/fixed-statement.md)固定。</span><span class="sxs-lookup"><span data-stu-id="db151-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with the [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="db151-107">在運算式 `stackalloc T[E]` 中，`T` 必須是 [ unmanaged 型別](../builtin-types/unmanaged-types.md)，且 `E` 必須是 `int` 型別的運算式。</span><span class="sxs-lookup"><span data-stu-id="db151-107">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must be an expression of type `int`.</span></span>

<span data-ttu-id="db151-108">您可以將 `stackalloc` 運算子的結果指派至下列其中一個類型的變數：</span><span class="sxs-lookup"><span data-stu-id="db151-108">You can assign the result of the `stackalloc` operator to a variable of one of the following types:</span></span>

- <span data-ttu-id="db151-109"><xref:System.Span%601?displayProperty=nameWithType> 或 <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> (從 C# 7.2 開始)，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="db151-109">Starting with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="db151-110">當您將堆疊配置的記憶體區塊指派至 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 變數時，您不需要使用 [unsafe](../keywords/unsafe.md) 內容。</span><span class="sxs-lookup"><span data-stu-id="db151-110">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="db151-111">當您處理那些類型時，您可以使用[條件式](conditional-operator.md)或指派運算式中的 `stackalloc` 運算式，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="db151-111">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  > [!NOTE]
  > <span data-ttu-id="db151-112">我們建議盡可能使用 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 類型來處理堆疊配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="db151-112">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="db151-113">[指標類型](../../programming-guide/unsafe-code-pointers/pointer-types.md)，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="db151-113">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="db151-114">如先前的範例所示，您在使用指標類型時必須使用 `unsafe` 內容。</span><span class="sxs-lookup"><span data-stu-id="db151-114">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

<span data-ttu-id="db151-115">新配置記憶體的內容尚未被定義。</span><span class="sxs-lookup"><span data-stu-id="db151-115">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="db151-116">從 C# 7.3 開始，您可以使用陣列初始設定式語法來定義新配置記憶體的內容。</span><span class="sxs-lookup"><span data-stu-id="db151-116">Starting with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="db151-117">下列範例示範進行該操作的數種方法：</span><span class="sxs-lookup"><span data-stu-id="db151-117">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](~/samples/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

## <a name="security"></a><span data-ttu-id="db151-118">安全性</span><span class="sxs-lookup"><span data-stu-id="db151-118">Security</span></span>

<span data-ttu-id="db151-119">使用 `stackalloc` 會自動啟用 Common Language Runtime (CLR) 中的緩衝區滿溢偵測功能。</span><span class="sxs-lookup"><span data-stu-id="db151-119">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="db151-120">如果偵測到緩衝區滿溢，會盡快終止處理序，將執行惡意程式碼的機會降到最低。</span><span class="sxs-lookup"><span data-stu-id="db151-120">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="db151-121">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="db151-121">C# language specification</span></span>

<span data-ttu-id="db151-122">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[堆疊配置](~/_csharplang/spec/unsafe-code.md#stack-allocation)一節。</span><span class="sxs-lookup"><span data-stu-id="db151-122">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="db151-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db151-123">See also</span></span>

- [<span data-ttu-id="db151-124">C# 參考</span><span class="sxs-lookup"><span data-stu-id="db151-124">C# reference</span></span>](../index.md)
- [<span data-ttu-id="db151-125">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="db151-125">C# operators</span></span>](index.md)
- [<span data-ttu-id="db151-126">指標相關運算子</span><span class="sxs-lookup"><span data-stu-id="db151-126">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="db151-127">指標型別</span><span class="sxs-lookup"><span data-stu-id="db151-127">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="db151-128">記憶體與延伸相關類型</span><span class="sxs-lookup"><span data-stu-id="db151-128">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
