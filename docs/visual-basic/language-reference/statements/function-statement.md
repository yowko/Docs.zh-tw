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
ms.openlocfilehash: 49cf4fead2c5594b7ac6815f82fea0dc995ea436
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404624"
---
# <a name="function-statement-visual-basic"></a><span data-ttu-id="d083a-102">Function 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d083a-102">Function Statement (Visual Basic)</span></span>

<span data-ttu-id="d083a-103">宣告定義程式的名稱、參數和程式碼 `Function` 。</span><span class="sxs-lookup"><span data-stu-id="d083a-103">Declares the name, parameters, and code that define a `Function` procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="d083a-104">語法</span><span class="sxs-lookup"><span data-stu-id="d083a-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Function ]
    [ statements ]
End Function
```

## <a name="parts"></a><span data-ttu-id="d083a-105">組件</span><span class="sxs-lookup"><span data-stu-id="d083a-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="d083a-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d083a-106">Optional.</span></span> <span data-ttu-id="d083a-107">請參閱[屬性清單](attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="d083a-107">See [Attribute List](attribute-list.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="d083a-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d083a-108">Optional.</span></span> <span data-ttu-id="d083a-109">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="d083a-109">Can be one of the following:</span></span>

  - [<span data-ttu-id="d083a-110">公開</span><span class="sxs-lookup"><span data-stu-id="d083a-110">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="d083a-111">免受</span><span class="sxs-lookup"><span data-stu-id="d083a-111">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="d083a-112">給</span><span class="sxs-lookup"><span data-stu-id="d083a-112">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="d083a-113">私用</span><span class="sxs-lookup"><span data-stu-id="d083a-113">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="d083a-114">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="d083a-114">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="d083a-115">私用保護</span><span class="sxs-lookup"><span data-stu-id="d083a-115">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="d083a-116">請參閱[Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="d083a-116">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `proceduremodifiers`

  <span data-ttu-id="d083a-117">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d083a-117">Optional.</span></span> <span data-ttu-id="d083a-118">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="d083a-118">Can be one of the following:</span></span>

  - [<span data-ttu-id="d083a-119">多載</span><span class="sxs-lookup"><span data-stu-id="d083a-119">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="d083a-120">覆寫</span><span class="sxs-lookup"><span data-stu-id="d083a-120">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="d083a-121">Overrides</span><span class="sxs-lookup"><span data-stu-id="d083a-121">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="d083a-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="d083a-122">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="d083a-123">New</span><span class="sxs-lookup"><span data-stu-id="d083a-123">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="d083a-124">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d083a-124">Optional.</span></span> <span data-ttu-id="d083a-125">請參閱[共用](../modifiers/shared.md)。</span><span class="sxs-lookup"><span data-stu-id="d083a-125">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="d083a-126">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d083a-126">Optional.</span></span> <span data-ttu-id="d083a-127">請參閱[Shadows](../modifiers/shadows.md)。</span><span class="sxs-lookup"><span data-stu-id="d083a-127">See [Shadows](../modifiers/shadows.md).</span></span>

- `Async`

  <span data-ttu-id="d083a-128">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d083a-128">Optional.</span></span> <span data-ttu-id="d083a-129">請參閱[Async](../modifiers/async.md)。</span><span class="sxs-lookup"><span data-stu-id="d083a-129">See [Async](../modifiers/async.md).</span></span>

- `Iterator`

  <span data-ttu-id="d083a-130">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d083a-130">Optional.</span></span> <span data-ttu-id="d083a-131">請參閱[Iterator](../modifiers/iterator.md)。</span><span class="sxs-lookup"><span data-stu-id="d083a-131">See [Iterator](../modifiers/iterator.md).</span></span>

- `name`

  <span data-ttu-id="d083a-132">必要。</span><span class="sxs-lookup"><span data-stu-id="d083a-132">Required.</span></span> <span data-ttu-id="d083a-133">程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="d083a-133">Name of the procedure.</span></span> <span data-ttu-id="d083a-134">請參閱 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="d083a-134">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `typeparamlist`

  <span data-ttu-id="d083a-135">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d083a-135">Optional.</span></span> <span data-ttu-id="d083a-136">泛型程式的類型參數清單。</span><span class="sxs-lookup"><span data-stu-id="d083a-136">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="d083a-137">請參閱[類型清單](type-list.md)。</span><span class="sxs-lookup"><span data-stu-id="d083a-137">See [Type List](type-list.md).</span></span>

- `parameterlist`

  <span data-ttu-id="d083a-138">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d083a-138">Optional.</span></span> <span data-ttu-id="d083a-139">本機變數名稱的清單，代表此程式的參數。</span><span class="sxs-lookup"><span data-stu-id="d083a-139">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="d083a-140">請參閱[參數清單](parameter-list.md)。</span><span class="sxs-lookup"><span data-stu-id="d083a-140">See [Parameter List](parameter-list.md).</span></span>

- `returntype`

  <span data-ttu-id="d083a-141">如果 `Option Strict` 為，則為必要 `On` 。</span><span class="sxs-lookup"><span data-stu-id="d083a-141">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="d083a-142">這個程式所傳回之值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="d083a-142">Data type of the value returned by this procedure.</span></span>

- `Implements`

  <span data-ttu-id="d083a-143">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d083a-143">Optional.</span></span> <span data-ttu-id="d083a-144">指出此程式會執行一或多個 `Function` 程式，其中每一個都是在介面中所定義的介面中，其包含類別或結構。</span><span class="sxs-lookup"><span data-stu-id="d083a-144">Indicates that this procedure implements one or more `Function` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="d083a-145">請參閱[Implements 語句](implements-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="d083a-145">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="d083a-146">如果使用 `Implements`，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="d083a-146">Required if `Implements` is supplied.</span></span> <span data-ttu-id="d083a-147">實作之 `Function` 程序的清單。</span><span class="sxs-lookup"><span data-stu-id="d083a-147">List of `Function` procedures being implemented.</span></span>

  `implementedprocedure [ , implementedprocedure ... ]`

  <span data-ttu-id="d083a-148">每個 `implementedprocedure` 都具有下列語法和組件：</span><span class="sxs-lookup"><span data-stu-id="d083a-148">Each `implementedprocedure` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="d083a-149">部分</span><span class="sxs-lookup"><span data-stu-id="d083a-149">Part</span></span>|<span data-ttu-id="d083a-150">描述</span><span class="sxs-lookup"><span data-stu-id="d083a-150">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="d083a-151">必要。</span><span class="sxs-lookup"><span data-stu-id="d083a-151">Required.</span></span> <span data-ttu-id="d083a-152">此程式的包含類別或結構所實作為介面的名稱。</span><span class="sxs-lookup"><span data-stu-id="d083a-152">Name of an interface implemented by this procedure's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="d083a-153">必要。</span><span class="sxs-lookup"><span data-stu-id="d083a-153">Required.</span></span> <span data-ttu-id="d083a-154">名稱，據以在 `interface` 中定義程序。</span><span class="sxs-lookup"><span data-stu-id="d083a-154">Name by which the procedure is defined in `interface`.</span></span>|

- `Handles`

  <span data-ttu-id="d083a-155">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d083a-155">Optional.</span></span> <span data-ttu-id="d083a-156">指出此程式可以處理一或多個特定事件。</span><span class="sxs-lookup"><span data-stu-id="d083a-156">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="d083a-157">請參閱[控制碼](handles-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="d083a-157">See [Handles](handles-clause.md).</span></span>

- `eventlist`

  <span data-ttu-id="d083a-158">如果使用 `Handles`，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="d083a-158">Required if `Handles` is supplied.</span></span> <span data-ttu-id="d083a-159">此程式處理的事件清單。</span><span class="sxs-lookup"><span data-stu-id="d083a-159">List of events this procedure handles.</span></span>

  `eventspecifier [ , eventspecifier ... ]`

  <span data-ttu-id="d083a-160">每個 `eventspecifier` 都具有下列語法和組件：</span><span class="sxs-lookup"><span data-stu-id="d083a-160">Each `eventspecifier` has the following syntax and parts:</span></span>

  `eventvariable.event`

  |<span data-ttu-id="d083a-161">部分</span><span class="sxs-lookup"><span data-stu-id="d083a-161">Part</span></span>|<span data-ttu-id="d083a-162">描述</span><span class="sxs-lookup"><span data-stu-id="d083a-162">Description</span></span>|
  |---|---|
  |`eventvariable`|<span data-ttu-id="d083a-163">必要。</span><span class="sxs-lookup"><span data-stu-id="d083a-163">Required.</span></span> <span data-ttu-id="d083a-164">以引發事件之類別或結構的資料類型宣告的物件變數。</span><span class="sxs-lookup"><span data-stu-id="d083a-164">Object variable declared with the data type of the class or structure that raises the event.</span></span>|
  |`event`|<span data-ttu-id="d083a-165">必要。</span><span class="sxs-lookup"><span data-stu-id="d083a-165">Required.</span></span> <span data-ttu-id="d083a-166">這個程式處理的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="d083a-166">Name of the event this procedure handles.</span></span>|

- `statements`

  <span data-ttu-id="d083a-167">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d083a-167">Optional.</span></span> <span data-ttu-id="d083a-168">要在此程式中執行的語句區塊。</span><span class="sxs-lookup"><span data-stu-id="d083a-168">Block of statements to be executed within this procedure.</span></span>

- `End Function`

  <span data-ttu-id="d083a-169">終止這個程式的定義。</span><span class="sxs-lookup"><span data-stu-id="d083a-169">Terminates the definition of this procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="d083a-170">備註</span><span class="sxs-lookup"><span data-stu-id="d083a-170">Remarks</span></span>

<span data-ttu-id="d083a-171">所有可執行檔程式碼都必須在程式內。</span><span class="sxs-lookup"><span data-stu-id="d083a-171">All executable code must be inside a procedure.</span></span> <span data-ttu-id="d083a-172">接著，每個程式都會在類別、結構或稱為包含類別、結構或模組的模組中宣告。</span><span class="sxs-lookup"><span data-stu-id="d083a-172">Each procedure, in turn, is declared within a class, a structure, or a module that is referred to as the containing class, structure, or module.</span></span>

<span data-ttu-id="d083a-173">若要將值傳回給呼叫程式碼，請使用程式 `Function` ; 否則，請使用程式 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="d083a-173">To return a value to the calling code, use a `Function` procedure; otherwise, use a `Sub` procedure.</span></span>

## <a name="defining-a-function"></a><span data-ttu-id="d083a-174">定義函數</span><span class="sxs-lookup"><span data-stu-id="d083a-174">Defining a Function</span></span>

<span data-ttu-id="d083a-175">您 `Function` 只能在模組層級定義程式。</span><span class="sxs-lookup"><span data-stu-id="d083a-175">You can define a `Function` procedure only at the module level.</span></span> <span data-ttu-id="d083a-176">因此，函式的宣告內容必須是類別、結構、模組或介面，而且不能是原始程式檔、命名空間、程式或區塊。</span><span class="sxs-lookup"><span data-stu-id="d083a-176">Therefore, the declaration context for a function must be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="d083a-177">如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="d083a-177">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="d083a-178">`Function`程式預設為公用存取。</span><span class="sxs-lookup"><span data-stu-id="d083a-178">`Function` procedures default to public access.</span></span> <span data-ttu-id="d083a-179">您可以使用存取修飾詞來調整其存取層級。</span><span class="sxs-lookup"><span data-stu-id="d083a-179">You can adjust their access levels with the access modifiers.</span></span>

<span data-ttu-id="d083a-180">程式可以宣告此程式所傳回 `Function` 值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="d083a-180">A `Function` procedure can declare the data type of the value that the procedure returns.</span></span> <span data-ttu-id="d083a-181">您可以指定任何資料類型或列舉的名稱、結構、類別或介面。</span><span class="sxs-lookup"><span data-stu-id="d083a-181">You can specify any data type or the name of an enumeration, a structure, a class, or an interface.</span></span> <span data-ttu-id="d083a-182">如果您未指定 `returntype` 參數，此程式會傳回 `Object` 。</span><span class="sxs-lookup"><span data-stu-id="d083a-182">If you don't specify the `returntype` parameter, the procedure returns `Object`.</span></span>

<span data-ttu-id="d083a-183">如果此程式使用 `Implements` 關鍵字，則包含的類別或結構也必須有 `Implements` 緊接在其或語句後面的語句 `Class` `Structure` 。</span><span class="sxs-lookup"><span data-stu-id="d083a-183">If this procedure uses the `Implements` keyword, the containing class or structure must also have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="d083a-184">`Implements`語句必須包含中所指定的每個介面 `implementslist` 。</span><span class="sxs-lookup"><span data-stu-id="d083a-184">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="d083a-185">不過，介面用來定義 `Function` （在中）的名稱 `definedname` 不需要符合此程式的名稱（在中為 `name` ）。</span><span class="sxs-lookup"><span data-stu-id="d083a-185">However, the name by which an interface defines the `Function` (in `definedname`) doesn't need to match the name of this procedure (in `name`).</span></span>

> [!NOTE]
> <span data-ttu-id="d083a-186">您可以使用 lambda 運算式來定義內嵌函數運算式。</span><span class="sxs-lookup"><span data-stu-id="d083a-186">You can use lambda expressions to define function expressions inline.</span></span> <span data-ttu-id="d083a-187">如需詳細資訊，請參閱[函數運算式](../operators/function-expression.md)和[Lambda 運算式](../../programming-guide/language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="d083a-187">For more information, see [Function Expression](../operators/function-expression.md) and [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

## <a name="returning-from-a-function"></a><span data-ttu-id="d083a-188">從函式傳回</span><span class="sxs-lookup"><span data-stu-id="d083a-188">Returning from a Function</span></span>

<span data-ttu-id="d083a-189">當程式 `Function` 返回呼叫程式碼時，執行會繼續進行呼叫程式之語句後面的語句。</span><span class="sxs-lookup"><span data-stu-id="d083a-189">When the `Function` procedure returns to the calling code, execution continues with the statement that follows the statement that called the procedure.</span></span>

<span data-ttu-id="d083a-190">若要從函式傳回值，您可以將值指派給函數名稱，或將它包含在 `Return` 語句中。</span><span class="sxs-lookup"><span data-stu-id="d083a-190">To return a value from a function, you can either assign the value to the function name or include it in a `Return` statement.</span></span>

<span data-ttu-id="d083a-191">`Return`語句會同時指派傳回值並結束函式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d083a-191">The `Return` statement simultaneously assigns the return value and exits the function, as the following example shows.</span></span>

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

<span data-ttu-id="d083a-192">下列範例會將傳回值指派給函數名稱 `myFunction` ，然後使用語句傳回 `Exit Function` 。</span><span class="sxs-lookup"><span data-stu-id="d083a-192">The following example assigns the return value to the function name `myFunction` and then uses the `Exit Function` statement to return.</span></span>

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

<span data-ttu-id="d083a-193">`Exit Function`和 `Return` 語句會導致程式立即結束 `Function` 。</span><span class="sxs-lookup"><span data-stu-id="d083a-193">The `Exit Function` and `Return` statements cause an immediate exit from a `Function` procedure.</span></span> <span data-ttu-id="d083a-194">任何數目的 `Exit Function` 和 `Return` 語句都可以出現在程式中的任何位置，而且您可以混合使用 `Exit Function` 和 `Return` 語句。</span><span class="sxs-lookup"><span data-stu-id="d083a-194">Any number of `Exit Function` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Function` and `Return` statements.</span></span>

