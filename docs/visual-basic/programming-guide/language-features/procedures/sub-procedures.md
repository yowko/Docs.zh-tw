---
title: Sub 程序
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
ms.openlocfilehash: 9ca1d302a0bc8e989e0b2dddf8cce68e89211d57
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163809"
---
# <a name="sub-procedures-visual-basic"></a><span data-ttu-id="15a5b-102">Sub 程式（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="15a5b-102">Sub procedures (Visual Basic)</span></span>

<span data-ttu-id="15a5b-103">`Sub` 程式是以 `Sub` 和 `End Sub` 語句括住的一系列 Visual Basic 語句。</span><span class="sxs-lookup"><span data-stu-id="15a5b-103">A `Sub` procedure is a series of Visual Basic statements enclosed by the `Sub` and `End Sub` statements.</span></span> <span data-ttu-id="15a5b-104">`Sub` 程式會執行工作，然後將控制權傳回給呼叫程式碼，但不會將值傳回給呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="15a5b-104">The `Sub` procedure performs a task and then returns control to the calling code, but it does not return a value to the calling code.</span></span>

<span data-ttu-id="15a5b-105">每次呼叫程式時，都會執行其語句，從 `Sub` 語句後面的第一個可執行語句開始，並以遇到的第一個 `End Sub`、`Exit Sub`或 `Return` 語句為結尾。</span><span class="sxs-lookup"><span data-stu-id="15a5b-105">Each time the procedure is called, its statements are executed, starting with the first executable statement after the `Sub` statement and ending with the first `End Sub`, `Exit Sub`, or `Return` statement encountered.</span></span>

<span data-ttu-id="15a5b-106">您可以在模組、類別和結構中定義 `Sub` 程式。</span><span class="sxs-lookup"><span data-stu-id="15a5b-106">You can define a `Sub` procedure in modules, classes, and structures.</span></span> <span data-ttu-id="15a5b-107">根據預設，它是 `Public`的，這表示您可以從應用程式的任何位置呼叫它，以存取您在其中定義它的模組、類別或結構。</span><span class="sxs-lookup"><span data-stu-id="15a5b-107">By default, it is `Public`, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span> <span data-ttu-id="15a5b-108">詞彙*方法*描述從其定義模組、類別或結構之外存取的 `Sub` 或 `Function` 程式。</span><span class="sxs-lookup"><span data-stu-id="15a5b-108">The term *method* describes a `Sub` or `Function` procedure that is accessed from outside its defining module, class, or structure.</span></span> <span data-ttu-id="15a5b-109">如需詳細資訊，請參閱[程序](./index.md)。</span><span class="sxs-lookup"><span data-stu-id="15a5b-109">For more information, see [Procedures](./index.md).</span></span>

<span data-ttu-id="15a5b-110">`Sub` 程式可以接受引數，例如常數、變數或運算式，由呼叫程式碼傳遞給它。</span><span class="sxs-lookup"><span data-stu-id="15a5b-110">A `Sub` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="15a5b-111">宣告語法</span><span class="sxs-lookup"><span data-stu-id="15a5b-111">Declaration syntax</span></span>

<span data-ttu-id="15a5b-112">宣告 `Sub` 程式的語法如下：</span><span class="sxs-lookup"><span data-stu-id="15a5b-112">The syntax for declaring a `Sub` procedure is as follows:</span></span>

```vb
[modifiers] Sub SubName[(parameterList)]
    ' Statements of the Sub procedure.
End Sub
```

