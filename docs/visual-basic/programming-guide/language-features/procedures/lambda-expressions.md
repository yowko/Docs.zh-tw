---
title: Lambda 運算式
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: f3f963167e1b3633cc5fe6e1f435e374cd272cce
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345981"
---
# <a name="lambda-expressions-visual-basic"></a><span data-ttu-id="48649-102">Lambda 運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48649-102">Lambda Expressions (Visual Basic)</span></span>

<span data-ttu-id="48649-103">A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid.</span><span class="sxs-lookup"><span data-stu-id="48649-103">A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid.</span></span> <span data-ttu-id="48649-104">Lambda expressions can be functions or subroutines and can be single-line or multi-line.</span><span class="sxs-lookup"><span data-stu-id="48649-104">Lambda expressions can be functions or subroutines and can be single-line or multi-line.</span></span> <span data-ttu-id="48649-105">You can pass values from the current scope to a lambda expression.</span><span class="sxs-lookup"><span data-stu-id="48649-105">You can pass values from the current scope to a lambda expression.</span></span>

> [!NOTE]
> <span data-ttu-id="48649-106">The `RemoveHandler` statement is an exception.</span><span class="sxs-lookup"><span data-stu-id="48649-106">The `RemoveHandler` statement is an exception.</span></span> <span data-ttu-id="48649-107">You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="48649-107">You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.</span></span>

<span data-ttu-id="48649-108">You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine.</span><span class="sxs-lookup"><span data-stu-id="48649-108">You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine.</span></span> <span data-ttu-id="48649-109">However, lambda expressions are included in a statement.</span><span class="sxs-lookup"><span data-stu-id="48649-109">However, lambda expressions are included in a statement.</span></span>

<span data-ttu-id="48649-110">The following example is a lambda expression that increments its argument and returns the value.</span><span class="sxs-lookup"><span data-stu-id="48649-110">The following example is a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="48649-111">The example shows both the single-line and multi-line lambda expression syntax for a function.</span><span class="sxs-lookup"><span data-stu-id="48649-111">The example shows both the single-line and multi-line lambda expression syntax for a function.</span></span>

[!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]

<span data-ttu-id="48649-112">The following example is a lambda expression that writes a value to the console.</span><span class="sxs-lookup"><span data-stu-id="48649-112">The following example is a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="48649-113">The example shows both the single-line and multi-line lambda expression syntax for a subroutine.</span><span class="sxs-lookup"><span data-stu-id="48649-113">The example shows both the single-line and multi-line lambda expression syntax for a subroutine.</span></span>

[!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]

<span data-ttu-id="48649-114">Notice that in the previous examples the lambda expressions are assigned to a variable name.</span><span class="sxs-lookup"><span data-stu-id="48649-114">Notice that in the previous examples the lambda expressions are assigned to a variable name.</span></span> <span data-ttu-id="48649-115">Whenever you refer to the variable, you invoke the lambda expression.</span><span class="sxs-lookup"><span data-stu-id="48649-115">Whenever you refer to the variable, you invoke the lambda expression.</span></span> <span data-ttu-id="48649-116">You can also declare and invoke a lambda expression at the same time, as shown in the following example.</span><span class="sxs-lookup"><span data-stu-id="48649-116">You can also declare and invoke a lambda expression at the same time, as shown in the following example.</span></span>

[!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]

<span data-ttu-id="48649-117">A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.</span><span class="sxs-lookup"><span data-stu-id="48649-117">A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.</span></span>

[!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]

## <a name="lambda-expression-syntax"></a><span data-ttu-id="48649-118">Lambda 運算式語法</span><span class="sxs-lookup"><span data-stu-id="48649-118">Lambda Expression Syntax</span></span>

<span data-ttu-id="48649-119">The syntax of a lambda expression resembles that of a standard function or subroutine.</span><span class="sxs-lookup"><span data-stu-id="48649-119">The syntax of a lambda expression resembles that of a standard function or subroutine.</span></span> <span data-ttu-id="48649-120">The differences are as follows:</span><span class="sxs-lookup"><span data-stu-id="48649-120">The differences are as follows:</span></span>

- <span data-ttu-id="48649-121">A lambda expression does not have a name.</span><span class="sxs-lookup"><span data-stu-id="48649-121">A lambda expression does not have a name.</span></span>

- <span data-ttu-id="48649-122">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="48649-122">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>

- <span data-ttu-id="48649-123">Single-line lambda functions do not use an `As` clause to designate the return type.</span><span class="sxs-lookup"><span data-stu-id="48649-123">Single-line lambda functions do not use an `As` clause to designate the return type.</span></span> <span data-ttu-id="48649-124">Instead, the type is inferred from the value that the body of the lambda expression evaluates to.</span><span class="sxs-lookup"><span data-stu-id="48649-124">Instead, the type is inferred from the value that the body of the lambda expression evaluates to.</span></span> <span data-ttu-id="48649-125">For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="48649-125">For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.</span></span>