<span data-ttu-id="d083a-195">如果您使用 `Exit Function` ，但未將值指派給 `name` ，則程式會傳回中所指定之資料類型的預設值 `returntype` 。</span><span class="sxs-lookup"><span data-stu-id="d083a-195">If you use `Exit Function` without assigning a value to `name`, the procedure returns the default value for the data type that's specified in `returntype`.</span></span> <span data-ttu-id="d083a-196">如果 `returntype` 未指定，則 `Nothing` 程式會傳回，這是的預設值 `Object` 。</span><span class="sxs-lookup"><span data-stu-id="d083a-196">If `returntype` isn't specified, the procedure returns `Nothing`, which is the default value for `Object`.</span></span>

## <a name="calling-a-function"></a><span data-ttu-id="d083a-197">呼叫函式</span><span class="sxs-lookup"><span data-stu-id="d083a-197">Calling a Function</span></span>

<span data-ttu-id="d083a-198">您可以 `Function` 在運算式中使用程式名稱，後面接著以括弧括住的引數清單來呼叫程式。</span><span class="sxs-lookup"><span data-stu-id="d083a-198">You call a `Function` procedure by using the procedure name, followed by the argument list in parentheses, in an expression.</span></span> <span data-ttu-id="d083a-199">只有在未提供任何引數時，才可以省略括弧。</span><span class="sxs-lookup"><span data-stu-id="d083a-199">You can omit the parentheses only if you aren't supplying any arguments.</span></span> <span data-ttu-id="d083a-200">不過，如果您一律包含括弧，則程式碼會更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="d083a-200">However, your code is more readable if you always include the parentheses.</span></span>

