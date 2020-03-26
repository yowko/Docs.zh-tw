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
ms.openlocfilehash: 1827eb5630ed217527de25fc9d9c2bb8994b9aff
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249665"
---
# <a name="lambda-expressions-visual-basic"></a><span data-ttu-id="0af38-102">Lambda 運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0af38-102">Lambda Expressions (Visual Basic)</span></span>

<span data-ttu-id="0af38-103">*lambda 運算式*是一個函數或副程式，沒有名稱，可以在委託有效的地方使用。</span><span class="sxs-lookup"><span data-stu-id="0af38-103">A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid.</span></span> <span data-ttu-id="0af38-104">Lambda 運算式可以是函數或副程式，可以是單行運算式或多行運算式。</span><span class="sxs-lookup"><span data-stu-id="0af38-104">Lambda expressions can be functions or subroutines and can be single-line or multi-line.</span></span> <span data-ttu-id="0af38-105">可以將值從當前作用域傳遞到 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="0af38-105">You can pass values from the current scope to a lambda expression.</span></span>

> [!NOTE]
> <span data-ttu-id="0af38-106">該`RemoveHandler`語句是一個例外。</span><span class="sxs-lookup"><span data-stu-id="0af38-106">The `RemoveHandler` statement is an exception.</span></span> <span data-ttu-id="0af38-107">不能為 的委託參數傳遞 lambda 運算式`RemoveHandler`。</span><span class="sxs-lookup"><span data-stu-id="0af38-107">You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.</span></span>

<span data-ttu-id="0af38-108">使用`Function`or`Sub`關鍵字創建 lambda 運算式，就像創建標準函數或副程式一樣。</span><span class="sxs-lookup"><span data-stu-id="0af38-108">You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine.</span></span> <span data-ttu-id="0af38-109">但是，lambda 運算式包含在語句中。</span><span class="sxs-lookup"><span data-stu-id="0af38-109">However, lambda expressions are included in a statement.</span></span>

<span data-ttu-id="0af38-110">下面的示例是 lambda 運算式，該運算式遞增其參數並傳回值。</span><span class="sxs-lookup"><span data-stu-id="0af38-110">The following example is a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="0af38-111">該示例顯示了函數的單行和多行 lambda 運算式語法。</span><span class="sxs-lookup"><span data-stu-id="0af38-111">The example shows both the single-line and multi-line lambda expression syntax for a function.</span></span>

[!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]

<span data-ttu-id="0af38-112">下面的示例是 lambda 運算式，該運算式將值寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="0af38-112">The following example is a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="0af38-113">該示例顯示了副程式的單行和多行 lambda 運算式語法。</span><span class="sxs-lookup"><span data-stu-id="0af38-113">The example shows both the single-line and multi-line lambda expression syntax for a subroutine.</span></span>

[!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]

<span data-ttu-id="0af38-114">請注意，在前面的示例中，lambda 運算式被分配給一個變數名稱。</span><span class="sxs-lookup"><span data-stu-id="0af38-114">Notice that in the previous examples the lambda expressions are assigned to a variable name.</span></span> <span data-ttu-id="0af38-115">每當引用變數時，都會調用 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="0af38-115">Whenever you refer to the variable, you invoke the lambda expression.</span></span> <span data-ttu-id="0af38-116">您還可以同時聲明和調用 lambda 運算式，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="0af38-116">You can also declare and invoke a lambda expression at the same time, as shown in the following example.</span></span>

[!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]