<span data-ttu-id="15a5b-113">`modifiers` 可以指定有關多載、覆寫、共用和遮蔽的存取層級和資訊。</span><span class="sxs-lookup"><span data-stu-id="15a5b-113">The `modifiers` can specify access level and information about overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="15a5b-114">如需詳細資訊，請參閱[Sub 語句](../../../language-reference/statements/sub-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="15a5b-114">For more information, see [Sub Statement](../../../language-reference/statements/sub-statement.md).</span></span>

## <a name="parameter-declaration"></a><span data-ttu-id="15a5b-115">參數宣告</span><span class="sxs-lookup"><span data-stu-id="15a5b-115">Parameter declaration</span></span>

<span data-ttu-id="15a5b-116">您可以宣告每個程式參數，類似于宣告變數的方式，指定參數名稱和資料類型。</span><span class="sxs-lookup"><span data-stu-id="15a5b-116">You declare each procedure parameter similarly to how you declare a variable, specifying the parameter name and data type.</span></span> <span data-ttu-id="15a5b-117">您也可以指定傳遞機制，以及參數是否為選擇性或參數陣列。</span><span class="sxs-lookup"><span data-stu-id="15a5b-117">You can also specify the passing mechanism, and whether the parameter is optional or a parameter array.</span></span>

<span data-ttu-id="15a5b-118">參數清單中每個參數的語法如下：</span><span class="sxs-lookup"><span data-stu-id="15a5b-118">The syntax for each parameter in the parameter list is as follows:</span></span>

```vb
[Optional] [ByVal | ByRef] [ParamArray] parameterName As DataType
```

<span data-ttu-id="15a5b-119">如果參數是選擇性的，您也必須提供預設值做為其宣告的一部分。</span><span class="sxs-lookup"><span data-stu-id="15a5b-119">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="15a5b-120">指定預設值的語法如下：</span><span class="sxs-lookup"><span data-stu-id="15a5b-120">The syntax for specifying a default value is as follows:</span></span>

```vb
Optional [ByVal | ByRef]  parameterName As DataType = defaultValue
```

### <a name="parameters-as-local-variables"></a><span data-ttu-id="15a5b-121">參數作為區域變數</span><span class="sxs-lookup"><span data-stu-id="15a5b-121">Parameters as local variables</span></span>

<span data-ttu-id="15a5b-122">當控制項傳遞至程式時，會將每個參數視為本機變數。</span><span class="sxs-lookup"><span data-stu-id="15a5b-122">When control passes to the procedure, each parameter is treated as a local variable.</span></span> <span data-ttu-id="15a5b-123">這表示它的存留期與程式相同，而且其範圍為整個程式。</span><span class="sxs-lookup"><span data-stu-id="15a5b-123">This means that its lifetime is the same as that of the procedure, and its scope is the whole procedure.</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="15a5b-124">呼叫語法</span><span class="sxs-lookup"><span data-stu-id="15a5b-124">Calling syntax</span></span>

<span data-ttu-id="15a5b-125">您可以使用獨立的呼叫語句來明確叫用 `Sub` 程式。</span><span class="sxs-lookup"><span data-stu-id="15a5b-125">You invoke a `Sub` procedure explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="15a5b-126">您不能在運算式中使用它的名稱來呼叫它。</span><span class="sxs-lookup"><span data-stu-id="15a5b-126">You cannot call it by using its name in an expression.</span></span> <span data-ttu-id="15a5b-127">您必須提供所有非選擇性引數的值，而且必須將引數清單括在括弧中。</span><span class="sxs-lookup"><span data-stu-id="15a5b-127">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="15a5b-128">如果未提供任何引數，您可以選擇性地省略括弧。</span><span class="sxs-lookup"><span data-stu-id="15a5b-128">If no arguments are supplied, you can optionally omit the parentheses.</span></span> <span data-ttu-id="15a5b-129">`Call` 關鍵字是選擇性的，但不建議使用。</span><span class="sxs-lookup"><span data-stu-id="15a5b-129">The use of the `Call` keyword is optional but not recommended.</span></span>

<span data-ttu-id="15a5b-130">呼叫 `Sub` 程式的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="15a5b-130">The syntax for a call to a `Sub` procedure is as follows:</span></span>

```vb
[Call] SubName[(argumentlist)]
```

<span data-ttu-id="15a5b-131">您可以從定義它的類別外部呼叫 `Sub` 方法。</span><span class="sxs-lookup"><span data-stu-id="15a5b-131">You can call a `Sub` method from outside the class that defines it.</span></span> <span data-ttu-id="15a5b-132">首先，您必須使用 `New` 關鍵字來建立類別的實例，或呼叫方法來傳回類別的實例。</span><span class="sxs-lookup"><span data-stu-id="15a5b-132">First, you have to use the `New` keyword to create an instance of the class, or call a method that returns an instance of the class.</span></span> <span data-ttu-id="15a5b-133">如需詳細資訊，請參閱[New Operator](../../../language-reference/operators/new-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="15a5b-133">For more information, see [New Operator](../../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="15a5b-134">然後，您可以使用下列語法，在實例物件上呼叫 `Sub` 方法：</span><span class="sxs-lookup"><span data-stu-id="15a5b-134">Then, you can use the following syntax to call the `Sub` method on the instance object:</span></span>

```vb
object.MethodName[(argumentList)]
```

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="15a5b-135">宣告和呼叫的圖例</span><span class="sxs-lookup"><span data-stu-id="15a5b-135">Illustration of declaration and call</span></span>

<span data-ttu-id="15a5b-136">下列 `Sub` 程式會告訴電腦操作員應用程式即將執行哪一項工作，同時也會顯示時間戳記。</span><span class="sxs-lookup"><span data-stu-id="15a5b-136">The following `Sub` procedure tells the computer operator which task the application is about to perform, and also displays a time stamp.</span></span> <span data-ttu-id="15a5b-137">應用程式只會從不同位置呼叫 `tellOperator`，而不是在每個工作開始時複製此程式碼。</span><span class="sxs-lookup"><span data-stu-id="15a5b-137">Instead of duplicating this code at the start of every task, the application just calls `tellOperator` from various locations.</span></span> <span data-ttu-id="15a5b-138">每個呼叫都會在 `task` 引數中傳遞一個字串，以識別要啟動的工作。</span><span class="sxs-lookup"><span data-stu-id="15a5b-138">Each call passes a string in the `task` argument that identifies the task being started.</span></span>

[!code-vb[VbVbcnProcedures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#2)]

<span data-ttu-id="15a5b-139">下列範例顯示 `tellOperator`的一般呼叫。</span><span class="sxs-lookup"><span data-stu-id="15a5b-139">The following example shows a typical call to `tellOperator`.</span></span>

[!code-vb[VbVbcnProcedures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#3)]

## <a name="see-also"></a><span data-ttu-id="15a5b-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="15a5b-140">See also</span></span>

- [<span data-ttu-id="15a5b-141">程序</span><span class="sxs-lookup"><span data-stu-id="15a5b-141">Procedures</span></span>](./index.md)
- [<span data-ttu-id="15a5b-142">函式程序</span><span class="sxs-lookup"><span data-stu-id="15a5b-142">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="15a5b-143">屬性程序</span><span class="sxs-lookup"><span data-stu-id="15a5b-143">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="15a5b-144">運算子程序</span><span class="sxs-lookup"><span data-stu-id="15a5b-144">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="15a5b-145">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="15a5b-145">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="15a5b-146">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="15a5b-146">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="15a5b-147">如何：呼叫不傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="15a5b-147">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
- [<span data-ttu-id="15a5b-148">如何：在 Visual Basic 中呼叫事件處理常式</span><span class="sxs-lookup"><span data-stu-id="15a5b-148">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
