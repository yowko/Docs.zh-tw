---
title: "Function 陳述式 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 52e9210f9e715b6055e6ed199ef1aa4b919c6dd6
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="function-statement-visual-basic"></a><span data-ttu-id="546d3-102">Function 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="546d3-102">Function Statement (Visual Basic)</span></span>
<span data-ttu-id="546d3-103">名稱、 參數和定義的程式碼會宣告`Function`程序。</span><span class="sxs-lookup"><span data-stu-id="546d3-103">Declares the name, parameters, and code that define a `Function` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="546d3-104">語法</span><span class="sxs-lookup"><span data-stu-id="546d3-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]  
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Function ]  
    [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="546d3-105">組件</span><span class="sxs-lookup"><span data-stu-id="546d3-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="546d3-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="546d3-106">Optional.</span></span> <span data-ttu-id="546d3-107">請參閱[屬性清單](attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="546d3-107">See [Attribute List](attribute-list.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="546d3-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="546d3-108">Optional.</span></span> <span data-ttu-id="546d3-109">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="546d3-109">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="546d3-110">Public</span><span class="sxs-lookup"><span data-stu-id="546d3-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="546d3-111">Protected</span><span class="sxs-lookup"><span data-stu-id="546d3-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="546d3-112">Friend</span><span class="sxs-lookup"><span data-stu-id="546d3-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="546d3-113">Private</span><span class="sxs-lookup"><span data-stu-id="546d3-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="546d3-114">請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="546d3-114">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `proceduremodifiers`  
  
     <span data-ttu-id="546d3-115">選擇性。</span><span class="sxs-lookup"><span data-stu-id="546d3-115">Optional.</span></span> <span data-ttu-id="546d3-116">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="546d3-116">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="546d3-117">多載</span><span class="sxs-lookup"><span data-stu-id="546d3-117">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [<span data-ttu-id="546d3-118">Overrides</span><span class="sxs-lookup"><span data-stu-id="546d3-118">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [<span data-ttu-id="546d3-119">Overridable</span><span class="sxs-lookup"><span data-stu-id="546d3-119">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [<span data-ttu-id="546d3-120">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="546d3-120">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="546d3-121">MustOverride</span><span class="sxs-lookup"><span data-stu-id="546d3-121">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="546d3-122">選擇性。</span><span class="sxs-lookup"><span data-stu-id="546d3-122">Optional.</span></span> <span data-ttu-id="546d3-123">請參閱[共用](../../../visual-basic/language-reference/modifiers/shared.md)。</span><span class="sxs-lookup"><span data-stu-id="546d3-123">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="546d3-124">選擇性。</span><span class="sxs-lookup"><span data-stu-id="546d3-124">Optional.</span></span> <span data-ttu-id="546d3-125">請參閱[陰影](../../../visual-basic/language-reference/modifiers/shadows.md)。</span><span class="sxs-lookup"><span data-stu-id="546d3-125">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `Async`  
  
     <span data-ttu-id="546d3-126">選擇性。</span><span class="sxs-lookup"><span data-stu-id="546d3-126">Optional.</span></span> <span data-ttu-id="546d3-127">請參閱[非同步](../../../visual-basic/language-reference/modifiers/async.md)。</span><span class="sxs-lookup"><span data-stu-id="546d3-127">See [Async](../../../visual-basic/language-reference/modifiers/async.md).</span></span>  
  
-   `Iterator`  
  
     <span data-ttu-id="546d3-128">選擇性。</span><span class="sxs-lookup"><span data-stu-id="546d3-128">Optional.</span></span> <span data-ttu-id="546d3-129">請參閱[迭代器](../../../visual-basic/language-reference/modifiers/iterator.md)。</span><span class="sxs-lookup"><span data-stu-id="546d3-129">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="546d3-130">必要。</span><span class="sxs-lookup"><span data-stu-id="546d3-130">Required.</span></span> <span data-ttu-id="546d3-131">程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="546d3-131">Name of the procedure.</span></span> <span data-ttu-id="546d3-132">請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="546d3-132">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `typeparamlist`  
  
     <span data-ttu-id="546d3-133">選擇性。</span><span class="sxs-lookup"><span data-stu-id="546d3-133">Optional.</span></span> <span data-ttu-id="546d3-134">泛型程序中的型別參數的清單。</span><span class="sxs-lookup"><span data-stu-id="546d3-134">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="546d3-135">請參閱[輸入清單](type-list.md)。</span><span class="sxs-lookup"><span data-stu-id="546d3-135">See [Type List](type-list.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="546d3-136">選擇性。</span><span class="sxs-lookup"><span data-stu-id="546d3-136">Optional.</span></span> <span data-ttu-id="546d3-137">本機變數的名稱，表示此程序的參數清單。</span><span class="sxs-lookup"><span data-stu-id="546d3-137">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="546d3-138">請參閱[參數清單](parameter-list.md)。</span><span class="sxs-lookup"><span data-stu-id="546d3-138">See [Parameter List](parameter-list.md).</span></span>  
  
-   `returntype`  
  
     <span data-ttu-id="546d3-139">若`Option Strict`是`On`。</span><span class="sxs-lookup"><span data-stu-id="546d3-139">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="546d3-140">這個程序所傳回之值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="546d3-140">Data type of the value returned by this procedure.</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="546d3-141">選擇性。</span><span class="sxs-lookup"><span data-stu-id="546d3-141">Optional.</span></span> <span data-ttu-id="546d3-142">表示此程序會實作一或多個`Function`程序，每一個定義中包含這個程序的類別或結構所實作的介面。</span><span class="sxs-lookup"><span data-stu-id="546d3-142">Indicates that this procedure implements one or more `Function` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="546d3-143">請參閱[實作陳述式](implements-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="546d3-143">See [Implements Statement](implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="546d3-144">如果使用 `Implements`，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="546d3-144">Required if `Implements` is supplied.</span></span> <span data-ttu-id="546d3-145">實作之 `Function` 程序的清單。</span><span class="sxs-lookup"><span data-stu-id="546d3-145">List of `Function` procedures being implemented.</span></span>  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     <span data-ttu-id="546d3-146">每個 `implementedprocedure` 都具有下列語法和組件：</span><span class="sxs-lookup"><span data-stu-id="546d3-146">Each `implementedprocedure` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="546d3-147">組件</span><span class="sxs-lookup"><span data-stu-id="546d3-147">Part</span></span>|<span data-ttu-id="546d3-148">描述</span><span class="sxs-lookup"><span data-stu-id="546d3-148">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="546d3-149">必要。</span><span class="sxs-lookup"><span data-stu-id="546d3-149">Required.</span></span> <span data-ttu-id="546d3-150">這個程序所實作的介面名稱所含的類別或結構。</span><span class="sxs-lookup"><span data-stu-id="546d3-150">Name of an interface implemented by this procedure's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="546d3-151">必要。</span><span class="sxs-lookup"><span data-stu-id="546d3-151">Required.</span></span> <span data-ttu-id="546d3-152">名稱，據以在 `interface` 中定義程序。</span><span class="sxs-lookup"><span data-stu-id="546d3-152">Name by which the procedure is defined in `interface`.</span></span>|  
  
-   `Handles`  
  
     <span data-ttu-id="546d3-153">選擇性。</span><span class="sxs-lookup"><span data-stu-id="546d3-153">Optional.</span></span> <span data-ttu-id="546d3-154">指出此程序可以處理一或多個特定事件。</span><span class="sxs-lookup"><span data-stu-id="546d3-154">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="546d3-155">請參閱[處理](handles-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="546d3-155">See [Handles](handles-clause.md).</span></span>  
  
-   `eventlist`  
  
     <span data-ttu-id="546d3-156">如果使用 `Handles`，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="546d3-156">Required if `Handles` is supplied.</span></span> <span data-ttu-id="546d3-157">此程序處理的事件清單。</span><span class="sxs-lookup"><span data-stu-id="546d3-157">List of events this procedure handles.</span></span>  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     <span data-ttu-id="546d3-158">每個 `eventspecifier` 都具有下列語法和組件：</span><span class="sxs-lookup"><span data-stu-id="546d3-158">Each `eventspecifier` has the following syntax and parts:</span></span>  
  
     `eventvariable.event`  
  
    |<span data-ttu-id="546d3-159">組件</span><span class="sxs-lookup"><span data-stu-id="546d3-159">Part</span></span>|<span data-ttu-id="546d3-160">描述</span><span class="sxs-lookup"><span data-stu-id="546d3-160">Description</span></span>|  
    |---|---|  
    |`eventvariable`|<span data-ttu-id="546d3-161">必要。</span><span class="sxs-lookup"><span data-stu-id="546d3-161">Required.</span></span> <span data-ttu-id="546d3-162">宣告的類別或結構，會引發事件的資料類型的物件變數。</span><span class="sxs-lookup"><span data-stu-id="546d3-162">Object variable declared with the data type of the class or structure that raises the event.</span></span>|  
    |`event`|<span data-ttu-id="546d3-163">必要。</span><span class="sxs-lookup"><span data-stu-id="546d3-163">Required.</span></span> <span data-ttu-id="546d3-164">此程序處理事件的名稱。</span><span class="sxs-lookup"><span data-stu-id="546d3-164">Name of the event this procedure handles.</span></span>|  
  
-   `statements`  
  
     <span data-ttu-id="546d3-165">選擇性。</span><span class="sxs-lookup"><span data-stu-id="546d3-165">Optional.</span></span> <span data-ttu-id="546d3-166">要執行此程序內的陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="546d3-166">Block of statements to be executed within this procedure.</span></span>  
  
-   `End Function`  
  
     <span data-ttu-id="546d3-167">結束此程序的定義。</span><span class="sxs-lookup"><span data-stu-id="546d3-167">Terminates the definition of this procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="546d3-168">備註</span><span class="sxs-lookup"><span data-stu-id="546d3-168">Remarks</span></span>  
 <span data-ttu-id="546d3-169">所有可執行程式碼必須是程序內。</span><span class="sxs-lookup"><span data-stu-id="546d3-169">All executable code must be inside a procedure.</span></span> <span data-ttu-id="546d3-170">每個程序中，依次是類別、 結構、 或包含的類別、 結構或模組指模組內宣告。</span><span class="sxs-lookup"><span data-stu-id="546d3-170">Each procedure, in turn, is declared within a class, a structure, or a module that is referred to as the containing class, structure, or module.</span></span>  
  
 <span data-ttu-id="546d3-171">若要將值傳回給呼叫程式碼，使用`Function`程序; 否則，請使用`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="546d3-171">To return a value to the calling code, use a `Function` procedure; otherwise, use a `Sub` procedure.</span></span>  
  
## <a name="defining-a-function"></a><span data-ttu-id="546d3-172">定義函式</span><span class="sxs-lookup"><span data-stu-id="546d3-172">Defining a Function</span></span>  
 <span data-ttu-id="546d3-173">您可以定義`Function`程序只能在模組層級。</span><span class="sxs-lookup"><span data-stu-id="546d3-173">You can define a `Function` procedure only at the module level.</span></span> <span data-ttu-id="546d3-174">因此，函式的宣告內容必須是類別、 結構、 模組或介面，而且不能在原始程式檔、 命名空間、 程序或區塊。</span><span class="sxs-lookup"><span data-stu-id="546d3-174">Therefore, the declaration context for a function must be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="546d3-175">如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="546d3-175">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="546d3-176">`Function`程序預設為公用存取。</span><span class="sxs-lookup"><span data-stu-id="546d3-176">`Function` procedures default to public access.</span></span> <span data-ttu-id="546d3-177">您可以調整其存取層級，使用存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="546d3-177">You can adjust their access levels with the access modifiers.</span></span>  
  
 <span data-ttu-id="546d3-178">A`Function`程序可以宣告此程序傳回值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="546d3-178">A `Function` procedure can declare the data type of the value that the procedure returns.</span></span> <span data-ttu-id="546d3-179">您可以指定任何資料類型或列舉、 結構、 類別或介面的名稱。</span><span class="sxs-lookup"><span data-stu-id="546d3-179">You can specify any data type or the name of an enumeration, a structure, a class, or an interface.</span></span> <span data-ttu-id="546d3-180">如果您未指定`returntype`參數，此程序傳回`Object`。</span><span class="sxs-lookup"><span data-stu-id="546d3-180">If you don't specify the `returntype` parameter, the procedure returns `Object`.</span></span>  
  
 <span data-ttu-id="546d3-181">如果此程序使用`Implements`關鍵字、 包含的類別或結構也必須`Implements`緊接在後面的陳述式其`Class`或`Structure`陳述式。</span><span class="sxs-lookup"><span data-stu-id="546d3-181">If this procedure uses the `Implements` keyword, the containing class or structure must also have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="546d3-182">`Implements`陳述式必須包含每個介面中指定`implementslist`。</span><span class="sxs-lookup"><span data-stu-id="546d3-182">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="546d3-183">不過，用介面會定義的名稱`Function`(在`definedname`) 不需要符合此程序的名稱 (在`name`)。</span><span class="sxs-lookup"><span data-stu-id="546d3-183">However, the name by which an interface defines the `Function` (in `definedname`) doesn't need to match the name of this procedure (in `name`).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="546d3-184">您可以使用 lambda 運算式來定義函式運算式內嵌。</span><span class="sxs-lookup"><span data-stu-id="546d3-184">You can use lambda expressions to define function expressions inline.</span></span> <span data-ttu-id="546d3-185">如需詳細資訊，請參閱[函式運算式](../../../visual-basic/language-reference/operators/function-expression.md)和[Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="546d3-185">For more information, see [Function Expression](../../../visual-basic/language-reference/operators/function-expression.md) and [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
## <a name="returning-from-a-function"></a><span data-ttu-id="546d3-186">傳回從函式</span><span class="sxs-lookup"><span data-stu-id="546d3-186">Returning from a Function</span></span>  
 <span data-ttu-id="546d3-187">當`Function`程序傳回呼叫程式碼，執行會繼續進行之後呼叫程序的陳述式的陳述式。</span><span class="sxs-lookup"><span data-stu-id="546d3-187">When the `Function` procedure returns to the calling code, execution continues with the statement that follows the statement that called the procedure.</span></span>  
  
 <span data-ttu-id="546d3-188">若要從函式傳回值，您可以將值指派給函式名稱，或將它併入`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="546d3-188">To return a value from a function, you can either assign the value to the function name or include it in a `Return` statement.</span></span>  
  
 <span data-ttu-id="546d3-189">`Return`陳述式同時指派傳回值，並結束函式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="546d3-189">The `Return` statement simultaneously assigns the return value and exits the function, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_1.vb)]  
  
 <span data-ttu-id="546d3-190">下列範例將傳回的值指派給函式名稱`myFunction`，然後使用`Exit Function`陳述式來傳回。</span><span class="sxs-lookup"><span data-stu-id="546d3-190">The following example assigns the return value to the function name `myFunction` and then uses the `Exit Function` statement to return.</span></span>  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_2.vb)]  
  
 <span data-ttu-id="546d3-191">`Exit Function`和`Return`陳述式會導致立即結束`Function`程序。</span><span class="sxs-lookup"><span data-stu-id="546d3-191">The `Exit Function` and `Return` statements cause an immediate exit from a `Function` procedure.</span></span> <span data-ttu-id="546d3-192">任何數目的`Exit Function`和`Return`陳述式可以出現在任何地方程序，且您可以混合`Exit Function`和`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="546d3-192">Any number of `Exit Function` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Function` and `Return` statements.</span></span>  
  
 <span data-ttu-id="546d3-193">如果您使用`Exit Function`而不指派值給`name`，程序會傳回中所指定的資料類型的預設值`returntype`。</span><span class="sxs-lookup"><span data-stu-id="546d3-193">If you use `Exit Function` without assigning a value to `name`, the procedure returns the default value for the data type that's specified in `returntype`.</span></span> <span data-ttu-id="546d3-194">如果`returntype`未指定，此程序傳回`Nothing`，這是預設值`Object`。</span><span class="sxs-lookup"><span data-stu-id="546d3-194">If `returntype` isn't specified, the procedure returns `Nothing`, which is the default value for `Object`.</span></span>  
  
## <a name="calling-a-function"></a><span data-ttu-id="546d3-195">呼叫函式</span><span class="sxs-lookup"><span data-stu-id="546d3-195">Calling a Function</span></span>  
 <span data-ttu-id="546d3-196">您呼叫`Function`使用程序名稱，後面接著以括號，在運算式中的引數清單的程序。</span><span class="sxs-lookup"><span data-stu-id="546d3-196">You call a `Function` procedure by using the procedure name, followed by the argument list in parentheses, in an expression.</span></span> <span data-ttu-id="546d3-197">只有當您未提供任何引數，您可以省略括號。</span><span class="sxs-lookup"><span data-stu-id="546d3-197">You can omit the parentheses only if you aren't supplying any arguments.</span></span> <span data-ttu-id="546d3-198">不過，您的程式碼的可讀性您加上括號。</span><span class="sxs-lookup"><span data-stu-id="546d3-198">However, your code is more readable if you always include the parentheses.</span></span>  
  
 <span data-ttu-id="546d3-199">您呼叫`Function`程序相同的方式，您呼叫任何程式庫函式例如`Sqrt`， `Cos`，或`ChrW`。</span><span class="sxs-lookup"><span data-stu-id="546d3-199">You call a `Function` procedure the same way that you call any library function such as `Sqrt`, `Cos`, or `ChrW`.</span></span>  
  
 <span data-ttu-id="546d3-200">您也可以呼叫函式使用`Call`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="546d3-200">You can also call a function by using the `Call` keyword.</span></span> <span data-ttu-id="546d3-201">在此情況下，會忽略傳回值。</span><span class="sxs-lookup"><span data-stu-id="546d3-201">In that case, the return value is ignored.</span></span> <span data-ttu-id="546d3-202">使用`Call`關鍵字時，不建議在大部分情況下。</span><span class="sxs-lookup"><span data-stu-id="546d3-202">Use of the `Call` keyword isn't recommended in most cases.</span></span> <span data-ttu-id="546d3-203">如需詳細資訊，請參閱[Call 陳述式](call-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="546d3-203">For more information, see [Call Statement](call-statement.md).</span></span>  
  
 <span data-ttu-id="546d3-204">Visual Basic 有時會重新排列算術運算式，以提高內部的效率。</span><span class="sxs-lookup"><span data-stu-id="546d3-204">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="546d3-205">因此，您不應該使用`Function`函式相同的運算式中的變數值變更時的算術運算式中的程序。</span><span class="sxs-lookup"><span data-stu-id="546d3-205">For that reason, you shouldn't use a `Function` procedure in an arithmetic expression when the function changes the value of variables in the same expression.</span></span>  
  
## <a name="async-functions"></a><span data-ttu-id="546d3-206">非同步函式</span><span class="sxs-lookup"><span data-stu-id="546d3-206">Async Functions</span></span>  
 <span data-ttu-id="546d3-207">*非同步*功能可讓您叫用的非同步函式，而不使用明確回呼或手動將您的程式碼分散到多個函式或 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="546d3-207">The *Async* feature allows you to invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>  
  
 <span data-ttu-id="546d3-208">如果您將標記的函式[非同步](../../../visual-basic/language-reference/modifiers/async.md)修飾詞，您可以使用[Await](../../../visual-basic/language-reference/operators/await-operator.md)函式中的運算子。</span><span class="sxs-lookup"><span data-stu-id="546d3-208">If you mark a function with the [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the function.</span></span> <span data-ttu-id="546d3-209">當控制項到達`Await`中的運算式`Async`函式，控制權回到呼叫端，和函式中的進度會暫停，直到等候的工作完成。</span><span class="sxs-lookup"><span data-stu-id="546d3-209">When control reaches an `Await` expression in the `Async` function, control returns to the caller, and progress in the function is suspended until the awaited task completes.</span></span> <span data-ttu-id="546d3-210">當工作完成時，可以繼續執行，函式中。</span><span class="sxs-lookup"><span data-stu-id="546d3-210">When the task is complete, execution can resume in the function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="546d3-211">`Async`程序會傳回給呼叫者，可能會在遇到尚未完成，第一個等候的物件或是到達結尾`Async`程序中，何者先發生。</span><span class="sxs-lookup"><span data-stu-id="546d3-211">An `Async` procedure returns to the caller when either it encounters the first awaited object that’s not yet complete, or it gets to the end of the `Async` procedure, whichever occurs first.</span></span>  
  
 <span data-ttu-id="546d3-212">`Async`函式可以有傳回類型為<xref:System.Threading.Tasks.Task%601>或<xref:System.Threading.Tasks.Task>。</span><span class="sxs-lookup"><span data-stu-id="546d3-212">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="546d3-213">舉例來說，`Async`函式的傳回型別<xref:System.Threading.Tasks.Task%601>底下提供。</span><span class="sxs-lookup"><span data-stu-id="546d3-213">An example of an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601> is provided below.</span></span>  
  
 <span data-ttu-id="546d3-214">`Async`函式不可以宣告任何[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)參數。</span><span class="sxs-lookup"><span data-stu-id="546d3-214">An `Async` function cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="546d3-215">A [Sub 陳述式](sub-statement.md)也可以使用標記`Async`修飾詞。</span><span class="sxs-lookup"><span data-stu-id="546d3-215">A [Sub Statement](sub-statement.md) can also be marked with the `Async` modifier.</span></span> <span data-ttu-id="546d3-216">這主要用於事件處理常式，不會傳回的值。</span><span class="sxs-lookup"><span data-stu-id="546d3-216">This is primarily used for event handlers, where a value cannot be returned.</span></span> <span data-ttu-id="546d3-217">`Async``Sub`無法等候程序，和呼叫端的`Async``Sub`程序無法攔截所擲回的例外狀況`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="546d3-217">An `Async``Sub` procedure can't be awaited, and the caller of an `Async``Sub` procedure can't catch exceptions that are thrown by the `Sub` procedure.</span></span>  
  
 <span data-ttu-id="546d3-218">如需有關`Async`函式，請參閱[使用 Async 和 Await 進行非同步程式設計](../../../visual-basic/programming-guide/concepts/async/index.md)，[非同步程式中的控制流程](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)，和[非同步傳回型別](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="546d3-218">For more information about `Async` functions, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="iterator-functions"></a><span data-ttu-id="546d3-219">Iterator 函式</span><span class="sxs-lookup"><span data-stu-id="546d3-219">Iterator Functions</span></span>  
 <span data-ttu-id="546d3-220">*迭代器*函式集合，例如清單或陣列上執行自訂反覆項目。</span><span class="sxs-lookup"><span data-stu-id="546d3-220">An *iterator* function performs a custom iteration over a collection, such as a list or array.</span></span> <span data-ttu-id="546d3-221">Iterator 函式會使用[產生](yield-statement.md)陳述式來一次傳回一個項目。</span><span class="sxs-lookup"><span data-stu-id="546d3-221">An iterator function uses the [Yield](yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="546d3-222">當[產生](yield-statement.md)到達陳述式時，會記住在程式碼中的目前位置。</span><span class="sxs-lookup"><span data-stu-id="546d3-222">When a [Yield](yield-statement.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="546d3-223">下次呼叫迭代器函式時，便會從這個位置重新開始執行。</span><span class="sxs-lookup"><span data-stu-id="546d3-223">Execution is restarted from that location the next time the iterator function is called.</span></span>  
  
 <span data-ttu-id="546d3-224">從用戶端程式碼呼叫迭代器使用[每個...下一步](for-each-next-statement.md)陳述式。</span><span class="sxs-lookup"><span data-stu-id="546d3-224">You call an iterator from client code by using a [For Each…Next](for-each-next-statement.md) statement.</span></span>  
  
 <span data-ttu-id="546d3-225">Iterator 函式的傳回型別可以是<xref:System.Collections.IEnumerable>， <xref:System.Collections.Generic.IEnumerable%601>， <xref:System.Collections.IEnumerator>，或<xref:System.Collections.Generic.IEnumerator%601>。</span><span class="sxs-lookup"><span data-stu-id="546d3-225">The return type of an iterator function can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="546d3-226">如需詳細資訊，請參閱[迭代器](../../programming-guide/concepts/iterators.md)。</span><span class="sxs-lookup"><span data-stu-id="546d3-226">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="546d3-227">範例</span><span class="sxs-lookup"><span data-stu-id="546d3-227">Example</span></span>  
 <span data-ttu-id="546d3-228">下列範例會使用`Function`陳述式來宣告名稱、 參數和形成主體的程式碼`Function`程序。</span><span class="sxs-lookup"><span data-stu-id="546d3-228">The following example uses the `Function` statement to declare the name, parameters, and code that form the body of a `Function` procedure.</span></span> <span data-ttu-id="546d3-229">`ParamArray`修飾詞會啟用要接受可變數目的引數的函式。</span><span class="sxs-lookup"><span data-stu-id="546d3-229">The `ParamArray` modifier enables the function to accept a variable number of arguments.</span></span>  
  
 [!code-vb[VbVbalrStatements#25](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="546d3-230">範例</span><span class="sxs-lookup"><span data-stu-id="546d3-230">Example</span></span>  
 <span data-ttu-id="546d3-231">下列範例會叫用前一個範例中宣告的函式。</span><span class="sxs-lookup"><span data-stu-id="546d3-231">The following example invokes the function declared in the preceding example.</span></span>  
  
 [!code-vb[VbVbalrStatements#26](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="546d3-232">範例</span><span class="sxs-lookup"><span data-stu-id="546d3-232">Example</span></span>  
 <span data-ttu-id="546d3-233">在下列範例中，`DelayAsync`是`Async``Function`具有傳回類型為<xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="546d3-233">In the following example, `DelayAsync` is an `Async``Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="546d3-234">`DelayAsync` 具有傳回整數的 `Return` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="546d3-234">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="546d3-235">因此函式宣告的`DelayAsync`必須有傳回類型為`Task(Of Integer)`。</span><span class="sxs-lookup"><span data-stu-id="546d3-235">Therefore the function declaration of `DelayAsync` needs to have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="546d3-236">因為傳回類型為`Task(Of Integer)`，評估`Await`中的運算式`DoSomethingAsync`會產生整數。</span><span class="sxs-lookup"><span data-stu-id="546d3-236">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer.</span></span> <span data-ttu-id="546d3-237">這示範於這個陳述式： `Dim result As Integer = Await delayTask`。</span><span class="sxs-lookup"><span data-stu-id="546d3-237">This is demonstrated in this statement: `Dim result As Integer = Await delayTask`.</span></span>  
  
 <span data-ttu-id="546d3-238">`startButton_Click`程序是範例`Async Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="546d3-238">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="546d3-239">因為`DoSomethingAsync`是`Async`函式，呼叫工作`DoSomethingAsync`必須等候，如下列陳述式所示範： `Await DoSomethingAsync()`。</span><span class="sxs-lookup"><span data-stu-id="546d3-239">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement demonstrates: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="546d3-240">`startButton_Click``Sub`程序都必須定義`Async`修飾詞因為它有`Await`運算式。</span><span class="sxs-lookup"><span data-stu-id="546d3-240">The `startButton_Click``Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/function-statement_5.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="546d3-241">請參閱</span><span class="sxs-lookup"><span data-stu-id="546d3-241">See Also</span></span>  
 [<span data-ttu-id="546d3-242">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="546d3-242">Sub Statement</span></span>](sub-statement.md)  
 [<span data-ttu-id="546d3-243">函式程序</span><span class="sxs-lookup"><span data-stu-id="546d3-243">Function Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)  
 [<span data-ttu-id="546d3-244">參數清單</span><span class="sxs-lookup"><span data-stu-id="546d3-244">Parameter List</span></span>](parameter-list.md)  
 [<span data-ttu-id="546d3-245">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="546d3-245">Dim Statement</span></span>](dim-statement.md)  
 [<span data-ttu-id="546d3-246">Call 陳述式</span><span class="sxs-lookup"><span data-stu-id="546d3-246">Call Statement</span></span>](call-statement.md)  
 [<span data-ttu-id="546d3-247">Of</span><span class="sxs-lookup"><span data-stu-id="546d3-247">Of</span></span>](of-clause.md)  
 [<span data-ttu-id="546d3-248">參數陣列</span><span class="sxs-lookup"><span data-stu-id="546d3-248">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [<span data-ttu-id="546d3-249">如何：使用泛型類別</span><span class="sxs-lookup"><span data-stu-id="546d3-249">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="546d3-250">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="546d3-250">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [<span data-ttu-id="546d3-251">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="546d3-251">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="546d3-252">函式運算式</span><span class="sxs-lookup"><span data-stu-id="546d3-252">Function Expression</span></span>](../../../visual-basic/language-reference/operators/function-expression.md)
