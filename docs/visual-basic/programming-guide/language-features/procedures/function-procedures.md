---
title: Function 程序
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: b0ba96a875fd8785e45eee565beefe4b961ffc9d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388747"
---
# <a name="function-procedures-visual-basic"></a><span data-ttu-id="0533d-102">函數程式（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="0533d-102">Function procedures (Visual Basic)</span></span>

<span data-ttu-id="0533d-103">`Function`程式是由和語句括住的一系列 Visual Basic `Function` 語句 `End Function` 。</span><span class="sxs-lookup"><span data-stu-id="0533d-103">A `Function` procedure is a series of Visual Basic statements enclosed by the `Function` and `End Function` statements.</span></span> <span data-ttu-id="0533d-104">程式會 `Function` 執行工作，然後將控制權傳回給呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="0533d-104">The `Function` procedure performs a task and then returns control to the calling code.</span></span> <span data-ttu-id="0533d-105">當它傳回 control 時，它也會將值傳回給呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="0533d-105">When it returns control, it also returns a value to the calling code.</span></span>

<span data-ttu-id="0533d-106">每次呼叫程式時，其語句都會執行，從語句後面的第一個可執行語句開始， `Function` 並以第一個 `End Function` 、 `Exit Function` 或 `Return` 語句結尾。</span><span class="sxs-lookup"><span data-stu-id="0533d-106">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span></span>

<span data-ttu-id="0533d-107">您可以 `Function` 在模組、類別或結構中定義程式。</span><span class="sxs-lookup"><span data-stu-id="0533d-107">You can define a `Function` procedure in a module, class, or structure.</span></span> <span data-ttu-id="0533d-108">預設為 `Public` ，這表示您可以從應用程式的任何位置呼叫它，以存取您在其中定義它的模組、類別或結構。</span><span class="sxs-lookup"><span data-stu-id="0533d-108">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span>

<span data-ttu-id="0533d-109">`Function`程式可以接受引數，例如常數、變數或運算式，並由呼叫程式碼傳遞給它。</span><span class="sxs-lookup"><span data-stu-id="0533d-109">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="0533d-110">宣告語法</span><span class="sxs-lookup"><span data-stu-id="0533d-110">Declaration syntax</span></span>

<span data-ttu-id="0533d-111">宣告程式的語法如下 `Function` ：</span><span class="sxs-lookup"><span data-stu-id="0533d-111">The syntax for declaring a `Function` procedure is as follows:</span></span>

```vb
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType
    [Statements]
End Function
```

