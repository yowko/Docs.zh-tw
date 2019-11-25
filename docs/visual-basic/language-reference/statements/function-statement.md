---
title: Function 陳述式
ms.date: 05/12/2018
f1_keywords:
- vb.Function
helpviewer_keywords:
- procedures [Visual Basic], creating
- Function procedures [Visual Basic], Function statement syntax
- functions [Visual Basic], function procedures
- ParamArray keyword [Visual Basic], Function statements
- Private keyword [Visual Basic], Function statements
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- Public keyword [Visual Basic], in Function statement
- ByVal keyword [Visual Basic], Function statements
- procedures [Visual Basic], recursive
- Implements keyword [Visual Basic], Function statements
- procedures [Visual Basic], returning values
- Exit statement [Visual Basic], in Function procedures
- recursive procedures
- As keyword [Visual Basic], in Function statement
- Optional keyword [Visual Basic], Function statements
- Function statement [Visual Basic]
- Visual Basic code, Function procedures
- procedures [Visual Basic], function
- ByRef keyword [Visual Basic], Function statements
- Friend keyword [Visual Basic], Function statements
- End keyword [Visual Basic], Function statements
- Handles keyword [Visual Basic], Function statements
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
ms.openlocfilehash: 8140c7e6267e66c69c20d413a11d04372400c581
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345925"
---
# <a name="function-statement-visual-basic"></a><span data-ttu-id="0b698-102">Function 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b698-102">Function Statement (Visual Basic)</span></span>

<span data-ttu-id="0b698-103">Declares the name, parameters, and code that define a `Function` procedure.</span><span class="sxs-lookup"><span data-stu-id="0b698-103">Declares the name, parameters, and code that define a `Function` procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="0b698-104">語法</span><span class="sxs-lookup"><span data-stu-id="0b698-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Function ]
    [ statements ]
