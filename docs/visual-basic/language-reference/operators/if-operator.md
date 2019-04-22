---
title: If 運算子 (Visual Basic)
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
ms.openlocfilehash: 9ab01755d75c91ce87acf83e7f406b26c466aef6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834630"
---
# <a name="if-operator-visual-basic"></a><span data-ttu-id="cbf60-102">If 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cbf60-102">If Operator (Visual Basic)</span></span>
<span data-ttu-id="cbf60-103">使用最少運算評估，有條件地傳回兩個值之一。</span><span class="sxs-lookup"><span data-stu-id="cbf60-103">Uses short-circuit evaluation to conditionally return one of two values.</span></span> <span data-ttu-id="cbf60-104">`If`與三個引數或兩個引數，就可以呼叫運算子。</span><span class="sxs-lookup"><span data-stu-id="cbf60-104">The `If` operator can be called with three arguments or with two arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbf60-105">語法</span><span class="sxs-lookup"><span data-stu-id="cbf60-105">Syntax</span></span>  
  
```  
If( [argument1,] argument2, argument3 )  
```  
  
## <a name="if-operator-called-with-three-arguments"></a><span data-ttu-id="cbf60-106">如果使用三個引數來呼叫運算子</span><span class="sxs-lookup"><span data-stu-id="cbf60-106">If Operator Called with Three Arguments</span></span>  
 <span data-ttu-id="cbf60-107">當`If`稱為藉由使用三個引數，第一個引數必須評估為值，可以轉換成`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="cbf60-107">When `If` is called by using three arguments, the first argument must evaluate to a value that can be cast as a `Boolean`.</span></span> <span data-ttu-id="cbf60-108">`Boolean`值將決定哪些其他兩個引數會評估並傳回。</span><span class="sxs-lookup"><span data-stu-id="cbf60-108">That `Boolean` value will determine which of the other two arguments is evaluated and returned.</span></span> <span data-ttu-id="cbf60-109">下列清單時，才適用`If`使用三個引數呼叫運算子。</span><span class="sxs-lookup"><span data-stu-id="cbf60-109">The following list applies only when the `If` operator is called by using three arguments.</span></span>  
  
## <a name="parts"></a><span data-ttu-id="cbf60-110">組件</span><span class="sxs-lookup"><span data-stu-id="cbf60-110">Parts</span></span>  
  
|<span data-ttu-id="cbf60-111">詞彙</span><span class="sxs-lookup"><span data-stu-id="cbf60-111">Term</span></span>|<span data-ttu-id="cbf60-112">定義</span><span class="sxs-lookup"><span data-stu-id="cbf60-112">Definition</span></span>|  
|---|---|  
|`argument1`|<span data-ttu-id="cbf60-113">必要項。</span><span class="sxs-lookup"><span data-stu-id="cbf60-113">Required.</span></span> <span data-ttu-id="cbf60-114">`Boolean`.</span><span class="sxs-lookup"><span data-stu-id="cbf60-114">`Boolean`.</span></span> <span data-ttu-id="cbf60-115">判斷其中一個要評估及傳回的其他引數。</span><span class="sxs-lookup"><span data-stu-id="cbf60-115">Determines which of the other arguments to evaluate and return.</span></span>|  
|`argument2`|<span data-ttu-id="cbf60-116">必要項。</span><span class="sxs-lookup"><span data-stu-id="cbf60-116">Required.</span></span> <span data-ttu-id="cbf60-117">`Object`.</span><span class="sxs-lookup"><span data-stu-id="cbf60-117">`Object`.</span></span> <span data-ttu-id="cbf60-118">評估並傳回 if`argument1`評估為`True`。</span><span class="sxs-lookup"><span data-stu-id="cbf60-118">Evaluated and returned if `argument1` evaluates to `True`.</span></span>|  
|`argument3`|<span data-ttu-id="cbf60-119">必要項。</span><span class="sxs-lookup"><span data-stu-id="cbf60-119">Required.</span></span> <span data-ttu-id="cbf60-120">`Object`.</span><span class="sxs-lookup"><span data-stu-id="cbf60-120">`Object`.</span></span> <span data-ttu-id="cbf60-121">評估並傳回 if`argument1`評估為`False`或者`argument1`是[Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean`變數評估為[Nothing](../../../visual-basic/language-reference/nothing.md)。</span><span class="sxs-lookup"><span data-stu-id="cbf60-121">Evaluated and returned if `argument1` evaluates to `False` or if `argument1` is a [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean` variable that evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md).</span></span>|  
  
 <span data-ttu-id="cbf60-122">`If`運算子，會使用三個引數呼叫的運作方式類似`IIf`函式不同之處在於它會使用最少運算評估。</span><span class="sxs-lookup"><span data-stu-id="cbf60-122">An `If` operator that is called with three arguments works like an `IIf` function except that it uses short-circuit evaluation.</span></span> <span data-ttu-id="cbf60-123">`IIf`函式一律會評估其引數，這三個，而`If`有三個引數的運算子會評估只有兩個。</span><span class="sxs-lookup"><span data-stu-id="cbf60-123">An `IIf` function always evaluates all three of its arguments, whereas an `If` operator that has three arguments evaluates only two of them.</span></span> <span data-ttu-id="cbf60-124">第一個`If`引數會評估和結果轉換成`Boolean`的值，`True`或`False`。</span><span class="sxs-lookup"><span data-stu-id="cbf60-124">The first `If` argument is evaluated and the result is cast as a `Boolean` value, `True` or `False`.</span></span> <span data-ttu-id="cbf60-125">如果值為`True`，`argument2`會評估並傳回其值，但`argument3`不會評估。</span><span class="sxs-lookup"><span data-stu-id="cbf60-125">If the value is `True`, `argument2` is evaluated and its value is returned, but `argument3` is not evaluated.</span></span> <span data-ttu-id="cbf60-126">如果的值`Boolean`運算式`False`，`argument3`會評估並傳回其值，但`argument2`不會評估。</span><span class="sxs-lookup"><span data-stu-id="cbf60-126">If the value of the `Boolean` expression is `False`, `argument3` is evaluated and its value is returned, but `argument2` is not evaluated.</span></span> <span data-ttu-id="cbf60-127">下列範例說明使用`If`三個引數使用時：</span><span class="sxs-lookup"><span data-stu-id="cbf60-127">The following examples illustrate the use of `If` when three arguments are used:</span></span>  
  
 [!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]  
  
 <span data-ttu-id="cbf60-128">下列範例說明值的最少運算評估。</span><span class="sxs-lookup"><span data-stu-id="cbf60-128">The following example illustrates the value of short-circuit evaluation.</span></span> <span data-ttu-id="cbf60-129">此範例示範兩次嘗試將變數`number`變數所`divisor`除非`divisor`為零。</span><span class="sxs-lookup"><span data-stu-id="cbf60-129">The example shows two attempts to divide variable `number` by variable `divisor` except when `divisor` is zero.</span></span> <span data-ttu-id="cbf60-130">在此情況下，應該會傳回 「 0 」，並不應該嘗試執行除法運算，因為會造成執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="cbf60-130">In that case, a 0 should be returned, and no attempt should be made to perform the division because a run-time error would result.</span></span> <span data-ttu-id="cbf60-131">因為`If`運算式會使用最少運算的評估，它會評估第二個或第三個引數，第一個引數的值而定。</span><span class="sxs-lookup"><span data-stu-id="cbf60-131">Because the `If` expression uses short-circuit evaluation, it evaluates either the second or the third argument, depending on the value of the first argument.</span></span> <span data-ttu-id="cbf60-132">如果第一個引數為 true，除數為零並不安全地評估第二個引數，並執行除法。</span><span class="sxs-lookup"><span data-stu-id="cbf60-132">If the first argument is true, the divisor is not zero and it is safe to evaluate the second argument and perform the division.</span></span> <span data-ttu-id="cbf60-133">如果第一個引數為 false，會評估第三個引數，就會傳回 0。</span><span class="sxs-lookup"><span data-stu-id="cbf60-133">If the first argument is false, only the third argument is evaluated and a 0 is returned.</span></span> <span data-ttu-id="cbf60-134">因此，除數為 0 時，不會嘗試執行除法並不會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="cbf60-134">Therefore, when the divisor is 0, no attempt is made to perform the division and no error results.</span></span> <span data-ttu-id="cbf60-135">不過，因為`IIf`不會使用最少運算評估，即使在第一個引數為 false 時，才評估第二個引數。</span><span class="sxs-lookup"><span data-stu-id="cbf60-135">However, because `IIf` does not use short-circuit evaluation, the second argument is evaluated even when the first argument is false.</span></span> <span data-ttu-id="cbf60-136">這會導致執行階段除以零錯誤。</span><span class="sxs-lookup"><span data-stu-id="cbf60-136">This causes a run-time divide-by-zero error.</span></span>  
  
 [!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]  
  
## <a name="if-operator-called-with-two-arguments"></a><span data-ttu-id="cbf60-137">如果兩個引數呼叫運算子</span><span class="sxs-lookup"><span data-stu-id="cbf60-137">If Operator Called with Two Arguments</span></span>  
 <span data-ttu-id="cbf60-138">第一個引數`If`可以省略。</span><span class="sxs-lookup"><span data-stu-id="cbf60-138">The first argument to `If` can be omitted.</span></span> <span data-ttu-id="cbf60-139">這可讓操作員使用只有兩個引數來呼叫。</span><span class="sxs-lookup"><span data-stu-id="cbf60-139">This enables the operator to be called by using only two arguments.</span></span> <span data-ttu-id="cbf60-140">下列清單時，才適用`If`使用兩個引數呼叫運算子。</span><span class="sxs-lookup"><span data-stu-id="cbf60-140">The following list applies only when the `If` operator is called with two arguments.</span></span>  
  
## <a name="parts"></a><span data-ttu-id="cbf60-141">組件</span><span class="sxs-lookup"><span data-stu-id="cbf60-141">Parts</span></span>  
  
|<span data-ttu-id="cbf60-142">詞彙</span><span class="sxs-lookup"><span data-stu-id="cbf60-142">Term</span></span>|<span data-ttu-id="cbf60-143">定義</span><span class="sxs-lookup"><span data-stu-id="cbf60-143">Definition</span></span>|  
|---|---|  
|`argument2`|<span data-ttu-id="cbf60-144">必要項。</span><span class="sxs-lookup"><span data-stu-id="cbf60-144">Required.</span></span> <span data-ttu-id="cbf60-145">`Object`.</span><span class="sxs-lookup"><span data-stu-id="cbf60-145">`Object`.</span></span> <span data-ttu-id="cbf60-146">必須是參考或可為 null 的型別。</span><span class="sxs-lookup"><span data-stu-id="cbf60-146">Must be a reference or nullable type.</span></span> <span data-ttu-id="cbf60-147">評估並傳回其評估結果為任何項目以外時`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="cbf60-147">Evaluated and returned when it evaluates to anything other than `Nothing`.</span></span>|  
|`argument3`|<span data-ttu-id="cbf60-148">必要項。</span><span class="sxs-lookup"><span data-stu-id="cbf60-148">Required.</span></span> <span data-ttu-id="cbf60-149">`Object`.</span><span class="sxs-lookup"><span data-stu-id="cbf60-149">`Object`.</span></span> <span data-ttu-id="cbf60-150">評估並傳回 if`argument2`評估為`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="cbf60-150">Evaluated and returned if `argument2` evaluates to `Nothing`.</span></span>|  
  
 <span data-ttu-id="cbf60-151">當`Boolean`省略引數，第一個引數必須是參考或可為 null 的型別。</span><span class="sxs-lookup"><span data-stu-id="cbf60-151">When the `Boolean` argument is omitted, the first argument must be a reference or nullable type.</span></span> <span data-ttu-id="cbf60-152">如果第一個引數評估為`Nothing`，會傳回第二個引數的值。</span><span class="sxs-lookup"><span data-stu-id="cbf60-152">If the first argument evaluates to `Nothing`, the value of the second argument is returned.</span></span> <span data-ttu-id="cbf60-153">在其他情況下，會傳回第一個引數的值。</span><span class="sxs-lookup"><span data-stu-id="cbf60-153">In all other cases, the value of the first argument is returned.</span></span> <span data-ttu-id="cbf60-154">下列範例說明這項評估的運作方式。</span><span class="sxs-lookup"><span data-stu-id="cbf60-154">The following example illustrates how this evaluation works.</span></span>  
  
 [!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="cbf60-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbf60-155">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [<span data-ttu-id="cbf60-156">可為 Null 的值類型</span><span class="sxs-lookup"><span data-stu-id="cbf60-156">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="cbf60-157">Nothing</span><span class="sxs-lookup"><span data-stu-id="cbf60-157">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
