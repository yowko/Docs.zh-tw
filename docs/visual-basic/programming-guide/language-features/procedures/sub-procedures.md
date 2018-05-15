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
ms.openlocfilehash: 3286df1a5babfcf7d6b759ff5c9a920bb44f51ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="sub-procedures-visual-basic"></a><span data-ttu-id="fbedb-102">Sub 程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbedb-102">Sub Procedures (Visual Basic)</span></span>
<span data-ttu-id="fbedb-103">A`Sub`程序是一系列的 Visual Basic 陳述式加上`Sub`和`End Sub`陳述式。</span><span class="sxs-lookup"><span data-stu-id="fbedb-103">A `Sub` procedure is a series of Visual Basic statements enclosed by the `Sub` and `End Sub` statements.</span></span> <span data-ttu-id="fbedb-104">`Sub`程序執行的工作，並再將控制權傳回給呼叫的程式碼，但不會傳回值，呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="fbedb-104">The `Sub` procedure performs a task and then returns control to the calling code, but it does not return a value to the calling code.</span></span>  
  
 <span data-ttu-id="fbedb-105">每次呼叫程序時，其執行陳述式，從開始之後的第一個可執行陳述式`Sub`陳述式，並與第一個結束`End Sub`， `Exit Sub`，或`Return`出現陳述式。</span><span class="sxs-lookup"><span data-stu-id="fbedb-105">Each time the procedure is called, its statements are executed, starting with the first executable statement after the `Sub` statement and ending with the first `End Sub`, `Exit Sub`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="fbedb-106">您可以定義`Sub`模組、 類別和結構中的程序。</span><span class="sxs-lookup"><span data-stu-id="fbedb-106">You can define a `Sub` procedure in modules, classes, and structures.</span></span> <span data-ttu-id="fbedb-107">根據預設，它是`Public`，這表示您可以呼叫從任何地方存取模組、 類別或結構定義它的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="fbedb-107">By default, it is `Public`, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span> <span data-ttu-id="fbedb-108">詞彙*方法*，描述`Sub`或`Function`從其定義外部存取的程序模組、 類別或結構。</span><span class="sxs-lookup"><span data-stu-id="fbedb-108">The term, *method*, describes a `Sub` or `Function` procedure that is accessed from outside its defining module, class, or structure.</span></span> <span data-ttu-id="fbedb-109">如需詳細資訊，請參閱[程序](./index.md)。</span><span class="sxs-lookup"><span data-stu-id="fbedb-109">For more information, see [Procedures](./index.md).</span></span>  
  
 <span data-ttu-id="fbedb-110">A`Sub`程序可以接受引數，例如常數、 變數或運算式，則呼叫程式碼傳遞給它。</span><span class="sxs-lookup"><span data-stu-id="fbedb-110">A `Sub` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="fbedb-111">宣告語法</span><span class="sxs-lookup"><span data-stu-id="fbedb-111">Declaration Syntax</span></span>  
 <span data-ttu-id="fbedb-112">宣告的語法`Sub`程序如下所示：</span><span class="sxs-lookup"><span data-stu-id="fbedb-112">The syntax for declaring a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="fbedb-113">`[` *修飾詞* `] Sub` *subname* `[(` *parameterlist* `)]`</span><span class="sxs-lookup"><span data-stu-id="fbedb-113">`[` *modifiers* `] Sub`  *subname* `[(` *parameterlist* `)]`</span></span>  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 <span data-ttu-id="fbedb-114">`modifiers`可以指定存取層級和多載，覆寫、 共用、 與遮蔽的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fbedb-114">The `modifiers` can specify access level and information about overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="fbedb-115">如需詳細資訊，請參閱[Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="fbedb-115">For more information, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="fbedb-116">參數宣告</span><span class="sxs-lookup"><span data-stu-id="fbedb-116">Parameter Declaration</span></span>  
 <span data-ttu-id="fbedb-117">您宣告類似於如何您宣告一個變數，指定參數名稱和資料類型的每個程序參數。</span><span class="sxs-lookup"><span data-stu-id="fbedb-117">You declare each procedure parameter similarly to how you declare a variable, specifying the parameter name and data type.</span></span> <span data-ttu-id="fbedb-118">您也可以指定傳遞機制，以及參數是選擇性或參數陣列。</span><span class="sxs-lookup"><span data-stu-id="fbedb-118">You can also specify the passing mechanism, and whether the parameter is optional or a parameter array.</span></span>  
  
 <span data-ttu-id="fbedb-119">參數清單中的每個參數的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="fbedb-119">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 <span data-ttu-id="fbedb-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *參數名稱*`As`*資料類型*</span><span class="sxs-lookup"><span data-stu-id="fbedb-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*  `As`  *datatype*</span></span>  
  
 <span data-ttu-id="fbedb-121">如果參數是選擇性的您也必須提供預設值做為其宣告的一部分。</span><span class="sxs-lookup"><span data-stu-id="fbedb-121">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="fbedb-122">指定預設值的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="fbedb-122">The syntax for specifying a default value is as follows:</span></span>  
  
 <span data-ttu-id="fbedb-123">`Optional [ByVal | ByRef]`  *參數名稱*`As`*datatype*`=`*defaultvalue*</span><span class="sxs-lookup"><span data-stu-id="fbedb-123">`Optional [ByVal | ByRef]`  *parametername*  `As`  *datatype*  `=`  *defaultvalue*</span></span>  
  
