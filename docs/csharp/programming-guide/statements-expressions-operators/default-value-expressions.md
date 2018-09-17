---
title: 預設值運算式 (C# 程式設計指南)
description: 預設值運算式會為任何參考型別或實值型別產生預設值
ms.date: 04/25/2018
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.openlocfilehash: 94866f22fb3ad921a834cffb16fe17e44cef5965
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2018
ms.locfileid: "45615338"
---
# <a name="default-value-expressions-c-programming-guide"></a><span data-ttu-id="f96db-103">預設值運算式 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="f96db-103">default value expressions (C# programming guide)</span></span>

<span data-ttu-id="f96db-104">預設值運算式 `default(T)` 會產生型別 `T` 的預設值。</span><span class="sxs-lookup"><span data-stu-id="f96db-104">A default value expression `default(T)` produces the default value of a type `T`.</span></span> <span data-ttu-id="f96db-105">下表顯示將為各種型別產生哪些值：</span><span class="sxs-lookup"><span data-stu-id="f96db-105">The following table shows which values are produced for various types:</span></span>

|<span data-ttu-id="f96db-106">類型</span><span class="sxs-lookup"><span data-stu-id="f96db-106">Type</span></span>|<span data-ttu-id="f96db-107">預設值</span><span class="sxs-lookup"><span data-stu-id="f96db-107">Default value</span></span>|
|---------|---------|
|<span data-ttu-id="f96db-108">任何參考類型</span><span class="sxs-lookup"><span data-stu-id="f96db-108">Any reference type</span></span>|`null`|
|<span data-ttu-id="f96db-109">數值型別</span><span class="sxs-lookup"><span data-stu-id="f96db-109">Numeric value type</span></span>|<span data-ttu-id="f96db-110">零</span><span class="sxs-lookup"><span data-stu-id="f96db-110">Zero</span></span>|
|[<span data-ttu-id="f96db-111">bool</span><span class="sxs-lookup"><span data-stu-id="f96db-111">bool</span></span>](../../language-reference/keywords/bool.md)|`false`|
|[<span data-ttu-id="f96db-112">char</span><span class="sxs-lookup"><span data-stu-id="f96db-112">char</span></span>](../../language-reference/keywords/char.md)|`'\0'`|
|[<span data-ttu-id="f96db-113">enum</span><span class="sxs-lookup"><span data-stu-id="f96db-113">enum</span></span>](../../language-reference/keywords/enum.md)|<span data-ttu-id="f96db-114">這個值是由運算式 `(E)0` 所產生，其中 `E` 是列舉識別碼。</span><span class="sxs-lookup"><span data-stu-id="f96db-114">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="f96db-115">struct</span><span class="sxs-lookup"><span data-stu-id="f96db-115">struct</span></span>](../../language-reference/keywords/struct.md)|<span data-ttu-id="f96db-116">這個值是藉由將所有實值型別欄位設定為其預設值，並將所有參考型別欄位設定為 `null` 所產生。</span><span class="sxs-lookup"><span data-stu-id="f96db-116">The value produced by setting all value type fields to their default value and all reference type fields to `null`.</span></span>|
|<span data-ttu-id="f96db-117">可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="f96db-117">Nullable type</span></span>|<span data-ttu-id="f96db-118"><xref:System.Nullable%601.HasValue%2A> 屬性是 `false` 且未定義 <xref:System.Nullable%601.Value%2A> 屬性的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f96db-118">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span>|

<span data-ttu-id="f96db-119">預設值運算式對泛型類別和方法特別有用。</span><span class="sxs-lookup"><span data-stu-id="f96db-119">Default value expressions are particularly useful in generic classes and methods.</span></span> <span data-ttu-id="f96db-120">使用泛型時會發生一個問題，也就是當您無法預先知道下列資訊時，如何指派參數化型別 `T` 的預設值：</span><span class="sxs-lookup"><span data-stu-id="f96db-120">One issue that arises using generics is how to assign a default value of a parameterized type `T` when you don't know the following in advance:</span></span>

- <span data-ttu-id="f96db-121">`T` 是參考型別或實值型別。</span><span class="sxs-lookup"><span data-stu-id="f96db-121">Whether `T` is a reference type or a value type.</span></span>
- <span data-ttu-id="f96db-122">如果 `T` 是實值型別，則其是數值還是結構。</span><span class="sxs-lookup"><span data-stu-id="f96db-122">If `T` is a value type, whether it's a numeric value or a struct.</span></span>

 <span data-ttu-id="f96db-123">假設有參數化型別 `T` 的變數 `t`，陳述式 `t = null` 就只在 `T` 為參考型別時有效。</span><span class="sxs-lookup"><span data-stu-id="f96db-123">Given a variable `t` of a parameterized type `T`, the statement `t = null` is only valid if `T` is a reference type.</span></span> <span data-ttu-id="f96db-124">指派 `t = 0` 僅適用於數值型別，而不適用於結構。</span><span class="sxs-lookup"><span data-stu-id="f96db-124">The assignment `t = 0` only works for numeric value types but not for structs.</span></span> <span data-ttu-id="f96db-125">若要解決該問題，請使用預設值運算式：</span><span class="sxs-lookup"><span data-stu-id="f96db-125">To solve that, use a default value expression:</span></span>