- <span data-ttu-id="48649-126">In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred.</span><span class="sxs-lookup"><span data-stu-id="48649-126">In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred.</span></span> <span data-ttu-id="48649-127">When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function.</span><span class="sxs-lookup"><span data-stu-id="48649-127">When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function.</span></span> <span data-ttu-id="48649-128">The *dominant type* is a unique type that all other types can widen to.</span><span class="sxs-lookup"><span data-stu-id="48649-128">The *dominant type* is a unique type that all other types can widen to.</span></span> <span data-ttu-id="48649-129">If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to.</span><span class="sxs-lookup"><span data-stu-id="48649-129">If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to.</span></span> <span data-ttu-id="48649-130">如果這些類型皆無法決定，則主類型為 `Object`。</span><span class="sxs-lookup"><span data-stu-id="48649-130">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="48649-131">In this case, if `Option Strict` is set to `On`, a compiler error occurs.</span><span class="sxs-lookup"><span data-stu-id="48649-131">In this case, if `Option Strict` is set to `On`, a compiler error occurs.</span></span>

     <span data-ttu-id="48649-132">For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span><span class="sxs-lookup"><span data-stu-id="48649-132">For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="48649-133">Both `Integer` and `Long` widen to `Double` and only `Double`.</span><span class="sxs-lookup"><span data-stu-id="48649-133">Both `Integer` and `Long` widen to `Double` and only `Double`.</span></span> <span data-ttu-id="48649-134">因此， `Double` 是主類型。</span><span class="sxs-lookup"><span data-stu-id="48649-134">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="48649-135">如需詳細資訊，請參閱 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="48649-135">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>

- <span data-ttu-id="48649-136">The body of a single-line function must be an expression that returns a value, not a statement.</span><span class="sxs-lookup"><span data-stu-id="48649-136">The body of a single-line function must be an expression that returns a value, not a statement.</span></span> <span data-ttu-id="48649-137">There is no `Return` statement for single-line functions.</span><span class="sxs-lookup"><span data-stu-id="48649-137">There is no `Return` statement for single-line functions.</span></span> <span data-ttu-id="48649-138">The value returned by the single-line function is the value of the expression in the body of the function.</span><span class="sxs-lookup"><span data-stu-id="48649-138">The value returned by the single-line function is the value of the expression in the body of the function.</span></span>

- <span data-ttu-id="48649-139">The body of a single-line subroutine must be single-line statement.</span><span class="sxs-lookup"><span data-stu-id="48649-139">The body of a single-line subroutine must be single-line statement.</span></span>

- <span data-ttu-id="48649-140">Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.</span><span class="sxs-lookup"><span data-stu-id="48649-140">Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.</span></span>

- <span data-ttu-id="48649-141">You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred.</span><span class="sxs-lookup"><span data-stu-id="48649-141">You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred.</span></span> <span data-ttu-id="48649-142">Either all parameters must have specified data types or all must be inferred.</span><span class="sxs-lookup"><span data-stu-id="48649-142">Either all parameters must have specified data types or all must be inferred.</span></span>

- <span data-ttu-id="48649-143">`Optional` and `Paramarray` parameters are not permitted.</span><span class="sxs-lookup"><span data-stu-id="48649-143">`Optional` and `Paramarray` parameters are not permitted.</span></span>

- <span data-ttu-id="48649-144">Generic parameters are not permitted.</span><span class="sxs-lookup"><span data-stu-id="48649-144">Generic parameters are not permitted.</span></span>

## <a name="async-lambdas"></a><span data-ttu-id="48649-145">非同步 Lambda</span><span class="sxs-lookup"><span data-stu-id="48649-145">Async Lambdas</span></span>

<span data-ttu-id="48649-146">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../../visual-basic/language-reference/modifiers/async.md) and [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) keywords.</span><span class="sxs-lookup"><span data-stu-id="48649-146">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../../visual-basic/language-reference/modifiers/async.md) and [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) keywords.</span></span> <span data-ttu-id="48649-147">例如，下列 Windows Form 範例包含呼叫並等候非同步方法 `ExampleMethodAsync`的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="48649-147">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

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

<span data-ttu-id="48649-148">You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="48649-148">You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="48649-149">若要加入這個處理常式，請將 `Async` 修飾詞加入至 Lambda 參數清單前面，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="48649-149">To add this handler, add an `Async` modifier before the lambda parameter list, as the following example shows.</span></span>

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

<span data-ttu-id="48649-150">For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="48649-150">For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

## <a name="context"></a><span data-ttu-id="48649-151">內容</span><span class="sxs-lookup"><span data-stu-id="48649-151">Context</span></span>

<span data-ttu-id="48649-152">A lambda expression shares its context with the scope within which it is defined.</span><span class="sxs-lookup"><span data-stu-id="48649-152">A lambda expression shares its context with the scope within which it is defined.</span></span> <span data-ttu-id="48649-153">It has the same access rights as any code written in the containing scope.</span><span class="sxs-lookup"><span data-stu-id="48649-153">It has the same access rights as any code written in the containing scope.</span></span> <span data-ttu-id="48649-154">This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.</span><span class="sxs-lookup"><span data-stu-id="48649-154">This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.</span></span>

