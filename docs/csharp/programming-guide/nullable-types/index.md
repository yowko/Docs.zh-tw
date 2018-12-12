---
title: 可為 Null 的型別 - C# 程式設計指南
ms.custom: seodec18
description: 深入了解 C# 可為 Null 的型別和其使用方式
ms.date: 07/30/2018
helpviewer_keywords:
- nullable types [C#]
- C# language, nullable types
- types [C#], nullable
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
ms.openlocfilehash: cd5ac40ca73f7c528a903d5863f3cf5880738f11
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245119"
---
# <a name="nullable-types-c-programming-guide"></a><span data-ttu-id="a90a4-103">可為 Null 的型別 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="a90a4-103">Nullable types (C# Programming Guide)</span></span>

<span data-ttu-id="a90a4-104">可為 Null 的型別是 <xref:System.Nullable%601?displayProperty=nameWithType> 結構的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a90a4-104">Nullable types are instances of the <xref:System.Nullable%601?displayProperty=nameWithType> struct.</span></span> <span data-ttu-id="a90a4-105">可為 Null 的型別能代表基礎類型 `T` 的所有值，以及額外的 [null](../../language-reference/keywords/null.md) 值。</span><span class="sxs-lookup"><span data-stu-id="a90a4-105">Nullable types can represent all the values of an underlying type `T`, and an additional [null](../../language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="a90a4-106">基礎類型 `T` 可以是任何不可為 Null 的[實值型別](../../language-reference/keywords/value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="a90a4-106">The underlying type `T` can be any non-nullable [value type](../../language-reference/keywords/value-types.md).</span></span> <span data-ttu-id="a90a4-107">`T` 不可為參考型別。</span><span class="sxs-lookup"><span data-stu-id="a90a4-107">`T` cannot be a reference type.</span></span>

<span data-ttu-id="a90a4-108">例如，您可以指派 `null` 或介於 <xref:System.Int32.MinValue?displayProperty=nameWithType> 到 <xref:System.Int32.MaxValue?displayProperty=nameWithType> 的任何整數值給 `Nullable<int>`，以及指派 [true](../../language-reference/keywords/true-literal.md)、[false](../../language-reference/keywords/false-literal.md) 或 `null` 給 `Nullable<bool>`。</span><span class="sxs-lookup"><span data-stu-id="a90a4-108">For example, you can assign `null` or any integer value from <xref:System.Int32.MinValue?displayProperty=nameWithType> to <xref:System.Int32.MaxValue?displayProperty=nameWithType> to a `Nullable<int>` and [true](../../language-reference/keywords/true-literal.md), [false](../../language-reference/keywords/false-literal.md), or `null` to a `Nullable<bool>`.</span></span>

<span data-ttu-id="a90a4-109">當您需要表示基礎類型的未定義值時，可使用可為 Null 的型別。</span><span class="sxs-lookup"><span data-stu-id="a90a4-109">You use a nullable type when you need to represent the undefined value of an underlying type.</span></span> <span data-ttu-id="a90a4-110">布林值變數只可有兩個值：true 和 false。</span><span class="sxs-lookup"><span data-stu-id="a90a4-110">A Boolean variable can have only two values: true and false.</span></span> <span data-ttu-id="a90a4-111">但不會有任何「未定義」的值。</span><span class="sxs-lookup"><span data-stu-id="a90a4-111">There is no "undefined" value.</span></span> <span data-ttu-id="a90a4-112">在許多程式設計應用程式最值得注意的資料庫互動中，可能未定義或缺少變數值。</span><span class="sxs-lookup"><span data-stu-id="a90a4-112">In many programming applications, most notably database interactions, a variable value can be undefined or missing.</span></span> <span data-ttu-id="a90a4-113">例如，資料庫中的欄位可能包含 true 或 false 兩種值，但也可能完全不包含任何值。</span><span class="sxs-lookup"><span data-stu-id="a90a4-113">For example, a field in a database may contain the values true or false, or it may contain no value at all.</span></span> <span data-ttu-id="a90a4-114">在此情況下，可使用 `Nullable<bool>` 類型。</span><span class="sxs-lookup"><span data-stu-id="a90a4-114">You use a `Nullable<bool>` type in that case.</span></span>

<span data-ttu-id="a90a4-115">可為 Null 的型別特色如下：</span><span class="sxs-lookup"><span data-stu-id="a90a4-115">Nullable types have the following characteristics:</span></span>
  
- <span data-ttu-id="a90a4-116">可為 Null 的型別代表可指派 `null` 值的實值型別變數。</span><span class="sxs-lookup"><span data-stu-id="a90a4-116">Nullable types represent value-type variables that can be assigned the `null` value.</span></span> <span data-ttu-id="a90a4-117">您無法根據參考型別建立可為 Null 的型別。</span><span class="sxs-lookup"><span data-stu-id="a90a4-117">You cannot create a nullable type based on a reference type.</span></span> <span data-ttu-id="a90a4-118">(參考型別已經支援 `null` 值)。</span><span class="sxs-lookup"><span data-stu-id="a90a4-118">(Reference types already support the `null` value.)</span></span>  
  
- <span data-ttu-id="a90a4-119">語法 `T?`是 `Nullable<T>` 的略寫。</span><span class="sxs-lookup"><span data-stu-id="a90a4-119">The syntax `T?` is shorthand for `Nullable<T>`.</span></span> <span data-ttu-id="a90a4-120">這兩種格式是可互換的。</span><span class="sxs-lookup"><span data-stu-id="a90a4-120">The two forms are interchangeable.</span></span>  
  
- <span data-ttu-id="a90a4-121">將值指派給可為 Null 的型別，就像您指派值給基礎實值型別一樣：`int? x = 10;` 或 `double? d = 4.108;`。</span><span class="sxs-lookup"><span data-stu-id="a90a4-121">Assign a value to a nullable type just as you would for an underlying value type: `int? x = 10;` or `double? d = 4.108;`.</span></span> <span data-ttu-id="a90a4-122">您也可以指派 `null` 值：`int? x = null;`。</span><span class="sxs-lookup"><span data-stu-id="a90a4-122">You also can assign the `null` value: `int? x = null;`.</span></span>  
  
- <span data-ttu-id="a90a4-123">使用 <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> 和 <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> 唯讀屬性可測試是否有 Null，並擷取該值，如下列範例所示：`if (x.HasValue) y = x.Value;`</span><span class="sxs-lookup"><span data-stu-id="a90a4-123">Use the <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> and <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> readonly properties to test for null and retrieve the value, as shown in the following example: `if (x.HasValue) y = x.Value;`</span></span>  
  
  - <span data-ttu-id="a90a4-124">如果變數包含值，<xref:System.Nullable%601.HasValue%2A> 屬性會傳回 `true`，若為 `null`，則傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="a90a4-124">The <xref:System.Nullable%601.HasValue%2A> property returns `true` if the variable contains a value, or `false` if it's `null`.</span></span>
  
  - <span data-ttu-id="a90a4-125">若 <xref:System.Nullable%601.HasValue%2A> 傳回 `true`，<xref:System.Nullable%601.Value%2A> 屬性會傳回值。</span><span class="sxs-lookup"><span data-stu-id="a90a4-125">The <xref:System.Nullable%601.Value%2A> property returns a value if <xref:System.Nullable%601.HasValue%2A> returns `true`.</span></span> <span data-ttu-id="a90a4-126">否則會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="a90a4-126">Otherwise, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
- <span data-ttu-id="a90a4-127">您也可以使用 `==` 和 `!=` 運算子搭配可為 Null 的型別，如下列範例所示︰`if (x != null) y = x.Value;`。</span><span class="sxs-lookup"><span data-stu-id="a90a4-127">You can also use the `==` and `!=` operators with a nullable type, as shown in the following example: `if (x != null) y = x.Value;`.</span></span> <span data-ttu-id="a90a4-128">如果 `a` 和 `b` 都是 Null，`a == b` 會評估為 `true`。</span><span class="sxs-lookup"><span data-stu-id="a90a4-128">If `a` and `b` are both null, `a == b` evaluates to `true`.</span></span>  

- <span data-ttu-id="a90a4-129">從 C# 7.0 開始，您就可以使用[模式比對](../../pattern-matching.md#the-is-type-pattern-expression)檢查及取得可為 Null 型別的值：`if (x is int valueOfX) y = valueOfX;`。</span><span class="sxs-lookup"><span data-stu-id="a90a4-129">Beginning with C# 7.0, you can use [pattern matching](../../pattern-matching.md#the-is-type-pattern-expression) to both examine and get a value of a nullable type: `if (x is int valueOfX) y = valueOfX;`.</span></span>
  
- <span data-ttu-id="a90a4-130">`T?` 的預設值為 <xref:System.Nullable%601.HasValue%2A> 屬性傳回 `false` 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a90a4-130">The default value of `T?` is an instance whose <xref:System.Nullable%601.HasValue%2A> property returns `false`.</span></span>  

- <span data-ttu-id="a90a4-131">使用 <xref:System.Nullable%601.GetValueOrDefault> 方法可傳回指派的值，如果可為 Null 的型別值為 `null`，則傳回基礎實值型別的[預設](../../language-reference/keywords/default-values-table.md)值。</span><span class="sxs-lookup"><span data-stu-id="a90a4-131">Use the <xref:System.Nullable%601.GetValueOrDefault> method to return either the assigned value, or the [default](../../language-reference/keywords/default-values-table.md) value of the underlying value type if the value of the nullable type is `null`.</span></span>  

- <span data-ttu-id="a90a4-132">使用 <xref:System.Nullable%601.GetValueOrDefault(%600)> 方法可傳回指派的值，如果可為 Null 的型別值為 `null`，則傳回提供的預設值。</span><span class="sxs-lookup"><span data-stu-id="a90a4-132">Use the <xref:System.Nullable%601.GetValueOrDefault(%600)> method to return either the assigned value, or the provided default value if the value of the nullable type is `null`.</span></span>
  
- <span data-ttu-id="a90a4-133">使用[聯合 Null 的運算子](../../language-reference/operators/null-coalescing-operator.md) `??`可將值指派給以可為 Null 之型別值為基礎的基礎類型：`int? x = null; int y = x ?? -1;`。</span><span class="sxs-lookup"><span data-stu-id="a90a4-133">Use the [null-coalescing operator](../../language-reference/operators/null-coalescing-operator.md), `??`, to assign a value to an underlying type based on a value of the nullable type: `int? x = null; int y = x ?? -1;`.</span></span> <span data-ttu-id="a90a4-134">在範例中，因為 `x` 是 Null，所以結果值 `y` 是 `-1`。</span><span class="sxs-lookup"><span data-stu-id="a90a4-134">In the example, since `x` is null, the result value of `y` is `-1`.</span></span>

- <span data-ttu-id="a90a4-135">如果在兩種資料類別之間定義使用者定義轉換，則這些資料類型的可為 Null 版本也可使用相同的轉換。</span><span class="sxs-lookup"><span data-stu-id="a90a4-135">If a user-defined conversion is defined between two data types, the same conversion can also be used with the nullable versions of these data types.</span></span>
  
- <span data-ttu-id="a90a4-136">不允許巢狀可為 Null 的型別。</span><span class="sxs-lookup"><span data-stu-id="a90a4-136">Nested nullable types are not allowed.</span></span> <span data-ttu-id="a90a4-137">系統不會編譯下列這一行：`Nullable<Nullable<int>> n;`</span><span class="sxs-lookup"><span data-stu-id="a90a4-137">The following line doesn't compile: `Nullable<Nullable<int>> n;`</span></span>  

<span data-ttu-id="a90a4-138">如需詳細資訊，請參閱[可為 Null 的型別](using-nullable-types.md)與[如何：識別可為 Null 的型別](how-to-identify-a-nullable-type.md)主題。</span><span class="sxs-lookup"><span data-stu-id="a90a4-138">For more information, see the [Using nullable types](using-nullable-types.md) and [How to: Identify a nullable type](how-to-identify-a-nullable-type.md) topics.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a90a4-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a90a4-139">See Also</span></span>

- <xref:System.Nullable%601?displayProperty=nameWithType>  
- <xref:System.Nullable?displayProperty=nameWithType>  
- [<span data-ttu-id="a90a4-140">??運算子</span><span class="sxs-lookup"><span data-stu-id="a90a4-140">?? Operator</span></span>](../../language-reference/operators/null-coalescing-operator.md)  
- [<span data-ttu-id="a90a4-141">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="a90a4-141">C# Programming Guide</span></span>](../index.md)  
- [<span data-ttu-id="a90a4-142">C# 指南</span><span class="sxs-lookup"><span data-stu-id="a90a4-142">C# Guide</span></span>](../../index.md)  
- [<span data-ttu-id="a90a4-143">C# 參考</span><span class="sxs-lookup"><span data-stu-id="a90a4-143">C# Reference</span></span>](../../language-reference/index.md)  
- [<span data-ttu-id="a90a4-144">可為 Null 的實值型別 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a90a4-144">Nullable Value Types (Visual Basic)</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
