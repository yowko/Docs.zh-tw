---
title: DebugView 屬性 (C#) 所使用的語法
description: 描述 DebugView 屬性用來產生運算式樹狀架構之字串呈現的特殊語法
author: zspitz
ms.author: wiwagn
ms.date: 05/22/2019
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: ba695fc808108c49a4eee3c70a305b24c91769d8
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661720"
---
# <a name="debugview-syntax"></a><span data-ttu-id="da6e2-103">`DebugView` 語法</span><span class="sxs-lookup"><span data-stu-id="da6e2-103">`DebugView` syntax</span></span>

<span data-ttu-id="da6e2-104">`DebugView` 屬性 (僅於偵錯時提供使用) 能提供運算式樹狀架構的字串呈現。</span><span class="sxs-lookup"><span data-stu-id="da6e2-104">The `DebugView` property (available only when debugging) provides a string rendering of expression trees.</span></span> <span data-ttu-id="da6e2-105">此語法大部分皆相當容易了解；其特殊案例已於下列各節中描述。</span><span class="sxs-lookup"><span data-stu-id="da6e2-105">Most of the syntax is fairly straightforward to understand; the special cases are described in the following sections.</span></span>

<span data-ttu-id="da6e2-106">每個範例後面都會有區塊註解，其中包含 `DebugView`。</span><span class="sxs-lookup"><span data-stu-id="da6e2-106">Each example is followed by a block comment, containing the `DebugView`.</span></span>

## <a name="parameterexpression"></a><span data-ttu-id="da6e2-107">ParameterExpression</span><span class="sxs-lookup"><span data-stu-id="da6e2-107">ParameterExpression</span></span>

<span data-ttu-id="da6e2-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> 變數名稱顯示時，其開頭會加上 `$` 符號。</span><span class="sxs-lookup"><span data-stu-id="da6e2-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> variable names are displayed with a `$` symbol at the beginning.</span></span>

<span data-ttu-id="da6e2-109">如果參數沒有名稱，會指派自動產生的名稱給它，例如 `$var1` 或 `$var2`。</span><span class="sxs-lookup"><span data-stu-id="da6e2-109">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>

### <a name="examples"></a><span data-ttu-id="da6e2-110">範例</span><span class="sxs-lookup"><span data-stu-id="da6e2-110">Examples</span></span>

```csharp
ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");
/*
    $num
*/

ParameterExpression numParam =  Expression.Parameter(typeof(int));
/*
    $var1
*/
```

## <a name="constantexpression"></a><span data-ttu-id="da6e2-111">ConstantExpression</span><span class="sxs-lookup"><span data-stu-id="da6e2-111">ConstantExpression</span></span>

<span data-ttu-id="da6e2-112">對於代表整數值、字串和 `null` 的 <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> 物件，會顯示常數的值。</span><span class="sxs-lookup"><span data-stu-id="da6e2-112">For <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>

<span data-ttu-id="da6e2-113">對於具有標準尾碼為 C# 常值的數值類型，尾碼會新增至值。</span><span class="sxs-lookup"><span data-stu-id="da6e2-113">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="da6e2-114">下表顯示各種不同之數值類型的相關聯尾碼。</span><span class="sxs-lookup"><span data-stu-id="da6e2-114">The following table shows the suffixes associated with various numeric types.</span></span>

| <span data-ttu-id="da6e2-115">類型</span><span class="sxs-lookup"><span data-stu-id="da6e2-115">Type</span></span> | <span data-ttu-id="da6e2-116">關鍵字</span><span class="sxs-lookup"><span data-stu-id="da6e2-116">Keyword</span></span> | <span data-ttu-id="da6e2-117">尾碼</span><span class="sxs-lookup"><span data-stu-id="da6e2-117">Suffix</span></span> |
|--|--|--|
| <xref:System.UInt32?displayProperty=nameWithType> | [<span data-ttu-id="da6e2-118">uint</span><span class="sxs-lookup"><span data-stu-id="da6e2-118">uint</span></span>](../../../language-reference/builtin-types/integral-numeric-types.md) | <span data-ttu-id="da6e2-119">U</span><span class="sxs-lookup"><span data-stu-id="da6e2-119">U</span></span> |
| <xref:System.Int64?displayProperty=nameWithType> | [<span data-ttu-id="da6e2-120">long</span><span class="sxs-lookup"><span data-stu-id="da6e2-120">long</span></span>](../../../language-reference/builtin-types/integral-numeric-types.md) | <span data-ttu-id="da6e2-121">L</span><span class="sxs-lookup"><span data-stu-id="da6e2-121">L</span></span> |
| <xref:System.UInt64?displayProperty=nameWithType> | [<span data-ttu-id="da6e2-122">ulong</span><span class="sxs-lookup"><span data-stu-id="da6e2-122">ulong</span></span>](../../../language-reference/builtin-types/integral-numeric-types.md) | <span data-ttu-id="da6e2-123">UL</span><span class="sxs-lookup"><span data-stu-id="da6e2-123">UL</span></span> |
| <xref:System.Double?displayProperty=nameWithType> | [<span data-ttu-id="da6e2-124">double</span><span class="sxs-lookup"><span data-stu-id="da6e2-124">double</span></span>](../../../language-reference/builtin-types/floating-point-numeric-types.md) | <span data-ttu-id="da6e2-125">D</span><span class="sxs-lookup"><span data-stu-id="da6e2-125">D</span></span> |
| <xref:System.Single?displayProperty=nameWithType> | [<span data-ttu-id="da6e2-126">float</span><span class="sxs-lookup"><span data-stu-id="da6e2-126">float</span></span>](../../../language-reference/builtin-types/floating-point-numeric-types.md) | <span data-ttu-id="da6e2-127">F</span><span class="sxs-lookup"><span data-stu-id="da6e2-127">F</span></span> |
| <xref:System.Decimal?displayProperty=nameWithType> | [<span data-ttu-id="da6e2-128">decimal</span><span class="sxs-lookup"><span data-stu-id="da6e2-128">decimal</span></span>](../../../language-reference/builtin-types/floating-point-numeric-types.md) | <span data-ttu-id="da6e2-129">M</span><span class="sxs-lookup"><span data-stu-id="da6e2-129">M</span></span> |

### <a name="examples"></a><span data-ttu-id="da6e2-130">範例</span><span class="sxs-lookup"><span data-stu-id="da6e2-130">Examples</span></span>

```csharp
int num = 10;
ConstantExpression expr = Expression.Constant(num);
/*
    10
*/

double num = 10;
ConstantExpression expr = Expression.Constant(num);
/*
    10D
*/
```

## <a name="blockexpression"></a><span data-ttu-id="da6e2-131">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="da6e2-131">BlockExpression</span></span>

<span data-ttu-id="da6e2-132">如果 <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> 物件的類型與區塊中最後一個運算式的類型不同，該類型會顯示於角括弧 (`<` 和 `>`) 之內。</span><span class="sxs-lookup"><span data-stu-id="da6e2-132">If the type of a <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> object differs from the type of the last expression in the block, the type is displayed within angle brackets (`<` and `>`).</span></span> <span data-ttu-id="da6e2-133">否則，不會顯示 <xref:System.Linq.Expressions.BlockExpression> 物件的類型。</span><span class="sxs-lookup"><span data-stu-id="da6e2-133">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="da6e2-134">範例</span><span class="sxs-lookup"><span data-stu-id="da6e2-134">Examples</span></span>

```csharp
BlockExpression block = Expression.Block(Expression.Constant("test"));
/*
    .Block() {
        "test"
    }
*/

BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));
/*
    .Block<System.Object>() {
        "test"
    }
*/
```

## <a name="lambdaexpression"></a><span data-ttu-id="da6e2-135">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="da6e2-135">LambdaExpression</span></span>

<span data-ttu-id="da6e2-136"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> 物件會與其委派類型一起顯示。</span><span class="sxs-lookup"><span data-stu-id="da6e2-136"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> objects are displayed together with their delegate types.</span></span>

<span data-ttu-id="da6e2-137">如果 Lambda 運算式沒有名稱，會指派自動產生的名稱給它，例如 `#Lambda1` 或 `#Lambda2`。</span><span class="sxs-lookup"><span data-stu-id="da6e2-137">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>

### <a name="examples"></a><span data-ttu-id="da6e2-138">範例</span><span class="sxs-lookup"><span data-stu-id="da6e2-138">Examples</span></span>

```csharp
LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));
/*
    .Lambda #Lambda1<System.Func'1[System.Int32]>() {
        1
    }
*/

LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);
/*
    .Lambda #SampleLambda<System.Func'1[System.Int32]>() {
        1
    }
*/
```

## <a name="labelexpression"></a><span data-ttu-id="da6e2-139">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="da6e2-139">LabelExpression</span></span>

<span data-ttu-id="da6e2-140">如果您指定 <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> 物件的預設值，這個值會顯示在 <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> 物件之前。</span><span class="sxs-lookup"><span data-stu-id="da6e2-140">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> object.</span></span>

<span data-ttu-id="da6e2-141">`.Label` 語彙基元表示標籤的開頭。</span><span class="sxs-lookup"><span data-stu-id="da6e2-141">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="da6e2-142">`.LabelTarget` 語彙基元表示要跳至的目標目的地。</span><span class="sxs-lookup"><span data-stu-id="da6e2-142">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>

<span data-ttu-id="da6e2-143">如果標籤沒有名稱，會指派自動產生的名稱給它，例如 `#Label1` 或 `#Label2`。</span><span class="sxs-lookup"><span data-stu-id="da6e2-143">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>

### <a name="examples"></a><span data-ttu-id="da6e2-144">範例</span><span class="sxs-lookup"><span data-stu-id="da6e2-144">Examples</span></span>

```csharp
LabelTarget target = Expression.Label(typeof(int), "SampleLabel");
BlockExpression block = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1))
);
/*
    .Block() {
        .Goto SampleLabel { 0 };
        .Label
            -1
        .LabelTarget SampleLabel:
    }
*/

LabelTarget target = Expression.Label();
BlockExpression block = Expression.Block(
    Expression.Goto(target),
    Expression.Label(target)
);
/*
    .Block() {
        .Goto #Label1 { };
        .Label
        .LabelTarget #Label1:
    }
*/
```

## <a name="checked-operators"></a><span data-ttu-id="da6e2-145">檢查的運算子</span><span class="sxs-lookup"><span data-stu-id="da6e2-145">Checked Operators</span></span>

<span data-ttu-id="da6e2-146">顯示檢查的運算子時，運算子前面會有 `#` 符號。</span><span class="sxs-lookup"><span data-stu-id="da6e2-146">Checked operators are displayed with the `#` symbol in front of the operator.</span></span> <span data-ttu-id="da6e2-147">例如，已檢查的加法運算子會顯示為 `#+`。</span><span class="sxs-lookup"><span data-stu-id="da6e2-147">For example, the checked addition operator is displayed as `#+`.</span></span>

### <a name="examples"></a><span data-ttu-id="da6e2-148">範例</span><span class="sxs-lookup"><span data-stu-id="da6e2-148">Examples</span></span>

```csharp
Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));
/*
    1 #+ 2
*/

Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));
/*
    #(System.Int32)10D
*/
```
