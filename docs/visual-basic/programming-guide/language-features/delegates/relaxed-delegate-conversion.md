---
title: "寬鬆委派轉換 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0cca3d09b538905714f627c9fa006187b8927383
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="relaxed-delegate-conversion-visual-basic"></a><span data-ttu-id="d3bb1-102">寬鬆委派轉換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3bb1-102">Relaxed Delegate Conversion (Visual Basic)</span></span>
<span data-ttu-id="d3bb1-103">寬鬆的委派轉換可讓您將訂閱和函式指派給處理常式或委派，即使它們的簽章不相同。</span><span class="sxs-lookup"><span data-stu-id="d3bb1-103">Relaxed delegate conversion enables you to assign subs and functions to delegates or handlers even when their signatures are not identical.</span></span> <span data-ttu-id="d3bb1-104">因此，委派繫結可與已經達到所允許的方法引動過程的繫結一致。</span><span class="sxs-lookup"><span data-stu-id="d3bb1-104">Therefore, binding to delegates becomes consistent with the binding already allowed for method invocations.</span></span>  
  
## <a name="parameters-and-return-type"></a><span data-ttu-id="d3bb1-105">參數和傳回型別</span><span class="sxs-lookup"><span data-stu-id="d3bb1-105">Parameters and Return Type</span></span>  
 <span data-ttu-id="d3bb1-106">簽章完全相符項目，取代寬鬆的方式轉換需要符合下列條件時`Option Strict`設`On`:</span><span class="sxs-lookup"><span data-stu-id="d3bb1-106">In place of exact signature match, relaxed conversion requires that the following conditions be met when `Option Strict` is set to `On`:</span></span>  
  
-   <span data-ttu-id="d3bb1-107">擴展轉換指派函式的對應參數的資料類型時，必須從每個委派參數的資料類型或`Sub`。</span><span class="sxs-lookup"><span data-stu-id="d3bb1-107">A widening conversion must exist from the data type of each delegate parameter to the data type of the corresponding parameter of the assigned function or `Sub`.</span></span> <span data-ttu-id="d3bb1-108">在下列範例中，委派`Del1`具有一個參數， `Integer`。</span><span class="sxs-lookup"><span data-stu-id="d3bb1-108">In the following example, the delegate `Del1` has one parameter, an `Integer`.</span></span> <span data-ttu-id="d3bb1-109">參數`m`中指派的 lambda 運算式必須有擴展轉換為的資料類型`Integer`，例如`Long`或`Double`。</span><span class="sxs-lookup"><span data-stu-id="d3bb1-109">Parameter `m` in the assigned lambda expressions must have a data type for which there is a widening conversion from `Integer`, such as `Long` or `Double`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_2.vb)]  
  
     <span data-ttu-id="d3bb1-110">縮小轉換時，才允許`Option Strict`設`Off`。</span><span class="sxs-lookup"><span data-stu-id="d3bb1-110">Narrowing conversions are permitted only when `Option Strict` is set to `Off`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_3.vb)]  
  
-   <span data-ttu-id="d3bb1-111">擴展轉換必須存在於以相反的方向，從指定的函式的傳回型別或`Sub`委派的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="d3bb1-111">A widening conversion must exist in the opposite direction from the return type of the assigned function or `Sub` to the return type of the delegate.</span></span> <span data-ttu-id="d3bb1-112">在下列範例中，每個指派的 lambda 運算式的主體必須評估為資料類型可擴展成`Integer`因為傳回型別`del1`是`Integer`。</span><span class="sxs-lookup"><span data-stu-id="d3bb1-112">In the following examples, the body of each assigned lambda expression must evaluate to a data type that widens to `Integer` because the return type of `del1` is `Integer`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_4.vb)]  
  
 <span data-ttu-id="d3bb1-113">如果`Option Strict`設`Off`、 擴展限制會移除兩個方向。</span><span class="sxs-lookup"><span data-stu-id="d3bb1-113">If `Option Strict` is set to `Off`, the widening restriction is removed in both directions.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_5.vb)]  
  