End Function
```

## <a name="parts"></a><span data-ttu-id="0b698-105">組件</span><span class="sxs-lookup"><span data-stu-id="0b698-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="0b698-106">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0b698-106">Optional.</span></span> <span data-ttu-id="0b698-107">See [Attribute List](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="0b698-107">See [Attribute List](attribute-list.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="0b698-108">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0b698-108">Optional.</span></span> <span data-ttu-id="0b698-109">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="0b698-109">Can be one of the following:</span></span>

  - [<span data-ttu-id="0b698-110">Public</span><span class="sxs-lookup"><span data-stu-id="0b698-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)

  - [<span data-ttu-id="0b698-111">Protected</span><span class="sxs-lookup"><span data-stu-id="0b698-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)

  - [<span data-ttu-id="0b698-112">Friend</span><span class="sxs-lookup"><span data-stu-id="0b698-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)

  - [<span data-ttu-id="0b698-113">Private</span><span class="sxs-lookup"><span data-stu-id="0b698-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)

  - [<span data-ttu-id="0b698-114">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="0b698-114">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

  - [<span data-ttu-id="0b698-115">Private Protected</span><span class="sxs-lookup"><span data-stu-id="0b698-115">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

  <span data-ttu-id="0b698-116">請參閱 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="0b698-116">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `proceduremodifiers`

  <span data-ttu-id="0b698-117">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0b698-117">Optional.</span></span> <span data-ttu-id="0b698-118">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="0b698-118">Can be one of the following:</span></span>

  - [<span data-ttu-id="0b698-119">多載</span><span class="sxs-lookup"><span data-stu-id="0b698-119">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)

  - [<span data-ttu-id="0b698-120">Overrides</span><span class="sxs-lookup"><span data-stu-id="0b698-120">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)

  - [<span data-ttu-id="0b698-121">Overridable</span><span class="sxs-lookup"><span data-stu-id="0b698-121">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)

  - [<span data-ttu-id="0b698-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="0b698-122">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)

  - [<span data-ttu-id="0b698-123">New</span><span class="sxs-lookup"><span data-stu-id="0b698-123">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="0b698-124">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0b698-124">Optional.</span></span> <span data-ttu-id="0b698-125">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="0b698-125">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="0b698-126">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0b698-126">Optional.</span></span> <span data-ttu-id="0b698-127">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="0b698-127">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>

- `Async`

  <span data-ttu-id="0b698-128">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0b698-128">Optional.</span></span> <span data-ttu-id="0b698-129">See [Async](../../../visual-basic/language-reference/modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="0b698-129">See [Async](../../../visual-basic/language-reference/modifiers/async.md).</span></span>

- `Iterator`

  <span data-ttu-id="0b698-130">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0b698-130">Optional.</span></span> <span data-ttu-id="0b698-131">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="0b698-131">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>

- `name`

  <span data-ttu-id="0b698-132">必要項。</span><span class="sxs-lookup"><span data-stu-id="0b698-132">Required.</span></span> <span data-ttu-id="0b698-133">Name of the procedure.</span><span class="sxs-lookup"><span data-stu-id="0b698-133">Name of the procedure.</span></span> <span data-ttu-id="0b698-134">請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="0b698-134">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `typeparamlist`

  <span data-ttu-id="0b698-135">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0b698-135">Optional.</span></span> <span data-ttu-id="0b698-136">List of type parameters for a generic procedure.</span><span class="sxs-lookup"><span data-stu-id="0b698-136">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="0b698-137">See [Type List](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="0b698-137">See [Type List](type-list.md).</span></span>

- `parameterlist`

  <span data-ttu-id="0b698-138">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0b698-138">Optional.</span></span> <span data-ttu-id="0b698-139">List of local variable names representing the parameters of this procedure.</span><span class="sxs-lookup"><span data-stu-id="0b698-139">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="0b698-140">See [Parameter List](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="0b698-140">See [Parameter List](parameter-list.md).</span></span>

- `returntype`

  <span data-ttu-id="0b698-141">Required if `Option Strict` is `On`.</span><span class="sxs-lookup"><span data-stu-id="0b698-141">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="0b698-142">Data type of the value returned by this procedure.</span><span class="sxs-lookup"><span data-stu-id="0b698-142">Data type of the value returned by this procedure.</span></span>

- `Implements`

  <span data-ttu-id="0b698-143">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0b698-143">Optional.</span></span> <span data-ttu-id="0b698-144">Indicates that this procedure implements one or more `Function` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span><span class="sxs-lookup"><span data-stu-id="0b698-144">Indicates that this procedure implements one or more `Function` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="0b698-145">See [Implements Statement](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0b698-145">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="0b698-146">如果使用 `Implements`，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="0b698-146">Required if `Implements` is supplied.</span></span> <span data-ttu-id="0b698-147">實作之 `Function` 程序的清單。</span><span class="sxs-lookup"><span data-stu-id="0b698-147">List of `Function` procedures being implemented.</span></span>

  `implementedprocedure [ , implementedprocedure ... ]`

  <span data-ttu-id="0b698-148">每個 `implementedprocedure` 都具有下列語法和組件：</span><span class="sxs-lookup"><span data-stu-id="0b698-148">Each `implementedprocedure` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="0b698-149">組件</span><span class="sxs-lookup"><span data-stu-id="0b698-149">Part</span></span>|<span data-ttu-id="0b698-150">描述</span><span class="sxs-lookup"><span data-stu-id="0b698-150">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="0b698-151">必要項。</span><span class="sxs-lookup"><span data-stu-id="0b698-151">Required.</span></span> <span data-ttu-id="0b698-152">Name of an interface implemented by this procedure's containing class or structure.</span><span class="sxs-lookup"><span data-stu-id="0b698-152">Name of an interface implemented by this procedure's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="0b698-153">必要項。</span><span class="sxs-lookup"><span data-stu-id="0b698-153">Required.</span></span> <span data-ttu-id="0b698-154">名稱，據以在 `interface` 中定義程序。</span><span class="sxs-lookup"><span data-stu-id="0b698-154">Name by which the procedure is defined in `interface`.</span></span>|

- `Handles`

  <span data-ttu-id="0b698-155">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0b698-155">Optional.</span></span> <span data-ttu-id="0b698-156">Indicates that this procedure can handle one or more specific events.</span><span class="sxs-lookup"><span data-stu-id="0b698-156">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="0b698-157">See [Handles](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="0b698-157">See [Handles](handles-clause.md).</span></span>

- `eventlist`

  <span data-ttu-id="0b698-158">如果使用 `Handles`，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="0b698-158">Required if `Handles` is supplied.</span></span> <span data-ttu-id="0b698-159">List of events this procedure handles.</span><span class="sxs-lookup"><span data-stu-id="0b698-159">List of events this procedure handles.</span></span>

  `eventspecifier [ , eventspecifier ... ]`

  <span data-ttu-id="0b698-160">每個 `eventspecifier` 都具有下列語法和組件：</span><span class="sxs-lookup"><span data-stu-id="0b698-160">Each `eventspecifier` has the following syntax and parts:</span></span>

  `eventvariable.event`

  |<span data-ttu-id="0b698-161">組件</span><span class="sxs-lookup"><span data-stu-id="0b698-161">Part</span></span>|<span data-ttu-id="0b698-162">描述</span><span class="sxs-lookup"><span data-stu-id="0b698-162">Description</span></span>|
  |---|---|
  |`eventvariable`|<span data-ttu-id="0b698-163">必要項。</span><span class="sxs-lookup"><span data-stu-id="0b698-163">Required.</span></span> <span data-ttu-id="0b698-164">Object variable declared with the data type of the class or structure that raises the event.</span><span class="sxs-lookup"><span data-stu-id="0b698-164">Object variable declared with the data type of the class or structure that raises the event.</span></span>|
  |`event`|<span data-ttu-id="0b698-165">必要項。</span><span class="sxs-lookup"><span data-stu-id="0b698-165">Required.</span></span> <span data-ttu-id="0b698-166">Name of the event this procedure handles.</span><span class="sxs-lookup"><span data-stu-id="0b698-166">Name of the event this procedure handles.</span></span>|

- `statements`

  <span data-ttu-id="0b698-167">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0b698-167">Optional.</span></span> <span data-ttu-id="0b698-168">Block of statements to be executed within this procedure.</span><span class="sxs-lookup"><span data-stu-id="0b698-168">Block of statements to be executed within this procedure.</span></span>

- `End Function`

  <span data-ttu-id="0b698-169">Terminates the definition of this procedure.</span><span class="sxs-lookup"><span data-stu-id="0b698-169">Terminates the definition of this procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="0b698-170">備註</span><span class="sxs-lookup"><span data-stu-id="0b698-170">Remarks</span></span>

<span data-ttu-id="0b698-171">All executable code must be inside a procedure.</span><span class="sxs-lookup"><span data-stu-id="0b698-171">All executable code must be inside a procedure.</span></span> <span data-ttu-id="0b698-172">Each procedure, in turn, is declared within a class, a structure, or a module that is referred to as the containing class, structure, or module.</span><span class="sxs-lookup"><span data-stu-id="0b698-172">Each procedure, in turn, is declared within a class, a structure, or a module that is referred to as the containing class, structure, or module.</span></span>

<span data-ttu-id="0b698-173">To return a value to the calling code, use a `Function` procedure; otherwise, use a `Sub` procedure.</span><span class="sxs-lookup"><span data-stu-id="0b698-173">To return a value to the calling code, use a `Function` procedure; otherwise, use a `Sub` procedure.</span></span>

## <a name="defining-a-function"></a><span data-ttu-id="0b698-174">Defining a Function</span><span class="sxs-lookup"><span data-stu-id="0b698-174">Defining a Function</span></span>

<span data-ttu-id="0b698-175">You can define a `Function` procedure only at the module level.</span><span class="sxs-lookup"><span data-stu-id="0b698-175">You can define a `Function` procedure only at the module level.</span></span> <span data-ttu-id="0b698-176">Therefore, the declaration context for a function must be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span><span class="sxs-lookup"><span data-stu-id="0b698-176">Therefore, the declaration context for a function must be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="0b698-177">如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="0b698-177">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="0b698-178">`Function` procedures default to public access.</span><span class="sxs-lookup"><span data-stu-id="0b698-178">`Function` procedures default to public access.</span></span> <span data-ttu-id="0b698-179">You can adjust their access levels with the access modifiers.</span><span class="sxs-lookup"><span data-stu-id="0b698-179">You can adjust their access levels with the access modifiers.</span></span>

<span data-ttu-id="0b698-180">A `Function` procedure can declare the data type of the value that the procedure returns.</span><span class="sxs-lookup"><span data-stu-id="0b698-180">A `Function` procedure can declare the data type of the value that the procedure returns.</span></span> <span data-ttu-id="0b698-181">You can specify any data type or the name of an enumeration, a structure, a class, or an interface.</span><span class="sxs-lookup"><span data-stu-id="0b698-181">You can specify any data type or the name of an enumeration, a structure, a class, or an interface.</span></span> <span data-ttu-id="0b698-182">If you don't specify the `returntype` parameter, the procedure returns `Object`.</span><span class="sxs-lookup"><span data-stu-id="0b698-182">If you don't specify the `returntype` parameter, the procedure returns `Object`.</span></span>

<span data-ttu-id="0b698-183">If this procedure uses the `Implements` keyword, the containing class or structure must also have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span><span class="sxs-lookup"><span data-stu-id="0b698-183">If this procedure uses the `Implements` keyword, the containing class or structure must also have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="0b698-184">The `Implements` statement must include each interface that's specified in `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="0b698-184">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="0b698-185">However, the name by which an interface defines the `Function` (in `definedname`) doesn't need to match the name of this procedure (in `name`).</span><span class="sxs-lookup"><span data-stu-id="0b698-185">However, the name by which an interface defines the `Function` (in `definedname`) doesn't need to match the name of this procedure (in `name`).</span></span>

