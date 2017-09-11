---
title: "Lambda 運算式 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.LambdaFunction
dev_langs:
- VB
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
caps.latest.revision: 52
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: e4624e5f20beeebf85656c893043030566200557
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---
# <a name="lambda-expressions-visual-basic"></a><span data-ttu-id="0ad6d-102">Lambda 運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ad6d-102">Lambda Expressions (Visual Basic)</span></span>
<span data-ttu-id="0ad6d-103">A *lambda 運算式*函式或副程式沒有就可以使用委派是有效的名稱。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-103">A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid.</span></span> <span data-ttu-id="0ad6d-104">Lambda 運算式可以是函式或副程式，而且可以是單行或多行。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-104">Lambda expressions can be functions or subroutines and can be single-line or multi-line.</span></span> <span data-ttu-id="0ad6d-105">Lambda 運算式，您可以從目前的範圍傳遞值。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-105">You can pass values from the current scope to a lambda expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ad6d-106">`RemoveHandler`陳述式是例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-106">The `RemoveHandler` statement is an exception.</span></span> <span data-ttu-id="0ad6d-107">您無法傳遞的委派參數的 lambda 運算式中`RemoveHandler`。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-107">You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.</span></span>  
  
 <span data-ttu-id="0ad6d-108">使用建立 lambda 運算式`Function`或`Sub`關鍵字，就像建立標準函式或副程式。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-108">You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine.</span></span> <span data-ttu-id="0ad6d-109">不過，lambda 運算式會包含陳述式中。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-109">However, lambda expressions are included in a statement.</span></span>  
  
 <span data-ttu-id="0ad6d-110">下列範例是遞增其引數和傳回值的 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-110">The following example is a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="0ad6d-111">函式的兩個單行或多行 lambda 運算式語法範例。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-111">The example shows both the single-line and multi-line lambda expression syntax for a function.</span></span>  
  
 <span data-ttu-id="0ad6d-112">[!code-vb[VbVbalrLambdas #&14;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="0ad6d-112">[!code-vb[VbVbalrLambdas#14](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_1.vb)]</span></span>  
  
 <span data-ttu-id="0ad6d-113">下列範例會將值寫入主控台的 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-113">The following example is a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="0ad6d-114">範例會示範這兩個單行或多行 lambda 運算式語法的副程式。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-114">The example shows both the single-line and multi-line lambda expression syntax for a subroutine.</span></span>  
  
 <span data-ttu-id="0ad6d-115">[!code-vb[VbVbalrLambdas #&15;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="0ad6d-115">[!code-vb[VbVbalrLambdas#15](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_2.vb)]</span></span>  
  
 <span data-ttu-id="0ad6d-116">請注意，上述範例中 lambda 運算式指派給變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-116">Notice that in the previous examples the lambda expressions are assigned to a variable name.</span></span> <span data-ttu-id="0ad6d-117">每當您參考變數，您就會叫用 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-117">Whenever you refer to the variable, you invoke the lambda expression.</span></span> <span data-ttu-id="0ad6d-118">您也可以宣告和叫用一次，lambda 運算式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-118">You can also declare and invoke a lambda expression at the same time, as shown in the following example.</span></span>  
  
 <span data-ttu-id="0ad6d-119">[!code-vb[VbVbalrLambdas #&3;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="0ad6d-119">[!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_3.vb)]</span></span>  
  
 <span data-ttu-id="0ad6d-120">Lambda 運算式可以傳回做為函式呼叫的值 (在此範例所示[內容](#context)本主題稍後的章節)，或在傳遞做為引數至參數採用委派型別，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-120">A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.</span></span>  
  
 <span data-ttu-id="0ad6d-121">[!code-vb[VbVbalrLambdas #&8;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="0ad6d-121">[!code-vb[VbVbalrLambdas#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_4.vb)]</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="0ad6d-122">Lambda 運算式語法</span><span class="sxs-lookup"><span data-stu-id="0ad6d-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="0ad6d-123">Lambda 運算式的語法類似於標準函式或副程式。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-123">The syntax of a lambda expression resembles that of a standard function or subroutine.</span></span> <span data-ttu-id="0ad6d-124">差異如下︰</span><span class="sxs-lookup"><span data-stu-id="0ad6d-124">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="0ad6d-125">Lambda 運算式沒有名稱。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-125">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="0ad6d-126">Lambda 運算式不能有修飾詞，例如`Overloads`或`Overrides`。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="0ad6d-127">不使用單行 lambda 函式`As`子句來指定傳回型別。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-127">Single-line lambda functions do not use an `As` clause to designate the return type.</span></span> <span data-ttu-id="0ad6d-128">相反地，從 lambda 運算式的主體會評估為值推斷型別。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-128">Instead, the type is inferred from the value that the body of the lambda expression evaluates to.</span></span> <span data-ttu-id="0ad6d-129">例如，如果 lambda 運算式的主體是`cust.City = "London"`，其傳回型別是`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-129">For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="0ad6d-130">在多行 lambda 函式中，您可以指定傳回型別使用`As`子句，或省略`As`子句，以便傳回型別推斷。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-130">In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred.</span></span> <span data-ttu-id="0ad6d-131">當`As`子句省略多行 lambda 函式，傳回的型別推斷為主控項的型別，從所有`Return`多行 lambda 函式中的陳述式。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-131">When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function.</span></span> <span data-ttu-id="0ad6d-132">*優勢型別*是所有其他型別可以擴展成的唯一類型。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-132">The *dominant type* is a unique type that all other types can widen to.</span></span> <span data-ttu-id="0ad6d-133">如果無法判斷此唯一的型別，主控項的型別是陣列中的所有其他類型可以縮小到唯一的型別。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-133">If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to.</span></span> <span data-ttu-id="0ad6d-134">如果這些類型皆無法決定，則主類型為 `Object`。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-134">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="0ad6d-135">在此情況下，如果`Option Strict`設為`On`，就會發生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-135">In this case, if `Option Strict` is set to `On`, a compiler error occurs.</span></span>  
  
     <span data-ttu-id="0ad6d-136">例如，如果運算式提供給`Return`陳述式包含型別的值`Integer`， `Long`，和`Double`，產生的陣列是類型的`Double`。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-136">For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="0ad6d-137">同時`Integer`和`Long`擴展為`Double`只有`Double`。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-137">Both `Integer` and `Long` widen to `Double` and only `Double`.</span></span> <span data-ttu-id="0ad6d-138">因此， `Double` 是主類型。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-138">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="0ad6d-139">如需詳細資訊，請參閱[擴大和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-139">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
-   <span data-ttu-id="0ad6d-140">單行函式的主體必須是傳回值，而不是陳述式的運算式。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-140">The body of a single-line function must be an expression that returns a value, not a statement.</span></span> <span data-ttu-id="0ad6d-141">有沒有`Return`單行函式的陳述式。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-141">There is no `Return` statement for single-line functions.</span></span> <span data-ttu-id="0ad6d-142">單行函式所傳回的值是函式主體中運算式的值。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-142">The value returned by the single-line function is the value of the expression in the body of the function.</span></span>  
  
-   <span data-ttu-id="0ad6d-143">單行副程式的主體必須是單行陳述式。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-143">The body of a single-line subroutine must be single-line statement.</span></span>  
  
-   <span data-ttu-id="0ad6d-144">不包含單行函式和副程式`End Function`或`End Sub`陳述式。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-144">Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.</span></span>  
  
-   <span data-ttu-id="0ad6d-145">您可以使用指定的 lambda 運算式參數的資料型別`As`關鍵字或參數的資料型別來推斷。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-145">You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred.</span></span> <span data-ttu-id="0ad6d-146">必須推斷資料型別或所有必須指定所有參數。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-146">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="0ad6d-147">`Optional`和`Paramarray`不允許使用參數。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-147">`Optional` and `Paramarray` parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="0ad6d-148">不允許泛型參數。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-148">Generic parameters are not permitted.</span></span>  
  
## <a name="async-lambdas"></a><span data-ttu-id="0ad6d-149">非同步 Lambda</span><span class="sxs-lookup"><span data-stu-id="0ad6d-149">Async Lambdas</span></span>  
 <span data-ttu-id="0ad6d-150">您可以輕鬆地建立 lambda 運算式和陳述式使用結合非同步處理[非同步](../../../../visual-basic/language-reference/modifiers/async.md)和[Await 運算子](../../../../visual-basic/language-reference/operators/await-operator.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-150">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../../visual-basic/language-reference/modifiers/async.md) and [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) keywords.</span></span> <span data-ttu-id="0ad6d-151">例如，下列 Windows Form 範例包含呼叫並等候非同步方法 `ExampleMethodAsync`的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-151">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>  
  
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
  
 <span data-ttu-id="0ad6d-152">您可以使用非同步 lambda 中的新增相同的事件處理常式[AddHandler 陳述式](../../../../visual-basic/language-reference/statements/addhandler-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-152">You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="0ad6d-153">若要加入這個處理常式，請將 `Async` 修飾詞加入至 Lambda 參數清單前面，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-153">To add this handler, add an `Async` modifier before the lambda parameter list, as the following example shows.</span></span>  
  
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
  
 <span data-ttu-id="0ad6d-154">如需如何建立和使用非同步方法的詳細資訊，請參閱[使用 Async 和 Await 進行非同步程式設計](../../../../visual-basic/programming-guide/concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-154">For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
##  <span data-ttu-id="0ad6d-155"><a name="context"></a>內容</span><span class="sxs-lookup"><span data-stu-id="0ad6d-155"><a name="context"></a> Context</span></span>  
 <span data-ttu-id="0ad6d-156">Lambda 運算式共用其內容與在其中定義的範圍。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-156">A lambda expression shares its context with the scope within which it is defined.</span></span> <span data-ttu-id="0ad6d-157">其包含的範圍中撰寫程式碼的相同存取權限。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-157">It has the same access rights as any code written in the containing scope.</span></span> <span data-ttu-id="0ad6d-158">這包括存取成員變數、 函式和子函數， `Me`，涵蓋範圍的區域變數和參數。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-158">This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.</span></span>  
  
 <span data-ttu-id="0ad6d-159">存取區域變數和參數中包含的範圍可以擴充到超出該範圍的存留期間。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-159">Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope.</span></span> <span data-ttu-id="0ad6d-160">只要委派來參考 lambda 運算式不適用於記憶體回收，會保留在原始環境變數的存取權。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-160">As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained.</span></span> <span data-ttu-id="0ad6d-161">在下列範例中，變數`target`本機`makeTheGame`，此方法用於 lambda 運算式`playTheGame`定義。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-161">In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined.</span></span> <span data-ttu-id="0ad6d-162">請注意，傳回的 lambda 運算式指派給`takeAGuess`中`Main`，仍然可以存取本機變數`target`。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-162">Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.</span></span>  
  
 <span data-ttu-id="0ad6d-163">[!code-vb[VbVbalrLambdas #&12;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="0ad6d-163">[!code-vb[VbVbalrLambdas#12](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_5.vb)]</span></span>  
  
 <span data-ttu-id="0ad6d-164">下列範例將示範各種的巢狀的 lambda 運算式的存取權限。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-164">The following example demonstrates the wide range of access rights of the nested lambda expression.</span></span> <span data-ttu-id="0ad6d-165">從執行傳回的 lambda 運算式會`Main`為`aDel`，它會存取這些項目︰</span><span class="sxs-lookup"><span data-stu-id="0ad6d-165">When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:</span></span>  
  
-   <span data-ttu-id="0ad6d-166">在定義類別的欄位︰`aField`</span><span class="sxs-lookup"><span data-stu-id="0ad6d-166">A field of the class in which it is defined: `aField`</span></span>  
  
-   <span data-ttu-id="0ad6d-167">在定義類別的屬性︰`aProp`</span><span class="sxs-lookup"><span data-stu-id="0ad6d-167">A property of the class in which it is defined: `aProp`</span></span>  
  
-   <span data-ttu-id="0ad6d-168">方法的參數`functionWithNestedLambda`，在其中定義︰`level1`</span><span class="sxs-lookup"><span data-stu-id="0ad6d-168">A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`</span></span>  
  
-   <span data-ttu-id="0ad6d-169">區域變數的`functionWithNestedLambda`:`localVar`</span><span class="sxs-lookup"><span data-stu-id="0ad6d-169">A local variable of `functionWithNestedLambda`: `localVar`</span></span>  
  
-   <span data-ttu-id="0ad6d-170">在它巢狀 lambda 運算式的參數︰`level2`</span><span class="sxs-lookup"><span data-stu-id="0ad6d-170">A parameter of the lambda expression in which it is nested: `level2`</span></span>  
  
 <span data-ttu-id="0ad6d-171">[!code-vb[VbVbalrLambdas #&9;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="0ad6d-171">[!code-vb[VbVbalrLambdas#9](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_6.vb)]</span></span>  
  
## <a name="converting-to-a-delegate-type"></a><span data-ttu-id="0ad6d-172">轉換為委派型別</span><span class="sxs-lookup"><span data-stu-id="0ad6d-172">Converting to a Delegate Type</span></span>  
 <span data-ttu-id="0ad6d-173">Lambda 運算式可以隱含地轉換成相容的委派型別。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-173">A lambda expression can be implicitly converted to a compatible delegate type.</span></span> <span data-ttu-id="0ad6d-174">一般相容性需求的詳細資訊，請參閱[寬鬆委派轉換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-174">For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span> <span data-ttu-id="0ad6d-175">例如，下列程式碼範例顯示的 lambda 運算式隱含地轉換成`Func(Of Integer, Boolean)`或相符的委派簽章。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-175">For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.</span></span>  
  
 <span data-ttu-id="0ad6d-176">[!code-vb[VbVbalrLambdas #&16;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="0ad6d-176">[!code-vb[VbVbalrLambdas#16](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_7.vb)]</span></span>  
  
 <span data-ttu-id="0ad6d-177">下列程式碼範例示範 lambda 運算式的隱含地轉換成`Sub(Of Double, String, Double)`或相符的委派簽章。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-177">The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.</span></span>  
  
 <span data-ttu-id="0ad6d-178">[!code-vb[VbVbalrLambdas #&23;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="0ad6d-178">[!code-vb[VbVbalrLambdas#23](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_8.vb)]</span></span>  
  
 <span data-ttu-id="0ad6d-179">當您將 lambda 運算式指派給委派，或將其做為引數傳遞至程序時，您可以指定參數名稱，但省略其資料型別，以便進行委派的型別。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-179">When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="0ad6d-180">範例</span><span class="sxs-lookup"><span data-stu-id="0ad6d-180">Examples</span></span>  
  
-   <span data-ttu-id="0ad6d-181">下列範例會定義傳回的 lambda 運算式`True`如果指派的值，可為 null 引數和`False`如果其值為`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-181">The following example defines a lambda expression that returns `True` if the nullable argument has an assigned value, and `False` if its value is `Nothing`.</span></span>  
  
     <span data-ttu-id="0ad6d-182">[!code-vb[VbVbalrLambdas #&4;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="0ad6d-182">[!code-vb[VbVbalrLambdas#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_9.vb)]</span></span>  
  
-   <span data-ttu-id="0ad6d-183">下列範例會定義 lambda 運算式以傳回陣列中的最後一個項目的索引。</span><span class="sxs-lookup"><span data-stu-id="0ad6d-183">The following example defines a lambda expression that returns the index of the last element in an array.</span></span>  
  
     <span data-ttu-id="0ad6d-184">[!code-vb[VbVbalrLambdas #&5;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="0ad6d-184">[!code-vb[VbVbalrLambdas#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_10.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ad6d-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ad6d-185">See Also</span></span>  
 <span data-ttu-id="0ad6d-186">[程序](./index.md) </span><span class="sxs-lookup"><span data-stu-id="0ad6d-186">[Procedures](./index.md) </span></span>  
<span data-ttu-id="0ad6d-187"> [在 Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="0ad6d-187"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="0ad6d-188"> [委派](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="0ad6d-188"> [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="0ad6d-189"> [Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="0ad6d-189"> [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="0ad6d-190"> [Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="0ad6d-190"> [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="0ad6d-191"> [可為 null 的實值型別](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) </span><span class="sxs-lookup"><span data-stu-id="0ad6d-191"> [Nullable Value Types](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) </span></span>  
<span data-ttu-id="0ad6d-192"> [如何︰ 將傳遞至另一個程序，在 Visual Basic 中的程序](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="0ad6d-192"> [How to: Pass Procedures to Another Procedure in Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md) </span></span>  
<span data-ttu-id="0ad6d-193"> [如何︰ 建立 Lambda 運算式](./how-to-create-a-lambda-expression.md) </span><span class="sxs-lookup"><span data-stu-id="0ad6d-193"> [How to: Create a Lambda Expression](./how-to-create-a-lambda-expression.md) </span></span>  
<span data-ttu-id="0ad6d-194"> [寬鬆委派轉換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="0ad6d-194"> [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)</span></span>