## <a name="omitting-parameter-specifications"></a><span data-ttu-id="d3bb1-114">省略的參數規格</span><span class="sxs-lookup"><span data-stu-id="d3bb1-114">Omitting Parameter Specifications</span></span>  
 <span data-ttu-id="d3bb1-115">寬鬆的委派也可讓您完全省略指派方法中的參數規格：</span><span class="sxs-lookup"><span data-stu-id="d3bb1-115">Relaxed delegates also allow you to completely omit parameter specifications in the assigned method:</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_6.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_7.vb)]  
  
 <span data-ttu-id="d3bb1-116">請注意您無法指定一些參數並省略其他人。</span><span class="sxs-lookup"><span data-stu-id="d3bb1-116">Note that you cannot specify some parameters and omit others.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_8.vb)]  
  
 <span data-ttu-id="d3bb1-117">省略參數的能力是很有幫助的情況下，例如定義事件處理常式，其中牽涉到多個複雜參數。</span><span class="sxs-lookup"><span data-stu-id="d3bb1-117">The ability to omit parameters is helpful in a situation such as defining an event handler, where several complex parameters are involved.</span></span> <span data-ttu-id="d3bb1-118">不會使用某些事件處理常式的引數。</span><span class="sxs-lookup"><span data-stu-id="d3bb1-118">The arguments to some event handlers are not used.</span></span> <span data-ttu-id="d3bb1-119">相反地，此處理常式直接存取的控制項的事件註冊，並忽略引數的狀態。</span><span class="sxs-lookup"><span data-stu-id="d3bb1-119">Instead, the handler directly accesses the state of the control on which the event is registered, and ignores the arguments.</span></span> <span data-ttu-id="d3bb1-120">寬鬆的委派可讓您省略此類宣告時沒有模稜兩可的結果中的引數。</span><span class="sxs-lookup"><span data-stu-id="d3bb1-120">Relaxed delegates allow you to omit the arguments in such declarations when no ambiguities result.</span></span> <span data-ttu-id="d3bb1-121">在下列範例中，完整指定的方法`OnClick`可以重寫為`RelaxedOnClick`。</span><span class="sxs-lookup"><span data-stu-id="d3bb1-121">In the following example, the fully specified method `OnClick` can be rewritten as `RelaxedOnClick`.</span></span>  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a><span data-ttu-id="d3bb1-122">AddressOf 範例</span><span class="sxs-lookup"><span data-stu-id="d3bb1-122">AddressOf Examples</span></span>  
 <span data-ttu-id="d3bb1-123">針對上述範例中使用 lambda 運算式可讓您輕鬆查看的類型關聯性。</span><span class="sxs-lookup"><span data-stu-id="d3bb1-123">Lambda expressions are used in the previous examples to make the type relationships easy to see.</span></span> <span data-ttu-id="d3bb1-124">不過，使用的委派指派允許相同 relaxations `AddressOf`， `Handles`，或`AddHandler`。</span><span class="sxs-lookup"><span data-stu-id="d3bb1-124">However, the same relaxations are permitted for delegate assignments that use `AddressOf`, `Handles`, or `AddHandler`.</span></span>  
  
 <span data-ttu-id="d3bb1-125">在下列範例中，函式`f1`， `f2`， `f3`，和`f4`所有可指派給`Del1`。</span><span class="sxs-lookup"><span data-stu-id="d3bb1-125">In the following example, functions `f1`, `f2`, `f3`, and `f4` can all be assigned to `Del1`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_9.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_10.vb)]  
  
 <span data-ttu-id="d3bb1-126">下列範例是有效時，才`Option Strict`設`Off`。</span><span class="sxs-lookup"><span data-stu-id="d3bb1-126">The following example is valid only when `Option Strict` is set to `Off`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_11.vb)]  
  
## <a name="dropping-function-returns"></a><span data-ttu-id="d3bb1-127">卸除函數會傳回</span><span class="sxs-lookup"><span data-stu-id="d3bb1-127">Dropping Function Returns</span></span>  
 <span data-ttu-id="d3bb1-128">寬鬆的委派轉換可讓您指派函式來`Sub`委派，有效地略過函式的傳回值。</span><span class="sxs-lookup"><span data-stu-id="d3bb1-128">Relaxed delegate conversion enables you to assign a function to a `Sub` delegate, effectively ignoring the return value of the function.</span></span> <span data-ttu-id="d3bb1-129">不過，您無法指派`Sub`函式委派。</span><span class="sxs-lookup"><span data-stu-id="d3bb1-129">However, you cannot assign a `Sub` to a function delegate.</span></span> <span data-ttu-id="d3bb1-130">在下列範例中，函式的位址`doubler`指派給`Sub`委派`Del3`。</span><span class="sxs-lookup"><span data-stu-id="d3bb1-130">In the following example, the address of function `doubler` is assigned to `Sub` delegate `Del3`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_12.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_13.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d3bb1-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3bb1-131">See Also</span></span>  
 [<span data-ttu-id="d3bb1-132">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="d3bb1-132">Lambda Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="d3bb1-133">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="d3bb1-133">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="d3bb1-134">委派</span><span class="sxs-lookup"><span data-stu-id="d3bb1-134">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="d3bb1-135">如何：在 Visual Basic 中將程序傳遞至其他程序</span><span class="sxs-lookup"><span data-stu-id="d3bb1-135">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [<span data-ttu-id="d3bb1-136">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="d3bb1-136">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="d3bb1-137">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="d3bb1-137">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
