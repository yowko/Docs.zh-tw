---
title: "Sub 程序 (Visual Basic) |Microsoft 文件"
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
- Sub procedures, about Sub procedures
- statement blocks
- Sub procedures, calling
- procedures, calling
- Sub procedures, syntax
- Sub procedures
- procedures, Sub
- syntax, Sub procedures
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
caps.latest.revision: 21
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
ms.openlocfilehash: 83f0a16498accf383da96d702c4e3a4b7de1c861
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="sub-procedures-visual-basic"></a><span data-ttu-id="c9724-102">Sub 程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9724-102">Sub Procedures (Visual Basic)</span></span>
<span data-ttu-id="c9724-103">A`Sub`程序是一系列的[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]陳述式括住`Sub`和`End Sub`陳述式。</span><span class="sxs-lookup"><span data-stu-id="c9724-103">A `Sub` procedure is a series of [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] statements enclosed by the `Sub` and `End Sub` statements.</span></span> <span data-ttu-id="c9724-104">`Sub`程序執行的工作，然後將控制權還給呼叫的程式碼，但它不會傳回呼叫程式碼的值。</span><span class="sxs-lookup"><span data-stu-id="c9724-104">The `Sub` procedure performs a task and then returns control to the calling code, but it does not return a value to the calling code.</span></span>  
  
 <span data-ttu-id="c9724-105">每次呼叫此程序時，其執行陳述式，從開始之後的第一個可執行陳述式`Sub`陳述式，直到第一個`End Sub`， `Exit Sub`，或`Return`陳述式時發生。</span><span class="sxs-lookup"><span data-stu-id="c9724-105">Each time the procedure is called, its statements are executed, starting with the first executable statement after the `Sub` statement and ending with the first `End Sub`, `Exit Sub`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="c9724-106">您可以定義`Sub`模組、 類別和結構中的程序。</span><span class="sxs-lookup"><span data-stu-id="c9724-106">You can define a `Sub` procedure in modules, classes, and structures.</span></span> <span data-ttu-id="c9724-107">根據預設，它是`Public`，這表示您可以呼叫從任何地方存取模組、 類別或結構定義它的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="c9724-107">By default, it is `Public`, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span> <span data-ttu-id="c9724-108">詞彙，*方法*，描述`Sub`或`Function`從其定義外部存取的程序模組、 類別或結構。</span><span class="sxs-lookup"><span data-stu-id="c9724-108">The term, *method*, describes a `Sub` or `Function` procedure that is accessed from outside its defining module, class, or structure.</span></span> <span data-ttu-id="c9724-109">如需詳細資訊，請參閱[程序](./index.md)。</span><span class="sxs-lookup"><span data-stu-id="c9724-109">For more information, see [Procedures](./index.md).</span></span>  
  
 <span data-ttu-id="c9724-110">A`Sub`程序可以取得引數，例如常數、 變數或運算式，則呼叫程式碼傳遞給它。</span><span class="sxs-lookup"><span data-stu-id="c9724-110">A `Sub` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="c9724-111">宣告語法</span><span class="sxs-lookup"><span data-stu-id="c9724-111">Declaration Syntax</span></span>  
 <span data-ttu-id="c9724-112">宣告的語法`Sub`程序如下︰</span><span class="sxs-lookup"><span data-stu-id="c9724-112">The syntax for declaring a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="c9724-113">`[`*modifiers* `] Sub`*subname* `[(` *parameterlist*  `)]`</span><span class="sxs-lookup"><span data-stu-id="c9724-113">`[` *modifiers* `] Sub`  *subname* `[(` *parameterlist* `)]`</span></span>  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 <span data-ttu-id="c9724-114">`modifiers`可以指定存取層級和多載、 覆寫、 共用、 及遮蔽的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c9724-114">The `modifiers` can specify access level and information about overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="c9724-115">如需詳細資訊，請參閱[Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="c9724-115">For more information, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="c9724-116">參數宣告</span><span class="sxs-lookup"><span data-stu-id="c9724-116">Parameter Declaration</span></span>  
 <span data-ttu-id="c9724-117">您可以宣告類似於如何宣告變數，指定參數名稱和資料類型的每個程序參數。</span><span class="sxs-lookup"><span data-stu-id="c9724-117">You declare each procedure parameter similarly to how you declare a variable, specifying the parameter name and data type.</span></span> <span data-ttu-id="c9724-118">您也可以指定傳遞機制，以及是否為選擇性參數或參數陣列。</span><span class="sxs-lookup"><span data-stu-id="c9724-118">You can also specify the passing mechanism, and whether the parameter is optional or a parameter array.</span></span>  
  
 <span data-ttu-id="c9724-119">參數清單中的每個參數的語法如下所示︰</span><span class="sxs-lookup"><span data-stu-id="c9724-119">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 <span data-ttu-id="c9724-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*`As`*資料型別    *</span><span class="sxs-lookup"><span data-stu-id="c9724-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*  `As`  *datatype*</span></span>  
  
 <span data-ttu-id="c9724-121">如果參數是選擇性的您也必須提供預設值，如其宣告的一部分。</span><span class="sxs-lookup"><span data-stu-id="c9724-121">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="c9724-122">指定預設值的語法如下所示︰</span><span class="sxs-lookup"><span data-stu-id="c9724-122">The syntax for specifying a default value is as follows:</span></span>  
  
 <span data-ttu-id="c9724-123">`Optional [ByVal | ByRef]`  *parametername*`As`*資料型別*`=`*預設值        *</span><span class="sxs-lookup"><span data-stu-id="c9724-123">`Optional [ByVal | ByRef]`  *parametername*  `As`  *datatype*  `=`  *defaultvalue*</span></span>  
  