<span data-ttu-id="d083a-201">呼叫 `Function` 程式的方法與呼叫任何程式庫函式（例如、或）的方式相同 `Sqrt` `Cos` `ChrW` 。</span><span class="sxs-lookup"><span data-stu-id="d083a-201">You call a `Function` procedure the same way that you call any library function such as `Sqrt`, `Cos`, or `ChrW`.</span></span>

<span data-ttu-id="d083a-202">您也可以使用關鍵字來呼叫函式 `Call` 。</span><span class="sxs-lookup"><span data-stu-id="d083a-202">You can also call a function by using the `Call` keyword.</span></span> <span data-ttu-id="d083a-203">在此情況下，會忽略傳回值。</span><span class="sxs-lookup"><span data-stu-id="d083a-203">In that case, the return value is ignored.</span></span> <span data-ttu-id="d083a-204">`Call`在大部分的情況下，不建議使用關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d083a-204">Use of the `Call` keyword isn't recommended in most cases.</span></span> <span data-ttu-id="d083a-205">如需詳細資訊，請參閱[Call 語句](call-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="d083a-205">For more information, see [Call Statement](call-statement.md).</span></span>

<span data-ttu-id="d083a-206">Visual Basic 有時會重新排列算術運算式，以提高內部效率。</span><span class="sxs-lookup"><span data-stu-id="d083a-206">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="d083a-207">基於這個理由， `Function` 當函數變更相同運算式中的變數值時，您不應該在算術運算式中使用程式。</span><span class="sxs-lookup"><span data-stu-id="d083a-207">For that reason, you shouldn't use a `Function` procedure in an arithmetic expression when the function changes the value of variables in the same expression.</span></span>