<span data-ttu-id="48649-155">Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope.</span><span class="sxs-lookup"><span data-stu-id="48649-155">Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope.</span></span> <span data-ttu-id="48649-156">As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained.</span><span class="sxs-lookup"><span data-stu-id="48649-156">As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained.</span></span> <span data-ttu-id="48649-157">In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined.</span><span class="sxs-lookup"><span data-stu-id="48649-157">In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined.</span></span> <span data-ttu-id="48649-158">Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.</span><span class="sxs-lookup"><span data-stu-id="48649-158">Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.</span></span>

[!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]

<span data-ttu-id="48649-159">The following example demonstrates the wide range of access rights of the nested lambda expression.</span><span class="sxs-lookup"><span data-stu-id="48649-159">The following example demonstrates the wide range of access rights of the nested lambda expression.</span></span> <span data-ttu-id="48649-160">When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:</span><span class="sxs-lookup"><span data-stu-id="48649-160">When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:</span></span>

- <span data-ttu-id="48649-161">A field of the class in which it is defined: `aField`</span><span class="sxs-lookup"><span data-stu-id="48649-161">A field of the class in which it is defined: `aField`</span></span>

- <span data-ttu-id="48649-162">A property of the class in which it is defined: `aProp`</span><span class="sxs-lookup"><span data-stu-id="48649-162">A property of the class in which it is defined: `aProp`</span></span>

- <span data-ttu-id="48649-163">A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`</span><span class="sxs-lookup"><span data-stu-id="48649-163">A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`</span></span>

- <span data-ttu-id="48649-164">A local variable of `functionWithNestedLambda`: `localVar`</span><span class="sxs-lookup"><span data-stu-id="48649-164">A local variable of `functionWithNestedLambda`: `localVar`</span></span>

- <span data-ttu-id="48649-165">A parameter of the lambda expression in which it is nested: `level2`</span><span class="sxs-lookup"><span data-stu-id="48649-165">A parameter of the lambda expression in which it is nested: `level2`</span></span>

 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]

## <a name="converting-to-a-delegate-type"></a><span data-ttu-id="48649-166">Converting to a Delegate Type</span><span class="sxs-lookup"><span data-stu-id="48649-166">Converting to a Delegate Type</span></span>

<span data-ttu-id="48649-167">A lambda expression can be implicitly converted to a compatible delegate type.</span><span class="sxs-lookup"><span data-stu-id="48649-167">A lambda expression can be implicitly converted to a compatible delegate type.</span></span> <span data-ttu-id="48649-168">For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="48649-168">For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span> <span data-ttu-id="48649-169">For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.</span><span class="sxs-lookup"><span data-stu-id="48649-169">For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.</span></span>

[!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]

<span data-ttu-id="48649-170">The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.</span><span class="sxs-lookup"><span data-stu-id="48649-170">The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.</span></span>

[!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]

<span data-ttu-id="48649-171">When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.</span><span class="sxs-lookup"><span data-stu-id="48649-171">When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.</span></span>

## <a name="examples"></a><span data-ttu-id="48649-172">範例</span><span class="sxs-lookup"><span data-stu-id="48649-172">Examples</span></span>

- <span data-ttu-id="48649-173">The following example defines a lambda expression that returns `True` if the nullable argument has an assigned value, and `False` if its value is `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="48649-173">The following example defines a lambda expression that returns `True` if the nullable argument has an assigned value, and `False` if its value is `Nothing`.</span></span>

     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]

- <span data-ttu-id="48649-174">The following example defines a lambda expression that returns the index of the last element in an array.</span><span class="sxs-lookup"><span data-stu-id="48649-174">The following example defines a lambda expression that returns the index of the last element in an array.</span></span>

     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="48649-175">請參閱</span><span class="sxs-lookup"><span data-stu-id="48649-175">See also</span></span>

- [<span data-ttu-id="48649-176">程序</span><span class="sxs-lookup"><span data-stu-id="48649-176">Procedures</span></span>](./index.md)
- [<span data-ttu-id="48649-177">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="48649-177">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="48649-178">委派</span><span class="sxs-lookup"><span data-stu-id="48649-178">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="48649-179">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="48649-179">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="48649-180">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="48649-180">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="48649-181">可為 Null 的值類型</span><span class="sxs-lookup"><span data-stu-id="48649-181">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="48649-182">如何：在 Visual Basic 中將程序傳遞至其他程序</span><span class="sxs-lookup"><span data-stu-id="48649-182">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="48649-183">如何：建立 Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="48649-183">How to: Create a Lambda Expression</span></span>](./how-to-create-a-lambda-expression.md)
- [<span data-ttu-id="48649-184">寬鬆委派轉換</span><span class="sxs-lookup"><span data-stu-id="48649-184">Relaxed Delegate Conversion</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
