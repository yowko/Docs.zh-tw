---
title: '[] 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 01/10/2019
f1_keywords:
- '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
ms.openlocfilehash: 9088393f61d300ee76e56e320bec17b4a79bfebb
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835586"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="e2b98-102">[] 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="e2b98-102">[] operator (C# Reference)</span></span>

<span data-ttu-id="e2b98-103">中括弧 (`[]`) 通常用於陣列、索引子或指標元素存取。</span><span class="sxs-lookup"><span data-stu-id="e2b98-103">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

<span data-ttu-id="e2b98-104">如需指標元素存取的詳細資訊，請參閱[如何：使用指標存取陣列元素](../../programming-guide/unsafe-code-pointers/how-to-access-an-array-element-with-a-pointer.md)。</span><span class="sxs-lookup"><span data-stu-id="e2b98-104">For more information about pointer element access, see [How to: access an array element with a pointer](../../programming-guide/unsafe-code-pointers/how-to-access-an-array-element-with-a-pointer.md).</span></span>

<span data-ttu-id="e2b98-105">您也可以使用中括弧來指定[屬性](../../programming-guide/concepts/attributes/index.md)：</span><span class="sxs-lookup"><span data-stu-id="e2b98-105">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="array-access"></a><span data-ttu-id="e2b98-106">陣列存取</span><span class="sxs-lookup"><span data-stu-id="e2b98-106">Array access</span></span>

<span data-ttu-id="e2b98-107">以下範例將示範如何存取陣列元素：</span><span class="sxs-lookup"><span data-stu-id="e2b98-107">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](~/samples/snippets/csharp/language-reference/operators/IndexOperatorExamples.cs#Arrays)]

<span data-ttu-id="e2b98-108">如果陣列索引超出陣列的對應維度界限，就會擲回 <xref:System.IndexOutOfRangeException>。</span><span class="sxs-lookup"><span data-stu-id="e2b98-108">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="e2b98-109">如上述範例所示，您也會在陣列類型的宣告和陣列執行個體的具現化中使用方括弧。</span><span class="sxs-lookup"><span data-stu-id="e2b98-109">As the preceding example shows, you also use square brackets in declaration of an array type and instantiation of array instances.</span></span>

<span data-ttu-id="e2b98-110">如需陣列的詳細資訊，請參閱[陣列](../../programming-guide/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e2b98-110">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

## <a name="indexer-access"></a><span data-ttu-id="e2b98-111">索引子存取</span><span class="sxs-lookup"><span data-stu-id="e2b98-111">Indexer access</span></span>

<span data-ttu-id="e2b98-112">下列範例使用 .NET<xref:System.Collections.Generic.Dictionary%602> 類型示範索引子存取：</span><span class="sxs-lookup"><span data-stu-id="e2b98-112">The following example uses .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](~/samples/snippets/csharp/language-reference/operators/IndexOperatorExamples.cs#Indexers)]

<span data-ttu-id="e2b98-113">索引子可讓您透過與陣列編製索引類似的方式，為使用者定義型別的執行個體編製索引。</span><span class="sxs-lookup"><span data-stu-id="e2b98-113">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="e2b98-114">與必須是整數的陣列索引不同，索引子引數可以宣告為任何類型。</span><span class="sxs-lookup"><span data-stu-id="e2b98-114">Unlike array indices, which must be integer, the indexer arguments can be declared to be of any type.</span></span>

<span data-ttu-id="e2b98-115">如需索引子的詳細資訊，請參閱[索引子](../../programming-guide/indexers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e2b98-115">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="e2b98-116">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="e2b98-116">Operator overloadability</span></span>

<span data-ttu-id="e2b98-117">元素存取 `[]` 不是可多載的運算子。</span><span class="sxs-lookup"><span data-stu-id="e2b98-117">Element access `[]` is not considered an overloadable operator.</span></span> <span data-ttu-id="e2b98-118">請使用[索引子](../../programming-guide/indexers/index.md)以支援使用使用者定義型別編製索引。</span><span class="sxs-lookup"><span data-stu-id="e2b98-118">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e2b98-119">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="e2b98-119">C# language specification</span></span>

<span data-ttu-id="e2b98-120">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[元素存取](~/_csharplang/spec/expressions.md#element-access)和[指標元素存取](~/_csharplang/spec/unsafe-code.md#pointer-element-access)小節。</span><span class="sxs-lookup"><span data-stu-id="e2b98-120">For more information, see the [Element access](~/_csharplang/spec/expressions.md#element-access) and [Pointer element access](~/_csharplang/spec/unsafe-code.md#pointer-element-access) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e2b98-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2b98-121">See also</span></span>

- [<span data-ttu-id="e2b98-122">C# 參考</span><span class="sxs-lookup"><span data-stu-id="e2b98-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e2b98-123">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e2b98-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e2b98-124">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="e2b98-124">C# Operators</span></span>](index.md)
- [<span data-ttu-id="e2b98-125">陣列</span><span class="sxs-lookup"><span data-stu-id="e2b98-125">Arrays</span></span>](../../programming-guide/arrays/index.md)
- [<span data-ttu-id="e2b98-126">索引子</span><span class="sxs-lookup"><span data-stu-id="e2b98-126">Indexers</span></span>](../../programming-guide/indexers/index.md)
- [<span data-ttu-id="e2b98-127">指標型別</span><span class="sxs-lookup"><span data-stu-id="e2b98-127">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="e2b98-128">屬性</span><span class="sxs-lookup"><span data-stu-id="e2b98-128">Attributes</span></span>](../../programming-guide/concepts/attributes/index.md)
- <span data-ttu-id="e2b98-129">[?. 和 ?[] 運算子](null-conditional-operators.md)</span><span class="sxs-lookup"><span data-stu-id="e2b98-129">[?. and ?[] operators](null-conditional-operators.md)</span></span>