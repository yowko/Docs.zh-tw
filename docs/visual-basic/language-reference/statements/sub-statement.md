---
title: Sub 陳述式
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
ms.openlocfilehash: e50b79c31c92ac116d6c82bcececba3340894d74
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404170"
---
# <a name="sub-statement-visual-basic"></a><span data-ttu-id="27bdd-102">Sub 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27bdd-102">Sub Statement (Visual Basic)</span></span>

<span data-ttu-id="27bdd-103">宣告定義程式的名稱、參數和程式碼 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="27bdd-103">Declares the name, parameters, and code that define a `Sub` procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="27bdd-104">語法</span><span class="sxs-lookup"><span data-stu-id="27bdd-104">Syntax</span></span>

```vb
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Sub ]
    [ statements ]
End Sub
```

## <a name="parts"></a><span data-ttu-id="27bdd-105">組件</span><span class="sxs-lookup"><span data-stu-id="27bdd-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="27bdd-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="27bdd-106">Optional.</span></span> <span data-ttu-id="27bdd-107">請參閱[屬性清單](attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="27bdd-107">See [Attribute List](attribute-list.md).</span></span>

- `Partial`

  <span data-ttu-id="27bdd-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="27bdd-108">Optional.</span></span> <span data-ttu-id="27bdd-109">表示部分方法的定義。</span><span class="sxs-lookup"><span data-stu-id="27bdd-109">Indicates definition of a partial method.</span></span> <span data-ttu-id="27bdd-110">請參閱[部分方法](../../programming-guide/language-features/procedures/partial-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="27bdd-110">See [Partial Methods](../../programming-guide/language-features/procedures/partial-methods.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="27bdd-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="27bdd-111">Optional.</span></span> <span data-ttu-id="27bdd-112">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="27bdd-112">Can be one of the following:</span></span>

  - [<span data-ttu-id="27bdd-113">公開</span><span class="sxs-lookup"><span data-stu-id="27bdd-113">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="27bdd-114">免受</span><span class="sxs-lookup"><span data-stu-id="27bdd-114">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="27bdd-115">給</span><span class="sxs-lookup"><span data-stu-id="27bdd-115">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="27bdd-116">私用</span><span class="sxs-lookup"><span data-stu-id="27bdd-116">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="27bdd-117">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="27bdd-117">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="27bdd-118">私用保護</span><span class="sxs-lookup"><span data-stu-id="27bdd-118">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="27bdd-119">請參閱[Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="27bdd-119">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `proceduremodifiers`

  <span data-ttu-id="27bdd-120">選擇性。</span><span class="sxs-lookup"><span data-stu-id="27bdd-120">Optional.</span></span> <span data-ttu-id="27bdd-121">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="27bdd-121">Can be one of the following:</span></span>

  - [<span data-ttu-id="27bdd-122">多載</span><span class="sxs-lookup"><span data-stu-id="27bdd-122">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="27bdd-123">覆寫</span><span class="sxs-lookup"><span data-stu-id="27bdd-123">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="27bdd-124">Overrides</span><span class="sxs-lookup"><span data-stu-id="27bdd-124">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="27bdd-125">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="27bdd-125">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="27bdd-126">New</span><span class="sxs-lookup"><span data-stu-id="27bdd-126">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="27bdd-127">選擇性。</span><span class="sxs-lookup"><span data-stu-id="27bdd-127">Optional.</span></span> <span data-ttu-id="27bdd-128">請參閱[共用](../modifiers/shared.md)。</span><span class="sxs-lookup"><span data-stu-id="27bdd-128">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="27bdd-129">選擇性。</span><span class="sxs-lookup"><span data-stu-id="27bdd-129">Optional.</span></span> <span data-ttu-id="27bdd-130">請參閱[Shadows](../modifiers/shadows.md)。</span><span class="sxs-lookup"><span data-stu-id="27bdd-130">See [Shadows](../modifiers/shadows.md).</span></span>

- `Async`

  <span data-ttu-id="27bdd-131">選擇性。</span><span class="sxs-lookup"><span data-stu-id="27bdd-131">Optional.</span></span> <span data-ttu-id="27bdd-132">請參閱[Async](../modifiers/async.md)。</span><span class="sxs-lookup"><span data-stu-id="27bdd-132">See [Async](../modifiers/async.md).</span></span>

- `name`

  <span data-ttu-id="27bdd-133">必要。</span><span class="sxs-lookup"><span data-stu-id="27bdd-133">Required.</span></span> <span data-ttu-id="27bdd-134">程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="27bdd-134">Name of the procedure.</span></span> <span data-ttu-id="27bdd-135">請參閱 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="27bdd-135">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span> <span data-ttu-id="27bdd-136">若要建立類別的方法，請將程式的名稱設定 `Sub` 為 `New` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="27bdd-136">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="27bdd-137">如需詳細資訊，請參閱[物件存留期：物件的建立和終結方式](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)。</span><span class="sxs-lookup"><span data-stu-id="27bdd-137">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

- `typeparamlist`

  <span data-ttu-id="27bdd-138">選擇性。</span><span class="sxs-lookup"><span data-stu-id="27bdd-138">Optional.</span></span> <span data-ttu-id="27bdd-139">泛型程式的類型參數清單。</span><span class="sxs-lookup"><span data-stu-id="27bdd-139">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="27bdd-140">請參閱[類型清單](type-list.md)。</span><span class="sxs-lookup"><span data-stu-id="27bdd-140">See [Type List](type-list.md).</span></span>

- `parameterlist`

  <span data-ttu-id="27bdd-141">選擇性。</span><span class="sxs-lookup"><span data-stu-id="27bdd-141">Optional.</span></span> <span data-ttu-id="27bdd-142">本機變數名稱的清單，代表此程式的參數。</span><span class="sxs-lookup"><span data-stu-id="27bdd-142">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="27bdd-143">請參閱[參數清單](parameter-list.md)。</span><span class="sxs-lookup"><span data-stu-id="27bdd-143">See [Parameter List](parameter-list.md).</span></span>

- `Implements`

  <span data-ttu-id="27bdd-144">選擇性。</span><span class="sxs-lookup"><span data-stu-id="27bdd-144">Optional.</span></span> <span data-ttu-id="27bdd-145">指出此程式會執行一或多個 `Sub` 程式，其中每一個都是在介面中所定義的介面中，其包含類別或結構。</span><span class="sxs-lookup"><span data-stu-id="27bdd-145">Indicates that this procedure implements one or more `Sub` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="27bdd-146">請參閱[Implements 語句](implements-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="27bdd-146">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="27bdd-147">如果使用 `Implements`，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="27bdd-147">Required if `Implements` is supplied.</span></span> <span data-ttu-id="27bdd-148">實作之 `Sub` 程序的清單。</span><span class="sxs-lookup"><span data-stu-id="27bdd-148">List of `Sub` procedures being implemented.</span></span>

  `implementedprocedure [ , implementedprocedure ... ]`

  <span data-ttu-id="27bdd-149">每個 `implementedprocedure` 都具有下列語法和組件：</span><span class="sxs-lookup"><span data-stu-id="27bdd-149">Each `implementedprocedure` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="27bdd-150">部分</span><span class="sxs-lookup"><span data-stu-id="27bdd-150">Part</span></span>|<span data-ttu-id="27bdd-151">描述</span><span class="sxs-lookup"><span data-stu-id="27bdd-151">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="27bdd-152">必要。</span><span class="sxs-lookup"><span data-stu-id="27bdd-152">Required.</span></span> <span data-ttu-id="27bdd-153">此程式的包含類別或結構所實作為介面的名稱。</span><span class="sxs-lookup"><span data-stu-id="27bdd-153">Name of an interface implemented by this procedure's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="27bdd-154">必要。</span><span class="sxs-lookup"><span data-stu-id="27bdd-154">Required.</span></span> <span data-ttu-id="27bdd-155">名稱，據以在 `interface` 中定義程序。</span><span class="sxs-lookup"><span data-stu-id="27bdd-155">Name by which the procedure is defined in `interface`.</span></span>|

- `Handles`

  <span data-ttu-id="27bdd-156">選擇性。</span><span class="sxs-lookup"><span data-stu-id="27bdd-156">Optional.</span></span> <span data-ttu-id="27bdd-157">指出此程式可以處理一或多個特定事件。</span><span class="sxs-lookup"><span data-stu-id="27bdd-157">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="27bdd-158">請參閱[控制碼](handles-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="27bdd-158">See [Handles](handles-clause.md).</span></span>

- `eventlist`

  <span data-ttu-id="27bdd-159">如果使用 `Handles`，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="27bdd-159">Required if `Handles` is supplied.</span></span> <span data-ttu-id="27bdd-160">此程式處理的事件清單。</span><span class="sxs-lookup"><span data-stu-id="27bdd-160">List of events this procedure handles.</span></span>

  `eventspecifier [ , eventspecifier ... ]`

  <span data-ttu-id="27bdd-161">每個 `eventspecifier` 都具有下列語法和組件：</span><span class="sxs-lookup"><span data-stu-id="27bdd-161">Each `eventspecifier` has the following syntax and parts:</span></span>

  `eventvariable.event`

  |<span data-ttu-id="27bdd-162">部分</span><span class="sxs-lookup"><span data-stu-id="27bdd-162">Part</span></span>|<span data-ttu-id="27bdd-163">描述</span><span class="sxs-lookup"><span data-stu-id="27bdd-163">Description</span></span>|
  |---|---|
  |`eventvariable`|<span data-ttu-id="27bdd-164">必要。</span><span class="sxs-lookup"><span data-stu-id="27bdd-164">Required.</span></span> <span data-ttu-id="27bdd-165">以引發事件之類別或結構的資料類型宣告的物件變數。</span><span class="sxs-lookup"><span data-stu-id="27bdd-165">Object variable declared with the data type of the class or structure that raises the event.</span></span>|
  |`event`|<span data-ttu-id="27bdd-166">必要。</span><span class="sxs-lookup"><span data-stu-id="27bdd-166">Required.</span></span> <span data-ttu-id="27bdd-167">這個程式處理的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="27bdd-167">Name of the event this procedure handles.</span></span>|

- `statements`

  <span data-ttu-id="27bdd-168">選擇性。</span><span class="sxs-lookup"><span data-stu-id="27bdd-168">Optional.</span></span> <span data-ttu-id="27bdd-169">要在此程式內執行的語句區塊。</span><span class="sxs-lookup"><span data-stu-id="27bdd-169">Block of statements to run within this procedure.</span></span>

- `End Sub`

  <span data-ttu-id="27bdd-170">終止這個程式的定義。</span><span class="sxs-lookup"><span data-stu-id="27bdd-170">Terminates the definition of this procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="27bdd-171">備註</span><span class="sxs-lookup"><span data-stu-id="27bdd-171">Remarks</span></span>

<span data-ttu-id="27bdd-172">所有可執行檔程式碼都必須在程式內。</span><span class="sxs-lookup"><span data-stu-id="27bdd-172">All executable code must be inside a procedure.</span></span> <span data-ttu-id="27bdd-173">`Sub`當您不想要將值傳回給呼叫程式碼時，請使用程式。</span><span class="sxs-lookup"><span data-stu-id="27bdd-173">Use a `Sub` procedure when you don't want to return a value to the calling code.</span></span> <span data-ttu-id="27bdd-174">`Function`當您想要傳回值時，請使用程式。</span><span class="sxs-lookup"><span data-stu-id="27bdd-174">Use a `Function` procedure when you want to return a value.</span></span>

## <a name="defining-a-sub-procedure"></a><span data-ttu-id="27bdd-175">定義 Sub 程式</span><span class="sxs-lookup"><span data-stu-id="27bdd-175">Defining a Sub Procedure</span></span>

<span data-ttu-id="27bdd-176">您 `Sub` 只能在模組層級定義程式。</span><span class="sxs-lookup"><span data-stu-id="27bdd-176">You can define a `Sub` procedure only at the module level.</span></span> <span data-ttu-id="27bdd-177">Sub 程式的宣告內容必須是類別、結構、模組或介面，而且不能是原始程式檔、命名空間、程式或區塊。</span><span class="sxs-lookup"><span data-stu-id="27bdd-177">The declaration context for a sub procedure must, therefore, be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="27bdd-178">如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="27bdd-178">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="27bdd-179">`Sub`程式預設為公用存取。</span><span class="sxs-lookup"><span data-stu-id="27bdd-179">`Sub` procedures default to public access.</span></span> <span data-ttu-id="27bdd-180">您可以使用存取修飾詞來調整其存取層級。</span><span class="sxs-lookup"><span data-stu-id="27bdd-180">You can adjust their access levels by using the access modifiers.</span></span>

<span data-ttu-id="27bdd-181">如果程式使用 `Implements` 關鍵字，則包含的類別或結構必須有緊接在 `Implements` 其或語句後面的 `Class` 語句 `Structure` 。</span><span class="sxs-lookup"><span data-stu-id="27bdd-181">If the procedure uses the `Implements` keyword, the containing class or structure must have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="27bdd-182">`Implements`語句必須包含中所指定的每個介面 `implementslist` 。</span><span class="sxs-lookup"><span data-stu-id="27bdd-182">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="27bdd-183">不過，介面用來定義 `Sub` （在中）的名稱 `definedname` 不一定要符合此程式的名稱（在中為 `name` ）。</span><span class="sxs-lookup"><span data-stu-id="27bdd-183">However, the name by which an interface defines the `Sub` (in `definedname`) doesn't have to match the name of this procedure (in `name`).</span></span>

## <a name="returning-from-a-sub-procedure"></a><span data-ttu-id="27bdd-184">從 Sub 程式傳回</span><span class="sxs-lookup"><span data-stu-id="27bdd-184">Returning from a Sub Procedure</span></span>

<span data-ttu-id="27bdd-185">當程式 `Sub` 返回呼叫程式碼時，執行會在呼叫它的語句後面繼續進行語句。</span><span class="sxs-lookup"><span data-stu-id="27bdd-185">When a `Sub` procedure returns to the calling code, execution continues with the statement after the statement that called it.</span></span>

<span data-ttu-id="27bdd-186">下列範例顯示從程式傳回的 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="27bdd-186">The following example shows a return from a `Sub` procedure.</span></span>

```vb
Sub mySub(ByVal q As String)
    Return
End Sub
```

<span data-ttu-id="27bdd-187">`Exit Sub`和 `Return` 語句會導致程式立即結束 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="27bdd-187">The `Exit Sub` and `Return` statements cause an immediate exit from a `Sub` procedure.</span></span> <span data-ttu-id="27bdd-188">任何數目的 `Exit Sub` 和 `Return` 語句都可以出現在程式中的任何位置，而且您可以混合使用 `Exit Sub` 和 `Return` 語句。</span><span class="sxs-lookup"><span data-stu-id="27bdd-188">Any number of `Exit Sub` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Sub` and `Return` statements.</span></span>

## <a name="calling-a-sub-procedure"></a><span data-ttu-id="27bdd-189">呼叫 Sub 程式</span><span class="sxs-lookup"><span data-stu-id="27bdd-189">Calling a Sub Procedure</span></span>

<span data-ttu-id="27bdd-190">您可以 `Sub` 使用語句中的程式名稱，然後在該名稱後面加上括弧中的引數清單，來呼叫程式。</span><span class="sxs-lookup"><span data-stu-id="27bdd-190">You call a `Sub` procedure by using the procedure name in a statement and then following that name with its argument list in parentheses.</span></span> <span data-ttu-id="27bdd-191">只有在未提供任何引數時，才可以省略括弧。</span><span class="sxs-lookup"><span data-stu-id="27bdd-191">You can omit the parentheses only if you don't supply any arguments.</span></span> <span data-ttu-id="27bdd-192">不過，如果您一律包含括弧，則程式碼會更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="27bdd-192">However, your code is more readable if you always include the parentheses.</span></span>

<span data-ttu-id="27bdd-193">程式 `Sub` 和程式 `Function` 可以有參數，並執行一系列的語句。</span><span class="sxs-lookup"><span data-stu-id="27bdd-193">A `Sub` procedure and a `Function` procedure  can have parameters and perform a series of statements.</span></span> <span data-ttu-id="27bdd-194">不過，程式 `Function` 會傳回值，而程式則 `Sub` 不會傳回。</span><span class="sxs-lookup"><span data-stu-id="27bdd-194">However, a `Function` procedure returns a value, and a `Sub` procedure doesn't.</span></span> <span data-ttu-id="27bdd-195">因此，您不能 `Sub` 在運算式中使用程式。</span><span class="sxs-lookup"><span data-stu-id="27bdd-195">Therefore, you can't use a `Sub` procedure in an expression.</span></span>

<span data-ttu-id="27bdd-196">`Call`當您呼叫程式時，可以使用關鍵字 `Sub` ，但不建議在大部分的情況下使用該關鍵字。</span><span class="sxs-lookup"><span data-stu-id="27bdd-196">You can use the `Call` keyword when you call a `Sub` procedure, but that keyword isn't recommended for most uses.</span></span> <span data-ttu-id="27bdd-197">如需詳細資訊，請參閱[Call 語句](call-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="27bdd-197">For more information, see [Call Statement](call-statement.md).</span></span>

<span data-ttu-id="27bdd-198">Visual Basic 有時會重新排列算術運算式，以提高內部效率。</span><span class="sxs-lookup"><span data-stu-id="27bdd-198">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="27bdd-199">基於這個理由，如果您的引數清單包含呼叫其他程式的運算式，您就不應該假設這些運算式會以特定順序呼叫。</span><span class="sxs-lookup"><span data-stu-id="27bdd-199">For that reason, if your argument list includes expressions that call other procedures, you shouldn't assume that those expressions will be called in a particular order.</span></span>

## <a name="async-sub-procedures"></a><span data-ttu-id="27bdd-200">非同步 Sub 程式</span><span class="sxs-lookup"><span data-stu-id="27bdd-200">Async Sub Procedures</span></span>

<span data-ttu-id="27bdd-201">藉由使用非同步功能，您可以叫用非同步函式，而不需使用明確回呼，或手動將程式碼分割成多個函數或 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="27bdd-201">By using the Async feature, you can invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>

<span data-ttu-id="27bdd-202">如果您使用[Async](../modifiers/async.md)修飾詞來標記程式，您可以在程式中使用[Await](../operators/await-operator.md)運算子。</span><span class="sxs-lookup"><span data-stu-id="27bdd-202">If you mark a procedure with the [Async](../modifiers/async.md) modifier, you can use the [Await](../operators/await-operator.md) operator in the procedure.</span></span> <span data-ttu-id="27bdd-203">當控制項到達程式 `Await` 中的運算式時 `Async` ，控制項會回到呼叫端，而程式中的進度會暫停，直到等候的工作完成為止。</span><span class="sxs-lookup"><span data-stu-id="27bdd-203">When control reaches an `Await` expression in the `Async` procedure, control returns to the caller, and progress in the procedure is suspended until the awaited task completes.</span></span> <span data-ttu-id="27bdd-204">當工作完成時，可以在程式中繼續執行。</span><span class="sxs-lookup"><span data-stu-id="27bdd-204">When the task is complete, execution can resume in the procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="27bdd-205">`Async`當遇到第一個尚未完成的等候物件或到達程式的結尾（以先發生者為准）時，程式會傳回給呼叫端 `Async` 。</span><span class="sxs-lookup"><span data-stu-id="27bdd-205">An `Async` procedure returns to the caller when either the first awaited object that’s not yet complete is encountered or the end of the `Async` procedure is reached, whichever occurs first.</span></span>

<span data-ttu-id="27bdd-206">您也可以使用修飾詞來標記[函數語句](function-statement.md) `Async` 。</span><span class="sxs-lookup"><span data-stu-id="27bdd-206">You can also mark a [Function Statement](function-statement.md) with the `Async` modifier.</span></span> <span data-ttu-id="27bdd-207">`Async`函數可以具有或的傳回類型 <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task> 。</span><span class="sxs-lookup"><span data-stu-id="27bdd-207">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="27bdd-208">本主題稍後的範例 `Async` 會顯示具有傳回類型的函式 <xref:System.Threading.Tasks.Task%601> 。</span><span class="sxs-lookup"><span data-stu-id="27bdd-208">An example later in this topic shows an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="27bdd-209">`Async``Sub`程式主要用於事件處理常式，因此無法傳回值。</span><span class="sxs-lookup"><span data-stu-id="27bdd-209">`Async` `Sub` procedures are primarily used for event handlers, where a value can't be returned.</span></span> <span data-ttu-id="27bdd-210">無法等候程式 `Async` `Sub` ，而且程式的呼叫端 `Async` `Sub` 無法攔截程式擲回的例外狀況 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="27bdd-210">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that the `Sub` procedure throws.</span></span>

<span data-ttu-id="27bdd-211">程式 `Async` 無法宣告任何[ByRef](../modifiers/byref.md)參數。</span><span class="sxs-lookup"><span data-stu-id="27bdd-211">An `Async` procedure can't declare any [ByRef](../modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="27bdd-212">如需有關程式的詳細資訊 `Async` ，請參閱[使用 Async 和 Await 進行非同步程式設計](../../programming-guide/concepts/async/index.md)、[非同步程式中的控制流程](../../programming-guide/concepts/async/control-flow-in-async-programs.md)和[非同步傳回類型](../../programming-guide/concepts/async/async-return-types.md)。</span><span class="sxs-lookup"><span data-stu-id="27bdd-212">For more information about `Async` procedures, see [Asynchronous Programming with Async and Await](../../programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="example"></a><span data-ttu-id="27bdd-213">範例</span><span class="sxs-lookup"><span data-stu-id="27bdd-213">Example</span></span>

<span data-ttu-id="27bdd-214">下列範例 `Sub` 會使用語句來定義構成程式主體的名稱、參數和代碼 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="27bdd-214">The following example uses the `Sub` statement to define the name, parameters, and code that form the body of a `Sub` procedure.</span></span>

[!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]

## <a name="example"></a><span data-ttu-id="27bdd-215">範例</span><span class="sxs-lookup"><span data-stu-id="27bdd-215">Example</span></span>

<span data-ttu-id="27bdd-216">在下列範例中， `DelayAsync` 是 `Async` `Function` 具有傳回類型的 <xref:System.Threading.Tasks.Task%601> 。</span><span class="sxs-lookup"><span data-stu-id="27bdd-216">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="27bdd-217">`DelayAsync` 具有傳回整數的 `Return` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="27bdd-217">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="27bdd-218">因此，的函式宣告 `DelayAsync` 必須有傳回型別 `Task(Of Integer)` 。</span><span class="sxs-lookup"><span data-stu-id="27bdd-218">Therefore, the function declaration of `DelayAsync` must have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="27bdd-219">因為傳回型別是 `Task(Of Integer)` ，所以 `Await` 中的運算式評估會 `DoSomethingAsync` 產生整數，如下列語句所示： `Dim result As Integer = Await delayTask` 。</span><span class="sxs-lookup"><span data-stu-id="27bdd-219">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer, as the following statement shows: `Dim result As Integer = Await delayTask`.</span></span>

<span data-ttu-id="27bdd-220">此程式 `startButton_Click` 是程式的範例 `Async Sub` 。</span><span class="sxs-lookup"><span data-stu-id="27bdd-220">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="27bdd-221">因為 `DoSomethingAsync` 是函式 `Async` ，所以的呼叫工作必須等候 `DoSomethingAsync` ，如下列語句所示： `Await DoSomethingAsync()` 。</span><span class="sxs-lookup"><span data-stu-id="27bdd-221">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="27bdd-222">程式 `startButton_Click` `Sub` 必須以修飾詞定義， `Async` 因為它有一個 `Await` 運算式。</span><span class="sxs-lookup"><span data-stu-id="27bdd-222">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="27bdd-223">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27bdd-223">See also</span></span>

- [<span data-ttu-id="27bdd-224">Implements 陳述式</span><span class="sxs-lookup"><span data-stu-id="27bdd-224">Implements Statement</span></span>](implements-statement.md)
- [<span data-ttu-id="27bdd-225">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="27bdd-225">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="27bdd-226">參數清單</span><span class="sxs-lookup"><span data-stu-id="27bdd-226">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="27bdd-227">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="27bdd-227">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="27bdd-228">Call 陳述式</span><span class="sxs-lookup"><span data-stu-id="27bdd-228">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="27bdd-229">的</span><span class="sxs-lookup"><span data-stu-id="27bdd-229">Of</span></span>](of-clause.md)
- [<span data-ttu-id="27bdd-230">參數陣列</span><span class="sxs-lookup"><span data-stu-id="27bdd-230">Parameter Arrays</span></span>](../../programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="27bdd-231">作法：使用泛型類別</span><span class="sxs-lookup"><span data-stu-id="27bdd-231">How to: Use a Generic Class</span></span>](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="27bdd-232">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="27bdd-232">Troubleshooting Procedures</span></span>](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="27bdd-233">部分方法</span><span class="sxs-lookup"><span data-stu-id="27bdd-233">Partial Methods</span></span>](../../programming-guide/language-features/procedures/partial-methods.md)