## <a name="async-functions"></a><span data-ttu-id="d083a-208">Async 函式</span><span class="sxs-lookup"><span data-stu-id="d083a-208">Async Functions</span></span>

<span data-ttu-id="d083a-209">*非同步*功能可讓您在不使用明確回呼的情況下叫用非同步函式，或在多個函式或 lambda 運算式中手動分割程式碼。</span><span class="sxs-lookup"><span data-stu-id="d083a-209">The *Async* feature allows you to invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>

<span data-ttu-id="d083a-210">如果您使用[Async](../modifiers/async.md)修飾詞來標示函式，您可以在函式中使用[Await](../operators/await-operator.md)運算子。</span><span class="sxs-lookup"><span data-stu-id="d083a-210">If you mark a function with the [Async](../modifiers/async.md) modifier, you can use the [Await](../operators/await-operator.md) operator in the function.</span></span> <span data-ttu-id="d083a-211">當控制項到達函式 `Await` 中的運算式時 `Async` ，控制項會回到呼叫端，而函式中的進度會暫停，直到等候的工作完成為止。</span><span class="sxs-lookup"><span data-stu-id="d083a-211">When control reaches an `Await` expression in the `Async` function, control returns to the caller, and progress in the function is suspended until the awaited task completes.</span></span> <span data-ttu-id="d083a-212">當工作完成時，可以在函式中繼續執行。</span><span class="sxs-lookup"><span data-stu-id="d083a-212">When the task is complete, execution can resume in the function.</span></span>