<span data-ttu-id="0af38-117">lambda 運算式可以作為函式呼叫的值返回（如本主題後面的["上下文](#context)"部分中的示例中所示），也可以作為參數傳遞給採用委託類型的參數，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="0af38-117">A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.</span></span>

[!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]

## <a name="lambda-expression-syntax"></a><span data-ttu-id="0af38-118">Lambda 運算式語法</span><span class="sxs-lookup"><span data-stu-id="0af38-118">Lambda Expression Syntax</span></span>

<span data-ttu-id="0af38-119">lambda 運算式的語法類似于標準函數或副程式的語法。</span><span class="sxs-lookup"><span data-stu-id="0af38-119">The syntax of a lambda expression resembles that of a standard function or subroutine.</span></span> <span data-ttu-id="0af38-120">差異如下：</span><span class="sxs-lookup"><span data-stu-id="0af38-120">The differences are as follows:</span></span>

- <span data-ttu-id="0af38-121">lambda 運算式沒有名稱。</span><span class="sxs-lookup"><span data-stu-id="0af38-121">A lambda expression does not have a name.</span></span>

- <span data-ttu-id="0af38-122">Lambda 運算式不能具有修飾符，如`Overloads`或`Overrides`。</span><span class="sxs-lookup"><span data-stu-id="0af38-122">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>

- <span data-ttu-id="0af38-123">單行 lambda 函數不使用子句`As`來指定返回類型。</span><span class="sxs-lookup"><span data-stu-id="0af38-123">Single-line lambda functions do not use an `As` clause to designate the return type.</span></span> <span data-ttu-id="0af38-124">相反，類型是從 lambda 運算式的正文計算到的值推斷的。</span><span class="sxs-lookup"><span data-stu-id="0af38-124">Instead, the type is inferred from the value that the body of the lambda expression evaluates to.</span></span> <span data-ttu-id="0af38-125">例如，如果 lambda 運算式的正文為`cust.City = "London"`，則其返回類型`Boolean`為 。</span><span class="sxs-lookup"><span data-stu-id="0af38-125">For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.</span></span>

- <span data-ttu-id="0af38-126">在多行 lambda 函數中，可以使用`As`子句指定返回類型，或者省略`As`子句，以便推斷返回類型。</span><span class="sxs-lookup"><span data-stu-id="0af38-126">In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred.</span></span> <span data-ttu-id="0af38-127">當多`As`行 lambda 函數省略子句時，返回類型被推斷為多行 lambda 函數中所有`Return`語句中的主要類型。</span><span class="sxs-lookup"><span data-stu-id="0af38-127">When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function.</span></span> <span data-ttu-id="0af38-128">*主導類型*是所有其他類型都可以擴展到的唯一類型。</span><span class="sxs-lookup"><span data-stu-id="0af38-128">The *dominant type* is a unique type that all other types can widen to.</span></span> <span data-ttu-id="0af38-129">如果無法確定此唯一類型，則主導類型是陣列中所有其他類型都可以縮小到的唯一類型。</span><span class="sxs-lookup"><span data-stu-id="0af38-129">If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to.</span></span> <span data-ttu-id="0af38-130">如果這些類型皆無法決定，則主類型為 `Object`。</span><span class="sxs-lookup"><span data-stu-id="0af38-130">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="0af38-131">在這種情況下，如果`Option Strict`設置為`On`，則會發生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="0af38-131">In this case, if `Option Strict` is set to `On`, a compiler error occurs.</span></span>

     <span data-ttu-id="0af38-132">例如`Return`，如果提供給語句的運算式包含 類型`Integer`的值 ，`Long`和`Double`， 生成的陣列的類型`Double`為 。</span><span class="sxs-lookup"><span data-stu-id="0af38-132">For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="0af38-133">兩`Integer`者`Long`加寬`Double`至和`Double`僅。</span><span class="sxs-lookup"><span data-stu-id="0af38-133">Both `Integer` and `Long` widen to `Double` and only `Double`.</span></span> <span data-ttu-id="0af38-134">因此， `Double` 是主類型。</span><span class="sxs-lookup"><span data-stu-id="0af38-134">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="0af38-135">如需詳細資訊，請參閱 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="0af38-135">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>

- <span data-ttu-id="0af38-136">單行函數的正文必須是傳回值的運算式，而不是語句。</span><span class="sxs-lookup"><span data-stu-id="0af38-136">The body of a single-line function must be an expression that returns a value, not a statement.</span></span> <span data-ttu-id="0af38-137">單行函數`Return`沒有語句。</span><span class="sxs-lookup"><span data-stu-id="0af38-137">There is no `Return` statement for single-line functions.</span></span> <span data-ttu-id="0af38-138">單行函數返回的值是函數正文中運算式的值。</span><span class="sxs-lookup"><span data-stu-id="0af38-138">The value returned by the single-line function is the value of the expression in the body of the function.</span></span>

- <span data-ttu-id="0af38-139">單行副程式的正文必須是單行語句。</span><span class="sxs-lookup"><span data-stu-id="0af38-139">The body of a single-line subroutine must be single-line statement.</span></span>

- <span data-ttu-id="0af38-140">單行函數和副程式不包括 或`End Function``End Sub`語句。</span><span class="sxs-lookup"><span data-stu-id="0af38-140">Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.</span></span>

- <span data-ttu-id="0af38-141">可以使用`As`關鍵字指定 lambda 運算式參數的資料類型，也可以推斷參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="0af38-141">You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred.</span></span> <span data-ttu-id="0af38-142">所有參數都必須具有指定的資料類型，或者必須推斷所有參數。</span><span class="sxs-lookup"><span data-stu-id="0af38-142">Either all parameters must have specified data types or all must be inferred.</span></span>

- <span data-ttu-id="0af38-143">`Optional`不允許`Paramarray`和參數。</span><span class="sxs-lookup"><span data-stu-id="0af38-143">`Optional` and `Paramarray` parameters are not permitted.</span></span>

- <span data-ttu-id="0af38-144">不允許使用通用參數。</span><span class="sxs-lookup"><span data-stu-id="0af38-144">Generic parameters are not permitted.</span></span>

## <a name="async-lambdas"></a><span data-ttu-id="0af38-145">非同步 Lambda</span><span class="sxs-lookup"><span data-stu-id="0af38-145">Async Lambdas</span></span>

<span data-ttu-id="0af38-146">通過使用[Async](../../../../visual-basic/language-reference/modifiers/async.md)和[Await 運算子](../../../../visual-basic/language-reference/operators/await-operator.md)關鍵字，可以輕鬆地創建包含非同步處理的 lambda 運算式和語句。</span><span class="sxs-lookup"><span data-stu-id="0af38-146">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../../visual-basic/language-reference/modifiers/async.md) and [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) keywords.</span></span> <span data-ttu-id="0af38-147">例如，下列 Windows Form 範例包含呼叫並等候非同步方法 `ExampleMethodAsync`的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="0af38-147">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

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

