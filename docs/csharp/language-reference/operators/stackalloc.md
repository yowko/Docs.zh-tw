---
title: stackalloc 運算子 - C# 參考
ms.custom: seodec18
ms.date: 09/20/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 4f3ba6594eb16cf16db6a1de78fe05509c5f4d7d
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345277"
---
# <a name="stackalloc-operator-c-reference"></a><span data-ttu-id="31837-102">stackalloc 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="31837-102">stackalloc operator (C# reference)</span></span>

<span data-ttu-id="31837-103">`stackalloc` 運算子會在堆疊上配置記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="31837-103">The `stackalloc` operator allocates a block of memory on the stack.</span></span> <span data-ttu-id="31837-104">在方法執行期間建立的堆疊配置的記憶體區塊，會在該方法傳回時自動被捨棄。</span><span class="sxs-lookup"><span data-stu-id="31837-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="31837-105">您無法明確釋放搭配 `stackalloc` 運算子配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="31837-105">You cannot explicitly free memory allocated with the `stackalloc` operator.</span></span> <span data-ttu-id="31837-106">堆疊配置的記憶體區塊不受[垃圾收集](../../../standard/garbage-collection/index.md)，也不需要使用[`fixed` 語句](../keywords/fixed-statement.md)來釘選。</span><span class="sxs-lookup"><span data-stu-id="31837-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with a [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="31837-107">您可以將 `stackalloc` 運算子的結果指派至下列其中一個類型的變數：</span><span class="sxs-lookup"><span data-stu-id="31837-107">You can assign the result of the `stackalloc` operator to a variable of one of the following types:</span></span>

- <span data-ttu-id="31837-108">從C# 7.2 開始，<xref:System.Span%601?displayProperty=nameWithType> 或 <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="31837-108">Beginning with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="31837-109">當您將堆疊配置的記憶體區塊指派至 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 變數時，您不需要使用 [unsafe](../keywords/unsafe.md) 內容。</span><span class="sxs-lookup"><span data-stu-id="31837-109">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="31837-110">當您處理那些類型時，您可以使用[條件式](conditional-operator.md)或指派運算式中的 `stackalloc` 運算式，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="31837-110">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  <span data-ttu-id="31837-111">從C# 8.0 開始，只要允許 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 變數，您就可以在其他運算式內使用 `stackalloc` 運算式，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="31837-111">Beginning with C# 8.0, you can use a `stackalloc` expression inside other expressions whenever a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable is allowed, as the following example shows:</span></span>

  [!code-csharp[stackalloc in nested expressions](~/samples/csharp/language-reference/operators/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <span data-ttu-id="31837-112">我們建議盡可能使用 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 類型來處理堆疊配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="31837-112">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="31837-113">[指標類型](../../programming-guide/unsafe-code-pointers/pointer-types.md)，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="31837-113">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="31837-114">如先前的範例所示，您在使用指標類型時必須使用 `unsafe` 內容。</span><span class="sxs-lookup"><span data-stu-id="31837-114">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

  <span data-ttu-id="31837-115">在指標類型的情況下，您只能使用區域變數宣告中的 `stackalloc` 運算式來初始化變數。</span><span class="sxs-lookup"><span data-stu-id="31837-115">In the case of pointer types, you can use a `stackalloc` expression only in a local variable declaration to initialize the variable.</span></span>

<span data-ttu-id="31837-116">新配置記憶體的內容尚未被定義。</span><span class="sxs-lookup"><span data-stu-id="31837-116">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="31837-117">從C# 7.3 開始，您可以使用陣列初始化運算式語法來定義新配置之記憶體的內容。</span><span class="sxs-lookup"><span data-stu-id="31837-117">Beginning with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="31837-118">下列範例示範進行該操作的數種方法：</span><span class="sxs-lookup"><span data-stu-id="31837-118">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](~/samples/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

<span data-ttu-id="31837-119">在 expression `stackalloc T[E]`中，`T` 必須是[非受控型](../builtin-types/unmanaged-types.md)別，而且 `E` 必須是[int](../builtin-types/integral-numeric-types.md)類型的運算式。</span><span class="sxs-lookup"><span data-stu-id="31837-119">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must be an expression of type [int](../builtin-types/integral-numeric-types.md).</span></span>

## <a name="security"></a><span data-ttu-id="31837-120">安全性</span><span class="sxs-lookup"><span data-stu-id="31837-120">Security</span></span>

<span data-ttu-id="31837-121">使用 `stackalloc` 會自動啟用 Common Language Runtime (CLR) 中的緩衝區滿溢偵測功能。</span><span class="sxs-lookup"><span data-stu-id="31837-121">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="31837-122">如果偵測到緩衝區滿溢，會盡快終止處理序，將執行惡意程式碼的機會降到最低。</span><span class="sxs-lookup"><span data-stu-id="31837-122">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="31837-123">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="31837-123">C# language specification</span></span>

<span data-ttu-id="31837-124">如需詳細資訊，請參閱[ C#語言規格](~/_csharplang/spec/introduction.md)的[堆疊配置](~/_csharplang/spec/unsafe-code.md#stack-allocation)一節和嵌套內容功能建議事項[中的允許 `stackalloc`](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) 。</span><span class="sxs-lookup"><span data-stu-id="31837-124">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the [Permit `stackalloc` in nested contexts](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) feature proposal note.</span></span>

## <a name="see-also"></a><span data-ttu-id="31837-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="31837-125">See also</span></span>

- [<span data-ttu-id="31837-126">C# 參考</span><span class="sxs-lookup"><span data-stu-id="31837-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="31837-127">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="31837-127">C# operators</span></span>](index.md)
- [<span data-ttu-id="31837-128">指標相關運算子</span><span class="sxs-lookup"><span data-stu-id="31837-128">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="31837-129">指標型別</span><span class="sxs-lookup"><span data-stu-id="31837-129">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="31837-130">記憶體與延伸相關類型</span><span class="sxs-lookup"><span data-stu-id="31837-130">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