> [!NOTE]
> <span data-ttu-id="d083a-213">程式會 `Async` 在遇到第一個尚未完成的等候物件，或到達程式結尾 `Async` （以先發生者為准）時，將它傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="d083a-213">An `Async` procedure returns to the caller when either it encounters the first awaited object that’s not yet complete, or it gets to the end of the `Async` procedure, whichever occurs first.</span></span>

<span data-ttu-id="d083a-214">`Async`函數可以具有或的傳回類型 <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task> 。</span><span class="sxs-lookup"><span data-stu-id="d083a-214">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="d083a-215">`Async`以下提供傳回類型為的函式範例 <xref:System.Threading.Tasks.Task%601> 。</span><span class="sxs-lookup"><span data-stu-id="d083a-215">An example of an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601> is provided below.</span></span>

<span data-ttu-id="d083a-216">函式 `Async` 不能宣告任何[ByRef](../modifiers/byref.md)參數。</span><span class="sxs-lookup"><span data-stu-id="d083a-216">An `Async` function cannot declare any [ByRef](../modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="d083a-217">[Sub 語句](sub-statement.md)也可以使用修飾詞來標記 `Async` 。</span><span class="sxs-lookup"><span data-stu-id="d083a-217">A [Sub Statement](sub-statement.md) can also be marked with the `Async` modifier.</span></span> <span data-ttu-id="d083a-218">這主要用於事件處理常式，無法傳回值。</span><span class="sxs-lookup"><span data-stu-id="d083a-218">This is primarily used for event handlers, where a value cannot be returned.</span></span> <span data-ttu-id="d083a-219">無法等候程式 `Async` `Sub` ，而且程式的呼叫端 `Async` `Sub` 無法攔截程式所擲回的例外狀況 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="d083a-219">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that are thrown by the `Sub` procedure.</span></span>

<span data-ttu-id="d083a-220">如需函式的詳細資訊 `Async` ，請參閱[使用 Async 和 Await 進行非同步程式設計](../../programming-guide/concepts/async/index.md)、[非同步程式中的控制流程](../../programming-guide/concepts/async/control-flow-in-async-programs.md)和[非同步傳回類型](../../programming-guide/concepts/async/async-return-types.md)。</span><span class="sxs-lookup"><span data-stu-id="d083a-220">For more information about `Async` functions, see [Asynchronous Programming with Async and Await](../../programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="iterator-functions"></a><span data-ttu-id="d083a-221">Iterator 函式</span><span class="sxs-lookup"><span data-stu-id="d083a-221">Iterator Functions</span></span>

<span data-ttu-id="d083a-222">*Iterator*函式會對集合執行自訂反復專案，例如清單或陣列。</span><span class="sxs-lookup"><span data-stu-id="d083a-222">An *iterator* function performs a custom iteration over a collection, such as a list or array.</span></span> <span data-ttu-id="d083a-223">Iterator 函數會使用[Yield](yield-statement.md)語句，一次傳回一個元素。</span><span class="sxs-lookup"><span data-stu-id="d083a-223">An iterator function uses the [Yield](yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="d083a-224">當達到[Yield](yield-statement.md)語句時，會記住程式碼中的目前位置。</span><span class="sxs-lookup"><span data-stu-id="d083a-224">When a [Yield](yield-statement.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="d083a-225">下次呼叫迭代器函式時，便會從這個位置重新開始執行。</span><span class="sxs-lookup"><span data-stu-id="d083a-225">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="d083a-226">您可以從用戶端程式代碼呼叫反覆運算器，方法是使用[For Each .。。下一個](for-each-next-statement.md)語句。</span><span class="sxs-lookup"><span data-stu-id="d083a-226">You call an iterator from client code by using a [For Each…Next](for-each-next-statement.md) statement.</span></span>

<span data-ttu-id="d083a-227">Iterator 函數的傳回型別可以是 <xref:System.Collections.IEnumerable> 、 <xref:System.Collections.Generic.IEnumerable%601> 、 <xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601> 。</span><span class="sxs-lookup"><span data-stu-id="d083a-227">The return type of an iterator function can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="d083a-228">如需詳細資訊，請參閱[反覆運算](../../programming-guide/concepts/iterators.md)器。</span><span class="sxs-lookup"><span data-stu-id="d083a-228">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>

## <a name="example"></a><span data-ttu-id="d083a-229">範例</span><span class="sxs-lookup"><span data-stu-id="d083a-229">Example</span></span>

<span data-ttu-id="d083a-230">下列範例 `Function` 會使用語句來宣告構成程式主體的名稱、參數和代碼 `Function` 。</span><span class="sxs-lookup"><span data-stu-id="d083a-230">The following example uses the `Function` statement to declare the name, parameters, and code that form the body of a `Function` procedure.</span></span> <span data-ttu-id="d083a-231">`ParamArray`修飾詞可讓函式接受可變數目的引數。</span><span class="sxs-lookup"><span data-stu-id="d083a-231">The `ParamArray` modifier enables the function to accept a variable number of arguments.</span></span>

[!code-vb[VbVbalrStatements#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#25)]

## <a name="example"></a><span data-ttu-id="d083a-232">範例</span><span class="sxs-lookup"><span data-stu-id="d083a-232">Example</span></span>

<span data-ttu-id="d083a-233">下列範例會叫用上述範例中所宣告的函式。</span><span class="sxs-lookup"><span data-stu-id="d083a-233">The following example invokes the function declared in the preceding example.</span></span>

[!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]

## <a name="example"></a><span data-ttu-id="d083a-234">範例</span><span class="sxs-lookup"><span data-stu-id="d083a-234">Example</span></span>

<span data-ttu-id="d083a-235">在下列範例中， `DelayAsync` 是 `Async` `Function` 具有傳回類型的 <xref:System.Threading.Tasks.Task%601> 。</span><span class="sxs-lookup"><span data-stu-id="d083a-235">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="d083a-236">`DelayAsync` 具有傳回整數的 `Return` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="d083a-236">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="d083a-237">因此，的函式宣告 `DelayAsync` 必須有的傳回型別 `Task(Of Integer)` 。</span><span class="sxs-lookup"><span data-stu-id="d083a-237">Therefore the function declaration of `DelayAsync` needs to have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="d083a-238">因為傳回型別是 `Task(Of Integer)` ，所以 `Await` 中的運算式評估會 `DoSomethingAsync` 產生整數。</span><span class="sxs-lookup"><span data-stu-id="d083a-238">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer.</span></span> <span data-ttu-id="d083a-239">這會在此語句中示範： `Dim result As Integer = Await delayTask` 。</span><span class="sxs-lookup"><span data-stu-id="d083a-239">This is demonstrated in this statement: `Dim result As Integer = Await delayTask`.</span></span>

<span data-ttu-id="d083a-240">此程式 `startButton_Click` 是程式的範例 `Async Sub` 。</span><span class="sxs-lookup"><span data-stu-id="d083a-240">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="d083a-241">因為 `DoSomethingAsync` 是函式 `Async` ，所以的呼叫工作必須等候 `DoSomethingAsync` ，如下列語句所示： `Await DoSomethingAsync()` 。</span><span class="sxs-lookup"><span data-stu-id="d083a-241">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement demonstrates: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="d083a-242">程式 `startButton_Click` `Sub` 必須以修飾詞定義， `Async` 因為它有一個 `Await` 運算式。</span><span class="sxs-lookup"><span data-stu-id="d083a-242">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="d083a-243">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d083a-243">See also</span></span>

- [<span data-ttu-id="d083a-244">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="d083a-244">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="d083a-245">Function 程序</span><span class="sxs-lookup"><span data-stu-id="d083a-245">Function Procedures</span></span>](../../programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="d083a-246">參數清單</span><span class="sxs-lookup"><span data-stu-id="d083a-246">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="d083a-247">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="d083a-247">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="d083a-248">Call 陳述式</span><span class="sxs-lookup"><span data-stu-id="d083a-248">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="d083a-249">的</span><span class="sxs-lookup"><span data-stu-id="d083a-249">Of</span></span>](of-clause.md)
- [<span data-ttu-id="d083a-250">參數陣列</span><span class="sxs-lookup"><span data-stu-id="d083a-250">Parameter Arrays</span></span>](../../programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="d083a-251">作法：使用泛型類別</span><span class="sxs-lookup"><span data-stu-id="d083a-251">How to: Use a Generic Class</span></span>](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="d083a-252">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="d083a-252">Troubleshooting Procedures</span></span>](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="d083a-253">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="d083a-253">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="d083a-254">函數運算式</span><span class="sxs-lookup"><span data-stu-id="d083a-254">Function Expression</span></span>](../operators/function-expression.md)