<span data-ttu-id="0533d-112">修飾*詞可以指定*有關多載、覆寫、共用和遮蔽的存取層級和資訊。</span><span class="sxs-lookup"><span data-stu-id="0533d-112">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="0533d-113">如需詳細資訊，請參閱[Function 語句](../../../language-reference/statements/function-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="0533d-113">For more information, see [Function Statement](../../../language-reference/statements/function-statement.md).</span></span>

<span data-ttu-id="0533d-114">您可以用與[Sub 程式](./sub-procedures.md)相同的方式宣告每個參數。</span><span class="sxs-lookup"><span data-stu-id="0533d-114">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="0533d-115">資料類型</span><span class="sxs-lookup"><span data-stu-id="0533d-115">Data type</span></span>

<span data-ttu-id="0533d-116">每個程式 `Function` 都有一種資料類型，就像每個變數一樣。</span><span class="sxs-lookup"><span data-stu-id="0533d-116">Every `Function` procedure has a data type, just as every variable does.</span></span> <span data-ttu-id="0533d-117">這個資料類型是由 `As` 語句中的子句所指定 `Function` ，它會判斷函式傳回給呼叫程式碼之值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="0533d-117">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span></span> <span data-ttu-id="0533d-118">下列範例宣告說明這種情況。</span><span class="sxs-lookup"><span data-stu-id="0533d-118">The following sample declarations illustrate this.</span></span>

```vb
Function Yesterday() As Date
End Function

Function FindSqrt(radicand As Single) As Single
End Function
```

<span data-ttu-id="0533d-119">如需詳細資訊，請參閱[Function 語句](../../../language-reference/statements/function-statement.md)中的「元件」。</span><span class="sxs-lookup"><span data-stu-id="0533d-119">For more information, see "Parts" in [Function Statement](../../../language-reference/statements/function-statement.md).</span></span>

### <a name="returning-values"></a><span data-ttu-id="0533d-120">傳回值</span><span class="sxs-lookup"><span data-stu-id="0533d-120">Returning values</span></span>

<span data-ttu-id="0533d-121">`Function`程式傳回給呼叫端程式碼的值稱為其傳回值。</span><span class="sxs-lookup"><span data-stu-id="0533d-121">The value a `Function` procedure sends back to the calling code is called its return value.</span></span> <span data-ttu-id="0533d-122">程式會以下列兩種方式的其中一種傳回此值：</span><span class="sxs-lookup"><span data-stu-id="0533d-122">The procedure returns this value in one of two ways:</span></span>

- <span data-ttu-id="0533d-123">它會使用 `Return` 語句來指定傳回值，並將控制權立即傳回給呼叫程式。</span><span class="sxs-lookup"><span data-stu-id="0533d-123">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span></span> <span data-ttu-id="0533d-124">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="0533d-124">The following example illustrates this.</span></span>

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement immediately transfers control back
      ' to the calling code and returns the value of Expression.
      Return Expression
  End Function
  ```

- <span data-ttu-id="0533d-125">它會在程式的一個或多個語句中，將值指派給它自己的函數名稱。</span><span class="sxs-lookup"><span data-stu-id="0533d-125">It assigns a value to its own function name in one or more statements of the procedure.</span></span> <span data-ttu-id="0533d-126">在 `Exit Function` 執行或語句之前，控制項不會回到呼叫程式 `End Function` 。</span><span class="sxs-lookup"><span data-stu-id="0533d-126">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span></span> <span data-ttu-id="0533d-127">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="0533d-127">The following example illustrates this.</span></span>

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement does not transfer control back to the calling code.
      FunctionName = Expression
      ' When control returns to the calling code, Expression is the return value.
  End Function
  ```

<span data-ttu-id="0533d-128">將傳回值指派給函數名稱的優點是，控制項不會從程式傳回，直到遇到 `Exit Function` 或 `End Function` 語句為止。</span><span class="sxs-lookup"><span data-stu-id="0533d-128">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span></span> <span data-ttu-id="0533d-129">這可讓您指派初步值，並在稍後視需要進行調整。</span><span class="sxs-lookup"><span data-stu-id="0533d-129">This allows you to assign a preliminary value and adjust it later if necessary.</span></span>

<span data-ttu-id="0533d-130">如需傳回值的詳細資訊，請參閱[Function 語句](../../../language-reference/statements/function-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="0533d-130">For more information about returning values, see [Function Statement](../../../language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="0533d-131">如需傳回陣列的詳細資訊，請參閱[陣列](../arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="0533d-131">For information about returning arrays, see [Arrays](../arrays/index.md).</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="0533d-132">呼叫語法</span><span class="sxs-lookup"><span data-stu-id="0533d-132">Calling syntax</span></span>

<span data-ttu-id="0533d-133">您可以藉 `Function` 由在指派語句的右邊或運算式中包含其名稱和引數來叫用程式。</span><span class="sxs-lookup"><span data-stu-id="0533d-133">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span> <span data-ttu-id="0533d-134">您必須提供所有非選擇性引數的值，而且必須將引數清單括在括弧中。</span><span class="sxs-lookup"><span data-stu-id="0533d-134">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="0533d-135">如果未提供任何引數，您可以選擇性地省略括弧。</span><span class="sxs-lookup"><span data-stu-id="0533d-135">If no arguments are supplied, you can optionally omit the parentheses.</span></span>

<span data-ttu-id="0533d-136">程式呼叫的語法如下所 `Function` 示。</span><span class="sxs-lookup"><span data-stu-id="0533d-136">The syntax for a call to a `Function` procedure is as follows.</span></span>

<span data-ttu-id="0533d-137">*左* `=` 值*functionname* `[(`*argumentlist*    `)]`</span><span class="sxs-lookup"><span data-stu-id="0533d-137">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span></span>

<span data-ttu-id="0533d-138">`If ((`*functionname* `[(`*argumentlist* `)] / 3) <=`*運算式*  `) Then`</span><span class="sxs-lookup"><span data-stu-id="0533d-138">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span></span>

<span data-ttu-id="0533d-139">當您呼叫程式時 `Function` ，不需要使用其傳回值。</span><span class="sxs-lookup"><span data-stu-id="0533d-139">When you call a `Function` procedure, you do not have to use its return value.</span></span> <span data-ttu-id="0533d-140">如果不這麼做，則會執行函式的所有動作，但會忽略傳回值。</span><span class="sxs-lookup"><span data-stu-id="0533d-140">If you do not, all the actions of the function are performed, but the return value is ignored.</span></span> <span data-ttu-id="0533d-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>通常會以這種方式呼叫。</span><span class="sxs-lookup"><span data-stu-id="0533d-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span></span>

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="0533d-142">宣告和呼叫的圖例</span><span class="sxs-lookup"><span data-stu-id="0533d-142">Illustration of declaration and call</span></span>

<span data-ttu-id="0533d-143">下列 `Function` 程式會計算直角三角形的最長邊（或斜邊），並指定其他兩邊的值。</span><span class="sxs-lookup"><span data-stu-id="0533d-143">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>

[!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

<span data-ttu-id="0533d-144">下列範例顯示的一般呼叫 `hypotenuse` 。</span><span class="sxs-lookup"><span data-stu-id="0533d-144">The following example shows a typical call to `hypotenuse`.</span></span>

[!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]

## <a name="see-also"></a><span data-ttu-id="0533d-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0533d-145">See also</span></span>

- [<span data-ttu-id="0533d-146">程序</span><span class="sxs-lookup"><span data-stu-id="0533d-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="0533d-147">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="0533d-147">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="0533d-148">屬性程序</span><span class="sxs-lookup"><span data-stu-id="0533d-148">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="0533d-149">運算子程序</span><span class="sxs-lookup"><span data-stu-id="0533d-149">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="0533d-150">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="0533d-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="0533d-151">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="0533d-151">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="0533d-152">如何：建立傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="0533d-152">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="0533d-153">如何：傳回程序的值</span><span class="sxs-lookup"><span data-stu-id="0533d-153">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="0533d-154">如何：呼叫傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="0533d-154">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
