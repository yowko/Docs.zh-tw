---
title: "Lambda 運算式 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
caps.latest.revision: "52"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 69ac88d295420277e99058d0f80a5ae1c2ce2e39
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="lambda-expressions-visual-basic"></a><span data-ttu-id="d1d6f-102">Lambda 運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d1d6f-102">Lambda Expressions (Visual Basic)</span></span>
<span data-ttu-id="d1d6f-103">A *lambda 運算式*函式或副程式沒有可用於委派是有效的名稱。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-103">A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid.</span></span> <span data-ttu-id="d1d6f-104">Lambda 運算式可以是函式或副程式，而且可以是單行或多行。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-104">Lambda expressions can be functions or subroutines and can be single-line or multi-line.</span></span> <span data-ttu-id="d1d6f-105">您可以在 lambda 運算式，從目前的範圍傳遞值。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-105">You can pass values from the current scope to a lambda expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1d6f-106">`RemoveHandler`陳述式是例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-106">The `RemoveHandler` statement is an exception.</span></span> <span data-ttu-id="d1d6f-107">您無法將傳遞的委派參數的 lambda 運算式中`RemoveHandler`。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-107">You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.</span></span>  
  
 <span data-ttu-id="d1d6f-108">使用建立 lambda 運算式`Function`或`Sub`關鍵字，就像建立標準函式或副程式。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-108">You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine.</span></span> <span data-ttu-id="d1d6f-109">不過，lambda 運算式會包含陳述式中。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-109">However, lambda expressions are included in a statement.</span></span>  
  
 <span data-ttu-id="d1d6f-110">下列範例是遞增其引數和傳回值的 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-110">The following example is a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="d1d6f-111">函式的兩個多行的單行 lambda 運算式語法範例。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-111">The example shows both the single-line and multi-line lambda expression syntax for a function.</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_1.vb)]  
  
 <span data-ttu-id="d1d6f-112">下列範例會將值寫入主控台的 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-112">The following example is a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="d1d6f-113">此範例顯示副程式的這兩個多行的單行 lambda 運算式的語法。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-113">The example shows both the single-line and multi-line lambda expression syntax for a subroutine.</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_2.vb)]  
  
 <span data-ttu-id="d1d6f-114">請注意，上述範例中的 lambda 運算式指派給變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-114">Notice that in the previous examples the lambda expressions are assigned to a variable name.</span></span> <span data-ttu-id="d1d6f-115">每當您參考的變數，您就會叫用 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-115">Whenever you refer to the variable, you invoke the lambda expression.</span></span> <span data-ttu-id="d1d6f-116">您也可以宣告和叫用相同的時間，lambda 運算式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-116">You can also declare and invoke a lambda expression at the same time, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_3.vb)]  
  
 <span data-ttu-id="d1d6f-117">Lambda 運算式可以傳回做為函式呼叫的值 (如下所示的範例[內容](#context)本主題稍後的章節)，或傳遞做為引數至參數會是委派類型，如下列所示範例。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-117">A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrLambdas#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_4.vb)]  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="d1d6f-118">Lambda 運算式語法</span><span class="sxs-lookup"><span data-stu-id="d1d6f-118">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="d1d6f-119">Lambda 運算式的語法類似於標準函式或副程式。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-119">The syntax of a lambda expression resembles that of a standard function or subroutine.</span></span> <span data-ttu-id="d1d6f-120">差異如下所示：</span><span class="sxs-lookup"><span data-stu-id="d1d6f-120">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="d1d6f-121">Lambda 運算式沒有名稱。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-121">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="d1d6f-122">Lambda 運算式不能有修飾詞，例如`Overloads`或`Overrides`。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-122">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="d1d6f-123">單行 lambda 函式就不會使用`As`子句來指定傳回型別。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-123">Single-line lambda functions do not use an `As` clause to designate the return type.</span></span> <span data-ttu-id="d1d6f-124">相反地，從 lambda 運算式的主體會評估為值推斷的類型。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-124">Instead, the type is inferred from the value that the body of the lambda expression evaluates to.</span></span> <span data-ttu-id="d1d6f-125">例如，如果 lambda 運算式的主體是`cust.City = "London"`，其傳回類型是`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-125">For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="d1d6f-126">在多行 lambda 函式，您可以指定傳回型別使用`As`子句，或省略`As`子句，讓推斷傳回類型。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-126">In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred.</span></span> <span data-ttu-id="d1d6f-127">當`As`子句省略多行 lambda 函式，就會推斷傳回型別是從所有主控項的類型`Return`多行 lambda 函式中的陳述式。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-127">When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function.</span></span> <span data-ttu-id="d1d6f-128">*主類型*是所有其他類型可以擴展成的唯一類型。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-128">The *dominant type* is a unique type that all other types can widen to.</span></span> <span data-ttu-id="d1d6f-129">無法決定此唯一類型，如果主類型是陣列中的其他類型皆可縮小到的唯一類型。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-129">If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to.</span></span> <span data-ttu-id="d1d6f-130">如果這些類型皆無法決定，則主類型為 `Object`。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-130">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="d1d6f-131">在此情況下，如果`Option Strict`設`On`，就會發生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-131">In this case, if `Option Strict` is set to `On`, a compiler error occurs.</span></span>  
  
     <span data-ttu-id="d1d6f-132">例如，如果運算式提供給`Return`陳述式包含類型的值`Integer`， `Long`，和`Double`，產生的陣列會屬於類型`Double`。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-132">For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="d1d6f-133">同時`Integer`和`Long`擴展為`Double`僅限和`Double`。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-133">Both `Integer` and `Long` widen to `Double` and only `Double`.</span></span> <span data-ttu-id="d1d6f-134">因此， `Double` 是主類型。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-134">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="d1d6f-135">如需詳細資訊，請參閱 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-135">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
-   <span data-ttu-id="d1d6f-136">單行函式的主體必須傳回值，而不是陳述式的運算式。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-136">The body of a single-line function must be an expression that returns a value, not a statement.</span></span> <span data-ttu-id="d1d6f-137">沒有任何`Return`單行函式的陳述式。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-137">There is no `Return` statement for single-line functions.</span></span> <span data-ttu-id="d1d6f-138">函式主體中的運算式的值為單行函式所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-138">The value returned by the single-line function is the value of the expression in the body of the function.</span></span>  
  
-   <span data-ttu-id="d1d6f-139">單行副程式的主體必須是單行陳述式。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-139">The body of a single-line subroutine must be single-line statement.</span></span>  
  
-   <span data-ttu-id="d1d6f-140">不包含單行函式和副程式`End Function`或`End Sub`陳述式。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-140">Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.</span></span>  
  
-   <span data-ttu-id="d1d6f-141">您可以使用指定的 lambda 運算式參數的資料型別`As`推斷關鍵字或參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-141">You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred.</span></span> <span data-ttu-id="d1d6f-142">必須推斷資料型別或所有必須指定所有參數。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-142">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="d1d6f-143">`Optional`和`Paramarray`參數不允許使用。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-143">`Optional` and `Paramarray` parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="d1d6f-144">不允許泛型參數。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-144">Generic parameters are not permitted.</span></span>  
  
## <a name="async-lambdas"></a><span data-ttu-id="d1d6f-145">非同步 Lambda</span><span class="sxs-lookup"><span data-stu-id="d1d6f-145">Async Lambdas</span></span>  
 <span data-ttu-id="d1d6f-146">您可以輕鬆地建立 lambda 運算式和陳述式結合非同步處理的使用[非同步](../../../../visual-basic/language-reference/modifiers/async.md)和[Await 運算子](../../../../visual-basic/language-reference/operators/await-operator.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-146">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../../visual-basic/language-reference/modifiers/async.md) and [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) keywords.</span></span> <span data-ttu-id="d1d6f-147">例如，下列 Windows Form 範例包含呼叫並等候非同步方法 `ExampleMethodAsync`的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-147">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>  
  
```vb  
Public Class Form1  
  
    Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
        ' ExampleMethodAsync returns a Task.  
        Await ExampleMethodAsync()  
        TextBox1.Text = vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Async Function ExampleMethodAsync() As Task  
        ' The following line simulates a task-returning asynchronous process.  
        Await Task.Delay(1000)  
    End Function  
  
End Class  
```  
  
 <span data-ttu-id="d1d6f-148">您可以使用在非同步 lambda 加入相同的事件處理常式[AddHandler 陳述式](../../../../visual-basic/language-reference/statements/addhandler-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-148">You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="d1d6f-149">若要加入這個處理常式，請將 `Async` 修飾詞加入至 Lambda 參數清單前面，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-149">To add this handler, add an `Async` modifier before the lambda parameter list, as the following example shows.</span></span>  
  
```vb  
Public Class Form1  
  
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
        AddHandler Button1.Click,   
            Async Sub(sender1, e1)  
                ' ExampleMethodAsync returns a Task.  
                Await ExampleMethodAsync()  
                TextBox1.Text = vbCrLf & "Control returned to Button1_ Click."  
            End Sub  
    End Sub  
  
    Async Function ExampleMethodAsync() As Task  
        ' The following line simulates a task-returning asynchronous process.  
        Await Task.Delay(1000)  
    End Function  
  
End Class  
```  
  
 <span data-ttu-id="d1d6f-150">如需如何建立和使用非同步方法的詳細資訊，請參閱[使用 Async 和 Await 進行非同步程式設計](../../../../visual-basic/programming-guide/concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-150">For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
##  <a name="context"></a><span data-ttu-id="d1d6f-151">內容</span><span class="sxs-lookup"><span data-stu-id="d1d6f-151">Context</span></span>  
 <span data-ttu-id="d1d6f-152">Lambda 運算式內定義的範圍與共用其內容。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-152">A lambda expression shares its context with the scope within which it is defined.</span></span> <span data-ttu-id="d1d6f-153">其包含的範圍中撰寫任何程式碼的相同存取權限。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-153">It has the same access rights as any code written in the containing scope.</span></span> <span data-ttu-id="d1d6f-154">這包括存取成員變數、 函式和子函數， `Me`，在包含的範圍中的區域變數和參數。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-154">This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.</span></span>  
  
 <span data-ttu-id="d1d6f-155">存取區域變數和參數中包含的範圍可以擴充到超出該範圍的存留期間。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-155">Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope.</span></span> <span data-ttu-id="d1d6f-156">只要參考 lambda 運算式的委派不適用於記憶體回收，會保留原始的環境變數的存取權。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-156">As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained.</span></span> <span data-ttu-id="d1d6f-157">在下列範例中，變數`target`本機`makeTheGame`，此方法用於 lambda 運算式`playTheGame`定義。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-157">In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined.</span></span> <span data-ttu-id="d1d6f-158">請注意，傳回的 lambda 運算式中，指派給`takeAGuess`中`Main`，仍然可以存取區域變數`target`。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-158">Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#12](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_5.vb)]  
  
 <span data-ttu-id="d1d6f-159">下列範例會示範各種不同的存取權限的巢狀的 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-159">The following example demonstrates the wide range of access rights of the nested lambda expression.</span></span> <span data-ttu-id="d1d6f-160">從執行傳回的 lambda 運算式時`Main`為`aDel`，它會存取這些項目：</span><span class="sxs-lookup"><span data-stu-id="d1d6f-160">When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:</span></span>  
  
-   <span data-ttu-id="d1d6f-161">在定義類別的欄位：`aField`</span><span class="sxs-lookup"><span data-stu-id="d1d6f-161">A field of the class in which it is defined: `aField`</span></span>  
  
-   <span data-ttu-id="d1d6f-162">在定義類別的屬性：`aProp`</span><span class="sxs-lookup"><span data-stu-id="d1d6f-162">A property of the class in which it is defined: `aProp`</span></span>  
  
-   <span data-ttu-id="d1d6f-163">方法的參數`functionWithNestedLambda`，它會定義：`level1`</span><span class="sxs-lookup"><span data-stu-id="d1d6f-163">A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`</span></span>  
  
-   <span data-ttu-id="d1d6f-164">本機變數`functionWithNestedLambda`:`localVar`</span><span class="sxs-lookup"><span data-stu-id="d1d6f-164">A local variable of `functionWithNestedLambda`: `localVar`</span></span>  
  
-   <span data-ttu-id="d1d6f-165">在它巢狀 lambda 運算式的參數：`level2`</span><span class="sxs-lookup"><span data-stu-id="d1d6f-165">A parameter of the lambda expression in which it is nested: `level2`</span></span>  
  
 [!code-vb[VbVbalrLambdas#9](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_6.vb)]  
  
## <a name="converting-to-a-delegate-type"></a><span data-ttu-id="d1d6f-166">轉換成委派類型</span><span class="sxs-lookup"><span data-stu-id="d1d6f-166">Converting to a Delegate Type</span></span>  
 <span data-ttu-id="d1d6f-167">Lambda 運算式可以隱含地轉換成相容的委派類型。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-167">A lambda expression can be implicitly converted to a compatible delegate type.</span></span> <span data-ttu-id="d1d6f-168">如需相容性的一般需求資訊，請參閱[寬鬆委派轉換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-168">For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span> <span data-ttu-id="d1d6f-169">例如，下列程式碼範例示範隱含地轉換成的 lambda 運算式`Func(Of Integer, Boolean)`或相符的委派簽章。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-169">For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.</span></span>  
  
 [!code-vb[VbVbalrLambdas#16](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_7.vb)]  
  
 <span data-ttu-id="d1d6f-170">下列程式碼範例示範 lambda 運算式的隱含地轉換成`Sub(Of Double, String, Double)`或相符的委派簽章。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-170">The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.</span></span>  
  
 [!code-vb[VbVbalrLambdas#23](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_8.vb)]  
  
 <span data-ttu-id="d1d6f-171">當您將 lambda 運算式指派給委派，或將其做為引數傳遞至程序時，您可以指定參數名稱，但省略其資料型別，以便從委派的類型。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-171">When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="d1d6f-172">範例</span><span class="sxs-lookup"><span data-stu-id="d1d6f-172">Examples</span></span>  
  
-   <span data-ttu-id="d1d6f-173">下列範例會定義傳回的 lambda 運算式`True`可為 null 的引數必須具有指派的值，如果和`False`如果其值為`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-173">The following example defines a lambda expression that returns `True` if the nullable argument has an assigned value, and `False` if its value is `Nothing`.</span></span>  
  
     [!code-vb[VbVbalrLambdas#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_9.vb)]  
  
-   <span data-ttu-id="d1d6f-174">下列範例會定義傳回最後一個項目的索引陣列中的 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="d1d6f-174">The following example defines a lambda expression that returns the index of the last element in an array.</span></span>  
  
     [!code-vb[VbVbalrLambdas#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_10.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d1d6f-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1d6f-175">See Also</span></span>  
 [<span data-ttu-id="d1d6f-176">程序</span><span class="sxs-lookup"><span data-stu-id="d1d6f-176">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="d1d6f-177">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="d1d6f-177">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="d1d6f-178">委派</span><span class="sxs-lookup"><span data-stu-id="d1d6f-178">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="d1d6f-179">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="d1d6f-179">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="d1d6f-180">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="d1d6f-180">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="d1d6f-181">可為 Null 的值類型</span><span class="sxs-lookup"><span data-stu-id="d1d6f-181">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [<span data-ttu-id="d1d6f-182">如何：在 Visual Basic 中將程序傳遞至其他程序</span><span class="sxs-lookup"><span data-stu-id="d1d6f-182">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [<span data-ttu-id="d1d6f-183">如何：建立 Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="d1d6f-183">How to: Create a Lambda Expression</span></span>](./how-to-create-a-lambda-expression.md)  
 [<span data-ttu-id="d1d6f-184">寬鬆委派轉換</span><span class="sxs-lookup"><span data-stu-id="d1d6f-184">Relaxed Delegate Conversion</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
