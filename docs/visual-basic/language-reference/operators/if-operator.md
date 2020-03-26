---
title: If 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.IfOperator
- IfOperator
helpviewer_keywords:
- ternary operators [Visual Basic]
- conditional execution
- If expressions [Visual Basic]
- conditional operator [Visual Basic]
- If Operator [Visual Basic]
ms.assetid: dd56c9df-7cd4-442c-9ba6-20c70ee44c8f
ms.openlocfilehash: 3b45a5afe331bd00c2b92f8c305351b77bc319cf
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249483"
---
# <a name="if-operator-visual-basic"></a><span data-ttu-id="3d842-102">If 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d842-102">If Operator (Visual Basic)</span></span>

<span data-ttu-id="3d842-103">使用短路評估有條件地返回兩個值之一。</span><span class="sxs-lookup"><span data-stu-id="3d842-103">Uses short-circuit evaluation to conditionally return one of two values.</span></span> <span data-ttu-id="3d842-104">可以使用`If`三個參數或兩個參數調用運算子。</span><span class="sxs-lookup"><span data-stu-id="3d842-104">The `If` operator can be called with three arguments or with two arguments.</span></span>

## <a name="syntax"></a><span data-ttu-id="3d842-105">語法</span><span class="sxs-lookup"><span data-stu-id="3d842-105">Syntax</span></span>

```vb
If( [argument1,] argument2, argument3 )
```

## <a name="if-operator-called-with-three-arguments"></a><span data-ttu-id="3d842-106">如果運算子使用三個參數調用</span><span class="sxs-lookup"><span data-stu-id="3d842-106">If operator called with three arguments</span></span>

