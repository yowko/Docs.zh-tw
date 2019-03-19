---
title: typeof - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords:
- typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
ms.openlocfilehash: f218414bf60a86b95461d747fb6c557f03bcfcb3
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2019
ms.locfileid: "57846112"
---
# <a name="typeof-c-reference"></a><span data-ttu-id="d2621-102">typeof (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="d2621-102">typeof (C# Reference)</span></span>

<span data-ttu-id="d2621-103">用來取得類型的 <xref:System.Type?displayProperty=nameWithType> 物件。</span><span class="sxs-lookup"><span data-stu-id="d2621-103">Used to obtain the <xref:System.Type?displayProperty=nameWithType> object for a type.</span></span> <span data-ttu-id="d2621-104">`typeof` 運算式有下列形式：</span><span class="sxs-lookup"><span data-stu-id="d2621-104">A `typeof` expression takes the following form:</span></span>

```csharp
System.Type type = typeof(int);
```

## <a name="remarks"></a><span data-ttu-id="d2621-105">備註</span><span class="sxs-lookup"><span data-stu-id="d2621-105">Remarks</span></span>

<span data-ttu-id="d2621-106">若要取得運算式的執行階段類型，您可以使用 .NET Framework 方法 <xref:System.Object.GetType%2A>，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="d2621-106">To obtain the run-time type of an expression, you can use the .NET Framework method <xref:System.Object.GetType%2A>, as in the following example:</span></span>

```csharp
int i = 0;
System.Type type = i.GetType();
```

<span data-ttu-id="d2621-107">無法多載 `typeof` 運算子。</span><span class="sxs-lookup"><span data-stu-id="d2621-107">The `typeof` operator cannot be overloaded.</span></span>

<span data-ttu-id="d2621-108">`typeof` 運算子也可以用於開放式泛型型別。</span><span class="sxs-lookup"><span data-stu-id="d2621-108">The `typeof` operator can also be used on open generic types.</span></span> <span data-ttu-id="d2621-109">在規格中，具有多個型別參數的類型必須具有適當數目的逗號。</span><span class="sxs-lookup"><span data-stu-id="d2621-109">Types with more than one type parameter must have the appropriate number of commas in the specification.</span></span> <span data-ttu-id="d2621-110">例如，<xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWIthType> 有兩個型別引數，因此您會使用一個逗號：</span><span class="sxs-lookup"><span data-stu-id="d2621-110">For example, the <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWIthType> has two type arguments, so you use one comma:</span></span>

```csharp
Type t = typeof(System.Collection.Generic.Dictionary<,>);
```

<span data-ttu-id="d2621-111">下列範例示範如何判斷方法的傳回型別是否為泛型 <xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="d2621-111">The following example shows how to determine whether the return type of a method is a generic <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="d2621-112">如果傳回型別不是 <xref:System.Collections.Generic.IEnumerable%601> 泛型型別，<xref:System.Type.GetInterface%2A?displayProperty=nameWithType> 會傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="d2621-112"><xref:System.Type.GetInterface%2A?displayProperty=nameWithType> will return `null` if the return type is not an <xref:System.Collections.Generic.IEnumerable%601> generic type.</span></span>

[!code-csharp[typeof_3.cs](~/samples/snippets/csharp/keywords/typeof/typeof_3.cs)]

## <a name="example"></a><span data-ttu-id="d2621-113">範例</span><span class="sxs-lookup"><span data-stu-id="d2621-113">Example</span></span>

[!code-csharp[csrefKeywordsOperator#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#12)] 

## <a name="example"></a><span data-ttu-id="d2621-114">範例</span><span class="sxs-lookup"><span data-stu-id="d2621-114">Example</span></span>

<span data-ttu-id="d2621-115">這個範例使用 <xref:System.Object.GetType%2A> 方法，判斷用來包含數值計算結果的類型。</span><span class="sxs-lookup"><span data-stu-id="d2621-115">This sample uses the <xref:System.Object.GetType%2A> method to determine the type that is used to contain the result of a numeric calculation.</span></span> <span data-ttu-id="d2621-116">這取決於所產生數字的儲存需求。</span><span class="sxs-lookup"><span data-stu-id="d2621-116">This depends on the storage requirements of the resulting number.</span></span>

[!code-csharp[csrefKeywordsOperator#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#13)]

## <a name="c-language-specification"></a><span data-ttu-id="d2621-117">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="d2621-117">C# language specification</span></span>

<span data-ttu-id="d2621-118">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的 [typeof 運算子](~/_csharplang/spec/expressions.md#the-typeof-operator)。</span><span class="sxs-lookup"><span data-stu-id="d2621-118">For more information, see [The typeof operator](~/_csharplang/spec/expressions.md#the-typeof-operator) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="d2621-119">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="d2621-119">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="d2621-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2621-120">See also</span></span>

- <xref:System.Type?displayProperty=nameWithType>
- [<span data-ttu-id="d2621-121">C# 參考</span><span class="sxs-lookup"><span data-stu-id="d2621-121">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="d2621-122">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="d2621-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d2621-123">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="d2621-123">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="d2621-124">is</span><span class="sxs-lookup"><span data-stu-id="d2621-124">is</span></span>](../../../csharp/language-reference/keywords/is.md)
- [<span data-ttu-id="d2621-125">運算子關鍵字</span><span class="sxs-lookup"><span data-stu-id="d2621-125">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
