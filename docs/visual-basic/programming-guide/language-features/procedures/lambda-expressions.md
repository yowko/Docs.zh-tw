---
title: Lambda 運算式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: e688beac18e782367bf39ddec8339df2b2735225
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928908"
---
# <a name="lambda-expressions-visual-basic"></a><span data-ttu-id="bc53f-102">Lambda 運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc53f-102">Lambda Expressions (Visual Basic)</span></span>
<span data-ttu-id="bc53f-103">*Lambda 運算式*是一個不含名稱的函式或副程式, 可以在委派有效的任何地方使用。</span><span class="sxs-lookup"><span data-stu-id="bc53f-103">A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid.</span></span> <span data-ttu-id="bc53f-104">Lambda 運算式可以是函數或副程式, 而且可以是單行或多行。</span><span class="sxs-lookup"><span data-stu-id="bc53f-104">Lambda expressions can be functions or subroutines and can be single-line or multi-line.</span></span> <span data-ttu-id="bc53f-105">您可以將值從目前範圍傳遞至 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="bc53f-105">You can pass values from the current scope to a lambda expression.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bc53f-106">`RemoveHandler`語句是例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bc53f-106">The `RemoveHandler` statement is an exception.</span></span> <span data-ttu-id="bc53f-107">您無法在中傳遞的 lambda 運算式做為的委派`RemoveHandler`參數。</span><span class="sxs-lookup"><span data-stu-id="bc53f-107">You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.</span></span>  
  
 <span data-ttu-id="bc53f-108">您可以使用`Function`或`Sub`關鍵字來建立 lambda 運算式, 就如同建立標準函數或副程式一樣。</span><span class="sxs-lookup"><span data-stu-id="bc53f-108">You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine.</span></span> <span data-ttu-id="bc53f-109">不過, lambda 運算式會包含在語句中。</span><span class="sxs-lookup"><span data-stu-id="bc53f-109">However, lambda expressions are included in a statement.</span></span>  
  
 <span data-ttu-id="bc53f-110">下列範例是 lambda 運算式, 它會遞增其引數並傳回值。</span><span class="sxs-lookup"><span data-stu-id="bc53f-110">The following example is a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="bc53f-111">此範例會顯示函數的單行和多行 lambda 運算式語法。</span><span class="sxs-lookup"><span data-stu-id="bc53f-111">The example shows both the single-line and multi-line lambda expression syntax for a function.</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
 <span data-ttu-id="bc53f-112">下列範例是將值寫入主控台的 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="bc53f-112">The following example is a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="bc53f-113">此範例會顯示副程式的單行和多行 lambda 運算式語法。</span><span class="sxs-lookup"><span data-stu-id="bc53f-113">The example shows both the single-line and multi-line lambda expression syntax for a subroutine.</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
 <span data-ttu-id="bc53f-114">請注意, 在先前的範例中, lambda 運算式會指派給變數名稱。</span><span class="sxs-lookup"><span data-stu-id="bc53f-114">Notice that in the previous examples the lambda expressions are assigned to a variable name.</span></span> <span data-ttu-id="bc53f-115">每當您參考變數時, 就會叫用 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="bc53f-115">Whenever you refer to the variable, you invoke the lambda expression.</span></span> <span data-ttu-id="bc53f-116">您也可以同時宣告和叫用 lambda 運算式, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="bc53f-116">You can also declare and invoke a lambda expression at the same time, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
 <span data-ttu-id="bc53f-117">Lambda 運算式可以當做函式呼叫的值傳回 (如本主題稍後的[內容](#context)章節中的範例所示), 或當做引數傳遞給採用委派類型的參數, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="bc53f-117">A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="bc53f-118">Lambda 運算式語法</span><span class="sxs-lookup"><span data-stu-id="bc53f-118">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="bc53f-119">Lambda 運算式的語法類似于標準函式或副程式。</span><span class="sxs-lookup"><span data-stu-id="bc53f-119">The syntax of a lambda expression resembles that of a standard function or subroutine.</span></span> <span data-ttu-id="bc53f-120">差異如下:</span><span class="sxs-lookup"><span data-stu-id="bc53f-120">The differences are as follows:</span></span>  
  
- <span data-ttu-id="bc53f-121">Lambda 運算式沒有名稱。</span><span class="sxs-lookup"><span data-stu-id="bc53f-121">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="bc53f-122">Lambda 運算式不能有修飾詞, `Overloads`例如`Overrides`或。</span><span class="sxs-lookup"><span data-stu-id="bc53f-122">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="bc53f-123">單行 lambda 函數不會使用`As`子句來指定傳回類型。</span><span class="sxs-lookup"><span data-stu-id="bc53f-123">Single-line lambda functions do not use an `As` clause to designate the return type.</span></span> <span data-ttu-id="bc53f-124">相反地, 型別是從 lambda 運算式主體評估為的值推斷而來。</span><span class="sxs-lookup"><span data-stu-id="bc53f-124">Instead, the type is inferred from the value that the body of the lambda expression evaluates to.</span></span> <span data-ttu-id="bc53f-125">例如, 如果 lambda 運算式的主體是`cust.City = "London"`, 其傳回型別會是。 `Boolean`</span><span class="sxs-lookup"><span data-stu-id="bc53f-125">For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
- <span data-ttu-id="bc53f-126">在多行 lambda 函式中, 您可以使用`As`子句來指定傳回類型, 或`As`省略子句, 以推斷傳回類型。</span><span class="sxs-lookup"><span data-stu-id="bc53f-126">In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred.</span></span> <span data-ttu-id="bc53f-127">當多行 lambda 函數省略`Return` 子句時,會將傳回型別推斷為多行lambda函式中所有語句的主要型別。`As`</span><span class="sxs-lookup"><span data-stu-id="bc53f-127">When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function.</span></span> <span data-ttu-id="bc53f-128">*主要類型*是所有其他類型都可以擴展的唯一類型。</span><span class="sxs-lookup"><span data-stu-id="bc53f-128">The *dominant type* is a unique type that all other types can widen to.</span></span> <span data-ttu-id="bc53f-129">如果無法判斷此唯一類型, 則主要類型是陣列中所有其他類型都可以縮小為的唯一類型。</span><span class="sxs-lookup"><span data-stu-id="bc53f-129">If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to.</span></span> <span data-ttu-id="bc53f-130">如果這些類型皆無法決定，則主類型為 `Object`。</span><span class="sxs-lookup"><span data-stu-id="bc53f-130">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="bc53f-131">在此情況下, `Option Strict`如果設定為`On`, 則會發生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="bc53f-131">In this case, if `Option Strict` is set to `On`, a compiler error occurs.</span></span>  
  
     <span data-ttu-id="bc53f-132">例如`Return` , 如果提供給語句的運算式包含型`Integer`別、 `Long`和`Double`的值, 則產生的陣列會是型`Double`別。</span><span class="sxs-lookup"><span data-stu-id="bc53f-132">For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="bc53f-133">和只會擴大`Double`為和。 `Double` `Long` `Integer`</span><span class="sxs-lookup"><span data-stu-id="bc53f-133">Both `Integer` and `Long` widen to `Double` and only `Double`.</span></span> <span data-ttu-id="bc53f-134">因此， `Double` 是主類型。</span><span class="sxs-lookup"><span data-stu-id="bc53f-134">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="bc53f-135">如需詳細資訊，請參閱 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="bc53f-135">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
- <span data-ttu-id="bc53f-136">單行函數的主體必須是傳回值的運算式, 而不是語句。</span><span class="sxs-lookup"><span data-stu-id="bc53f-136">The body of a single-line function must be an expression that returns a value, not a statement.</span></span> <span data-ttu-id="bc53f-137">沒有單行函式的語句。`Return`</span><span class="sxs-lookup"><span data-stu-id="bc53f-137">There is no `Return` statement for single-line functions.</span></span> <span data-ttu-id="bc53f-138">單行函式所傳回的值是函數主體中的運算式值。</span><span class="sxs-lookup"><span data-stu-id="bc53f-138">The value returned by the single-line function is the value of the expression in the body of the function.</span></span>  
  
- <span data-ttu-id="bc53f-139">單行副程式的主體必須是單行語句。</span><span class="sxs-lookup"><span data-stu-id="bc53f-139">The body of a single-line subroutine must be single-line statement.</span></span>  
  
- <span data-ttu-id="bc53f-140">單行函數和副程式不包含`End Function`或`End Sub`語句。</span><span class="sxs-lookup"><span data-stu-id="bc53f-140">Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.</span></span>  
  
- <span data-ttu-id="bc53f-141">您可以使用`As`關鍵字來指定 lambda 運算式參數的資料類型, 或可以推斷參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="bc53f-141">You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred.</span></span> <span data-ttu-id="bc53f-142">所有參數都必須具有指定的資料類型, 否則必須推斷全部。</span><span class="sxs-lookup"><span data-stu-id="bc53f-142">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
- <span data-ttu-id="bc53f-143">`Optional`不`Paramarray`允許使用和參數。</span><span class="sxs-lookup"><span data-stu-id="bc53f-143">`Optional` and `Paramarray` parameters are not permitted.</span></span>  
  
- <span data-ttu-id="bc53f-144">不允許泛型參數。</span><span class="sxs-lookup"><span data-stu-id="bc53f-144">Generic parameters are not permitted.</span></span>  
  
## <a name="async-lambdas"></a><span data-ttu-id="bc53f-145">非同步 Lambda</span><span class="sxs-lookup"><span data-stu-id="bc53f-145">Async Lambdas</span></span>  
 <span data-ttu-id="bc53f-146">您可以使用[Async](../../../../visual-basic/language-reference/modifiers/async.md)和[Await 運算子](../../../../visual-basic/language-reference/operators/await-operator.md)關鍵字, 輕鬆建立結合非同步處理的 lambda 運算式和語句。</span><span class="sxs-lookup"><span data-stu-id="bc53f-146">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../../visual-basic/language-reference/modifiers/async.md) and [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) keywords.</span></span> <span data-ttu-id="bc53f-147">例如，下列 Windows Form 範例包含呼叫並等候非同步方法 `ExampleMethodAsync`的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="bc53f-147">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>  
  
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
  
 <span data-ttu-id="bc53f-148">您可以在[AddHandler 語句](../../../../visual-basic/language-reference/statements/addhandler-statement.md)中使用非同步 lambda 來加入相同的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="bc53f-148">You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="bc53f-149">若要加入這個處理常式，請將 `Async` 修飾詞加入至 Lambda 參數清單前面，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="bc53f-149">To add this handler, add an `Async` modifier before the lambda parameter list, as the following example shows.</span></span>  
  
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
  
 <span data-ttu-id="bc53f-150">如需如何建立和使用非同步方法的詳細資訊, 請參閱[使用 async 和 Await 進行非同步程式設計](../../../../visual-basic/programming-guide/concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="bc53f-150">For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
## <a name="context"></a><span data-ttu-id="bc53f-151">內容</span><span class="sxs-lookup"><span data-stu-id="bc53f-151">Context</span></span>  
 <span data-ttu-id="bc53f-152">Lambda 運算式會與其定義所在的範圍共用其內容。</span><span class="sxs-lookup"><span data-stu-id="bc53f-152">A lambda expression shares its context with the scope within which it is defined.</span></span> <span data-ttu-id="bc53f-153">其存取權限與在包含範圍中撰寫的任何程式碼相同。</span><span class="sxs-lookup"><span data-stu-id="bc53f-153">It has the same access rights as any code written in the containing scope.</span></span> <span data-ttu-id="bc53f-154">這包括存取成員變數、函式和`Me`子函式, 以及包含範圍內的參數和區域變數。</span><span class="sxs-lookup"><span data-stu-id="bc53f-154">This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.</span></span>  
  
 <span data-ttu-id="bc53f-155">存取包含範圍中的本機變數和參數, 可以延伸超出該範圍的存留期。</span><span class="sxs-lookup"><span data-stu-id="bc53f-155">Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope.</span></span> <span data-ttu-id="bc53f-156">只要參考 lambda 運算式的委派無法用於垃圾收集, 就會保留原始環境中變數的存取權。</span><span class="sxs-lookup"><span data-stu-id="bc53f-156">As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained.</span></span> <span data-ttu-id="bc53f-157">在下列範例中, 變數`target`是的`makeTheGame`區域, 也就是定義 lambda 運算式`playTheGame`的方法。</span><span class="sxs-lookup"><span data-stu-id="bc53f-157">In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined.</span></span> <span data-ttu-id="bc53f-158">請注意, 指派`takeAGuess`給中`Main`的傳回 lambda 運算式仍然具有區域變數的`target`存取權。</span><span class="sxs-lookup"><span data-stu-id="bc53f-158">Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]  
  
 <span data-ttu-id="bc53f-159">下列範例示範嵌套 lambda 運算式的範圍存取權限。</span><span class="sxs-lookup"><span data-stu-id="bc53f-159">The following example demonstrates the wide range of access rights of the nested lambda expression.</span></span> <span data-ttu-id="bc53f-160">`Main` 從`aDel`執行傳回的 lambda 運算式時, 它會存取下列元素:</span><span class="sxs-lookup"><span data-stu-id="bc53f-160">When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:</span></span>  
  
- <span data-ttu-id="bc53f-161">其定義所在類別的欄位:`aField`</span><span class="sxs-lookup"><span data-stu-id="bc53f-161">A field of the class in which it is defined: `aField`</span></span>  
  
- <span data-ttu-id="bc53f-162">其定義所在之類別的屬性:`aProp`</span><span class="sxs-lookup"><span data-stu-id="bc53f-162">A property of the class in which it is defined: `aProp`</span></span>  
  
- <span data-ttu-id="bc53f-163">方法`functionWithNestedLambda`的參數, 其定義如下:`level1`</span><span class="sxs-lookup"><span data-stu-id="bc53f-163">A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`</span></span>  
  
- <span data-ttu-id="bc53f-164">的`functionWithNestedLambda`本機變數:`localVar`</span><span class="sxs-lookup"><span data-stu-id="bc53f-164">A local variable of `functionWithNestedLambda`: `localVar`</span></span>  
  
- <span data-ttu-id="bc53f-165">Lambda 運算式的參數, 其會在其中加以嵌套:`level2`</span><span class="sxs-lookup"><span data-stu-id="bc53f-165">A parameter of the lambda expression in which it is nested: `level2`</span></span>  
  
 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]  
  
## <a name="converting-to-a-delegate-type"></a><span data-ttu-id="bc53f-166">轉換成委派類型</span><span class="sxs-lookup"><span data-stu-id="bc53f-166">Converting to a Delegate Type</span></span>  
 <span data-ttu-id="bc53f-167">Lambda 運算式可以隱含地轉換成相容的委派類型。</span><span class="sxs-lookup"><span data-stu-id="bc53f-167">A lambda expression can be implicitly converted to a compatible delegate type.</span></span> <span data-ttu-id="bc53f-168">如需相容性一般需求的相關資訊, 請參閱[寬鬆委派轉換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。</span><span class="sxs-lookup"><span data-stu-id="bc53f-168">For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span> <span data-ttu-id="bc53f-169">例如, 下列程式碼範例顯示隱含轉換成`Func(Of Integer, Boolean)`或相符委派簽章的 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="bc53f-169">For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.</span></span>  
  
 [!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]  
  
 <span data-ttu-id="bc53f-170">下列程式碼範例顯示隱含轉換成`Sub(Of Double, String, Double)`或相符之委派簽章的 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="bc53f-170">The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.</span></span>  
  
 [!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]  
  
 <span data-ttu-id="bc53f-171">當您將 lambda 運算式指派給委派, 或將它們當做引數傳遞給程式時, 您可以指定參數名稱但省略其資料類型, 讓型別可以從委派取得。</span><span class="sxs-lookup"><span data-stu-id="bc53f-171">When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="bc53f-172">範例</span><span class="sxs-lookup"><span data-stu-id="bc53f-172">Examples</span></span>  
  
- <span data-ttu-id="bc53f-173">下列範例會定義 lambda 運算式, `True`如果可為 null 的引數具有指派的值, 且`False`其值為`Nothing`, 則會傳回。</span><span class="sxs-lookup"><span data-stu-id="bc53f-173">The following example defines a lambda expression that returns `True` if the nullable argument has an assigned value, and `False` if its value is `Nothing`.</span></span>  
  
     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]  
  
- <span data-ttu-id="bc53f-174">下列範例會定義 lambda 運算式, 以傳回陣列中最後一個元素的索引。</span><span class="sxs-lookup"><span data-stu-id="bc53f-174">The following example defines a lambda expression that returns the index of the last element in an array.</span></span>  
  
     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="bc53f-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc53f-175">See also</span></span>

- [<span data-ttu-id="bc53f-176">程序</span><span class="sxs-lookup"><span data-stu-id="bc53f-176">Procedures</span></span>](./index.md)
- [<span data-ttu-id="bc53f-177">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="bc53f-177">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="bc53f-178">委派</span><span class="sxs-lookup"><span data-stu-id="bc53f-178">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="bc53f-179">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="bc53f-179">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="bc53f-180">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="bc53f-180">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="bc53f-181">可為 Null 的值類型</span><span class="sxs-lookup"><span data-stu-id="bc53f-181">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="bc53f-182">如何：將程式傳遞至 Visual Basic 中的另一個程式</span><span class="sxs-lookup"><span data-stu-id="bc53f-182">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="bc53f-183">如何：建立 Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="bc53f-183">How to: Create a Lambda Expression</span></span>](./how-to-create-a-lambda-expression.md)
- [<span data-ttu-id="bc53f-184">寬鬆委派轉換</span><span class="sxs-lookup"><span data-stu-id="bc53f-184">Relaxed Delegate Conversion</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
