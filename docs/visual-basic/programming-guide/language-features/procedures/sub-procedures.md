---
title: Sub 程序 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Sub procedures [Visual Basic], about Sub procedures
- statement blocks
- Sub procedures [Visual Basic], calling
- procedures [Visual Basic], calling
- Sub procedures [Visual Basic], syntax
- Sub procedures
- procedures [Visual Basic], Sub
- syntax [Visual Basic], Sub procedures
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
ms.openlocfilehash: 646d7d217891dc8ea5b78f7ce30fce19fab08316
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977574"
---
# <a name="sub-procedures-visual-basic"></a><span data-ttu-id="300c8-102">Sub 程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="300c8-102">Sub Procedures (Visual Basic)</span></span>
<span data-ttu-id="300c8-103">A`Sub`程序是一系列的 Visual Basic 陳述式加上`Sub`和`End Sub`陳述式。</span><span class="sxs-lookup"><span data-stu-id="300c8-103">A `Sub` procedure is a series of Visual Basic statements enclosed by the `Sub` and `End Sub` statements.</span></span> <span data-ttu-id="300c8-104">`Sub`程序執行的工作，然後將控制權傳回呼叫的程式碼，但它不會傳回呼叫程式碼的值。</span><span class="sxs-lookup"><span data-stu-id="300c8-104">The `Sub` procedure performs a task and then returns control to the calling code, but it does not return a value to the calling code.</span></span>  
  
 <span data-ttu-id="300c8-105">每次呼叫此程序時，其會執行陳述式，從開始之後的第一個可執行陳述式`Sub`陳述式，並與第一個結束`End Sub`， `Exit Sub`，或`Return`陳述式時發生。</span><span class="sxs-lookup"><span data-stu-id="300c8-105">Each time the procedure is called, its statements are executed, starting with the first executable statement after the `Sub` statement and ending with the first `End Sub`, `Exit Sub`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="300c8-106">您可以定義`Sub`模組、 類別和結構中的程序。</span><span class="sxs-lookup"><span data-stu-id="300c8-106">You can define a `Sub` procedure in modules, classes, and structures.</span></span> <span data-ttu-id="300c8-107">根據預設，它是`Public`，這表示您可以呼叫它從任何地方存取模組、 類別或結構定義它的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="300c8-107">By default, it is `Public`, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span> <span data-ttu-id="300c8-108">詞彙*方法*，說明`Sub`或`Function`從其定義外部存取的程序模組、 類別或結構。</span><span class="sxs-lookup"><span data-stu-id="300c8-108">The term, *method*, describes a `Sub` or `Function` procedure that is accessed from outside its defining module, class, or structure.</span></span> <span data-ttu-id="300c8-109">如需詳細資訊，請參閱[程序](./index.md)。</span><span class="sxs-lookup"><span data-stu-id="300c8-109">For more information, see [Procedures](./index.md).</span></span>  
  
 <span data-ttu-id="300c8-110">A`Sub`程序可以取得引數，例如常數、 變數或運算式，這會傳遞給它所呼叫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="300c8-110">A `Sub` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="300c8-111">宣告語法</span><span class="sxs-lookup"><span data-stu-id="300c8-111">Declaration Syntax</span></span>  
 <span data-ttu-id="300c8-112">宣告的語法`Sub`程序如下所示：</span><span class="sxs-lookup"><span data-stu-id="300c8-112">The syntax for declaring a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="300c8-113">`[` *modifiers* `] Sub`  *subname* `[(` *parameterlist* `)]`</span><span class="sxs-lookup"><span data-stu-id="300c8-113">`[` *modifiers* `] Sub`  *subname* `[(` *parameterlist* `)]`</span></span>  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 <span data-ttu-id="300c8-114">`modifiers`可以指定存取層級和多載、 覆寫，將分享，與遮蔽的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="300c8-114">The `modifiers` can specify access level and information about overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="300c8-115">如需詳細資訊，請參閱 < [Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="300c8-115">For more information, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="300c8-116">參數宣告</span><span class="sxs-lookup"><span data-stu-id="300c8-116">Parameter Declaration</span></span>  
 <span data-ttu-id="300c8-117">您宣告類似於如何宣告變數，指定參數名稱和資料類型的每個程序參數。</span><span class="sxs-lookup"><span data-stu-id="300c8-117">You declare each procedure parameter similarly to how you declare a variable, specifying the parameter name and data type.</span></span> <span data-ttu-id="300c8-118">您也可以指定傳遞機制，以及是否為選擇性參數或參數陣列。</span><span class="sxs-lookup"><span data-stu-id="300c8-118">You can also specify the passing mechanism, and whether the parameter is optional or a parameter array.</span></span>  
  
 <span data-ttu-id="300c8-119">參數清單中的每個參數的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="300c8-119">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 <span data-ttu-id="300c8-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*  `As`  *datatype*</span><span class="sxs-lookup"><span data-stu-id="300c8-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*  `As`  *datatype*</span></span>  
  
 <span data-ttu-id="300c8-121">如果參數是選擇性的您還必須提供預設值做為其宣告的一部分。</span><span class="sxs-lookup"><span data-stu-id="300c8-121">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="300c8-122">指定預設值的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="300c8-122">The syntax for specifying a default value is as follows:</span></span>  
  
 <span data-ttu-id="300c8-123">`Optional [ByVal | ByRef]`  *parametername*  `As`  *datatype*  `=`  *defaultvalue*</span><span class="sxs-lookup"><span data-stu-id="300c8-123">`Optional [ByVal | ByRef]`  *parametername*  `As`  *datatype*  `=`  *defaultvalue*</span></span>  
  
### <a name="parameters-as-local-variables"></a><span data-ttu-id="300c8-124">本機變數與參數</span><span class="sxs-lookup"><span data-stu-id="300c8-124">Parameters as Local Variables</span></span>  
 <span data-ttu-id="300c8-125">當控制權會傳遞至程序時，當做本機變數來處理每個參數。</span><span class="sxs-lookup"><span data-stu-id="300c8-125">When control passes to the procedure, each parameter is treated as a local variable.</span></span> <span data-ttu-id="300c8-126">這表示，其存留期與相同的程序，其範圍是整個程序。</span><span class="sxs-lookup"><span data-stu-id="300c8-126">This means that its lifetime is the same as that of the procedure, and its scope is the whole procedure.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="300c8-127">呼叫語法</span><span class="sxs-lookup"><span data-stu-id="300c8-127">Calling Syntax</span></span>  
 <span data-ttu-id="300c8-128">您可以叫用`Sub`明確地使用獨立的呼叫陳述式的程序。</span><span class="sxs-lookup"><span data-stu-id="300c8-128">You invoke a `Sub` procedure explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="300c8-129">您無法在運算式中使用它的名稱來呼叫它。</span><span class="sxs-lookup"><span data-stu-id="300c8-129">You cannot call it by using its name in an expression.</span></span> <span data-ttu-id="300c8-130">您必須提供值不是選擇性的所有引數，您必須將引數清單括在括號中。</span><span class="sxs-lookup"><span data-stu-id="300c8-130">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="300c8-131">如果已不提供任何引數，您可以選擇性地省略括號。</span><span class="sxs-lookup"><span data-stu-id="300c8-131">If no arguments are supplied, you can optionally omit the parentheses.</span></span> <span data-ttu-id="300c8-132">使用`Call`關鍵字是選擇性的但不是建議使用。</span><span class="sxs-lookup"><span data-stu-id="300c8-132">The use of the `Call` keyword is optional but not recommended.</span></span>  
  
 <span data-ttu-id="300c8-133">呼叫語法`Sub`程序如下所示：</span><span class="sxs-lookup"><span data-stu-id="300c8-133">The syntax for a call to a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="300c8-134">`[Call]`  *subname* `[(` *argumentlist* `)]`</span><span class="sxs-lookup"><span data-stu-id="300c8-134">`[Call]`  *subname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="300c8-135">您可以呼叫`Sub`方法外定義它的類別。</span><span class="sxs-lookup"><span data-stu-id="300c8-135">You can call a `Sub` method from outside the class that defines it.</span></span> <span data-ttu-id="300c8-136">首先，您必須使用`New`關鍵字來建立類別的執行個體，或呼叫方法會傳回類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="300c8-136">First, you have to use the `New` keyword to create an instance of the class, or call a method that returns an instance of the class.</span></span> <span data-ttu-id="300c8-137">如需詳細資訊，請參閱 < [New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="300c8-137">For more information, see [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="300c8-138">然後，您可以使用下列語法來呼叫`Sub`執行個體物件上的方法：</span><span class="sxs-lookup"><span data-stu-id="300c8-138">Then, you can use the following syntax to call the `Sub` method on the instance object:</span></span>  
  
 <span data-ttu-id="300c8-139">*物件*。*methodname*`[(`*argumentlist*`)]`</span><span class="sxs-lookup"><span data-stu-id="300c8-139">*Object*.*methodname*`[(`*argumentlist*`)]`</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="300c8-140">宣告和呼叫的圖例</span><span class="sxs-lookup"><span data-stu-id="300c8-140">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="300c8-141">下列`Sub`程序會告訴電腦運算子的應用程式即將執行的工作，也會顯示時間戳記。</span><span class="sxs-lookup"><span data-stu-id="300c8-141">The following `Sub` procedure tells the computer operator which task the application is about to perform, and also displays a time stamp.</span></span> <span data-ttu-id="300c8-142">而不必重複此程式碼開頭的每項工作，應用程式只會呼叫`tellOperator`從各種不同的位置。</span><span class="sxs-lookup"><span data-stu-id="300c8-142">Instead of duplicating this code at the start of every task, the application just calls `tellOperator` from various locations.</span></span> <span data-ttu-id="300c8-143">每個呼叫會傳遞的字串`task`識別啟動之工作的引數。</span><span class="sxs-lookup"><span data-stu-id="300c8-143">Each call passes a string in the `task` argument that identifies the task being started.</span></span>  
  
 [!code-vb[VbVbcnProcedures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#2)]  
  
 <span data-ttu-id="300c8-144">下列範例示範的典型呼叫`tellOperator`。</span><span class="sxs-lookup"><span data-stu-id="300c8-144">The following example shows a typical call to `tellOperator`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="300c8-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="300c8-145">See also</span></span>
- [<span data-ttu-id="300c8-146">程序</span><span class="sxs-lookup"><span data-stu-id="300c8-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="300c8-147">函式程序</span><span class="sxs-lookup"><span data-stu-id="300c8-147">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="300c8-148">屬性程序</span><span class="sxs-lookup"><span data-stu-id="300c8-148">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="300c8-149">運算子程序</span><span class="sxs-lookup"><span data-stu-id="300c8-149">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="300c8-150">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="300c8-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="300c8-151">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="300c8-151">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="300c8-152">如何：呼叫不傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="300c8-152">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
- [<span data-ttu-id="300c8-153">如何：在 Visual Basic 中呼叫事件處理常式</span><span class="sxs-lookup"><span data-stu-id="300c8-153">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
