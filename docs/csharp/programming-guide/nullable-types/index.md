---
title: 可為 null 的C#實數值型別-程式設計指南
ms.custom: seodec18
description: 瞭解C#可為 null 的實值型別，以及如何使用它們
ms.date: 09/26/2019
helpviewer_keywords:
- nullable value types [C#]
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
ms.openlocfilehash: b8b52e7fb34adf65d5c76d59811ea6dd0ab16a98
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71396214"
---
# <a name="nullable-value-types-c-programming-guide"></a><span data-ttu-id="29c77-103">可為 null 的C#實數值型別（程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="29c77-103">Nullable value types (C# Programming Guide)</span></span>

<span data-ttu-id="29c77-104">可為 null 的實數值型別是 <xref:System.Nullable%601?displayProperty=nameWithType> 結構的實例。</span><span class="sxs-lookup"><span data-stu-id="29c77-104">Nullable value types are instances of the <xref:System.Nullable%601?displayProperty=nameWithType> structure.</span></span> <span data-ttu-id="29c77-105">可為 null 的實數值型別可以代表基礎類型的所有值，`T`，以及額外的[null](../../language-reference/keywords/null.md)值。</span><span class="sxs-lookup"><span data-stu-id="29c77-105">Nullable value types can represent all the values of an underlying type `T`, and an additional [null](../../language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="29c77-106">基礎類型 `T` 可以是任何不可為 Null 的[實值型別](../../language-reference/keywords/value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="29c77-106">The underlying type `T` can be any non-nullable [value type](../../language-reference/keywords/value-types.md).</span></span> <span data-ttu-id="29c77-107">`T` 不可為參考型別。</span><span class="sxs-lookup"><span data-stu-id="29c77-107">`T` cannot be a reference type.</span></span>

> [!NOTE]
> <span data-ttu-id="29c77-108">C#8.0 引進了可為 null 的參考型別功能。</span><span class="sxs-lookup"><span data-stu-id="29c77-108">C# 8.0 introduces the nullable reference types feature.</span></span> <span data-ttu-id="29c77-109">如需詳細資訊，請參閱[可為 null 的參考型別](../../nullable-references.md)。</span><span class="sxs-lookup"><span data-stu-id="29c77-109">For more information, see [Nullable reference types](../../nullable-references.md).</span></span> <span data-ttu-id="29c77-110">從C# 2 開始可以使用可為 null 的實數值型別。</span><span class="sxs-lookup"><span data-stu-id="29c77-110">The nullable value types are available starting with C# 2.</span></span>

<span data-ttu-id="29c77-111">例如，您可以指派 `null` 或介於 <xref:System.Int32.MinValue?displayProperty=nameWithType> 到 <xref:System.Int32.MaxValue?displayProperty=nameWithType> 的任何整數值給 `Nullable<int>`，以及指派 [true](../../language-reference/keywords/true-literal.md)、[false](../../language-reference/keywords/false-literal.md) 或 `null` 給 `Nullable<bool>`。</span><span class="sxs-lookup"><span data-stu-id="29c77-111">For example, you can assign `null` or any integer value from <xref:System.Int32.MinValue?displayProperty=nameWithType> to <xref:System.Int32.MaxValue?displayProperty=nameWithType> to a `Nullable<int>` and [true](../../language-reference/keywords/true-literal.md), [false](../../language-reference/keywords/false-literal.md), or `null` to a `Nullable<bool>`.</span></span>

<span data-ttu-id="29c77-112">當您需要表示基礎類型的未定義值時，您可以使用可為 null 的實數值型別。</span><span class="sxs-lookup"><span data-stu-id="29c77-112">You use a nullable value type when you need to represent the undefined value of an underlying type.</span></span> <span data-ttu-id="29c77-113">布林變數只能有兩個值： `true` 和 `false`。</span><span class="sxs-lookup"><span data-stu-id="29c77-113">A Boolean variable can have only two values: `true` and `false`.</span></span> <span data-ttu-id="29c77-114">但不會有任何「未定義」的值。</span><span class="sxs-lookup"><span data-stu-id="29c77-114">There is no "undefined" value.</span></span> <span data-ttu-id="29c77-115">在許多程式設計應用程式最值得注意的資料庫互動中，可能未定義或缺少變數值。</span><span class="sxs-lookup"><span data-stu-id="29c77-115">In many programming applications, most notably database interactions, a variable value can be undefined or missing.</span></span> <span data-ttu-id="29c77-116">例如，資料庫中的欄位可能包含 true 或 false 兩種值，但也可能完全不包含任何值。</span><span class="sxs-lookup"><span data-stu-id="29c77-116">For example, a field in a database may contain the values true or false, or it may contain no value at all.</span></span> <span data-ttu-id="29c77-117">在此情況下，可使用 `Nullable<bool>` 類型。</span><span class="sxs-lookup"><span data-stu-id="29c77-117">You use a `Nullable<bool>` type in that case.</span></span>

<span data-ttu-id="29c77-118">可為 null 的實數值型別具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="29c77-118">Nullable value types have the following characteristics:</span></span>

- <span data-ttu-id="29c77-119">可為 null 的實數值型別代表可以指派給 `null` 值的實數值型別變數。</span><span class="sxs-lookup"><span data-stu-id="29c77-119">Nullable value types represent value-type variables that can be assigned the `null` value.</span></span>

- <span data-ttu-id="29c77-120">語法 `T?`是 `Nullable<T>` 的略寫。</span><span class="sxs-lookup"><span data-stu-id="29c77-120">The syntax `T?` is shorthand for `Nullable<T>`.</span></span> <span data-ttu-id="29c77-121">這兩種格式是可互換的。</span><span class="sxs-lookup"><span data-stu-id="29c77-121">The two forms are interchangeable.</span></span>

- <span data-ttu-id="29c77-122">將值指派給可為 null 的實值型別，就像您在基礎實值型別中所做的一樣： `int? x = 10;` 或 `double? d = 4.108;`。</span><span class="sxs-lookup"><span data-stu-id="29c77-122">Assign a value to a nullable value type just as you would for an underlying value type: `int? x = 10;` or `double? d = 4.108;`.</span></span> <span data-ttu-id="29c77-123">您也可以指派 `null` 值：`int? x = null;`。</span><span class="sxs-lookup"><span data-stu-id="29c77-123">You also can assign the `null` value: `int? x = null;`.</span></span>

- <span data-ttu-id="29c77-124">使用 <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> 和 <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> 唯讀屬性可測試是否有 Null，並擷取該值，如下列範例所示：`if (x.HasValue) y = x.Value;`</span><span class="sxs-lookup"><span data-stu-id="29c77-124">Use the <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> and <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> readonly properties to test for null and retrieve the value, as shown in the following example: `if (x.HasValue) y = x.Value;`</span></span>

  - <span data-ttu-id="29c77-125">如果變數包含值，<xref:System.Nullable%601.HasValue%2A> 屬性會傳回 `true`，若為 `null`，則傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="29c77-125">The <xref:System.Nullable%601.HasValue%2A> property returns `true` if the variable contains a value, or `false` if it's `null`.</span></span>

  - <span data-ttu-id="29c77-126">若 <xref:System.Nullable%601.HasValue%2A> 傳回 `true`，<xref:System.Nullable%601.Value%2A> 屬性會傳回值。</span><span class="sxs-lookup"><span data-stu-id="29c77-126">The <xref:System.Nullable%601.Value%2A> property returns a value if <xref:System.Nullable%601.HasValue%2A> returns `true`.</span></span> <span data-ttu-id="29c77-127">否則會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="29c77-127">Otherwise, an <xref:System.InvalidOperationException> is thrown.</span></span>

- <span data-ttu-id="29c77-128">您也可以使用具有 null 實數值型別的 `==` 和 `!=` 運算子，如下列範例所示： `if (x != null) y = x.Value;`。</span><span class="sxs-lookup"><span data-stu-id="29c77-128">You can also use the `==` and `!=` operators with a nullable value type, as shown in the following example: `if (x != null) y = x.Value;`.</span></span> <span data-ttu-id="29c77-129">如果 `a` 和 `b` 都是 Null，`a == b` 會評估為 `true`。</span><span class="sxs-lookup"><span data-stu-id="29c77-129">If `a` and `b` are both null, `a == b` evaluates to `true`.</span></span>

- <span data-ttu-id="29c77-130">從 C# 7.0 開始，您就可以使用[模式比對](../../pattern-matching.md#the-is-type-pattern-expression)檢查及取得可為 Null 型別的值：`if (x is int valueOfX) y = valueOfX;`。</span><span class="sxs-lookup"><span data-stu-id="29c77-130">Beginning with C# 7.0, you can use [pattern matching](../../pattern-matching.md#the-is-type-pattern-expression) to both examine and get a value of a nullable type: `if (x is int valueOfX) y = valueOfX;`.</span></span>

- <span data-ttu-id="29c77-131">`T?` 的預設值為 <xref:System.Nullable%601.HasValue%2A> 屬性傳回 `false` 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="29c77-131">The default value of `T?` is an instance whose <xref:System.Nullable%601.HasValue%2A> property returns `false`.</span></span>

- <span data-ttu-id="29c77-132">使用 <xref:System.Nullable%601.GetValueOrDefault> 方法可傳回指派的值，如果可為 Null 的型別值為 `null`，則傳回基礎實值型別的[預設](../../language-reference/keywords/default-values-table.md)值。</span><span class="sxs-lookup"><span data-stu-id="29c77-132">Use the <xref:System.Nullable%601.GetValueOrDefault> method to return either the assigned value, or the [default](../../language-reference/keywords/default-values-table.md) value of the underlying value type if the value of the nullable type is `null`.</span></span>

- <span data-ttu-id="29c77-133">使用 <xref:System.Nullable%601.GetValueOrDefault(%600)> 方法可傳回指派的值，如果可為 Null 的型別值為 `null`，則傳回提供的預設值。</span><span class="sxs-lookup"><span data-stu-id="29c77-133">Use the <xref:System.Nullable%601.GetValueOrDefault(%600)> method to return either the assigned value, or the provided default value if the value of the nullable type is `null`.</span></span>

- <span data-ttu-id="29c77-134">使用[null 聯合運算子](../../language-reference/operators/null-coalescing-operator.md)`??`，根據可為 null 的類型值，將值指派給基礎數值型別的變數： `int? x = null; int y = x ?? -1;`。</span><span class="sxs-lookup"><span data-stu-id="29c77-134">Use the [null-coalescing operator](../../language-reference/operators/null-coalescing-operator.md), `??`, to assign a value to a variable of an underlying value type based on a nullable-type value: `int? x = null; int y = x ?? -1;`.</span></span> <span data-ttu-id="29c77-135">在此範例中，由於 `x` 是 `null`，因此 `y` 的結果值會 `-1`。</span><span class="sxs-lookup"><span data-stu-id="29c77-135">In the example, since `x` is `null`, the result value of `y` is `-1`.</span></span>

- <span data-ttu-id="29c77-136">如果在兩個實數值型別之間定義使用者定義的轉換，則相同的轉換也可以搭配對應的可為 null 類型使用。</span><span class="sxs-lookup"><span data-stu-id="29c77-136">If a user-defined conversion is defined between two value types, the same conversion can also be used with the corresponding nullable types.</span></span>

- <span data-ttu-id="29c77-137">不允許嵌套的可為 null 的實數值型別。</span><span class="sxs-lookup"><span data-stu-id="29c77-137">Nested nullable value types are not allowed.</span></span> <span data-ttu-id="29c77-138">系統不會編譯下列這一行：`Nullable<Nullable<int>> n;`</span><span class="sxs-lookup"><span data-stu-id="29c77-138">The following line doesn't compile: `Nullable<Nullable<int>> n;`</span></span>

<span data-ttu-id="29c77-139">如需詳細資訊，請參閱[使用可為 null 的實數值型別](using-nullable-types.md)和[如何：識別可為 null 的實數值型別](how-to-identify-a-nullable-type.md)主題。</span><span class="sxs-lookup"><span data-stu-id="29c77-139">For more information, see the [Using nullable value types](using-nullable-types.md) and [How to: identify a nullable value type](how-to-identify-a-nullable-type.md) topics.</span></span>

## <a name="see-also"></a><span data-ttu-id="29c77-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29c77-140">See also</span></span>

- [<span data-ttu-id="29c77-141">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="29c77-141">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="29c77-142">??運算子</span><span class="sxs-lookup"><span data-stu-id="29c77-142">?? Operator</span></span>](../../language-reference/operators/null-coalescing-operator.md)
- [<span data-ttu-id="29c77-143">可為 Null 的實值型別 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29c77-143">Nullable Value Types (Visual Basic)</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
