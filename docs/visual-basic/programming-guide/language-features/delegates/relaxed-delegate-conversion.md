---
title: "寬鬆委派轉換 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions, relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 016c808145f7faba26a288cd5075f10d7f5279d5
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="relaxed-delegate-conversion-visual-basic"></a><span data-ttu-id="a7ebe-102">寬鬆委派轉換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7ebe-102">Relaxed Delegate Conversion (Visual Basic)</span></span>
<span data-ttu-id="a7ebe-103">寬鬆的委派轉換可讓您將函式和函式指派給委派或處理常式，即使它們的簽章不相同。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-103">Relaxed delegate conversion enables you to assign subs and functions to delegates or handlers even when their signatures are not identical.</span></span> <span data-ttu-id="a7ebe-104">因此，委派繫結可與已經達到所允許的方法引動過程的繫結一致。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-104">Therefore, binding to delegates becomes consistent with the binding already allowed for method invocations.</span></span>  
  
## <a name="parameters-and-return-type"></a><span data-ttu-id="a7ebe-105">參數和傳回型別</span><span class="sxs-lookup"><span data-stu-id="a7ebe-105">Parameters and Return Type</span></span>  
 <span data-ttu-id="a7ebe-106">簽章完全相符項目，取代寬鬆的轉換所需符合下列條件時`Option Strict`設為`On`:</span><span class="sxs-lookup"><span data-stu-id="a7ebe-106">In place of exact signature match, relaxed conversion requires that the following conditions be met when `Option Strict` is set to `On`:</span></span>  
  
