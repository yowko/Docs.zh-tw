---
title: 寬鬆委派轉換 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: e2838b6473b8c00927073a530b4b49870fcfa9c6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600373"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a><span data-ttu-id="f5958-102">寬鬆委派轉換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5958-102">Relaxed Delegate Conversion (Visual Basic)</span></span>
<span data-ttu-id="f5958-103">寬鬆的委派轉換，可讓您將 sub 和函式指派給委派或處理常式，即使它們的簽章並不相同。</span><span class="sxs-lookup"><span data-stu-id="f5958-103">Relaxed delegate conversion enables you to assign subs and functions to delegates or handlers even when their signatures are not identical.</span></span> <span data-ttu-id="f5958-104">因此，委派繫結會變成一致與繫結中允許的方法引動過程。</span><span class="sxs-lookup"><span data-stu-id="f5958-104">Therefore, binding to delegates becomes consistent with the binding already allowed for method invocations.</span></span>  
  
## <a name="parameters-and-return-type"></a><span data-ttu-id="f5958-105">參數和傳回類型</span><span class="sxs-lookup"><span data-stu-id="f5958-105">Parameters and Return Type</span></span>  
 <span data-ttu-id="f5958-106">簽章完全相符項目，取代寬鬆的轉換必須符合下列條件時`Option Strict`設為`On`:</span><span class="sxs-lookup"><span data-stu-id="f5958-106">In place of exact signature match, relaxed conversion requires that the following conditions be met when `Option Strict` is set to `On`:</span></span>  
  
-   <span data-ttu-id="f5958-107">擴展轉換至指派的函式的對應參數的資料類型時，必須從每個委派參數的資料型別或`Sub`。</span><span class="sxs-lookup"><span data-stu-id="f5958-107">A widening conversion must exist from the data type of each delegate parameter to the data type of the corresponding parameter of the assigned function or `Sub`.</span></span> <span data-ttu-id="f5958-108">在下列範例中，委派`Del1`有一個參數， `Integer`。</span><span class="sxs-lookup"><span data-stu-id="f5958-108">In the following example, the delegate `Del1` has one parameter, an `Integer`.</span></span> <span data-ttu-id="f5958-109">參數`m`中指派的 lambda 運算式必須具有擴展轉換的資料類型`Integer`，例如`Long`或`Double`。</span><span class="sxs-lookup"><span data-stu-id="f5958-109">Parameter `m` in the assigned lambda expressions must have a data type for which there is a widening conversion from `Integer`, such as `Long` or `Double`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_2.vb)]  
  
     <span data-ttu-id="f5958-110">縮小轉換允許時，才`Option Strict`設為`Off`。</span><span class="sxs-lookup"><span data-stu-id="f5958-110">Narrowing conversions are permitted only when `Option Strict` is set to `Off`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_3.vb)]  
  
-   <span data-ttu-id="f5958-111">擴展轉換必須存在於相反的方向，從指派的函式的傳回型別或`Sub`委派的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="f5958-111">A widening conversion must exist in the opposite direction from the return type of the assigned function or `Sub` to the return type of the delegate.</span></span> <span data-ttu-id="f5958-112">在下列範例中，每個指派的 lambda 運算式的主體必須評估為資料類型可擴展成`Integer`的傳回類型，因為`del1`是`Integer`。</span><span class="sxs-lookup"><span data-stu-id="f5958-112">In the following examples, the body of each assigned lambda expression must evaluate to a data type that widens to `Integer` because the return type of `del1` is `Integer`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_4.vb)]  
  
 <span data-ttu-id="f5958-113">如果`Option Strict`設為`Off`、 擴展限制兩個方向中已移除。</span><span class="sxs-lookup"><span data-stu-id="f5958-113">If `Option Strict` is set to `Off`, the widening restriction is removed in both directions.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_5.vb)]  
  