<span data-ttu-id="0af38-148">您可以通過在[AddHandler 語句](../../../../visual-basic/language-reference/statements/addhandler-statement.md)中使用非同步 lambda 來添加相同的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="0af38-148">You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="0af38-149">若要加入這個處理常式，請將 `Async` 修飾詞加入至 Lambda 參數清單前面，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="0af38-149">To add this handler, add an `Async` modifier before the lambda parameter list, as the following example shows.</span></span>

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

<span data-ttu-id="0af38-150">有關如何創建和使用非同步方法的詳細資訊，請參閱[使用非同步和 Await 進行非同步程式設計](../../../../visual-basic/programming-guide/concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="0af38-150">For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

## <a name="context"></a><span data-ttu-id="0af38-151">Context</span><span class="sxs-lookup"><span data-stu-id="0af38-151">Context</span></span>

<span data-ttu-id="0af38-152">lambda 運算式與其定義上下文的範圍共用上下文。</span><span class="sxs-lookup"><span data-stu-id="0af38-152">A lambda expression shares its context with the scope within which it is defined.</span></span> <span data-ttu-id="0af38-153">它具有與在包含作用域中編寫的任何代碼相同的存取權限。</span><span class="sxs-lookup"><span data-stu-id="0af38-153">It has the same access rights as any code written in the containing scope.</span></span> <span data-ttu-id="0af38-154">這包括訪問包含作用域中的成員變數、函數和子以及`Me`參數和區域變數。</span><span class="sxs-lookup"><span data-stu-id="0af38-154">This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.</span></span>

<span data-ttu-id="0af38-155">對包含作用域中的區域變數和參數的訪問可以超出該作用域的存留期。</span><span class="sxs-lookup"><span data-stu-id="0af38-155">Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope.</span></span> <span data-ttu-id="0af38-156">只要引用 lambda 運算式的委託不能用於垃圾回收，則將保留對原始環境中變數的訪問。</span><span class="sxs-lookup"><span data-stu-id="0af38-156">As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained.</span></span> <span data-ttu-id="0af38-157">在下面的示例中，變數`target`是 局部的`makeTheGame`， 在 其中定義 lambda 運算式`playTheGame`的方法。</span><span class="sxs-lookup"><span data-stu-id="0af38-157">In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined.</span></span> <span data-ttu-id="0af38-158">請注意，分配給`takeAGuess``Main`的返回 lambda 運算式仍有權訪問區域變數`target`。</span><span class="sxs-lookup"><span data-stu-id="0af38-158">Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.</span></span>

[!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]

<span data-ttu-id="0af38-159">下面的示例演示嵌套 lambda 運算式的廣泛存取權限。</span><span class="sxs-lookup"><span data-stu-id="0af38-159">The following example demonstrates the wide range of access rights of the nested lambda expression.</span></span> <span data-ttu-id="0af38-160">當返回的 lambda 運算式從`Main``aDel`執行 時，它將訪問以下元素：</span><span class="sxs-lookup"><span data-stu-id="0af38-160">When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:</span></span>

- <span data-ttu-id="0af38-161">在其中定義它的類的欄位：`aField`</span><span class="sxs-lookup"><span data-stu-id="0af38-161">A field of the class in which it is defined: `aField`</span></span>

- <span data-ttu-id="0af38-162">定義它的類的屬性：`aProp`</span><span class="sxs-lookup"><span data-stu-id="0af38-162">A property of the class in which it is defined: `aProp`</span></span>

- <span data-ttu-id="0af38-163">方法`functionWithNestedLambda`的參數，`level1`</span><span class="sxs-lookup"><span data-stu-id="0af38-163">A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`</span></span>

- <span data-ttu-id="0af38-164">的`functionWithNestedLambda`區域變數：`localVar`</span><span class="sxs-lookup"><span data-stu-id="0af38-164">A local variable of `functionWithNestedLambda`: `localVar`</span></span>

- <span data-ttu-id="0af38-165">嵌套在 lambda 運算式中的參數：`level2`</span><span class="sxs-lookup"><span data-stu-id="0af38-165">A parameter of the lambda expression in which it is nested: `level2`</span></span>

 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]

## <a name="converting-to-a-delegate-type"></a><span data-ttu-id="0af38-166">轉換為委託類型</span><span class="sxs-lookup"><span data-stu-id="0af38-166">Converting to a Delegate Type</span></span>

<span data-ttu-id="0af38-167">lambda 運算式可以隱式轉換為相容的委託類型。</span><span class="sxs-lookup"><span data-stu-id="0af38-167">A lambda expression can be implicitly converted to a compatible delegate type.</span></span> <span data-ttu-id="0af38-168">有關相容性的一般要求的資訊，請參閱[放寬委託轉換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。</span><span class="sxs-lookup"><span data-stu-id="0af38-168">For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span> <span data-ttu-id="0af38-169">例如，以下代碼示例顯示隱式轉換為`Func(Of Integer, Boolean)`或匹配委託簽名的 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="0af38-169">For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.</span></span>

[!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]

<span data-ttu-id="0af38-170">下面的代碼示例顯示隱式轉換為`Sub(Of Double, String, Double)`或匹配委託簽名的 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="0af38-170">The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.</span></span>

[!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]

<span data-ttu-id="0af38-171">將 lambda 運算式分配給委託或將它們作為參數傳遞給過程時，可以指定參數名稱，但省略其資料類型，允許從委託獲取類型。</span><span class="sxs-lookup"><span data-stu-id="0af38-171">When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.</span></span>

## <a name="examples"></a><span data-ttu-id="0af38-172">範例</span><span class="sxs-lookup"><span data-stu-id="0af38-172">Examples</span></span>

- <span data-ttu-id="0af38-173">下面的示例定義 lambda 運算式，如果空`True`數值型別參數具有賦值，並且`False`其值為`Nothing`，則返回該運算式。</span><span class="sxs-lookup"><span data-stu-id="0af38-173">The following example defines a lambda expression that returns `True` if the nullable value type argument has an assigned value, and `False` if its value is `Nothing`.</span></span>

     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]

- <span data-ttu-id="0af38-174">下面的示例定義一個 lambda 運算式，該運算式返回陣列中最後一個元素的索引。</span><span class="sxs-lookup"><span data-stu-id="0af38-174">The following example defines a lambda expression that returns the index of the last element in an array.</span></span>

     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="0af38-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0af38-175">See also</span></span>

- [<span data-ttu-id="0af38-176">程序</span><span class="sxs-lookup"><span data-stu-id="0af38-176">Procedures</span></span>](./index.md)
- [<span data-ttu-id="0af38-177">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="0af38-177">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="0af38-178">委派</span><span class="sxs-lookup"><span data-stu-id="0af38-178">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="0af38-179">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="0af38-179">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="0af38-180">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="0af38-180">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="0af38-181">空數值型別</span><span class="sxs-lookup"><span data-stu-id="0af38-181">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="0af38-182">如何：在 Visual Basic 中將程序傳遞至其他程序</span><span class="sxs-lookup"><span data-stu-id="0af38-182">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="0af38-183">如何：建立 Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="0af38-183">How to: Create a Lambda Expression</span></span>](./how-to-create-a-lambda-expression.md)
- [<span data-ttu-id="0af38-184">寬鬆委派轉換</span><span class="sxs-lookup"><span data-stu-id="0af38-184">Relaxed Delegate Conversion</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
