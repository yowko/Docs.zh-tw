---
title: Sub 陳述式 (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Sub
helpviewer_keywords:
- Public keyword [Visual Basic], Sub statements
- procedures [Visual Basic], creating
- declaring procedures [Visual Basic], Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword [Visual Basic], Sub statements
- Optional keyword [Visual Basic], Sub statements
- declarations [Visual Basic], procedures
- Sub keyword [Visual Basic]
- Handles keyword [Visual Basic], Sub statements
- Protected Friend keyword [Visual Basic]
- ParamArray keyword [Visual Basic], Sub statements
- Implements keyword [Visual Basic], Sub statements
- Sub statement [Visual Basic]
- subroutines
- ByRef keyword [Visual Basic], Sub statements
- Sub procedures [Visual Basic], Sub statement
- recursive procedures
- Private keyword [Visual Basic], Sub statements
- Friend keyword [Visual Basic], Sub statements
- Exit statement [Visual Basic], Sub statements
- procedures [Visual Basic], Sub
- End keyword [Visual Basic], Sub statements
- ByVal keyword [Visual Basic], Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
ms.openlocfilehash: 7dc0ea1f1b30f5ffb0db8917538adf440c5ef891
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583193"
---
# <a name="sub-statement-visual-basic"></a><span data-ttu-id="56062-102">Sub 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56062-102">Sub Statement (Visual Basic)</span></span>

<span data-ttu-id="56062-103">宣告定義 `Sub` 程式的名稱、參數和程式碼。</span><span class="sxs-lookup"><span data-stu-id="56062-103">Declares the name, parameters, and code that define a `Sub` procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="56062-104">語法</span><span class="sxs-lookup"><span data-stu-id="56062-104">Syntax</span></span>

```vb
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Sub ]
    [ statements ]
End Sub
```

## <a name="parts"></a><span data-ttu-id="56062-105">組件</span><span class="sxs-lookup"><span data-stu-id="56062-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="56062-106">選擇項。</span><span class="sxs-lookup"><span data-stu-id="56062-106">Optional.</span></span> <span data-ttu-id="56062-107">請參閱[屬性清單](attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="56062-107">See [Attribute List](attribute-list.md).</span></span>

- `Partial`

  <span data-ttu-id="56062-108">選擇項。</span><span class="sxs-lookup"><span data-stu-id="56062-108">Optional.</span></span> <span data-ttu-id="56062-109">表示部分方法的定義。</span><span class="sxs-lookup"><span data-stu-id="56062-109">Indicates definition of a partial method.</span></span> <span data-ttu-id="56062-110">請參閱[部分方法](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="56062-110">See [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="56062-111">選擇項。</span><span class="sxs-lookup"><span data-stu-id="56062-111">Optional.</span></span> <span data-ttu-id="56062-112">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="56062-112">Can be one of the following:</span></span>

  - [<span data-ttu-id="56062-113">Public</span><span class="sxs-lookup"><span data-stu-id="56062-113">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="56062-114">Protected</span><span class="sxs-lookup"><span data-stu-id="56062-114">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="56062-115">Friend</span><span class="sxs-lookup"><span data-stu-id="56062-115">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="56062-116">Private</span><span class="sxs-lookup"><span data-stu-id="56062-116">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="56062-117">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="56062-117">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

  - [<span data-ttu-id="56062-118">Private Protected</span><span class="sxs-lookup"><span data-stu-id="56062-118">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

  <span data-ttu-id="56062-119">請參閱 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="56062-119">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `proceduremodifiers`

  <span data-ttu-id="56062-120">選擇項。</span><span class="sxs-lookup"><span data-stu-id="56062-120">Optional.</span></span> <span data-ttu-id="56062-121">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="56062-121">Can be one of the following:</span></span>

  - [<span data-ttu-id="56062-122">多載</span><span class="sxs-lookup"><span data-stu-id="56062-122">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="56062-123">Overrides</span><span class="sxs-lookup"><span data-stu-id="56062-123">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="56062-124">Overridable</span><span class="sxs-lookup"><span data-stu-id="56062-124">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="56062-125">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="56062-125">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="56062-126">New</span><span class="sxs-lookup"><span data-stu-id="56062-126">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="56062-127">選擇項。</span><span class="sxs-lookup"><span data-stu-id="56062-127">Optional.</span></span> <span data-ttu-id="56062-128">請參閱[共用](../modifiers/shared.md)。</span><span class="sxs-lookup"><span data-stu-id="56062-128">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="56062-129">選擇項。</span><span class="sxs-lookup"><span data-stu-id="56062-129">Optional.</span></span> <span data-ttu-id="56062-130">請參閱[Shadows](../modifiers/shadows.md)。</span><span class="sxs-lookup"><span data-stu-id="56062-130">See [Shadows](../modifiers/shadows.md).</span></span>

- `Async`

  <span data-ttu-id="56062-131">選擇項。</span><span class="sxs-lookup"><span data-stu-id="56062-131">Optional.</span></span> <span data-ttu-id="56062-132">請參閱[Async](../modifiers/async.md)。</span><span class="sxs-lookup"><span data-stu-id="56062-132">See [Async](../modifiers/async.md).</span></span>

- `name`

  <span data-ttu-id="56062-133">必要項。</span><span class="sxs-lookup"><span data-stu-id="56062-133">Required.</span></span> <span data-ttu-id="56062-134">程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="56062-134">Name of the procedure.</span></span> <span data-ttu-id="56062-135">請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="56062-135">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span> <span data-ttu-id="56062-136">若要建立類別的函式程式，請將 `Sub` 程式的名稱設定為 `New` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="56062-136">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="56062-137">如需詳細資訊，請參閱[物件存留期：物件的建立和終結方式](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)。</span><span class="sxs-lookup"><span data-stu-id="56062-137">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

- `typeparamlist`

  <span data-ttu-id="56062-138">選擇項。</span><span class="sxs-lookup"><span data-stu-id="56062-138">Optional.</span></span> <span data-ttu-id="56062-139">泛型程式的類型參數清單。</span><span class="sxs-lookup"><span data-stu-id="56062-139">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="56062-140">請參閱[類型清單](type-list.md)。</span><span class="sxs-lookup"><span data-stu-id="56062-140">See [Type List](type-list.md).</span></span>

- `parameterlist`

  <span data-ttu-id="56062-141">選擇項。</span><span class="sxs-lookup"><span data-stu-id="56062-141">Optional.</span></span> <span data-ttu-id="56062-142">本機變數名稱的清單，代表此程式的參數。</span><span class="sxs-lookup"><span data-stu-id="56062-142">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="56062-143">請參閱[參數清單](parameter-list.md)。</span><span class="sxs-lookup"><span data-stu-id="56062-143">See [Parameter List](parameter-list.md).</span></span>

- `Implements`

  <span data-ttu-id="56062-144">選擇項。</span><span class="sxs-lookup"><span data-stu-id="56062-144">Optional.</span></span> <span data-ttu-id="56062-145">指出此程式會執行一或多個 `Sub` 程式，其中每一個都是在由這個程式的包含類別或結構所實的介面中定義。</span><span class="sxs-lookup"><span data-stu-id="56062-145">Indicates that this procedure implements one or more `Sub` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="56062-146">請參閱[Implements 語句](implements-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="56062-146">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="56062-147">如果使用 `Implements`，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="56062-147">Required if `Implements` is supplied.</span></span> <span data-ttu-id="56062-148">實作之 `Sub` 程序的清單。</span><span class="sxs-lookup"><span data-stu-id="56062-148">List of `Sub` procedures being implemented.</span></span>

  `implementedprocedure [ , implementedprocedure ... ]`

  <span data-ttu-id="56062-149">每個 `implementedprocedure` 都具有下列語法和組件：</span><span class="sxs-lookup"><span data-stu-id="56062-149">Each `implementedprocedure` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="56062-150">組件</span><span class="sxs-lookup"><span data-stu-id="56062-150">Part</span></span>|<span data-ttu-id="56062-151">描述</span><span class="sxs-lookup"><span data-stu-id="56062-151">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="56062-152">必要項。</span><span class="sxs-lookup"><span data-stu-id="56062-152">Required.</span></span> <span data-ttu-id="56062-153">此程式的包含類別或結構所實作為介面的名稱。</span><span class="sxs-lookup"><span data-stu-id="56062-153">Name of an interface implemented by this procedure's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="56062-154">必要項。</span><span class="sxs-lookup"><span data-stu-id="56062-154">Required.</span></span> <span data-ttu-id="56062-155">名稱，據以在 `interface` 中定義程序。</span><span class="sxs-lookup"><span data-stu-id="56062-155">Name by which the procedure is defined in `interface`.</span></span>|

- `Handles`

  <span data-ttu-id="56062-156">選擇項。</span><span class="sxs-lookup"><span data-stu-id="56062-156">Optional.</span></span> <span data-ttu-id="56062-157">指出此程式可以處理一或多個特定事件。</span><span class="sxs-lookup"><span data-stu-id="56062-157">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="56062-158">請參閱[控制碼](handles-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="56062-158">See [Handles](handles-clause.md).</span></span>

- `eventlist`

  <span data-ttu-id="56062-159">如果使用 `Handles`，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="56062-159">Required if `Handles` is supplied.</span></span> <span data-ttu-id="56062-160">此程式處理的事件清單。</span><span class="sxs-lookup"><span data-stu-id="56062-160">List of events this procedure handles.</span></span>

  `eventspecifier [ , eventspecifier ... ]`

  <span data-ttu-id="56062-161">每個 `eventspecifier` 都具有下列語法和組件：</span><span class="sxs-lookup"><span data-stu-id="56062-161">Each `eventspecifier` has the following syntax and parts:</span></span>

  `eventvariable.event`

  |<span data-ttu-id="56062-162">組件</span><span class="sxs-lookup"><span data-stu-id="56062-162">Part</span></span>|<span data-ttu-id="56062-163">描述</span><span class="sxs-lookup"><span data-stu-id="56062-163">Description</span></span>|
  |---|---|
  |`eventvariable`|<span data-ttu-id="56062-164">必要項。</span><span class="sxs-lookup"><span data-stu-id="56062-164">Required.</span></span> <span data-ttu-id="56062-165">以引發事件之類別或結構的資料類型宣告的物件變數。</span><span class="sxs-lookup"><span data-stu-id="56062-165">Object variable declared with the data type of the class or structure that raises the event.</span></span>|
  |`event`|<span data-ttu-id="56062-166">必要項。</span><span class="sxs-lookup"><span data-stu-id="56062-166">Required.</span></span> <span data-ttu-id="56062-167">這個程式處理的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="56062-167">Name of the event this procedure handles.</span></span>|

- `statements`

  <span data-ttu-id="56062-168">選擇項。</span><span class="sxs-lookup"><span data-stu-id="56062-168">Optional.</span></span> <span data-ttu-id="56062-169">要在此程式內執行的語句區塊。</span><span class="sxs-lookup"><span data-stu-id="56062-169">Block of statements to run within this procedure.</span></span>

- `End Sub`

  <span data-ttu-id="56062-170">終止這個程式的定義。</span><span class="sxs-lookup"><span data-stu-id="56062-170">Terminates the definition of this procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="56062-171">備註</span><span class="sxs-lookup"><span data-stu-id="56062-171">Remarks</span></span>

<span data-ttu-id="56062-172">所有可執行檔程式碼都必須在程式內。</span><span class="sxs-lookup"><span data-stu-id="56062-172">All executable code must be inside a procedure.</span></span> <span data-ttu-id="56062-173">當您不想要將值傳回給呼叫程式碼時，請使用 `Sub` 程式。</span><span class="sxs-lookup"><span data-stu-id="56062-173">Use a `Sub` procedure when you don't want to return a value to the calling code.</span></span> <span data-ttu-id="56062-174">當您想要傳回值時，請使用 `Function` 程式。</span><span class="sxs-lookup"><span data-stu-id="56062-174">Use a `Function` procedure when you want to return a value.</span></span>

## <a name="defining-a-sub-procedure"></a><span data-ttu-id="56062-175">定義 Sub 程式</span><span class="sxs-lookup"><span data-stu-id="56062-175">Defining a Sub Procedure</span></span>

<span data-ttu-id="56062-176">您只能在模組層級定義 `Sub` 程式。</span><span class="sxs-lookup"><span data-stu-id="56062-176">You can define a `Sub` procedure only at the module level.</span></span> <span data-ttu-id="56062-177">Sub 程式的宣告內容必須是類別、結構、模組或介面，而且不能是原始程式檔、命名空間、程式或區塊。</span><span class="sxs-lookup"><span data-stu-id="56062-177">The declaration context for a sub procedure must, therefore, be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="56062-178">如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="56062-178">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="56062-179">`Sub` 程式預設為公開存取。</span><span class="sxs-lookup"><span data-stu-id="56062-179">`Sub` procedures default to public access.</span></span> <span data-ttu-id="56062-180">您可以使用存取修飾詞來調整其存取層級。</span><span class="sxs-lookup"><span data-stu-id="56062-180">You can adjust their access levels by using the access modifiers.</span></span>

<span data-ttu-id="56062-181">如果程式使用 `Implements` 關鍵字，則包含的類別或結構必須具有緊接在其 `Class` 或 `Structure` 語句後面的 `Implements` 語句。</span><span class="sxs-lookup"><span data-stu-id="56062-181">If the procedure uses the `Implements` keyword, the containing class or structure must have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="56062-182">@No__t_0 語句必須包含 `implementslist` 中指定的每個介面。</span><span class="sxs-lookup"><span data-stu-id="56062-182">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="56062-183">不過，介面用來定義 `Sub` （在 `definedname` 中）的名稱不一定要符合此程式的名稱（在 `name` 中）。</span><span class="sxs-lookup"><span data-stu-id="56062-183">However, the name by which an interface defines the `Sub` (in `definedname`) doesn't have to match the name of this procedure (in `name`).</span></span>

## <a name="returning-from-a-sub-procedure"></a><span data-ttu-id="56062-184">從 Sub 程式傳回</span><span class="sxs-lookup"><span data-stu-id="56062-184">Returning from a Sub Procedure</span></span>

<span data-ttu-id="56062-185">當 `Sub` 程式傳回呼叫程式碼時，會在呼叫它的語句後面繼續執行語句。</span><span class="sxs-lookup"><span data-stu-id="56062-185">When a `Sub` procedure returns to the calling code, execution continues with the statement after the statement that called it.</span></span>

<span data-ttu-id="56062-186">下列範例顯示從 `Sub` 程式傳回的。</span><span class="sxs-lookup"><span data-stu-id="56062-186">The following example shows a return from a `Sub` procedure.</span></span>

```vb
Sub mySub(ByVal q As String)
    Return
End Sub
```

<span data-ttu-id="56062-187">@No__t_0 和 `Return` 語句會導致立即離開 `Sub` 程式。</span><span class="sxs-lookup"><span data-stu-id="56062-187">The `Exit Sub` and `Return` statements cause an immediate exit from a `Sub` procedure.</span></span> <span data-ttu-id="56062-188">任何數目的 `Exit Sub` 和 `Return` 語句都可以出現在程式中的任何位置，而且您可以混合 `Exit Sub` 和 `Return` 語句。</span><span class="sxs-lookup"><span data-stu-id="56062-188">Any number of `Exit Sub` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Sub` and `Return` statements.</span></span>

## <a name="calling-a-sub-procedure"></a><span data-ttu-id="56062-189">呼叫 Sub 程式</span><span class="sxs-lookup"><span data-stu-id="56062-189">Calling a Sub Procedure</span></span>

<span data-ttu-id="56062-190">您可以使用語句中的程式名稱來呼叫 `Sub` 程式，然後在該名稱後面加上括弧中的引數清單。</span><span class="sxs-lookup"><span data-stu-id="56062-190">You call a `Sub` procedure by using the procedure name in a statement and then following that name with its argument list in parentheses.</span></span> <span data-ttu-id="56062-191">只有在未提供任何引數時，才可以省略括弧。</span><span class="sxs-lookup"><span data-stu-id="56062-191">You can omit the parentheses only if you don't supply any arguments.</span></span> <span data-ttu-id="56062-192">不過，如果您一律包含括弧，則程式碼會更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="56062-192">However, your code is more readable if you always include the parentheses.</span></span>

<span data-ttu-id="56062-193">@No__t_0 程式和 `Function` 程式都可以有參數，並執行一連串的語句。</span><span class="sxs-lookup"><span data-stu-id="56062-193">A `Sub` procedure and a `Function` procedure  can have parameters and perform a series of statements.</span></span> <span data-ttu-id="56062-194">不過，`Function` 程式會傳回值，而 `Sub` 程式則不會。</span><span class="sxs-lookup"><span data-stu-id="56062-194">However, a `Function` procedure returns a value, and a `Sub` procedure doesn't.</span></span> <span data-ttu-id="56062-195">因此，您不能在運算式中使用 `Sub` 程式。</span><span class="sxs-lookup"><span data-stu-id="56062-195">Therefore, you can't use a `Sub` procedure in an expression.</span></span>

<span data-ttu-id="56062-196">當您呼叫 `Sub` 程式時，可以使用 `Call` 關鍵字，但不建議在大部分的情況下使用該關鍵字。</span><span class="sxs-lookup"><span data-stu-id="56062-196">You can use the `Call` keyword when you call a `Sub` procedure, but that keyword isn't recommended for most uses.</span></span> <span data-ttu-id="56062-197">如需詳細資訊，請參閱[Call 語句](call-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="56062-197">For more information, see [Call Statement](call-statement.md).</span></span>

<span data-ttu-id="56062-198">Visual Basic 有時會重新排列算術運算式，以提高內部效率。</span><span class="sxs-lookup"><span data-stu-id="56062-198">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="56062-199">基於這個理由，如果您的引數清單包含呼叫其他程式的運算式，您就不應該假設這些運算式會以特定順序呼叫。</span><span class="sxs-lookup"><span data-stu-id="56062-199">For that reason, if your argument list includes expressions that call other procedures, you shouldn't assume that those expressions will be called in a particular order.</span></span>

## <a name="async-sub-procedures"></a><span data-ttu-id="56062-200">非同步 Sub 程式</span><span class="sxs-lookup"><span data-stu-id="56062-200">Async Sub Procedures</span></span>

<span data-ttu-id="56062-201">藉由使用非同步功能，您可以叫用非同步函式，而不需使用明確回呼，或手動將程式碼分割成多個函數或 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="56062-201">By using the Async feature, you can invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>

<span data-ttu-id="56062-202">如果您使用[Async](../modifiers/async.md)修飾詞來標記程式，您可以在程式中使用[Await](../../../visual-basic/language-reference/operators/await-operator.md)運算子。</span><span class="sxs-lookup"><span data-stu-id="56062-202">If you mark a procedure with the [Async](../modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the procedure.</span></span> <span data-ttu-id="56062-203">當控制項到達 `Async` 程式中的 `Await` 運算式時，控制項會回到呼叫端，而程式中的進度會暫停，直到等候的工作完成為止。</span><span class="sxs-lookup"><span data-stu-id="56062-203">When control reaches an `Await` expression in the `Async` procedure, control returns to the caller, and progress in the procedure is suspended until the awaited task completes.</span></span> <span data-ttu-id="56062-204">當工作完成時，可以在程式中繼續執行。</span><span class="sxs-lookup"><span data-stu-id="56062-204">When the task is complete, execution can resume in the procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="56062-205">當遇到第一個尚未完成的等候物件或到達 `Async` 程式的結尾（以先發生者為准）時，`Async` 程式會傳回呼叫端。</span><span class="sxs-lookup"><span data-stu-id="56062-205">An `Async` procedure returns to the caller when either the first awaited object that’s not yet complete is encountered or the end of the `Async` procedure is reached, whichever occurs first.</span></span>

<span data-ttu-id="56062-206">您也可以使用 `Async` 修飾詞來標記[函數語句](function-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="56062-206">You can also mark a [Function Statement](function-statement.md) with the `Async` modifier.</span></span> <span data-ttu-id="56062-207">@No__t_0 函式的傳回型別可以是 <xref:System.Threading.Tasks.Task%601> 或 <xref:System.Threading.Tasks.Task>。</span><span class="sxs-lookup"><span data-stu-id="56062-207">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="56062-208">本主題稍後的範例會顯示具有 <xref:System.Threading.Tasks.Task%601> 傳回類型的 `Async` 函式。</span><span class="sxs-lookup"><span data-stu-id="56062-208">An example later in this topic shows an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="56062-209">`Async` `Sub` 程式主要用於事件處理常式，因此無法傳回值。</span><span class="sxs-lookup"><span data-stu-id="56062-209">`Async` `Sub` procedures are primarily used for event handlers, where a value can't be returned.</span></span> <span data-ttu-id="56062-210">無法等候 `Async` `Sub` 程式，`Async` `Sub` 程式的呼叫端無法攔截 `Sub` 程式擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="56062-210">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that the `Sub` procedure throws.</span></span>

<span data-ttu-id="56062-211">@No__t_0 程式無法宣告任何[ByRef](../modifiers/byref.md)參數。</span><span class="sxs-lookup"><span data-stu-id="56062-211">An `Async` procedure can't declare any [ByRef](../modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="56062-212">如需 `Async` 程式的詳細資訊，請參閱[使用 async 和 Await 進行非同步程式設計](../../../visual-basic/programming-guide/concepts/async/index.md)、[非同步程式中的控制流程](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)和[非同步傳回類型](../../../visual-basic/programming-guide/concepts/async/async-return-types.md)。</span><span class="sxs-lookup"><span data-stu-id="56062-212">For more information about `Async` procedures, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="example"></a><span data-ttu-id="56062-213">範例</span><span class="sxs-lookup"><span data-stu-id="56062-213">Example</span></span>

<span data-ttu-id="56062-214">下列範例會使用 `Sub` 語句來定義構成 `Sub` 程式主體的名稱、參數和代碼。</span><span class="sxs-lookup"><span data-stu-id="56062-214">The following example uses the `Sub` statement to define the name, parameters, and code that form the body of a `Sub` procedure.</span></span>

[!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]

## <a name="example"></a><span data-ttu-id="56062-215">範例</span><span class="sxs-lookup"><span data-stu-id="56062-215">Example</span></span>

<span data-ttu-id="56062-216">在下列範例中，`DelayAsync` 是具有 <xref:System.Threading.Tasks.Task%601> 傳回類型的 `Async` `Function`。</span><span class="sxs-lookup"><span data-stu-id="56062-216">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="56062-217">`DelayAsync` 具有傳回整數的 `Return` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="56062-217">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="56062-218">因此，`DelayAsync` 的函式宣告必須具有 `Task(Of Integer)` 的傳回類型。</span><span class="sxs-lookup"><span data-stu-id="56062-218">Therefore, the function declaration of `DelayAsync` must have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="56062-219">因為傳回型別是 `Task(Of Integer)`，所以 `DoSomethingAsync` 中 `Await` 運算式的評估會產生整數，如下列語句所示： `Dim result As Integer = Await delayTask`。</span><span class="sxs-lookup"><span data-stu-id="56062-219">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer, as the following statement shows: `Dim result As Integer = Await delayTask`.</span></span>

<span data-ttu-id="56062-220">@No__t_0 的程式是 `Async Sub` 程式的範例。</span><span class="sxs-lookup"><span data-stu-id="56062-220">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="56062-221">因為 `DoSomethingAsync` 是 `Async` 函式，所以必須等候 `DoSomethingAsync` 呼叫的工作，如下列語句所示： `Await DoSomethingAsync()`。</span><span class="sxs-lookup"><span data-stu-id="56062-221">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="56062-222">@No__t_0 `Sub` 程式必須使用 `Async` 修飾詞加以定義，因為它有 `Await` 運算式。</span><span class="sxs-lookup"><span data-stu-id="56062-222">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="56062-223">請參閱</span><span class="sxs-lookup"><span data-stu-id="56062-223">See also</span></span>

- [<span data-ttu-id="56062-224">Implements 陳述式</span><span class="sxs-lookup"><span data-stu-id="56062-224">Implements Statement</span></span>](implements-statement.md)
- [<span data-ttu-id="56062-225">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="56062-225">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="56062-226">參數清單</span><span class="sxs-lookup"><span data-stu-id="56062-226">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="56062-227">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="56062-227">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="56062-228">Call 陳述式</span><span class="sxs-lookup"><span data-stu-id="56062-228">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="56062-229">Of</span><span class="sxs-lookup"><span data-stu-id="56062-229">Of</span></span>](of-clause.md)
- [<span data-ttu-id="56062-230">參數陣列</span><span class="sxs-lookup"><span data-stu-id="56062-230">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="56062-231">如何：使用泛型類別</span><span class="sxs-lookup"><span data-stu-id="56062-231">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="56062-232">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="56062-232">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="56062-233">部分方法</span><span class="sxs-lookup"><span data-stu-id="56062-233">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
