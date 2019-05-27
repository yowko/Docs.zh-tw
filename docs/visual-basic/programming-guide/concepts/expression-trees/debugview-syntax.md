---
title: 使用 DebugView 屬性 (Visual Basic) 的語法
description: 描述用來產生運算式樹狀架構的字串表示 DebugView 屬性的特殊語法
author: zspitz
ms.author: wiwagn
ms.date: 05/22/2019
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: 1b2a1164f02208cc7578820d8f8ed3bc145fb5b8
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2019
ms.locfileid: "66196528"
---
# <a name="debugview-syntax"></a><span data-ttu-id="5051d-103">`DebugView` 語法</span><span class="sxs-lookup"><span data-stu-id="5051d-103">`DebugView` syntax</span></span> 

<span data-ttu-id="5051d-104">`DebugView`屬性 （只在偵錯時，才會提供） 所提供的運算式樹狀架構的字串呈現。</span><span class="sxs-lookup"><span data-stu-id="5051d-104">The `DebugView` property (available only when debugging) provides a string rendering of expression trees.</span></span> <span data-ttu-id="5051d-105">大部分是語法的很容易就能了解;特殊的情況下是由下列各節所述。</span><span class="sxs-lookup"><span data-stu-id="5051d-105">Most of the syntax is fairly straightforward to understand; the special cases are described in the following sections.</span></span>

<span data-ttu-id="5051d-106">每個範例後面的註解區塊包含`DebugView`。</span><span class="sxs-lookup"><span data-stu-id="5051d-106">Each example is followed by a comment block containing the `DebugView`.</span></span> 

## <a name="parameterexpression"></a><span data-ttu-id="5051d-107">ParameterExpression</span><span class="sxs-lookup"><span data-stu-id="5051d-107">ParameterExpression</span></span>

<span data-ttu-id="5051d-108">顯示 <xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> 變數名稱時，其開頭會加上 "$" 符號。</span><span class="sxs-lookup"><span data-stu-id="5051d-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> variable names are displayed with a "$" symbol at the beginning.</span></span>

<span data-ttu-id="5051d-109">如果參數沒有名稱，會指派自動產生的名稱給它，例如 `$var1` 或 `$var2`。</span><span class="sxs-lookup"><span data-stu-id="5051d-109">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>

### <a name="examples"></a><span data-ttu-id="5051d-110">範例</span><span class="sxs-lookup"><span data-stu-id="5051d-110">Examples</span></span>

```vb
Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer), "num")
'
'    $num
'

Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer))
'
'    $var1
'
```

## <a name="constantexpressions"></a><span data-ttu-id="5051d-111">ConstantExpression</span><span class="sxs-lookup"><span data-stu-id="5051d-111">ConstantExpressions</span></span>

<span data-ttu-id="5051d-112">對於代表整數值、字串和 `null` 的 <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> 物件，會顯示常數的值。</span><span class="sxs-lookup"><span data-stu-id="5051d-112">For <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>

<span data-ttu-id="5051d-113">對於某些數值類型，尾碼新增到的值：</span><span class="sxs-lookup"><span data-stu-id="5051d-113">For some numeric types, a suffix is added to the value:</span></span>

| <span data-ttu-id="5051d-114">類型</span><span class="sxs-lookup"><span data-stu-id="5051d-114">Type</span></span> | <span data-ttu-id="5051d-115">關鍵字</span><span class="sxs-lookup"><span data-stu-id="5051d-115">Keyword</span></span> | <span data-ttu-id="5051d-116">尾碼</span><span class="sxs-lookup"><span data-stu-id="5051d-116">Suffix</span></span> |  
|--|--|--|
| <xref:System.UInt32> | [<span data-ttu-id="5051d-117">UInteger</span><span class="sxs-lookup"><span data-stu-id="5051d-117">UInteger</span></span>](../../../language-reference/data-types/uinteger-data-type.md) | <span data-ttu-id="5051d-118">U</span><span class="sxs-lookup"><span data-stu-id="5051d-118">U</span></span> |
| <xref:System.Int64> | [<span data-ttu-id="5051d-119">Long</span><span class="sxs-lookup"><span data-stu-id="5051d-119">Long</span></span>](../../../language-reference/data-types/long-data-type.md) | <span data-ttu-id="5051d-120">L</span><span class="sxs-lookup"><span data-stu-id="5051d-120">L</span></span> |
| <xref:System.UInt64> | [<span data-ttu-id="5051d-121">ULong</span><span class="sxs-lookup"><span data-stu-id="5051d-121">ULong</span></span>](../../../language-reference/data-types/ulong-data-type.md) | <span data-ttu-id="5051d-122">UL</span><span class="sxs-lookup"><span data-stu-id="5051d-122">UL</span></span> |
| <xref:System.Double> | [<span data-ttu-id="5051d-123">Double</span><span class="sxs-lookup"><span data-stu-id="5051d-123">Double</span></span>](../../../language-reference/data-types/double-data-type.md) | <span data-ttu-id="5051d-124">D</span><span class="sxs-lookup"><span data-stu-id="5051d-124">D</span></span> |
| <xref:System.Single> | [<span data-ttu-id="5051d-125">Single</span><span class="sxs-lookup"><span data-stu-id="5051d-125">Single</span></span>](../../../language-reference/data-types/single-data-type.md) | <span data-ttu-id="5051d-126">F</span><span class="sxs-lookup"><span data-stu-id="5051d-126">F</span></span> | 
| <xref:System.Decimal> | [<span data-ttu-id="5051d-127">Decimal</span><span class="sxs-lookup"><span data-stu-id="5051d-127">Decimal</span></span>](../../../language-reference/data-types/decimal-data-type.md) | <span data-ttu-id="5051d-128">M</span><span class="sxs-lookup"><span data-stu-id="5051d-128">M</span></span> |