```csharp
T t = default(T);
```

<span data-ttu-id="f96db-126">`default(T)` 運算式不限於泛型類別及方法。</span><span class="sxs-lookup"><span data-stu-id="f96db-126">The `default(T)` expression is not limited to generic classes and methods.</span></span> <span data-ttu-id="f96db-127">預設值運算式可搭配任何 managed 型別使用。</span><span class="sxs-lookup"><span data-stu-id="f96db-127">Default value expressions can be used with any managed type.</span></span> <span data-ttu-id="f96db-128">以下任一運算式均有效：</span><span class="sxs-lookup"><span data-stu-id="f96db-128">Any of these expressions are valid:</span></span>

 [!code-csharp[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 <span data-ttu-id="f96db-129">下列 `GenericList<T>` 類別的範例示範如何在泛型類別中使用 `default(T)` 運算子。</span><span class="sxs-lookup"><span data-stu-id="f96db-129">The following example from the `GenericList<T>` class shows how to use the `default(T)` operator in a generic class.</span></span> <span data-ttu-id="f96db-130">如需詳細資訊，請參閱[泛型簡介](../generics/introduction-to-generics.md)。</span><span class="sxs-lookup"><span data-stu-id="f96db-130">For more information, see [Introduction to Generics](../generics/introduction-to-generics.md).</span></span>

 [!code-csharp[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]

## <a name="default-literal-and-type-inference"></a><span data-ttu-id="f96db-131">預設常值和型別推斷</span><span class="sxs-lookup"><span data-stu-id="f96db-131">default literal and type inference</span></span>

<span data-ttu-id="f96db-132">從 C# 7.1 開始，可以在編譯器能推斷運算式型別時，將 `default` 用於預設值運算式。</span><span class="sxs-lookup"><span data-stu-id="f96db-132">Beginning with C# 7.1, the `default` literal can be used for default value expressions when the compiler can infer the type of the expression.</span></span> <span data-ttu-id="f96db-133">`default` 常值會產生與對等 `default(T)` 相同的值，其中 `T` 是推斷出來的型別。</span><span class="sxs-lookup"><span data-stu-id="f96db-133">The `default` literal produces the same value as the equivalent `default(T)` where `T` is the inferred type.</span></span> <span data-ttu-id="f96db-134">這樣能夠減少宣告型別一次以上所產生的冗餘，讓程式碼更精簡。</span><span class="sxs-lookup"><span data-stu-id="f96db-134">This can make code more concise by reducing the redundancy of declaring a type more than once.</span></span> <span data-ttu-id="f96db-135">`default` 常值可以用在下列任一位置：</span><span class="sxs-lookup"><span data-stu-id="f96db-135">The `default` literal can be used in any of the following locations:</span></span>

- <span data-ttu-id="f96db-136">變數初始設定式</span><span class="sxs-lookup"><span data-stu-id="f96db-136">variable initializer</span></span>
- <span data-ttu-id="f96db-137">變數設定</span><span class="sxs-lookup"><span data-stu-id="f96db-137">variable assignment</span></span>
- <span data-ttu-id="f96db-138">宣告選用參數的預設值</span><span class="sxs-lookup"><span data-stu-id="f96db-138">declaring the default value for an optional parameter</span></span>
- <span data-ttu-id="f96db-139">提供方法呼叫引數的值</span><span class="sxs-lookup"><span data-stu-id="f96db-139">providing the value for a method call argument</span></span>
- <span data-ttu-id="f96db-140">傳回陳述式 (或運算式主體成員中的運算式)</span><span class="sxs-lookup"><span data-stu-id="f96db-140">return statement (or expression in an expression bodied member)</span></span>

<span data-ttu-id="f96db-141">下列範例示範 `default` 常值在預設值運算式中的多種使用方式：</span><span class="sxs-lookup"><span data-stu-id="f96db-141">The following example shows many usages of the `default` literal in a default value expression:</span></span>

[!code-csharp[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]

## <a name="see-also"></a><span data-ttu-id="f96db-142">請參閱</span><span class="sxs-lookup"><span data-stu-id="f96db-142">See Also</span></span>

- <xref:System.Collections.Generic>  
- [<span data-ttu-id="f96db-143">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f96db-143">C# Programming Guide</span></span>](../index.md)  
- [<span data-ttu-id="f96db-144">泛型 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="f96db-144">Generics (C# Programming Guide)</span></span>](../generics/index.md)  
- [<span data-ttu-id="f96db-145">泛型方法</span><span class="sxs-lookup"><span data-stu-id="f96db-145">Generic Methods</span></span>](../generics/generic-methods.md)  
- [<span data-ttu-id="f96db-146">.NET 的泛型</span><span class="sxs-lookup"><span data-stu-id="f96db-146">Generics in .NET</span></span>](~/docs/standard/generics/index.md)  
- [<span data-ttu-id="f96db-147">預設值表</span><span class="sxs-lookup"><span data-stu-id="f96db-147">Default values table</span></span>](../../language-reference/keywords/default-values-table.md)