-   <span data-ttu-id="a7ebe-107">擴展轉換必須從每個委派參數的資料型別指派函式的對應參數的資料型別或`Sub`。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-107">A widening conversion must exist from the data type of each delegate parameter to the data type of the corresponding parameter of the assigned function or `Sub`.</span></span> <span data-ttu-id="a7ebe-108">在下列範例中，委派`Del1`具有一個參數， `Integer`。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-108">In the following example, the delegate `Del1` has one parameter, an `Integer`.</span></span> <span data-ttu-id="a7ebe-109">參數`m`在指派的 lambda 運算式必須具有擴展轉換為資料類型`Integer`，例如`Long`或`Double`。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-109">Parameter `m` in the assigned lambda expressions must have a data type for which there is a widening conversion from `Integer`, such as `Long` or `Double`.</span></span>  
  
     <span data-ttu-id="a7ebe-110">[!code-vb[VbVbalrRelaxedDelegates #&1;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a7ebe-110">[!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]</span></span>  
  
     <span data-ttu-id="a7ebe-111">[!code-vb[VbVbalrRelaxedDelegates #&2;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="a7ebe-111">[!code-vb[VbVbalrRelaxedDelegates#2](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_2.vb)]</span></span>  
  
     <span data-ttu-id="a7ebe-112">縮小轉換時，才允許`Option Strict`設為`Off`。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-112">Narrowing conversions are permitted only when `Option Strict` is set to `Off`.</span></span>  
  
     <span data-ttu-id="a7ebe-113">[!code-vb[VbVbalrRelaxedDelegates #&8;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="a7ebe-113">[!code-vb[VbVbalrRelaxedDelegates#8](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_3.vb)]</span></span>  
  
-   <span data-ttu-id="a7ebe-114">擴展轉換必須存在於相反的方向，從指定的函式的傳回型別或`Sub`委派的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-114">A widening conversion must exist in the opposite direction from the return type of the assigned function or `Sub` to the return type of the delegate.</span></span> <span data-ttu-id="a7ebe-115">在下列範例中，每個指派的 lambda 運算式的主體必須評估為資料型別擴展至`Integer`因為傳回型別`del1`是`Integer`。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-115">In the following examples, the body of each assigned lambda expression must evaluate to a data type that widens to `Integer` because the return type of `del1` is `Integer`.</span></span>  
  
     <span data-ttu-id="a7ebe-116">[!code-vb[VbVbalrRelaxedDelegates #&3;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="a7ebe-116">[!code-vb[VbVbalrRelaxedDelegates#3](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_4.vb)]</span></span>  
  
 <span data-ttu-id="a7ebe-117">如果`Option Strict`設為`Off`、 擴展限制已移除兩個方向。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-117">If `Option Strict` is set to `Off`, the widening restriction is removed in both directions.</span></span>  
  
 <span data-ttu-id="a7ebe-118">[!code-vb[VbVbalrRelaxedDelegates #&4;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="a7ebe-118">[!code-vb[VbVbalrRelaxedDelegates#4](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_5.vb)]</span></span>  
  
## <a name="omitting-parameter-specifications"></a><span data-ttu-id="a7ebe-119">省略參數規格</span><span class="sxs-lookup"><span data-stu-id="a7ebe-119">Omitting Parameter Specifications</span></span>  
 <span data-ttu-id="a7ebe-120">寬鬆的委派也可讓您完全省略參數規格中指定的方法︰</span><span class="sxs-lookup"><span data-stu-id="a7ebe-120">Relaxed delegates also allow you to completely omit parameter specifications in the assigned method:</span></span>  
  
 <span data-ttu-id="a7ebe-121">[!code-vb[VbVbalrRelaxedDelegates #&5;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="a7ebe-121">[!code-vb[VbVbalrRelaxedDelegates#5](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_6.vb)]</span></span>  
  
 <span data-ttu-id="a7ebe-122">[!code-vb[VbVbalrRelaxedDelegates #&6;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="a7ebe-122">[!code-vb[VbVbalrRelaxedDelegates#6](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_7.vb)]</span></span>  
  
 <span data-ttu-id="a7ebe-123">請注意您無法指定一些參數，並省略其他人。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-123">Note that you cannot specify some parameters and omit others.</span></span>  
  
 <span data-ttu-id="a7ebe-124">[!code-vb[VbVbalrRelaxedDelegates #&15;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="a7ebe-124">[!code-vb[VbVbalrRelaxedDelegates#15](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_8.vb)]</span></span>  
  
 <span data-ttu-id="a7ebe-125">省略參數的能力是很有幫助的情況下，例如定義事件處理常式，其中牽涉到多個複雜參數。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-125">The ability to omit parameters is helpful in a situation such as defining an event handler, where several complex parameters are involved.</span></span> <span data-ttu-id="a7ebe-126">不會使用一些事件處理常式的引數。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-126">The arguments to some event handlers are not used.</span></span> <span data-ttu-id="a7ebe-127">相反地，此處理常式直接存取的控制項的事件註冊，並忽略引數的狀態。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-127">Instead, the handler directly accesses the state of the control on which the event is registered, and ignores the arguments.</span></span> <span data-ttu-id="a7ebe-128">寬鬆的委派可讓您省略此類宣告時沒有模稜兩可的結果中的引數。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-128">Relaxed delegates allow you to omit the arguments in such declarations when no ambiguities result.</span></span> <span data-ttu-id="a7ebe-129">在下列範例中，完整指定方法`OnClick`可以重寫為`RelaxedOnClick`。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-129">In the following example, the fully specified method `OnClick` can be rewritten as `RelaxedOnClick`.</span></span>  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a><span data-ttu-id="a7ebe-130">AddressOf 範例</span><span class="sxs-lookup"><span data-stu-id="a7ebe-130">AddressOf Examples</span></span>  
 <span data-ttu-id="a7ebe-131">上一個範例中所用 lambda 運算式，可讓您輕鬆查看的型別關聯性。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-131">Lambda expressions are used in the previous examples to make the type relationships easy to see.</span></span> <span data-ttu-id="a7ebe-132">不過，相同 relaxations 則可以使用的委派指派`AddressOf`， `Handles`，或`AddHandler`。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-132">However, the same relaxations are permitted for delegate assignments that use `AddressOf`, `Handles`, or `AddHandler`.</span></span>  
  
 <span data-ttu-id="a7ebe-133">在下列範例中，函式`f1`， `f2`， `f3`，和`f4`所有可指派給`Del1`。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-133">In the following example, functions `f1`, `f2`, `f3`, and `f4` can all be assigned to `Del1`.</span></span>  
  
 <span data-ttu-id="a7ebe-134">[!code-vb[VbVbalrRelaxedDelegates #&1;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a7ebe-134">[!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]</span></span>  
  
 <span data-ttu-id="a7ebe-135">[!code-vb[VbVbalrRelaxedDelegates #&7;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="a7ebe-135">[!code-vb[VbVbalrRelaxedDelegates#7](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_9.vb)]</span></span>  
  
 <span data-ttu-id="a7ebe-136">[!code-vb[VbVbalrRelaxedDelegates #&9;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="a7ebe-136">[!code-vb[VbVbalrRelaxedDelegates#9](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_10.vb)]</span></span>  
  
 <span data-ttu-id="a7ebe-137">下列範例是時才有效`Option Strict`設為`Off`。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-137">The following example is valid only when `Option Strict` is set to `Off`.</span></span>  
  
 <span data-ttu-id="a7ebe-138">[!code-vb[VbVbalrRelaxedDelegates #&14;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_11.vb)]</span><span class="sxs-lookup"><span data-stu-id="a7ebe-138">[!code-vb[VbVbalrRelaxedDelegates#14](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_11.vb)]</span></span>  
  
## <a name="dropping-function-returns"></a><span data-ttu-id="a7ebe-139">卸除函式傳回</span><span class="sxs-lookup"><span data-stu-id="a7ebe-139">Dropping Function Returns</span></span>  
 <span data-ttu-id="a7ebe-140">寬鬆的委派轉換可讓您將函式來指派`Sub`委派，進而有效地忽略函式的傳回值。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-140">Relaxed delegate conversion enables you to assign a function to a `Sub` delegate, effectively ignoring the return value of the function.</span></span> <span data-ttu-id="a7ebe-141">不過，您無法指派`Sub`函式委派。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-141">However, you cannot assign a `Sub` to a function delegate.</span></span> <span data-ttu-id="a7ebe-142">在下列範例中，函式的位址`doubler`指派給`Sub`委派`Del3`。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-142">In the following example, the address of function `doubler` is assigned to `Sub` delegate `Del3`.</span></span>  
  
 <span data-ttu-id="a7ebe-143">[!code-vb[VbVbalrRelaxedDelegates #&10;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_12.vb)]</span><span class="sxs-lookup"><span data-stu-id="a7ebe-143">[!code-vb[VbVbalrRelaxedDelegates#10](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_12.vb)]</span></span>  
  
 <span data-ttu-id="a7ebe-144">[!code-vb[VbVbalrRelaxedDelegates #&11;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_13.vb)]</span><span class="sxs-lookup"><span data-stu-id="a7ebe-144">[!code-vb[VbVbalrRelaxedDelegates#11](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_13.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7ebe-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7ebe-145">See Also</span></span>  
 <span data-ttu-id="a7ebe-146">[Lambda 運算式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="a7ebe-146">[Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span></span>  
<span data-ttu-id="a7ebe-147"> [擴展和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="a7ebe-147"> [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) </span></span>  
<span data-ttu-id="a7ebe-148"> [委派](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="a7ebe-148"> [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="a7ebe-149"> [如何︰ 將傳遞至另一個程序，在 Visual Basic 中的程序](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="a7ebe-149"> [How to: Pass Procedures to Another Procedure in Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md) </span></span>  
<span data-ttu-id="a7ebe-150"> [區域型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="a7ebe-150"> [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="a7ebe-151"> [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)</span><span class="sxs-lookup"><span data-stu-id="a7ebe-151"> [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)</span></span>