### <a name="parameters-as-local-variables"></a><span data-ttu-id="c9724-124">本機變數與參數</span><span class="sxs-lookup"><span data-stu-id="c9724-124">Parameters as Local Variables</span></span>  
 <span data-ttu-id="c9724-125">當控制權會傳遞至程序時，每個參數會被視為本機變數中。</span><span class="sxs-lookup"><span data-stu-id="c9724-125">When control passes to the procedure, each parameter is treated as a local variable.</span></span> <span data-ttu-id="c9724-126">這表示，其存留期相同的程序，且其範圍是整個程序。</span><span class="sxs-lookup"><span data-stu-id="c9724-126">This means that its lifetime is the same as that of the procedure, and its scope is the whole procedure.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="c9724-127">呼叫語法</span><span class="sxs-lookup"><span data-stu-id="c9724-127">Calling Syntax</span></span>  
 <span data-ttu-id="c9724-128">您可以叫用`Sub`明確地用獨立呼叫的陳述式的程序。</span><span class="sxs-lookup"><span data-stu-id="c9724-128">You invoke a `Sub` procedure explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="c9724-129">您無法使用該名稱在運算式中呼叫它。</span><span class="sxs-lookup"><span data-stu-id="c9724-129">You cannot call it by using its name in an expression.</span></span> <span data-ttu-id="c9724-130">您必須提供值不是選擇性的所有引數，您必須將引數清單括在括號中。</span><span class="sxs-lookup"><span data-stu-id="c9724-130">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="c9724-131">如果已不提供任何引數，您可以省略括號。</span><span class="sxs-lookup"><span data-stu-id="c9724-131">If no arguments are supplied, you can optionally omit the parentheses.</span></span> <span data-ttu-id="c9724-132">使用`Call`關鍵字是選擇性的但不是建議使用。</span><span class="sxs-lookup"><span data-stu-id="c9724-132">The use of the `Call` keyword is optional but not recommended.</span></span>  
  
 <span data-ttu-id="c9724-133">呼叫語法`Sub`程序如下︰</span><span class="sxs-lookup"><span data-stu-id="c9724-133">The syntax for a call to a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="c9724-134">`[Call]`  *subname* `[(` *argumentlist*`)]`</span><span class="sxs-lookup"><span data-stu-id="c9724-134">`[Call]`  *subname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="c9724-135">您可以呼叫`Sub`方法從其定義在類別之外。</span><span class="sxs-lookup"><span data-stu-id="c9724-135">You can call a `Sub` method from outside the class that defines it.</span></span> <span data-ttu-id="c9724-136">首先，您必須使用`New`關鍵字來建立類別的執行個體或呼叫的方法會傳回類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c9724-136">First, you have to use the `New` keyword to create an instance of the class, or call a method that returns an instance of the class.</span></span> <span data-ttu-id="c9724-137">如需詳細資訊，請參閱[New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="c9724-137">For more information, see [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="c9724-138">然後，您可以使用下列語法來呼叫`Sub`執行個體物件上的方法︰</span><span class="sxs-lookup"><span data-stu-id="c9724-138">Then, you can use the following syntax to call the `Sub` method on the instance object:</span></span>  
  
 <span data-ttu-id="c9724-139">*Object*.*methodname*`[(`*argumentlist*`)]`</span><span class="sxs-lookup"><span data-stu-id="c9724-139">*Object*.*methodname*`[(`*argumentlist*`)]`</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="c9724-140">宣告和呼叫的圖例</span><span class="sxs-lookup"><span data-stu-id="c9724-140">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="c9724-141">下列`Sub`程序會告知電腦運算子若要執行，應用程式的工作也會顯示時間戳記。</span><span class="sxs-lookup"><span data-stu-id="c9724-141">The following `Sub` procedure tells the computer operator which task the application is about to perform, and also displays a time stamp.</span></span> <span data-ttu-id="c9724-142">而不必重複此程式碼開頭的每項工作，應用程式只會呼叫`tellOperator`從不同位置。</span><span class="sxs-lookup"><span data-stu-id="c9724-142">Instead of duplicating this code at the start of every task, the application just calls `tellOperator` from various locations.</span></span> <span data-ttu-id="c9724-143">每個呼叫會傳遞的字串`task`識別正在啟動工作的引數。</span><span class="sxs-lookup"><span data-stu-id="c9724-143">Each call passes a string in the `task` argument that identifies the task being started.</span></span>  
  
 <span data-ttu-id="c9724-144">[!code-vb[VbVbcnProcedures #&2;](./codesnippet/VisualBasic/sub-procedures_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c9724-144">[!code-vb[VbVbcnProcedures#2](./codesnippet/VisualBasic/sub-procedures_1.vb)]</span></span>  
  
 <span data-ttu-id="c9724-145">下列範例會示範一般呼叫`tellOperator`。</span><span class="sxs-lookup"><span data-stu-id="c9724-145">The following example shows a typical call to `tellOperator`.</span></span>  
  
 <span data-ttu-id="c9724-146">[!code-vb[VbVbcnProcedures #&3;](./codesnippet/VisualBasic/sub-procedures_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="c9724-146">[!code-vb[VbVbcnProcedures#3](./codesnippet/VisualBasic/sub-procedures_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9724-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9724-147">See Also</span></span>  
 <span data-ttu-id="c9724-148">[程序](./index.md) </span><span class="sxs-lookup"><span data-stu-id="c9724-148">[Procedures](./index.md) </span></span>  
<span data-ttu-id="c9724-149"> [Function 程序](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="c9724-149"> [Function Procedures](./function-procedures.md) </span></span>  
<span data-ttu-id="c9724-150"> [Property 程序](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="c9724-150"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="c9724-151"> [運算子程序](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="c9724-151"> [Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="c9724-152"> [程序參數和引數](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="c9724-152"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="c9724-153"> [Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="c9724-153"> [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="c9724-154"> [如何︰ 呼叫不傳回值的程序](./how-to-call-a-procedure-that-does-not-return-a-value.md) </span><span class="sxs-lookup"><span data-stu-id="c9724-154"> [How to: Call a Procedure that Does Not Return a Value](./how-to-call-a-procedure-that-does-not-return-a-value.md) </span></span>  
<span data-ttu-id="c9724-155"> [如何︰ 在 Visual Basic 中呼叫事件處理常式](./how-to-call-an-event-handler.md)</span><span class="sxs-lookup"><span data-stu-id="c9724-155"> [How to: Call an Event Handler in Visual Basic](./how-to-call-an-event-handler.md)</span></span>