### <a name="examples"></a><span data-ttu-id="5051d-129">範例</span><span class="sxs-lookup"><span data-stu-id="5051d-129">Examples</span></span>

```vb
Dim num as Integer = 10
Dim expr As ConstantExpression = Expression.Constant(num)
'
'    10
'

Dim num As Double = 10
Dim expr As ConstantExpression = Expression.Constant(num)
'
'    10D
'
```

## <a name="blockexpression"></a><span data-ttu-id="5051d-130">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="5051d-130">BlockExpression</span></span>

<span data-ttu-id="5051d-131">如果類型<xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType>物件不同於在區塊中的最後一個運算式的類型，類型會顯示在角括弧內 (`<`和`>`)。</span><span class="sxs-lookup"><span data-stu-id="5051d-131">If the type of a <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> object differs from the type of the last expression in the block, the type is displayed within angle brackets (`<` and `>`).</span></span> <span data-ttu-id="5051d-132">否則，不會顯示 <xref:System.Linq.Expressions.BlockExpression> 物件的類型。</span><span class="sxs-lookup"><span data-stu-id="5051d-132">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="5051d-133">範例</span><span class="sxs-lookup"><span data-stu-id="5051d-133">Examples</span></span>

```vb
Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))
'
'    .Block() {
'        "test"
'    }
'

Dim block As BlockExpression = Expression.Block(
    GetType(Object), 
    Expression.Constant("test")
)
'
'    .Block<System.Object>() {
'        "test"
'    }
'
```

## <a name="lambdaexpression"></a><span data-ttu-id="5051d-134">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="5051d-134">LambdaExpression</span></span>

<span data-ttu-id="5051d-135"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> 物件會與其委派類型一起顯示。</span><span class="sxs-lookup"><span data-stu-id="5051d-135"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> objects are displayed together with their delegate types.</span></span>

<span data-ttu-id="5051d-136">如果 Lambda 運算式沒有名稱，會指派自動產生的名稱給它，例如 `#Lambda1` 或 `#Lambda2`。</span><span class="sxs-lookup"><span data-stu-id="5051d-136">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>

### <a name="examples"></a><span data-ttu-id="5051d-137">範例</span><span class="sxs-lookup"><span data-stu-id="5051d-137">Examples</span></span>

```vb
Dim lambda As LambdaExpression = Expression.Lambda(Of Func(Of Integer))(
    Expression.Constant(1)
)
'
'    .Lambda #Lambda1<System.Func'1[System.Int32]>() {
'        1
'    }
'

Dim lambda As LambdaExpression = Expression.Lambda(Of Func(Of Integer))(
    Expression.Constant(1),
    "SampleLambda",
    Nothing
)
'
'    .Lambda #SampleLambda<System.Func'1[System.Int32]>() {
'        1
'    }
'
```

## <a name="labelexpression"></a><span data-ttu-id="5051d-138">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="5051d-138">LabelExpression</span></span>

<span data-ttu-id="5051d-139">如果您指定 <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> 物件的預設值，這個值會顯示在 <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> 物件之前。</span><span class="sxs-lookup"><span data-stu-id="5051d-139">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> object.</span></span>

<span data-ttu-id="5051d-140">`.Label` 語彙基元表示標籤的開頭。</span><span class="sxs-lookup"><span data-stu-id="5051d-140">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="5051d-141">`.LabelTarget` 語彙基元表示要跳至的目標目的地。</span><span class="sxs-lookup"><span data-stu-id="5051d-141">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>

<span data-ttu-id="5051d-142">如果標籤沒有名稱，會指派自動產生的名稱給它，例如 `#Label1` 或 `#Label2`。</span><span class="sxs-lookup"><span data-stu-id="5051d-142">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>

### <a name="examples"></a><span data-ttu-id="5051d-143">範例</span><span class="sxs-lookup"><span data-stu-id="5051d-143">Examples</span></span>

```vb
Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")
Dim label1 As BlockExpression = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1))
)
'
'    .Block() {
'        .Goto SampleLabel { 0 };
'        .Label
'            -1
'        .LabelTarget SampleLabel:
'    }
'

Dim target As LabelTarget = Expression.Label()
Dim block As BlockExpression = Expression.Block(
    Expression.Goto(target), 
    Expression.Label(target)
)
'
'    .Block() {
'        .Goto #Label1 { };
'        .Label
'        .LabelTarget #Label1:
'    }
'
```

## <a name="checked-operators"></a><span data-ttu-id="5051d-144">檢查的運算子</span><span class="sxs-lookup"><span data-stu-id="5051d-144">Checked Operators</span></span>

<span data-ttu-id="5051d-145">檢查的運算子中會顯示與`#`，運算子前面的符號。</span><span class="sxs-lookup"><span data-stu-id="5051d-145">Checked operators are displayed with the `#` symbol in front of the operator.</span></span> <span data-ttu-id="5051d-146">例如，已檢查的加法運算子會顯示為 `#+`。</span><span class="sxs-lookup"><span data-stu-id="5051d-146">For example, the checked addition operator is displayed as `#+`.</span></span>

### <a name="examples"></a><span data-ttu-id="5051d-147">範例</span><span class="sxs-lookup"><span data-stu-id="5051d-147">Examples</span></span>

```vb
Dim expr As Expression = Expression.AddChecked(
    Expression.Constant(1),
    Expression.Constant(2)
)
'
'     1 #+ 2
'

Dim expr As Expression = Expression.ConvertChecked(
    Expression.Constant(10.0),
    GetType(Integer)
)
'
'    #(System.Int32)10D
'
```