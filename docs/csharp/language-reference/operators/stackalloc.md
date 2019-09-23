---
title: stackalloc 運算子 - C# 參考
ms.custom: seodec18
ms.date: 09/20/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 9ef5f98f2b4973c5873417ecc9a71c187e7299b9
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182426"
---
# <a name="stackalloc-operator-c-reference"></a><span data-ttu-id="8fcce-102">stackalloc 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="8fcce-102">stackalloc operator (C# reference)</span></span>

<span data-ttu-id="8fcce-103">`stackalloc` 運算子會在堆疊上配置記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="8fcce-103">The `stackalloc` operator allocates a block of memory on the stack.</span></span> <span data-ttu-id="8fcce-104">在方法執行期間建立的堆疊配置的記憶體區塊，會在該方法傳回時自動被捨棄。</span><span class="sxs-lookup"><span data-stu-id="8fcce-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="8fcce-105">您無法明確釋放搭配 `stackalloc` 運算子配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="8fcce-105">You cannot explicitly free memory allocated with the `stackalloc` operator.</span></span> <span data-ttu-id="8fcce-106">堆疊配置的記憶體區塊不會被[記憶體回收](../../../standard/garbage-collection/index.md)，且不需要以 [`fixed` 陳述式](../keywords/fixed-statement.md)固定。</span><span class="sxs-lookup"><span data-stu-id="8fcce-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with the [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="8fcce-107">在運算式 `stackalloc T[E]` 中，`T` 必須是 [ unmanaged 型別](../builtin-types/unmanaged-types.md)，且 `E` 必須是 `int` 型別的運算式。</span><span class="sxs-lookup"><span data-stu-id="8fcce-107">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must be an expression of type `int`.</span></span>

<span data-ttu-id="8fcce-108">您可以將 `stackalloc` 運算子的結果指派至下列其中一個類型的變數：</span><span class="sxs-lookup"><span data-stu-id="8fcce-108">You can assign the result of the `stackalloc` operator to a variable of one of the following types:</span></span>

- <span data-ttu-id="8fcce-109"><xref:System.Span%601?displayProperty=nameWithType> 或 <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> (從 C# 7.2 開始)，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8fcce-109">Starting with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="8fcce-110">當您將堆疊配置的記憶體區塊指派至 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 變數時，您不需要使用 [unsafe](../keywords/unsafe.md) 內容。</span><span class="sxs-lookup"><span data-stu-id="8fcce-110">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="8fcce-111">當您處理那些類型時，您可以使用[條件式](conditional-operator.md)或指派運算式中的 `stackalloc` 運算式，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8fcce-111">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  <span data-ttu-id="8fcce-112">從C# 8.0 開始，只要允許`stackalloc` <xref:System.Span%601>或<xref:System.ReadOnlySpan%601>變數，您就可以在其他運算式內使用運算式，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8fcce-112">Starting with C# 8.0, you can use a `stackalloc` expression inside other expressions whenever a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable is allowed, as the following example shows:</span></span>

  [!code-csharp[stackalloc in nested expressions](~/samples/csharp/language-reference/operators/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <span data-ttu-id="8fcce-113">我們建議盡可能使用 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 類型來處理堆疊配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="8fcce-113">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="8fcce-114">[指標類型](../../programming-guide/unsafe-code-pointers/pointer-types.md)，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8fcce-114">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="8fcce-115">如先前的範例所示，您在使用指標類型時必須使用 `unsafe` 內容。</span><span class="sxs-lookup"><span data-stu-id="8fcce-115">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

  <span data-ttu-id="8fcce-116">在指標類型的情況下，您只能使用`stackalloc`區域變數宣告中的運算式來初始化變數。</span><span class="sxs-lookup"><span data-stu-id="8fcce-116">In the case of pointer types, you can use a `stackalloc` expression only in a local variable declaration to initialize the variable.</span></span>

<span data-ttu-id="8fcce-117">新配置記憶體的內容尚未被定義。</span><span class="sxs-lookup"><span data-stu-id="8fcce-117">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="8fcce-118">從 C# 7.3 開始，您可以使用陣列初始設定式語法來定義新配置記憶體的內容。</span><span class="sxs-lookup"><span data-stu-id="8fcce-118">Starting with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="8fcce-119">下列範例示範進行該操作的數種方法：</span><span class="sxs-lookup"><span data-stu-id="8fcce-119">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](~/samples/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

## <a name="security"></a><span data-ttu-id="8fcce-120">安全性</span><span class="sxs-lookup"><span data-stu-id="8fcce-120">Security</span></span>

<span data-ttu-id="8fcce-121">使用 `stackalloc` 會自動啟用 Common Language Runtime (CLR) 中的緩衝區滿溢偵測功能。</span><span class="sxs-lookup"><span data-stu-id="8fcce-121">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="8fcce-122">如果偵測到緩衝區滿溢，會盡快終止處理序，將執行惡意程式碼的機會降到最低。</span><span class="sxs-lookup"><span data-stu-id="8fcce-122">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8fcce-123">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="8fcce-123">C# language specification</span></span>

<span data-ttu-id="8fcce-124">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[堆疊配置](~/_csharplang/spec/unsafe-code.md#stack-allocation)一節。</span><span class="sxs-lookup"><span data-stu-id="8fcce-124">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8fcce-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8fcce-125">See also</span></span>

- [<span data-ttu-id="8fcce-126">C# 參考</span><span class="sxs-lookup"><span data-stu-id="8fcce-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="8fcce-127">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="8fcce-127">C# operators</span></span>](index.md)
- [<span data-ttu-id="8fcce-128">指標相關運算子</span><span class="sxs-lookup"><span data-stu-id="8fcce-128">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="8fcce-129">指標型別</span><span class="sxs-lookup"><span data-stu-id="8fcce-129">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="8fcce-130">記憶體與延伸相關類型</span><span class="sxs-lookup"><span data-stu-id="8fcce-130">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