> [!NOTE]
> <span data-ttu-id="0b698-186">You can use lambda expressions to define function expressions inline.</span><span class="sxs-lookup"><span data-stu-id="0b698-186">You can use lambda expressions to define function expressions inline.</span></span> <span data-ttu-id="0b698-187">For more information, see [Function Expression](../../../visual-basic/language-reference/operators/function-expression.md) and [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="0b698-187">For more information, see [Function Expression](../../../visual-basic/language-reference/operators/function-expression.md) and [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

## <a name="returning-from-a-function"></a><span data-ttu-id="0b698-188">Returning from a Function</span><span class="sxs-lookup"><span data-stu-id="0b698-188">Returning from a Function</span></span>

<span data-ttu-id="0b698-189">When the `Function` procedure returns to the calling code, execution continues with the statement that follows the statement that called the procedure.</span><span class="sxs-lookup"><span data-stu-id="0b698-189">When the `Function` procedure returns to the calling code, execution continues with the statement that follows the statement that called the procedure.</span></span>

<span data-ttu-id="0b698-190">To return a value from a function, you can either assign the value to the function name or include it in a `Return` statement.</span><span class="sxs-lookup"><span data-stu-id="0b698-190">To return a value from a function, you can either assign the value to the function name or include it in a `Return` statement.</span></span>

<span data-ttu-id="0b698-191">The `Return` statement simultaneously assigns the return value and exits the function, as the following example shows.</span><span class="sxs-lookup"><span data-stu-id="0b698-191">The `Return` statement simultaneously assigns the return value and exits the function, as the following example shows.</span></span>

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

<span data-ttu-id="0b698-192">The following example assigns the return value to the function name `myFunction` and then uses the `Exit Function` statement to return.</span><span class="sxs-lookup"><span data-stu-id="0b698-192">The following example assigns the return value to the function name `myFunction` and then uses the `Exit Function` statement to return.</span></span>

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

<span data-ttu-id="0b698-193">The `Exit Function` and `Return` statements cause an immediate exit from a `Function` procedure.</span><span class="sxs-lookup"><span data-stu-id="0b698-193">The `Exit Function` and `Return` statements cause an immediate exit from a `Function` procedure.</span></span> <span data-ttu-id="0b698-194">Any number of `Exit Function` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Function` and `Return` statements.</span><span class="sxs-lookup"><span data-stu-id="0b698-194">Any number of `Exit Function` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Function` and `Return` statements.</span></span>

<span data-ttu-id="0b698-195">If you use `Exit Function` without assigning a value to `name`, the procedure returns the default value for the data type that's specified in `returntype`.</span><span class="sxs-lookup"><span data-stu-id="0b698-195">If you use `Exit Function` without assigning a value to `name`, the procedure returns the default value for the data type that's specified in `returntype`.</span></span> <span data-ttu-id="0b698-196">If `returntype` isn't specified, the procedure returns `Nothing`, which is the default value for `Object`.</span><span class="sxs-lookup"><span data-stu-id="0b698-196">If `returntype` isn't specified, the procedure returns `Nothing`, which is the default value for `Object`.</span></span>

## <a name="calling-a-function"></a><span data-ttu-id="0b698-197">呼叫函式</span><span class="sxs-lookup"><span data-stu-id="0b698-197">Calling a Function</span></span>

<span data-ttu-id="0b698-198">You call a `Function` procedure by using the procedure name, followed by the argument list in parentheses, in an expression.</span><span class="sxs-lookup"><span data-stu-id="0b698-198">You call a `Function` procedure by using the procedure name, followed by the argument list in parentheses, in an expression.</span></span> <span data-ttu-id="0b698-199">You can omit the parentheses only if you aren't supplying any arguments.</span><span class="sxs-lookup"><span data-stu-id="0b698-199">You can omit the parentheses only if you aren't supplying any arguments.</span></span> <span data-ttu-id="0b698-200">However, your code is more readable if you always include the parentheses.</span><span class="sxs-lookup"><span data-stu-id="0b698-200">However, your code is more readable if you always include the parentheses.</span></span>

<span data-ttu-id="0b698-201">You call a `Function` procedure the same way that you call any library function such as `Sqrt`, `Cos`, or `ChrW`.</span><span class="sxs-lookup"><span data-stu-id="0b698-201">You call a `Function` procedure the same way that you call any library function such as `Sqrt`, `Cos`, or `ChrW`.</span></span>

<span data-ttu-id="0b698-202">You can also call a function by using the `Call` keyword.</span><span class="sxs-lookup"><span data-stu-id="0b698-202">You can also call a function by using the `Call` keyword.</span></span> <span data-ttu-id="0b698-203">In that case, the return value is ignored.</span><span class="sxs-lookup"><span data-stu-id="0b698-203">In that case, the return value is ignored.</span></span> <span data-ttu-id="0b698-204">Use of the `Call` keyword isn't recommended in most cases.</span><span class="sxs-lookup"><span data-stu-id="0b698-204">Use of the `Call` keyword isn't recommended in most cases.</span></span> <span data-ttu-id="0b698-205">For more information, see [Call Statement](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0b698-205">For more information, see [Call Statement](call-statement.md).</span></span>

<span data-ttu-id="0b698-206">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span><span class="sxs-lookup"><span data-stu-id="0b698-206">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="0b698-207">For that reason, you shouldn't use a `Function` procedure in an arithmetic expression when the function changes the value of variables in the same expression.</span><span class="sxs-lookup"><span data-stu-id="0b698-207">For that reason, you shouldn't use a `Function` procedure in an arithmetic expression when the function changes the value of variables in the same expression.</span></span>

## <a name="async-functions"></a><span data-ttu-id="0b698-208">Async Functions</span><span class="sxs-lookup"><span data-stu-id="0b698-208">Async Functions</span></span>

<span data-ttu-id="0b698-209">The *Async* feature allows you to invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span><span class="sxs-lookup"><span data-stu-id="0b698-209">The *Async* feature allows you to invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>

<span data-ttu-id="0b698-210">If you mark a function with the [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the function.</span><span class="sxs-lookup"><span data-stu-id="0b698-210">If you mark a function with the [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the function.</span></span> <span data-ttu-id="0b698-211">When control reaches an `Await` expression in the `Async` function, control returns to the caller, and progress in the function is suspended until the awaited task completes.</span><span class="sxs-lookup"><span data-stu-id="0b698-211">When control reaches an `Await` expression in the `Async` function, control returns to the caller, and progress in the function is suspended until the awaited task completes.</span></span> <span data-ttu-id="0b698-212">When the task is complete, execution can resume in the function.</span><span class="sxs-lookup"><span data-stu-id="0b698-212">When the task is complete, execution can resume in the function.</span></span>

> [!NOTE]
> <span data-ttu-id="0b698-213">An `Async` procedure returns to the caller when either it encounters the first awaited object that’s not yet complete, or it gets to the end of the `Async` procedure, whichever occurs first.</span><span class="sxs-lookup"><span data-stu-id="0b698-213">An `Async` procedure returns to the caller when either it encounters the first awaited object that’s not yet complete, or it gets to the end of the `Async` procedure, whichever occurs first.</span></span>

<span data-ttu-id="0b698-214">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="0b698-214">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="0b698-215">An example of an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601> is provided below.</span><span class="sxs-lookup"><span data-stu-id="0b698-215">An example of an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601> is provided below.</span></span>

<span data-ttu-id="0b698-216">An `Async` function cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.</span><span class="sxs-lookup"><span data-stu-id="0b698-216">An `Async` function cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="0b698-217">A [Sub Statement](sub-statement.md) can also be marked with the `Async` modifier.</span><span class="sxs-lookup"><span data-stu-id="0b698-217">A [Sub Statement](sub-statement.md) can also be marked with the `Async` modifier.</span></span> <span data-ttu-id="0b698-218">This is primarily used for event handlers, where a value cannot be returned.</span><span class="sxs-lookup"><span data-stu-id="0b698-218">This is primarily used for event handlers, where a value cannot be returned.</span></span> <span data-ttu-id="0b698-219">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that are thrown by the `Sub` procedure.</span><span class="sxs-lookup"><span data-stu-id="0b698-219">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that are thrown by the `Sub` procedure.</span></span>

<span data-ttu-id="0b698-220">For more information about `Async` functions, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="0b698-220">For more information about `Async` functions, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="iterator-functions"></a><span data-ttu-id="0b698-221">Iterator Functions</span><span class="sxs-lookup"><span data-stu-id="0b698-221">Iterator Functions</span></span>

<span data-ttu-id="0b698-222">An *iterator* function performs a custom iteration over a collection, such as a list or array.</span><span class="sxs-lookup"><span data-stu-id="0b698-222">An *iterator* function performs a custom iteration over a collection, such as a list or array.</span></span> <span data-ttu-id="0b698-223">An iterator function uses the [Yield](yield-statement.md) statement to return each element one at a time.</span><span class="sxs-lookup"><span data-stu-id="0b698-223">An iterator function uses the [Yield](yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="0b698-224">When a [Yield](yield-statement.md) statement is reached, the current location in code is remembered.</span><span class="sxs-lookup"><span data-stu-id="0b698-224">When a [Yield](yield-statement.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="0b698-225">下次呼叫迭代器函式時，便會從這個位置重新開始執行。</span><span class="sxs-lookup"><span data-stu-id="0b698-225">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="0b698-226">You call an iterator from client code by using a [For Each…Next](for-each-next-statement.md) statement.</span><span class="sxs-lookup"><span data-stu-id="0b698-226">You call an iterator from client code by using a [For Each…Next](for-each-next-statement.md) statement.</span></span>

<span data-ttu-id="0b698-227">The return type of an iterator function can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="0b698-227">The return type of an iterator function can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="0b698-228">如需詳細資訊，請參閱[迭代器](../../programming-guide/concepts/iterators.md)。</span><span class="sxs-lookup"><span data-stu-id="0b698-228">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>

## <a name="example"></a><span data-ttu-id="0b698-229">範例</span><span class="sxs-lookup"><span data-stu-id="0b698-229">Example</span></span>

<span data-ttu-id="0b698-230">The following example uses the `Function` statement to declare the name, parameters, and code that form the body of a `Function` procedure.</span><span class="sxs-lookup"><span data-stu-id="0b698-230">The following example uses the `Function` statement to declare the name, parameters, and code that form the body of a `Function` procedure.</span></span> <span data-ttu-id="0b698-231">The `ParamArray` modifier enables the function to accept a variable number of arguments.</span><span class="sxs-lookup"><span data-stu-id="0b698-231">The `ParamArray` modifier enables the function to accept a variable number of arguments.</span></span>

[!code-vb[VbVbalrStatements#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#25)]

## <a name="example"></a><span data-ttu-id="0b698-232">範例</span><span class="sxs-lookup"><span data-stu-id="0b698-232">Example</span></span>

<span data-ttu-id="0b698-233">The following example invokes the function declared in the preceding example.</span><span class="sxs-lookup"><span data-stu-id="0b698-233">The following example invokes the function declared in the preceding example.</span></span>

[!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]

## <a name="example"></a><span data-ttu-id="0b698-234">範例</span><span class="sxs-lookup"><span data-stu-id="0b698-234">Example</span></span>

<span data-ttu-id="0b698-235">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="0b698-235">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="0b698-236">`DelayAsync` 具有傳回整數的 `Return` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="0b698-236">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="0b698-237">Therefore the function declaration of `DelayAsync` needs to have a return type of `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="0b698-237">Therefore the function declaration of `DelayAsync` needs to have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="0b698-238">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer.</span><span class="sxs-lookup"><span data-stu-id="0b698-238">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer.</span></span> <span data-ttu-id="0b698-239">This is demonstrated in this statement: `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="0b698-239">This is demonstrated in this statement: `Dim result As Integer = Await delayTask`.</span></span>

<span data-ttu-id="0b698-240">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span><span class="sxs-lookup"><span data-stu-id="0b698-240">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="0b698-241">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement demonstrates: `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="0b698-241">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement demonstrates: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="0b698-242">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span><span class="sxs-lookup"><span data-stu-id="0b698-242">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="0b698-243">請參閱</span><span class="sxs-lookup"><span data-stu-id="0b698-243">See also</span></span>

- [<span data-ttu-id="0b698-244">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="0b698-244">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="0b698-245">函式程序</span><span class="sxs-lookup"><span data-stu-id="0b698-245">Function Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="0b698-246">參數清單</span><span class="sxs-lookup"><span data-stu-id="0b698-246">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="0b698-247">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="0b698-247">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="0b698-248">Call 陳述式</span><span class="sxs-lookup"><span data-stu-id="0b698-248">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="0b698-249">Of</span><span class="sxs-lookup"><span data-stu-id="0b698-249">Of</span></span>](of-clause.md)
- [<span data-ttu-id="0b698-250">參數陣列</span><span class="sxs-lookup"><span data-stu-id="0b698-250">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="0b698-251">如何：使用泛型類別</span><span class="sxs-lookup"><span data-stu-id="0b698-251">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="0b698-252">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="0b698-252">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="0b698-253">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="0b698-253">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="0b698-254">函式運算式</span><span class="sxs-lookup"><span data-stu-id="0b698-254">Function Expression</span></span>](../../../visual-basic/language-reference/operators/function-expression.md)
