---
title: stackalloc 運算子 - C# 參考
ms.date: 09/20/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 9c9767e0c9945a9589d049fa7abba192cb928ad5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846244"
---
# <a name="stackalloc-operator-c-reference"></a><span data-ttu-id="cd4a0-102">stackalloc 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="cd4a0-102">stackalloc operator (C# reference)</span></span>

<span data-ttu-id="cd4a0-103">`stackalloc` 運算子會在堆疊上配置記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="cd4a0-103">The `stackalloc` operator allocates a block of memory on the stack.</span></span> <span data-ttu-id="cd4a0-104">在方法執行期間建立的堆疊配置的記憶體區塊，會在該方法傳回時自動被捨棄。</span><span class="sxs-lookup"><span data-stu-id="cd4a0-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="cd4a0-105">您無法明確釋放搭配 `stackalloc` 運算子配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="cd4a0-105">You cannot explicitly free memory allocated with the `stackalloc` operator.</span></span> <span data-ttu-id="cd4a0-106">堆疊分配的區塊不受[垃圾回收](../../../standard/garbage-collection/index.md)，也不必用[`fixed`語句](../keywords/fixed-statement.md)固定。</span><span class="sxs-lookup"><span data-stu-id="cd4a0-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with a [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="cd4a0-107">您可以將 `stackalloc` 運算子的結果指派至下列其中一個類型的變數：</span><span class="sxs-lookup"><span data-stu-id="cd4a0-107">You can assign the result of the `stackalloc` operator to a variable of one of the following types:</span></span>

- <span data-ttu-id="cd4a0-108">從 C# 7.2 <xref:System.Span%601?displayProperty=nameWithType> <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>或 開始，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="cd4a0-108">Beginning with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](snippets/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="cd4a0-109">當您將堆疊配置的記憶體區塊指派至 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 變數時，您不需要使用 [unsafe](../keywords/unsafe.md) 內容。</span><span class="sxs-lookup"><span data-stu-id="cd4a0-109">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="cd4a0-110">當您處理那些類型時，您可以使用[條件式](conditional-operator.md)或指派運算式中的 `stackalloc` 運算式，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="cd4a0-110">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](snippets/StackallocOperator.cs#AsExpression)]

  <span data-ttu-id="cd4a0-111">從 C# 8.0 開始，只要`stackalloc`允許 或<xref:System.Span%601><xref:System.ReadOnlySpan%601>變數，都可以在其他運算式中使用運算式，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="cd4a0-111">Beginning with C# 8.0, you can use a `stackalloc` expression inside other expressions whenever a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable is allowed, as the following example shows:</span></span>

  [!code-csharp[stackalloc in nested expressions](snippets/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <span data-ttu-id="cd4a0-112">我們建議盡可能使用 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 類型來處理堆疊配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="cd4a0-112">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="cd4a0-113">[指標類型](../../programming-guide/unsafe-code-pointers/pointer-types.md)，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="cd4a0-113">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](snippets/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="cd4a0-114">如先前的範例所示，您在使用指標類型時必須使用 `unsafe` 內容。</span><span class="sxs-lookup"><span data-stu-id="cd4a0-114">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

  <span data-ttu-id="cd4a0-115">在指標類型中，只能在區域變數聲明中使用`stackalloc`運算式來初始化變數。</span><span class="sxs-lookup"><span data-stu-id="cd4a0-115">In the case of pointer types, you can use a `stackalloc` expression only in a local variable declaration to initialize the variable.</span></span>

<span data-ttu-id="cd4a0-116">新配置記憶體的內容尚未被定義。</span><span class="sxs-lookup"><span data-stu-id="cd4a0-116">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="cd4a0-117">從 C# 7.3 開始，可以使用陣列初始化器語法來定義新分配的記憶體的內容。</span><span class="sxs-lookup"><span data-stu-id="cd4a0-117">Beginning with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="cd4a0-118">下列範例示範進行該操作的數種方法：</span><span class="sxs-lookup"><span data-stu-id="cd4a0-118">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](snippets/StackallocOperator.cs#StackallocInit)]

<span data-ttu-id="cd4a0-119">在運算式`stackalloc T[E]`中`T`，必須是[非託管類型](../builtin-types/unmanaged-types.md)，並且必須`E`是[int](../builtin-types/integral-numeric-types.md)的運算式。</span><span class="sxs-lookup"><span data-stu-id="cd4a0-119">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must be an expression of type [int](../builtin-types/integral-numeric-types.md).</span></span>

## <a name="security"></a><span data-ttu-id="cd4a0-120">安全性</span><span class="sxs-lookup"><span data-stu-id="cd4a0-120">Security</span></span>

<span data-ttu-id="cd4a0-121">使用 `stackalloc` 會自動啟用 Common Language Runtime (CLR) 中的緩衝區滿溢偵測功能。</span><span class="sxs-lookup"><span data-stu-id="cd4a0-121">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="cd4a0-122">如果偵測到緩衝區滿溢，會盡快終止處理序，將執行惡意程式碼的機會降到最低。</span><span class="sxs-lookup"><span data-stu-id="cd4a0-122">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="cd4a0-123">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="cd4a0-123">C# language specification</span></span>

<span data-ttu-id="cd4a0-124">有關詳細資訊，請參閱[C# 語言規範](~/_csharplang/spec/introduction.md)的[堆疊分配](~/_csharplang/spec/unsafe-code.md#stack-allocation)部分和[嵌套上下文中的`stackalloc`"許可](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md)"功能建議說明。</span><span class="sxs-lookup"><span data-stu-id="cd4a0-124">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the [Permit `stackalloc` in nested contexts](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) feature proposal note.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd4a0-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd4a0-125">See also</span></span>

- [<span data-ttu-id="cd4a0-126">C# 參考</span><span class="sxs-lookup"><span data-stu-id="cd4a0-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="cd4a0-127">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="cd4a0-127">C# operators</span></span>](index.md)
- [<span data-ttu-id="cd4a0-128">指標相關運算子</span><span class="sxs-lookup"><span data-stu-id="cd4a0-128">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="cd4a0-129">指標類型</span><span class="sxs-lookup"><span data-stu-id="cd4a0-129">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="cd4a0-130">記憶體和跨距相關類型</span><span class="sxs-lookup"><span data-stu-id="cd4a0-130">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