<span data-ttu-id="3d842-107">使用`If`三個參數調用時，第一個參數必須計算為可以轉換為 的值`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="3d842-107">When `If` is called by using three arguments, the first argument must evaluate to a value that can be cast as a `Boolean`.</span></span> <span data-ttu-id="3d842-108">該`Boolean`值將確定計算並返回其他兩個參數中的哪一個。</span><span class="sxs-lookup"><span data-stu-id="3d842-108">That `Boolean` value will determine which of the other two arguments is evaluated and returned.</span></span> <span data-ttu-id="3d842-109">僅當使用三個參數調用運算子`If`時，以下清單才適用。</span><span class="sxs-lookup"><span data-stu-id="3d842-109">The following list applies only when the `If` operator is called by using three arguments.</span></span>

### <a name="parts"></a><span data-ttu-id="3d842-110">組件</span><span class="sxs-lookup"><span data-stu-id="3d842-110">Parts</span></span>

|<span data-ttu-id="3d842-111">詞彙</span><span class="sxs-lookup"><span data-stu-id="3d842-111">Term</span></span>|<span data-ttu-id="3d842-112">定義</span><span class="sxs-lookup"><span data-stu-id="3d842-112">Definition</span></span>|
|---|---|
|`argument1`|<span data-ttu-id="3d842-113">必要。</span><span class="sxs-lookup"><span data-stu-id="3d842-113">Required.</span></span> <span data-ttu-id="3d842-114">`Boolean`.</span><span class="sxs-lookup"><span data-stu-id="3d842-114">`Boolean`.</span></span> <span data-ttu-id="3d842-115">確定要計算和返回的其他參數。</span><span class="sxs-lookup"><span data-stu-id="3d842-115">Determines which of the other arguments to evaluate and return.</span></span>|
|`argument2`|<span data-ttu-id="3d842-116">必要。</span><span class="sxs-lookup"><span data-stu-id="3d842-116">Required.</span></span> <span data-ttu-id="3d842-117">`Object`.</span><span class="sxs-lookup"><span data-stu-id="3d842-117">`Object`.</span></span> <span data-ttu-id="3d842-118">如果`argument1`評估為`True`，則評估並返回。</span><span class="sxs-lookup"><span data-stu-id="3d842-118">Evaluated and returned if `argument1` evaluates to `True`.</span></span>|
|`argument3`|<span data-ttu-id="3d842-119">必要。</span><span class="sxs-lookup"><span data-stu-id="3d842-119">Required.</span></span> <span data-ttu-id="3d842-120">`Object`.</span><span class="sxs-lookup"><span data-stu-id="3d842-120">`Object`.</span></span> <span data-ttu-id="3d842-121">`argument1`如果計算為`False`或`argument1`如果為"[無"](../../../visual-basic/language-reference/nothing.md)[的可無變數](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean`，則計算並返回。</span><span class="sxs-lookup"><span data-stu-id="3d842-121">Evaluated and returned if `argument1` evaluates to `False` or if `argument1` is a [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean` variable that evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md).</span></span>|

<span data-ttu-id="3d842-122">使用`If`三個參數調用的運算子的工作方式類似于函數`IIf`，只不過它使用短路計算。</span><span class="sxs-lookup"><span data-stu-id="3d842-122">An `If` operator that is called with three arguments works like an `IIf` function except that it uses short-circuit evaluation.</span></span> <span data-ttu-id="3d842-123">函數`IIf`始終計算其所有三個參數，而具有三個`If`參數的運算子只計算其中兩個參數。</span><span class="sxs-lookup"><span data-stu-id="3d842-123">An `IIf` function always evaluates all three of its arguments, whereas an `If` operator that has three arguments evaluates only two of them.</span></span> <span data-ttu-id="3d842-124">計算第`If`一個`Boolean`參數，並將結果強制轉換為值或`True``False`。</span><span class="sxs-lookup"><span data-stu-id="3d842-124">The first `If` argument is evaluated and the result is cast as a `Boolean` value, `True` or `False`.</span></span> <span data-ttu-id="3d842-125">如果值為`True`，`argument2`則計算其值，但不`argument3`計算該值。</span><span class="sxs-lookup"><span data-stu-id="3d842-125">If the value is `True`, `argument2` is evaluated and its value is returned, but `argument3` is not evaluated.</span></span> <span data-ttu-id="3d842-126">如果`Boolean`運算式的值為`False`，`argument3`則計算其值並返回其值，但不`argument2`計算。</span><span class="sxs-lookup"><span data-stu-id="3d842-126">If the value of the `Boolean` expression is `False`, `argument3` is evaluated and its value is returned, but `argument2` is not evaluated.</span></span> <span data-ttu-id="3d842-127">以下示例說明了使用三個參數`If`時的使用：</span><span class="sxs-lookup"><span data-stu-id="3d842-127">The following examples illustrate the use of `If` when three arguments are used:</span></span>

[!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]

<span data-ttu-id="3d842-128">下面的示例說明了短路評估的價值。</span><span class="sxs-lookup"><span data-stu-id="3d842-128">The following example illustrates the value of short-circuit evaluation.</span></span> <span data-ttu-id="3d842-129">該示例顯示兩次嘗試將變數`number`除以變數`divisor`除以`divisor`變數，但為零時除外。</span><span class="sxs-lookup"><span data-stu-id="3d842-129">The example shows two attempts to divide variable `number` by variable `divisor` except when `divisor` is zero.</span></span> <span data-ttu-id="3d842-130">在這種情況下，應返回 0，並且不應嘗試執行除法，因為將導致執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="3d842-130">In that case, a 0 should be returned, and no attempt should be made to perform the division because a run-time error would result.</span></span> <span data-ttu-id="3d842-131">由於`If`運算式使用短路計算，因此根據第一個參數的值計算第二個或第三個參數。</span><span class="sxs-lookup"><span data-stu-id="3d842-131">Because the `If` expression uses short-circuit evaluation, it evaluates either the second or the third argument, depending on the value of the first argument.</span></span> <span data-ttu-id="3d842-132">如果第一個參數為 true，則除法不是零，可以安全地計算第二個參數並執行除法。</span><span class="sxs-lookup"><span data-stu-id="3d842-132">If the first argument is true, the divisor is not zero and it is safe to evaluate the second argument and perform the division.</span></span> <span data-ttu-id="3d842-133">如果第一個參數為 false，則僅計算第三個參數並返回 0。</span><span class="sxs-lookup"><span data-stu-id="3d842-133">If the first argument is false, only the third argument is evaluated and a 0 is returned.</span></span> <span data-ttu-id="3d842-134">因此，當除法器為 0 時，不會嘗試執行除法，也沒有錯誤結果。</span><span class="sxs-lookup"><span data-stu-id="3d842-134">Therefore, when the divisor is 0, no attempt is made to perform the division and no error results.</span></span> <span data-ttu-id="3d842-135">但是，由於`IIf`不使用短路計算，因此即使第一個參數為 false，也會計算第二個參數。</span><span class="sxs-lookup"><span data-stu-id="3d842-135">However, because `IIf` does not use short-circuit evaluation, the second argument is evaluated even when the first argument is false.</span></span> <span data-ttu-id="3d842-136">這將導致運行時除以零錯誤。</span><span class="sxs-lookup"><span data-stu-id="3d842-136">This causes a run-time divide-by-zero error.</span></span>

[!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]

## <a name="if-operator-called-with-two-arguments"></a><span data-ttu-id="3d842-137">如果運算子使用兩個參數調用</span><span class="sxs-lookup"><span data-stu-id="3d842-137">If operator called with two arguments</span></span>

<span data-ttu-id="3d842-138">`If`可以省略的第一個參數。</span><span class="sxs-lookup"><span data-stu-id="3d842-138">The first argument to `If` can be omitted.</span></span> <span data-ttu-id="3d842-139">這樣，只需使用兩個參數就可以調用運算子。</span><span class="sxs-lookup"><span data-stu-id="3d842-139">This enables the operator to be called by using only two arguments.</span></span> <span data-ttu-id="3d842-140">僅當使用兩個參數調用運算子`If`時，以下清單才適用。</span><span class="sxs-lookup"><span data-stu-id="3d842-140">The following list applies only when the `If` operator is called with two arguments.</span></span>

### <a name="parts"></a><span data-ttu-id="3d842-141">組件</span><span class="sxs-lookup"><span data-stu-id="3d842-141">Parts</span></span>

|<span data-ttu-id="3d842-142">詞彙</span><span class="sxs-lookup"><span data-stu-id="3d842-142">Term</span></span>|<span data-ttu-id="3d842-143">定義</span><span class="sxs-lookup"><span data-stu-id="3d842-143">Definition</span></span>|
|---|---|
|`argument2`|<span data-ttu-id="3d842-144">必要。</span><span class="sxs-lookup"><span data-stu-id="3d842-144">Required.</span></span> <span data-ttu-id="3d842-145">`Object`.</span><span class="sxs-lookup"><span data-stu-id="3d842-145">`Object`.</span></span> <span data-ttu-id="3d842-146">必須是引用值或空數值型別。</span><span class="sxs-lookup"><span data-stu-id="3d842-146">Must be a reference or nullable value type.</span></span> <span data-ttu-id="3d842-147">當它評估到 以外的任何`Nothing`內容時，它進行評估並返回。</span><span class="sxs-lookup"><span data-stu-id="3d842-147">Evaluated and returned when it evaluates to anything other than `Nothing`.</span></span>|
|`argument3`|<span data-ttu-id="3d842-148">必要。</span><span class="sxs-lookup"><span data-stu-id="3d842-148">Required.</span></span> <span data-ttu-id="3d842-149">`Object`.</span><span class="sxs-lookup"><span data-stu-id="3d842-149">`Object`.</span></span> <span data-ttu-id="3d842-150">如果`argument2`評估為`Nothing`，則評估並返回。</span><span class="sxs-lookup"><span data-stu-id="3d842-150">Evaluated and returned if `argument2` evaluates to `Nothing`.</span></span>|

<span data-ttu-id="3d842-151">省略`Boolean`參數時，第一個參數必須是引用數值型別或空數值型別。</span><span class="sxs-lookup"><span data-stu-id="3d842-151">When the `Boolean` argument is omitted, the first argument must be a reference or nullable value type.</span></span> <span data-ttu-id="3d842-152">如果第一個參數計算到`Nothing`，則返回第二個參數的值。</span><span class="sxs-lookup"><span data-stu-id="3d842-152">If the first argument evaluates to `Nothing`, the value of the second argument is returned.</span></span> <span data-ttu-id="3d842-153">在所有其他情況下，將返回第一個參數的值。</span><span class="sxs-lookup"><span data-stu-id="3d842-153">In all other cases, the value of the first argument is returned.</span></span> <span data-ttu-id="3d842-154">以下示例說明了此評估的工作原理：</span><span class="sxs-lookup"><span data-stu-id="3d842-154">The following example illustrates how this evaluation works:</span></span>

[!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]

## <a name="see-also"></a><span data-ttu-id="3d842-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d842-155">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [<span data-ttu-id="3d842-156">空數值型別</span><span class="sxs-lookup"><span data-stu-id="3d842-156">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="3d842-157">什麼</span><span class="sxs-lookup"><span data-stu-id="3d842-157">Nothing</span></span>](../nothing.md)