### <a name="parameters-as-local-variables"></a><span data-ttu-id="fbedb-124">本機變數與參數</span><span class="sxs-lookup"><span data-stu-id="fbedb-124">Parameters as Local Variables</span></span>  
 <span data-ttu-id="fbedb-125">當控制權會傳遞至程序中時，每個參數會被視為本機變數中。</span><span class="sxs-lookup"><span data-stu-id="fbedb-125">When control passes to the procedure, each parameter is treated as a local variable.</span></span> <span data-ttu-id="fbedb-126">這表示，其存留期相同的程序，且其範圍是整個程序。</span><span class="sxs-lookup"><span data-stu-id="fbedb-126">This means that its lifetime is the same as that of the procedure, and its scope is the whole procedure.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="fbedb-127">呼叫語法</span><span class="sxs-lookup"><span data-stu-id="fbedb-127">Calling Syntax</span></span>  
 <span data-ttu-id="fbedb-128">您可以叫用`Sub`明確地使用獨立的呼叫陳述式的程序。</span><span class="sxs-lookup"><span data-stu-id="fbedb-128">You invoke a `Sub` procedure explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="fbedb-129">您無法呼叫它在運算式中使用該名稱。</span><span class="sxs-lookup"><span data-stu-id="fbedb-129">You cannot call it by using its name in an expression.</span></span> <span data-ttu-id="fbedb-130">您必須提供值給不是選擇性的所有引數，您必須將引數清單括在括號中。</span><span class="sxs-lookup"><span data-stu-id="fbedb-130">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="fbedb-131">如果已不提供任何引數，您可以選擇性地省略括號。</span><span class="sxs-lookup"><span data-stu-id="fbedb-131">If no arguments are supplied, you can optionally omit the parentheses.</span></span> <span data-ttu-id="fbedb-132">使用`Call`關鍵字是選擇性的但不是建議使用。</span><span class="sxs-lookup"><span data-stu-id="fbedb-132">The use of the `Call` keyword is optional but not recommended.</span></span>  
  
 <span data-ttu-id="fbedb-133">若要呼叫的語法`Sub`程序如下所示：</span><span class="sxs-lookup"><span data-stu-id="fbedb-133">The syntax for a call to a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="fbedb-134">`[Call]`  *subname* `[(` *argumentlist* `)]`</span><span class="sxs-lookup"><span data-stu-id="fbedb-134">`[Call]`  *subname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="fbedb-135">您可以呼叫`Sub`方法從其定義在類別外部。</span><span class="sxs-lookup"><span data-stu-id="fbedb-135">You can call a `Sub` method from outside the class that defines it.</span></span> <span data-ttu-id="fbedb-136">首先，您必須使用`New`關鍵字來建立類別的執行個體，或呼叫的方法會傳回類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="fbedb-136">First, you have to use the `New` keyword to create an instance of the class, or call a method that returns an instance of the class.</span></span> <span data-ttu-id="fbedb-137">如需詳細資訊，請參閱[New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="fbedb-137">For more information, see [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="fbedb-138">然後，您可以使用下列語法來呼叫`Sub`執行個體物件上的方法：</span><span class="sxs-lookup"><span data-stu-id="fbedb-138">Then, you can use the following syntax to call the `Sub` method on the instance object:</span></span>  
  
 <span data-ttu-id="fbedb-139">*物件*。*methodname*`[(`*argumentlist*`)]`</span><span class="sxs-lookup"><span data-stu-id="fbedb-139">*Object*.*methodname*`[(`*argumentlist*`)]`</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="fbedb-140">宣告和呼叫的圖例</span><span class="sxs-lookup"><span data-stu-id="fbedb-140">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="fbedb-141">下列`Sub`程序會告訴電腦運算子在即將執行時，應用程式的工作也會顯示時間戳記。</span><span class="sxs-lookup"><span data-stu-id="fbedb-141">The following `Sub` procedure tells the computer operator which task the application is about to perform, and also displays a time stamp.</span></span> <span data-ttu-id="fbedb-142">而不必重複此程式碼在每個工作的開始，應用程式只會呼叫`tellOperator`從各種不同的位置。</span><span class="sxs-lookup"><span data-stu-id="fbedb-142">Instead of duplicating this code at the start of every task, the application just calls `tellOperator` from various locations.</span></span> <span data-ttu-id="fbedb-143">每個呼叫會傳遞的字串`task`識別正在啟動工作的引數。</span><span class="sxs-lookup"><span data-stu-id="fbedb-143">Each call passes a string in the `task` argument that identifies the task being started.</span></span>  
  
 [!code-vb[VbVbcnProcedures#2](./codesnippet/VisualBasic/sub-procedures_1.vb)]  
  
 <span data-ttu-id="fbedb-144">下列範例會示範一般呼叫`tellOperator`。</span><span class="sxs-lookup"><span data-stu-id="fbedb-144">The following example shows a typical call to `tellOperator`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#3](./codesnippet/VisualBasic/sub-procedures_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fbedb-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbedb-145">See Also</span></span>  
 [<span data-ttu-id="fbedb-146">程序</span><span class="sxs-lookup"><span data-stu-id="fbedb-146">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="fbedb-147">函式程序</span><span class="sxs-lookup"><span data-stu-id="fbedb-147">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="fbedb-148">屬性程序</span><span class="sxs-lookup"><span data-stu-id="fbedb-148">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="fbedb-149">運算子程序</span><span class="sxs-lookup"><span data-stu-id="fbedb-149">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="fbedb-150">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="fbedb-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="fbedb-151">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="fbedb-151">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="fbedb-152">如何：呼叫不傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="fbedb-152">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)  
 [<span data-ttu-id="fbedb-153">如何： 在 Visual Basic 中呼叫事件處理常式</span><span class="sxs-lookup"><span data-stu-id="fbedb-153">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
