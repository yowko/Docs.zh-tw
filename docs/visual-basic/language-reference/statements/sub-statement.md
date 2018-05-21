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
ms.openlocfilehash: 08be38cdbec82914b567ab5b86eed71181efcf57
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="sub-statement-visual-basic"></a><span data-ttu-id="0a026-102">Sub 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a026-102">Sub Statement (Visual Basic)</span></span>
<span data-ttu-id="0a026-103">名稱、 參數和定義的程式碼會宣告`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="0a026-103">Declares the name, parameters, and code that define a `Sub` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a026-104">語法</span><span class="sxs-lookup"><span data-stu-id="0a026-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]  
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Sub ]  
    [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="0a026-105">組件</span><span class="sxs-lookup"><span data-stu-id="0a026-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="0a026-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0a026-106">Optional.</span></span> <span data-ttu-id="0a026-107">請參閱[屬性清單](attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="0a026-107">See [Attribute List](attribute-list.md).</span></span>  
  
-   `Partial`  
  
     <span data-ttu-id="0a026-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0a026-108">Optional.</span></span> <span data-ttu-id="0a026-109">表示定義部分方法。</span><span class="sxs-lookup"><span data-stu-id="0a026-109">Indicates definition of a partial method.</span></span> <span data-ttu-id="0a026-110">請參閱[部分方法](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="0a026-110">See [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="0a026-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0a026-111">Optional.</span></span> <span data-ttu-id="0a026-112">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="0a026-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="0a026-113">Public</span><span class="sxs-lookup"><span data-stu-id="0a026-113">Public</span></span>](../modifiers/public.md)  
  
    -   [<span data-ttu-id="0a026-114">Protected</span><span class="sxs-lookup"><span data-stu-id="0a026-114">Protected</span></span>](../modifiers/protected.md)  
  
    -   [<span data-ttu-id="0a026-115">Friend</span><span class="sxs-lookup"><span data-stu-id="0a026-115">Friend</span></span>](../modifiers/friend.md)  
  
    -   [<span data-ttu-id="0a026-116">Private</span><span class="sxs-lookup"><span data-stu-id="0a026-116">Private</span></span>](../modifiers/private.md)  
  
    - [<span data-ttu-id="0a026-117">Protected 的 Friend</span><span class="sxs-lookup"><span data-stu-id="0a026-117">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

    - [<span data-ttu-id="0a026-118">受保護的私用</span><span class="sxs-lookup"><span data-stu-id="0a026-118">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)
  
     <span data-ttu-id="0a026-119">請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="0a026-119">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `proceduremodifiers`  
  
     <span data-ttu-id="0a026-120">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0a026-120">Optional.</span></span> <span data-ttu-id="0a026-121">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="0a026-121">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="0a026-122">多載</span><span class="sxs-lookup"><span data-stu-id="0a026-122">Overloads</span></span>](../modifiers/overloads.md)  
  
    -   [<span data-ttu-id="0a026-123">Overrides</span><span class="sxs-lookup"><span data-stu-id="0a026-123">Overrides</span></span>](../modifiers/overrides.md)  
  
    -   [<span data-ttu-id="0a026-124">Overridable</span><span class="sxs-lookup"><span data-stu-id="0a026-124">Overridable</span></span>](../modifiers/overridable.md)  
  
    -   [<span data-ttu-id="0a026-125">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="0a026-125">NotOverridable</span></span>](../modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="0a026-126">MustOverride</span><span class="sxs-lookup"><span data-stu-id="0a026-126">MustOverride</span></span>](../modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="0a026-127">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0a026-127">Optional.</span></span> <span data-ttu-id="0a026-128">請參閱[共用](../modifiers/shared.md)。</span><span class="sxs-lookup"><span data-stu-id="0a026-128">See [Shared](../modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="0a026-129">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0a026-129">Optional.</span></span> <span data-ttu-id="0a026-130">請參閱[陰影](../modifiers/shadows.md)。</span><span class="sxs-lookup"><span data-stu-id="0a026-130">See [Shadows](../modifiers/shadows.md).</span></span>  
  
-   `Async`  
  
     <span data-ttu-id="0a026-131">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0a026-131">Optional.</span></span> <span data-ttu-id="0a026-132">請參閱[非同步](../modifiers/async.md)。</span><span class="sxs-lookup"><span data-stu-id="0a026-132">See [Async](../modifiers/async.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="0a026-133">必要。</span><span class="sxs-lookup"><span data-stu-id="0a026-133">Required.</span></span> <span data-ttu-id="0a026-134">程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="0a026-134">Name of the procedure.</span></span> <span data-ttu-id="0a026-135">請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="0a026-135">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span> <span data-ttu-id="0a026-136">若要建立之類別的建構函式程序，將名稱設定`Sub`程序`New`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="0a026-136">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="0a026-137">如需詳細資訊，請參閱[物件存留期： 物件的建立和終結](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)。</span><span class="sxs-lookup"><span data-stu-id="0a026-137">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
-   `typeparamlist`  
  
     <span data-ttu-id="0a026-138">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0a026-138">Optional.</span></span> <span data-ttu-id="0a026-139">泛型程序中的型別參數的清單。</span><span class="sxs-lookup"><span data-stu-id="0a026-139">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="0a026-140">請參閱[輸入清單](type-list.md)。</span><span class="sxs-lookup"><span data-stu-id="0a026-140">See [Type List](type-list.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="0a026-141">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0a026-141">Optional.</span></span> <span data-ttu-id="0a026-142">本機變數的名稱，表示此程序的參數清單。</span><span class="sxs-lookup"><span data-stu-id="0a026-142">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="0a026-143">請參閱[參數清單](parameter-list.md)。</span><span class="sxs-lookup"><span data-stu-id="0a026-143">See [Parameter List](parameter-list.md).</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="0a026-144">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0a026-144">Optional.</span></span> <span data-ttu-id="0a026-145">表示此程序會實作一或多個`Sub`程序，每一個定義中包含這個程序的類別或結構所實作的介面。</span><span class="sxs-lookup"><span data-stu-id="0a026-145">Indicates that this procedure implements one or more `Sub` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="0a026-146">請參閱[實作陳述式](implements-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="0a026-146">See [Implements Statement](implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="0a026-147">如果使用 `Implements`，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="0a026-147">Required if `Implements` is supplied.</span></span> <span data-ttu-id="0a026-148">實作之 `Sub` 程序的清單。</span><span class="sxs-lookup"><span data-stu-id="0a026-148">List of `Sub` procedures being implemented.</span></span>  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     <span data-ttu-id="0a026-149">每個 `implementedprocedure` 都具有下列語法和組件：</span><span class="sxs-lookup"><span data-stu-id="0a026-149">Each `implementedprocedure` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="0a026-150">組件</span><span class="sxs-lookup"><span data-stu-id="0a026-150">Part</span></span>|<span data-ttu-id="0a026-151">描述</span><span class="sxs-lookup"><span data-stu-id="0a026-151">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="0a026-152">必要。</span><span class="sxs-lookup"><span data-stu-id="0a026-152">Required.</span></span> <span data-ttu-id="0a026-153">這個程序所實作的介面名稱所含的類別或結構。</span><span class="sxs-lookup"><span data-stu-id="0a026-153">Name of an interface implemented by this procedure's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="0a026-154">必要。</span><span class="sxs-lookup"><span data-stu-id="0a026-154">Required.</span></span> <span data-ttu-id="0a026-155">名稱，據以在 `interface` 中定義程序。</span><span class="sxs-lookup"><span data-stu-id="0a026-155">Name by which the procedure is defined in `interface`.</span></span>|  
  
-   `Handles`  
  
     <span data-ttu-id="0a026-156">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0a026-156">Optional.</span></span> <span data-ttu-id="0a026-157">指出此程序可以處理一或多個特定事件。</span><span class="sxs-lookup"><span data-stu-id="0a026-157">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="0a026-158">請參閱[處理](handles-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="0a026-158">See [Handles](handles-clause.md).</span></span>  
  
-   `eventlist`  
  
     <span data-ttu-id="0a026-159">如果使用 `Handles`，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="0a026-159">Required if `Handles` is supplied.</span></span> <span data-ttu-id="0a026-160">此程序處理的事件清單。</span><span class="sxs-lookup"><span data-stu-id="0a026-160">List of events this procedure handles.</span></span>  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     <span data-ttu-id="0a026-161">每個 `eventspecifier` 都具有下列語法和組件：</span><span class="sxs-lookup"><span data-stu-id="0a026-161">Each `eventspecifier` has the following syntax and parts:</span></span>  
  
     `eventvariable.event`  
  
    |<span data-ttu-id="0a026-162">組件</span><span class="sxs-lookup"><span data-stu-id="0a026-162">Part</span></span>|<span data-ttu-id="0a026-163">描述</span><span class="sxs-lookup"><span data-stu-id="0a026-163">Description</span></span>|  
    |---|---|  
    |`eventvariable`|<span data-ttu-id="0a026-164">必要。</span><span class="sxs-lookup"><span data-stu-id="0a026-164">Required.</span></span> <span data-ttu-id="0a026-165">宣告的類別或結構，會引發事件的資料類型的物件變數。</span><span class="sxs-lookup"><span data-stu-id="0a026-165">Object variable declared with the data type of the class or structure that raises the event.</span></span>|  
    |`event`|<span data-ttu-id="0a026-166">必要。</span><span class="sxs-lookup"><span data-stu-id="0a026-166">Required.</span></span> <span data-ttu-id="0a026-167">此程序處理事件的名稱。</span><span class="sxs-lookup"><span data-stu-id="0a026-167">Name of the event this procedure handles.</span></span>|  
  
-   `statements`  
  
     <span data-ttu-id="0a026-168">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0a026-168">Optional.</span></span> <span data-ttu-id="0a026-169">若要執行此程序內的陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="0a026-169">Block of statements to run within this procedure.</span></span>  
  
-   `End Sub`  
  
     <span data-ttu-id="0a026-170">結束此程序的定義。</span><span class="sxs-lookup"><span data-stu-id="0a026-170">Terminates the definition of this procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a026-171">備註</span><span class="sxs-lookup"><span data-stu-id="0a026-171">Remarks</span></span>  
 <span data-ttu-id="0a026-172">所有可執行程式碼必須是程序內。</span><span class="sxs-lookup"><span data-stu-id="0a026-172">All executable code must be inside a procedure.</span></span> <span data-ttu-id="0a026-173">使用`Sub`程序時您不想要將值傳回給呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="0a026-173">Use a `Sub` procedure when you don't want to return a value to the calling code.</span></span> <span data-ttu-id="0a026-174">使用`Function`程序，當您想要傳回的值。</span><span class="sxs-lookup"><span data-stu-id="0a026-174">Use a `Function` procedure when you want to return a value.</span></span>  
  
## <a name="defining-a-sub-procedure"></a><span data-ttu-id="0a026-175">定義 Sub 程序</span><span class="sxs-lookup"><span data-stu-id="0a026-175">Defining a Sub Procedure</span></span>  
 <span data-ttu-id="0a026-176">您可以定義`Sub`程序只能在模組層級。</span><span class="sxs-lookup"><span data-stu-id="0a026-176">You can define a `Sub` procedure only at the module level.</span></span> <span data-ttu-id="0a026-177">Sub 程序的宣告內容，因此，必須在類別、 結構、 模組或介面，且不能在原始程式檔、 命名空間、 程序或區塊。</span><span class="sxs-lookup"><span data-stu-id="0a026-177">The declaration context for a sub procedure must, therefore, be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="0a026-178">如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="0a026-178">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="0a026-179">`Sub` 程序預設為公用存取。</span><span class="sxs-lookup"><span data-stu-id="0a026-179">`Sub` procedures default to public access.</span></span> <span data-ttu-id="0a026-180">您可以使用存取修飾詞來調整其存取層級。</span><span class="sxs-lookup"><span data-stu-id="0a026-180">You can adjust their access levels by using the access modifiers.</span></span>  
  
 <span data-ttu-id="0a026-181">如果程序使用`Implements`關鍵字、 包含的類別或結構必須`Implements`緊接在後面的陳述式其`Class`或`Structure`陳述式。</span><span class="sxs-lookup"><span data-stu-id="0a026-181">If the procedure uses the `Implements` keyword, the containing class or structure must have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="0a026-182">`Implements`陳述式必須包含每個介面中指定`implementslist`。</span><span class="sxs-lookup"><span data-stu-id="0a026-182">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="0a026-183">不過，用介面會定義的名稱`Sub`(在`definedname`) 沒有符合此程序的名稱 (在`name`)。</span><span class="sxs-lookup"><span data-stu-id="0a026-183">However, the name by which an interface defines the `Sub` (in `definedname`) doesn't have to match the name of this procedure (in `name`).</span></span>  
  
## <a name="returning-from-a-sub-procedure"></a><span data-ttu-id="0a026-184">從 Sub 程序傳回</span><span class="sxs-lookup"><span data-stu-id="0a026-184">Returning from a Sub Procedure</span></span>  
 <span data-ttu-id="0a026-185">當`Sub`程序傳回呼叫程式碼，呼叫它的陳述式之後的陳述式繼續執行。</span><span class="sxs-lookup"><span data-stu-id="0a026-185">When a `Sub` procedure returns to the calling code, execution continues with the statement after the statement that called it.</span></span>  
  
 <span data-ttu-id="0a026-186">下列範例示範從傳回`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="0a026-186">The following example shows a return from a `Sub` procedure.</span></span>  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 <span data-ttu-id="0a026-187">`Exit Sub`和`Return`陳述式會導致立即結束`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="0a026-187">The `Exit Sub` and `Return` statements cause an immediate exit from a `Sub` procedure.</span></span> <span data-ttu-id="0a026-188">任何數目的`Exit Sub`和`Return`陳述式可以出現在任何地方程序，且您可以混合`Exit Sub`和`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="0a026-188">Any number of `Exit Sub` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Sub` and `Return` statements.</span></span>  
  
## <a name="calling-a-sub-procedure"></a><span data-ttu-id="0a026-189">呼叫 Sub 程序</span><span class="sxs-lookup"><span data-stu-id="0a026-189">Calling a Sub Procedure</span></span>  
 <span data-ttu-id="0a026-190">您呼叫`Sub`陳述式中使用的程序名稱，然後遵循與它的引數清單括號括住該名稱的程序。</span><span class="sxs-lookup"><span data-stu-id="0a026-190">You call a `Sub` procedure by using the procedure name in a statement and then following that name with its argument list in parentheses.</span></span> <span data-ttu-id="0a026-191">只有當您並未提供任何引數，您可以省略括號。</span><span class="sxs-lookup"><span data-stu-id="0a026-191">You can omit the parentheses only if you don't supply any arguments.</span></span> <span data-ttu-id="0a026-192">不過，您的程式碼的可讀性您加上括號。</span><span class="sxs-lookup"><span data-stu-id="0a026-192">However, your code is more readable if you always include the parentheses.</span></span>  
  
 <span data-ttu-id="0a026-193">A`Sub`程序和`Function`程序可以有參數，並且執行一系列的陳述式。</span><span class="sxs-lookup"><span data-stu-id="0a026-193">A `Sub` procedure and a `Function` procedure  can have parameters and perform a series of statements.</span></span> <span data-ttu-id="0a026-194">不過，`Function`程序傳回的值，以及`Sub`程序不會。</span><span class="sxs-lookup"><span data-stu-id="0a026-194">However, a `Function` procedure returns a value, and a `Sub` procedure doesn't.</span></span> <span data-ttu-id="0a026-195">因此，您無法使用`Sub`在運算式中的程序。</span><span class="sxs-lookup"><span data-stu-id="0a026-195">Therefore, you can't use a `Sub` procedure in an expression.</span></span>  
  
 <span data-ttu-id="0a026-196">您可以使用`Call`關鍵字，當您呼叫`Sub`程序，但該關鍵字時，不建議用於大部分用途。</span><span class="sxs-lookup"><span data-stu-id="0a026-196">You can use the `Call` keyword when you call a `Sub` procedure, but that keyword isn't recommended for most uses.</span></span> <span data-ttu-id="0a026-197">如需詳細資訊，請參閱[Call 陳述式](call-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="0a026-197">For more information, see [Call Statement](call-statement.md).</span></span>  
  
 <span data-ttu-id="0a026-198">Visual Basic 有時會重新排列算術運算式，以提高內部的效率。</span><span class="sxs-lookup"><span data-stu-id="0a026-198">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="0a026-199">基於這個原因，如果引數清單包含運算式呼叫其他程序，您不應該假設這些運算式，會以特定順序呼叫。</span><span class="sxs-lookup"><span data-stu-id="0a026-199">For that reason, if your argument list includes expressions that call other procedures, you shouldn't assume that those expressions will be called in a particular order.</span></span>  
  
## <a name="async-sub-procedures"></a><span data-ttu-id="0a026-200">Async Sub 程序</span><span class="sxs-lookup"><span data-stu-id="0a026-200">Async Sub Procedures</span></span>  
 <span data-ttu-id="0a026-201">使用 Async 功能，您可以不使用明確回呼或手動將您的程式碼分散到多個函式或 lambda 運算式呼叫的非同步函式。</span><span class="sxs-lookup"><span data-stu-id="0a026-201">By using the Async feature, you can invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>  
  
 <span data-ttu-id="0a026-202">如果您將標記的程序有[非同步](../modifiers/async.md)修飾詞，您可以使用[Await](../../../visual-basic/language-reference/operators/await-operator.md)程序中的運算子。</span><span class="sxs-lookup"><span data-stu-id="0a026-202">If you mark a procedure with the [Async](../modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the procedure.</span></span> <span data-ttu-id="0a026-203">當控制項到達`Await`中的運算式`Async`程序中，控制項會傳回給呼叫者，並在程序的進度會暫停，直到等候的工作完成。</span><span class="sxs-lookup"><span data-stu-id="0a026-203">When control reaches an `Await` expression in the `Async` procedure, control returns to the caller, and progress in the procedure is suspended until the awaited task completes.</span></span> <span data-ttu-id="0a026-204">工作完成時，可以在程序繼續執行。</span><span class="sxs-lookup"><span data-stu-id="0a026-204">When the task is complete, execution can resume in the procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0a026-205">`Async`程序傳回給呼叫端時遇到的其中一個第一次的等候的物件尚未完成或結束`Async`達到程序時，何者先發生。</span><span class="sxs-lookup"><span data-stu-id="0a026-205">An `Async` procedure returns to the caller when either the first awaited object that’s not yet complete is encountered or the end of the `Async` procedure is reached, whichever occurs first.</span></span>  
  
 <span data-ttu-id="0a026-206">您也可以將標記[Function 陳述式](function-statement.md)與`Async`修飾詞。</span><span class="sxs-lookup"><span data-stu-id="0a026-206">You can also mark a [Function Statement](function-statement.md) with the `Async` modifier.</span></span> <span data-ttu-id="0a026-207">`Async`函式可以有傳回類型為<xref:System.Threading.Tasks.Task%601>或<xref:System.Threading.Tasks.Task>。</span><span class="sxs-lookup"><span data-stu-id="0a026-207">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="0a026-208">範例稍後在本主題說明`Async`函式的傳回型別<xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="0a026-208">An example later in this topic shows an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="0a026-209">`Async` `Sub` 程序主要用於事件處理常式，不會傳回的值。</span><span class="sxs-lookup"><span data-stu-id="0a026-209">`Async` `Sub` procedures are primarily used for event handlers, where a value can't be returned.</span></span> <span data-ttu-id="0a026-210">`Async``Sub`無法等候程序，和呼叫端的`Async``Sub`程序無法攔截例外狀況，`Sub`程序會擲回。</span><span class="sxs-lookup"><span data-stu-id="0a026-210">An `Async``Sub` procedure can't be awaited, and the caller of an `Async``Sub` procedure can't catch exceptions that the `Sub` procedure throws.</span></span>  
  
 <span data-ttu-id="0a026-211">`Async`程序不可以宣告任何[ByRef](../modifiers/byref.md)參數。</span><span class="sxs-lookup"><span data-stu-id="0a026-211">An `Async` procedure can't declare any [ByRef](../modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="0a026-212">如需有關`Async`程序，請參閱[使用 Async 和 Await 進行非同步程式設計](../../../visual-basic/programming-guide/concepts/async/index.md)，[非同步程式中的控制流程](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)，和[非同步傳回型別](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="0a026-212">For more information about `Async` procedures, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a026-213">範例</span><span class="sxs-lookup"><span data-stu-id="0a026-213">Example</span></span>  
 <span data-ttu-id="0a026-214">下列範例會使用`Sub`陳述式來定義名稱、 參數和形成主體的程式碼`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="0a026-214">The following example uses the `Sub` statement to define the name, parameters, and code that form the body of a `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#58](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="0a026-215">範例</span><span class="sxs-lookup"><span data-stu-id="0a026-215">Example</span></span>  
 <span data-ttu-id="0a026-216">在下列範例中，`DelayAsync`是`Async``Function`具有傳回類型為<xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="0a026-216">In the following example, `DelayAsync` is an `Async``Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="0a026-217">`DelayAsync` 具有傳回整數的 `Return` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="0a026-217">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="0a026-218">因此，函式宣告的`DelayAsync`必須具有傳回類型為`Task(Of Integer)`。</span><span class="sxs-lookup"><span data-stu-id="0a026-218">Therefore, the function declaration of `DelayAsync` must have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="0a026-219">因為傳回類型為`Task(Of Integer)`，評估`Await`中的運算式`DoSomethingAsync`產生整數，如下列陳述式所示： `Dim result As Integer = Await delayTask`。</span><span class="sxs-lookup"><span data-stu-id="0a026-219">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer, as the following statement shows: `Dim result As Integer = Await delayTask`.</span></span>  
  
 <span data-ttu-id="0a026-220">`startButton_Click`程序是範例`Async Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="0a026-220">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="0a026-221">因為`DoSomethingAsync`是`Async`函式，呼叫工作`DoSomethingAsync`必須等候，如下列陳述式所示： `Await DoSomethingAsync()`。</span><span class="sxs-lookup"><span data-stu-id="0a026-221">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="0a026-222">`startButton_Click``Sub`程序都必須定義`Async`修飾詞因為它有`Await`運算式。</span><span class="sxs-lookup"><span data-stu-id="0a026-222">The `startButton_Click``Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0a026-223">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a026-223">See Also</span></span>  
 [<span data-ttu-id="0a026-224">Implements 陳述式</span><span class="sxs-lookup"><span data-stu-id="0a026-224">Implements Statement</span></span>](implements-statement.md)  
 [<span data-ttu-id="0a026-225">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="0a026-225">Function Statement</span></span>](function-statement.md)  
 [<span data-ttu-id="0a026-226">參數清單</span><span class="sxs-lookup"><span data-stu-id="0a026-226">Parameter List</span></span>](parameter-list.md)  
 [<span data-ttu-id="0a026-227">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="0a026-227">Dim Statement</span></span>](dim-statement.md)  
 [<span data-ttu-id="0a026-228">Call 陳述式</span><span class="sxs-lookup"><span data-stu-id="0a026-228">Call Statement</span></span>](call-statement.md)  
 [<span data-ttu-id="0a026-229">Of</span><span class="sxs-lookup"><span data-stu-id="0a026-229">Of</span></span>](of-clause.md)  
 [<span data-ttu-id="0a026-230">參數陣列</span><span class="sxs-lookup"><span data-stu-id="0a026-230">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [<span data-ttu-id="0a026-231">如何：使用泛型類別</span><span class="sxs-lookup"><span data-stu-id="0a026-231">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="0a026-232">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="0a026-232">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [<span data-ttu-id="0a026-233">部分方法</span><span class="sxs-lookup"><span data-stu-id="0a026-233">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