## <a name="omitting-parameter-specifications"></a><span data-ttu-id="f5958-114">省略參數規格</span><span class="sxs-lookup"><span data-stu-id="f5958-114">Omitting Parameter Specifications</span></span>  
 <span data-ttu-id="f5958-115">寬鬆的委派也可讓您完全略過指派方法中的參數規格：</span><span class="sxs-lookup"><span data-stu-id="f5958-115">Relaxed delegates also allow you to completely omit parameter specifications in the assigned method:</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_6.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_7.vb)]  
  
 <span data-ttu-id="f5958-116">請注意，您無法指定一些參數並省略其他人。</span><span class="sxs-lookup"><span data-stu-id="f5958-116">Note that you cannot specify some parameters and omit others.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_8.vb)]  
  
 <span data-ttu-id="f5958-117">省略參數的能力是很有幫助的情況下，例如定義事件處理常式，其中牽涉到多個複雜參數。</span><span class="sxs-lookup"><span data-stu-id="f5958-117">The ability to omit parameters is helpful in a situation such as defining an event handler, where several complex parameters are involved.</span></span> <span data-ttu-id="f5958-118">不會使用一些事件處理常式的引數。</span><span class="sxs-lookup"><span data-stu-id="f5958-118">The arguments to some event handlers are not used.</span></span> <span data-ttu-id="f5958-119">相反地，處理常式直接存取的控制項的事件註冊，並會忽略引數的狀態。</span><span class="sxs-lookup"><span data-stu-id="f5958-119">Instead, the handler directly accesses the state of the control on which the event is registered, and ignores the arguments.</span></span> <span data-ttu-id="f5958-120">寬鬆的委派可讓您略過這類宣告時沒有模稜兩可的結果中的引數。</span><span class="sxs-lookup"><span data-stu-id="f5958-120">Relaxed delegates allow you to omit the arguments in such declarations when no ambiguities result.</span></span> <span data-ttu-id="f5958-121">在下列範例中，完整指定的方法`OnClick`可以重寫為`RelaxedOnClick`。</span><span class="sxs-lookup"><span data-stu-id="f5958-121">In the following example, the fully specified method `OnClick` can be rewritten as `RelaxedOnClick`.</span></span>  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a><span data-ttu-id="f5958-122">AddressOf 範例</span><span class="sxs-lookup"><span data-stu-id="f5958-122">AddressOf Examples</span></span>  
 <span data-ttu-id="f5958-123">前一個範例中所用 lambda 運算式，以方便看到的類型關聯性。</span><span class="sxs-lookup"><span data-stu-id="f5958-123">Lambda expressions are used in the previous examples to make the type relationships easy to see.</span></span> <span data-ttu-id="f5958-124">不過，允許使用的委派指派相同 relaxations `AddressOf`， `Handles`，或`AddHandler`。</span><span class="sxs-lookup"><span data-stu-id="f5958-124">However, the same relaxations are permitted for delegate assignments that use `AddressOf`, `Handles`, or `AddHandler`.</span></span>  
  
 <span data-ttu-id="f5958-125">在下列範例中，函式`f1`， `f2`， `f3`，以及`f4`所有可指派給`Del1`。</span><span class="sxs-lookup"><span data-stu-id="f5958-125">In the following example, functions `f1`, `f2`, `f3`, and `f4` can all be assigned to `Del1`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_9.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_10.vb)]  
  
 <span data-ttu-id="f5958-126">下列範例是時才有效`Option Strict`設為`Off`。</span><span class="sxs-lookup"><span data-stu-id="f5958-126">The following example is valid only when `Option Strict` is set to `Off`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_11.vb)]  
  
## <a name="dropping-function-returns"></a><span data-ttu-id="f5958-127">卸除函數會傳回</span><span class="sxs-lookup"><span data-stu-id="f5958-127">Dropping Function Returns</span></span>  
 <span data-ttu-id="f5958-128">寬鬆的委派轉換可讓您指派的函式`Sub`委派，有效地略過函式的傳回值。</span><span class="sxs-lookup"><span data-stu-id="f5958-128">Relaxed delegate conversion enables you to assign a function to a `Sub` delegate, effectively ignoring the return value of the function.</span></span> <span data-ttu-id="f5958-129">不過，您無法指派`Sub`函式委派。</span><span class="sxs-lookup"><span data-stu-id="f5958-129">However, you cannot assign a `Sub` to a function delegate.</span></span> <span data-ttu-id="f5958-130">在下列範例中，函式的位址`doubler`指派給`Sub`委派`Del3`。</span><span class="sxs-lookup"><span data-stu-id="f5958-130">In the following example, the address of function `doubler` is assigned to `Sub` delegate `Del3`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_12.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_13.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f5958-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5958-131">See also</span></span>
- [<span data-ttu-id="f5958-132">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="f5958-132">Lambda Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="f5958-133">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="f5958-133">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="f5958-134">委派</span><span class="sxs-lookup"><span data-stu-id="f5958-134">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="f5958-135">如何：傳遞至另一個程序，在 Visual Basic 中的程序</span><span class="sxs-lookup"><span data-stu-id="f5958-135">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="f5958-136">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="f5958-136">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="f5958-137">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="f5958-137">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
