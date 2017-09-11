---
title: "Sub 陳述式 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Sub
dev_langs:
- VB
helpviewer_keywords:
- Public keyword, Sub statements
- procedures, creating
- declaring procedures, Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword, Sub statements
- Optional keyword, Sub statements
- declarations, procedures
- Sub keyword
- Handles keyword, Sub statements
- Protected Friend keyword
- ParamArray keyword, Sub statements
- Implements keyword, Sub statements
- Sub statement
- subroutines
- ByRef keyword, Sub statements
- Sub procedures, Sub statement
- recursive procedures
- Private keyword, Sub statements
- Friend keyword, Sub statements
- Exit statement, Sub statements
- procedures, Sub
- End keyword, Sub statements
- ByVal keyword, Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
caps.latest.revision: 52
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: dc1c456c71efb3cc6e60a8fdc77384e65975f110
ms.openlocfilehash: 61853a4f2321837683997b8e4241b688bc9f622c
ms.contentlocale: zh-tw
ms.lasthandoff: 05/15/2017

---
# <a name="sub-statement-visual-basic"></a><span data-ttu-id="a80a3-102">Sub 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a80a3-102">Sub Statement (Visual Basic)</span></span>
<span data-ttu-id="a80a3-103">名稱、 參數和定義的程式碼會宣告`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="a80a3-103">Declares the name, parameters, and code that define a `Sub` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a80a3-104">語法</span><span class="sxs-lookup"><span data-stu-id="a80a3-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]  
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Sub ]  
    [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="a80a3-105">組件</span><span class="sxs-lookup"><span data-stu-id="a80a3-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="a80a3-106">選擇項。</span><span class="sxs-lookup"><span data-stu-id="a80a3-106">Optional.</span></span> <span data-ttu-id="a80a3-107">請參閱[屬性清單](attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="a80a3-107">See [Attribute List](attribute-list.md).</span></span>  
  
-   `Partial`  
  
     <span data-ttu-id="a80a3-108">選擇項。</span><span class="sxs-lookup"><span data-stu-id="a80a3-108">Optional.</span></span> <span data-ttu-id="a80a3-109">表示部分方法的定義。</span><span class="sxs-lookup"><span data-stu-id="a80a3-109">Indicates definition of a partial method.</span></span> <span data-ttu-id="a80a3-110">請參閱[部分方法](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="a80a3-110">See [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="a80a3-111">選擇項。</span><span class="sxs-lookup"><span data-stu-id="a80a3-111">Optional.</span></span> <span data-ttu-id="a80a3-112">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="a80a3-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="a80a3-113">Public</span><span class="sxs-lookup"><span data-stu-id="a80a3-113">Public</span></span>](../modifiers/public.md)  
  
    -   [<span data-ttu-id="a80a3-114">Protected</span><span class="sxs-lookup"><span data-stu-id="a80a3-114">Protected</span></span>](../modifiers/protected.md)  
  
    -   [<span data-ttu-id="a80a3-115">Friend</span><span class="sxs-lookup"><span data-stu-id="a80a3-115">Friend</span></span>](../modifiers/friend.md)  
  
    -   [<span data-ttu-id="a80a3-116">Private</span><span class="sxs-lookup"><span data-stu-id="a80a3-116">Private</span></span>](../modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="a80a3-117">請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="a80a3-117">See [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `proceduremodifiers`  
  
     <span data-ttu-id="a80a3-118">選擇項。</span><span class="sxs-lookup"><span data-stu-id="a80a3-118">Optional.</span></span> <span data-ttu-id="a80a3-119">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="a80a3-119">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="a80a3-120">多載</span><span class="sxs-lookup"><span data-stu-id="a80a3-120">Overloads</span></span>](../modifiers/overloads.md)  
  
    -   [<span data-ttu-id="a80a3-121">Overrides</span><span class="sxs-lookup"><span data-stu-id="a80a3-121">Overrides</span></span>](../modifiers/overrides.md)  
  
    -   [<span data-ttu-id="a80a3-122">Overridable</span><span class="sxs-lookup"><span data-stu-id="a80a3-122">Overridable</span></span>](../modifiers/overridable.md)  
  
    -   [<span data-ttu-id="a80a3-123">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="a80a3-123">NotOverridable</span></span>](../modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="a80a3-124">MustOverride</span><span class="sxs-lookup"><span data-stu-id="a80a3-124">MustOverride</span></span>](../modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="a80a3-125">選擇項。</span><span class="sxs-lookup"><span data-stu-id="a80a3-125">Optional.</span></span> <span data-ttu-id="a80a3-126">請參閱[共用](../modifiers/shared.md)。</span><span class="sxs-lookup"><span data-stu-id="a80a3-126">See [Shared](../modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="a80a3-127">選擇項。</span><span class="sxs-lookup"><span data-stu-id="a80a3-127">Optional.</span></span> <span data-ttu-id="a80a3-128">請參閱[陰影](../modifiers/shadows.md)。</span><span class="sxs-lookup"><span data-stu-id="a80a3-128">See [Shadows](../modifiers/shadows.md).</span></span>  
  
-   `Async`  
  
     <span data-ttu-id="a80a3-129">選擇項。</span><span class="sxs-lookup"><span data-stu-id="a80a3-129">Optional.</span></span> <span data-ttu-id="a80a3-130">請參閱[非同步](../modifiers/async.md)。</span><span class="sxs-lookup"><span data-stu-id="a80a3-130">See [Async](../modifiers/async.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="a80a3-131">必要項。</span><span class="sxs-lookup"><span data-stu-id="a80a3-131">Required.</span></span> <span data-ttu-id="a80a3-132">程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="a80a3-132">Name of the procedure.</span></span> <span data-ttu-id="a80a3-133">請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="a80a3-133">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span> <span data-ttu-id="a80a3-134">若要建立類別的建構函式程序，將名稱設定`Sub`程序`New`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a80a3-134">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="a80a3-135">如需詳細資訊，請參閱[物件存留期︰ 物件的建立和終結](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)。</span><span class="sxs-lookup"><span data-stu-id="a80a3-135">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
-   `typeparamlist`  
  
     <span data-ttu-id="a80a3-136">選擇項。</span><span class="sxs-lookup"><span data-stu-id="a80a3-136">Optional.</span></span> <span data-ttu-id="a80a3-137">泛型程序的類型參數的清單。</span><span class="sxs-lookup"><span data-stu-id="a80a3-137">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="a80a3-138">請參閱[輸入清單](type-list.md)。</span><span class="sxs-lookup"><span data-stu-id="a80a3-138">See [Type List](type-list.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="a80a3-139">選擇項。</span><span class="sxs-lookup"><span data-stu-id="a80a3-139">Optional.</span></span> <span data-ttu-id="a80a3-140">代表此程序參數的本機變數名稱的清單。</span><span class="sxs-lookup"><span data-stu-id="a80a3-140">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="a80a3-141">請參閱[參數清單](parameter-list.md)。</span><span class="sxs-lookup"><span data-stu-id="a80a3-141">See [Parameter List](parameter-list.md).</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="a80a3-142">選擇項。</span><span class="sxs-lookup"><span data-stu-id="a80a3-142">Optional.</span></span> <span data-ttu-id="a80a3-143">表示此程序會實作一個或多個`Sub`程序，每一個定義在此程序包含類別或結構所實作的介面。</span><span class="sxs-lookup"><span data-stu-id="a80a3-143">Indicates that this procedure implements one or more `Sub` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="a80a3-144">請參閱[實作陳述式](implements-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="a80a3-144">See [Implements Statement](implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="a80a3-145">如果使用 `Implements`，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="a80a3-145">Required if `Implements` is supplied.</span></span> <span data-ttu-id="a80a3-146">實作之 `Sub` 程序的清單。</span><span class="sxs-lookup"><span data-stu-id="a80a3-146">List of `Sub` procedures being implemented.</span></span>  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     <span data-ttu-id="a80a3-147">每個 `implementedprocedure` 都具有下列語法和組件：</span><span class="sxs-lookup"><span data-stu-id="a80a3-147">Each `implementedprocedure` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="a80a3-148">組件</span><span class="sxs-lookup"><span data-stu-id="a80a3-148">Part</span></span>|<span data-ttu-id="a80a3-149">描述</span><span class="sxs-lookup"><span data-stu-id="a80a3-149">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="a80a3-150">必要項。</span><span class="sxs-lookup"><span data-stu-id="a80a3-150">Required.</span></span> <span data-ttu-id="a80a3-151">這個程序所實作的介面名稱的包含類別或結構。</span><span class="sxs-lookup"><span data-stu-id="a80a3-151">Name of an interface implemented by this procedure's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="a80a3-152">必要項。</span><span class="sxs-lookup"><span data-stu-id="a80a3-152">Required.</span></span> <span data-ttu-id="a80a3-153">名稱，據以在 `interface` 中定義程序。</span><span class="sxs-lookup"><span data-stu-id="a80a3-153">Name by which the procedure is defined in `interface`.</span></span>|  
  
-   `Handles`  
  
     <span data-ttu-id="a80a3-154">選擇項。</span><span class="sxs-lookup"><span data-stu-id="a80a3-154">Optional.</span></span> <span data-ttu-id="a80a3-155">表示此程序可以處理一或多個特定的事件。</span><span class="sxs-lookup"><span data-stu-id="a80a3-155">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="a80a3-156">請參閱[處理](handles-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="a80a3-156">See [Handles](handles-clause.md).</span></span>  
  
-   `eventlist`  
  
     <span data-ttu-id="a80a3-157">如果使用 `Handles`，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="a80a3-157">Required if `Handles` is supplied.</span></span> <span data-ttu-id="a80a3-158">此程序處理的事件清單。</span><span class="sxs-lookup"><span data-stu-id="a80a3-158">List of events this procedure handles.</span></span>  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     <span data-ttu-id="a80a3-159">每個 `eventspecifier` 都具有下列語法和組件：</span><span class="sxs-lookup"><span data-stu-id="a80a3-159">Each `eventspecifier` has the following syntax and parts:</span></span>  
  
     `eventvariable.event`  
  
    |<span data-ttu-id="a80a3-160">組件</span><span class="sxs-lookup"><span data-stu-id="a80a3-160">Part</span></span>|<span data-ttu-id="a80a3-161">描述</span><span class="sxs-lookup"><span data-stu-id="a80a3-161">Description</span></span>|  
    |---|---|  
    |`eventvariable`|<span data-ttu-id="a80a3-162">必要項。</span><span class="sxs-lookup"><span data-stu-id="a80a3-162">Required.</span></span> <span data-ttu-id="a80a3-163">宣告的類別或結構，會引發事件的資料類型的物件變數。</span><span class="sxs-lookup"><span data-stu-id="a80a3-163">Object variable declared with the data type of the class or structure that raises the event.</span></span>|  
    |`event`|<span data-ttu-id="a80a3-164">必要項。</span><span class="sxs-lookup"><span data-stu-id="a80a3-164">Required.</span></span> <span data-ttu-id="a80a3-165">此程序處理事件的名稱。</span><span class="sxs-lookup"><span data-stu-id="a80a3-165">Name of the event this procedure handles.</span></span>|  
  
-   `statements`  
  
     <span data-ttu-id="a80a3-166">選擇項。</span><span class="sxs-lookup"><span data-stu-id="a80a3-166">Optional.</span></span> <span data-ttu-id="a80a3-167">若要執行此程序內的陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="a80a3-167">Block of statements to run within this procedure.</span></span>  
  
-   `End Sub`  
  
     <span data-ttu-id="a80a3-168">結束這個程序的定義。</span><span class="sxs-lookup"><span data-stu-id="a80a3-168">Terminates the definition of this procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a80a3-169">備註</span><span class="sxs-lookup"><span data-stu-id="a80a3-169">Remarks</span></span>  
 <span data-ttu-id="a80a3-170">所有的可執行程式碼必須在程序。</span><span class="sxs-lookup"><span data-stu-id="a80a3-170">All executable code must be inside a procedure.</span></span> <span data-ttu-id="a80a3-171">使用`Sub`程序時您不想要將值傳回給呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="a80a3-171">Use a `Sub` procedure when you don't want to return a value to the calling code.</span></span> <span data-ttu-id="a80a3-172">使用`Function`程序，當您想要傳回的值。</span><span class="sxs-lookup"><span data-stu-id="a80a3-172">Use a `Function` procedure when you want to return a value.</span></span>  
  
## <a name="defining-a-sub-procedure"></a><span data-ttu-id="a80a3-173">定義 Sub 程序</span><span class="sxs-lookup"><span data-stu-id="a80a3-173">Defining a Sub Procedure</span></span>  
 <span data-ttu-id="a80a3-174">您可以定義`Sub`只能在模組層級的程序。</span><span class="sxs-lookup"><span data-stu-id="a80a3-174">You can define a `Sub` procedure only at the module level.</span></span> <span data-ttu-id="a80a3-175">Sub 程序宣告內容，因此，必須類別、 結構、 模組或介面，且不能是原始程式檔、 命名空間、 程序或區塊。</span><span class="sxs-lookup"><span data-stu-id="a80a3-175">The declaration context for a sub procedure must, therefore, be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="a80a3-176">如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="a80a3-176">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="a80a3-177">`Sub`程序預設為公用存取。</span><span class="sxs-lookup"><span data-stu-id="a80a3-177">`Sub` procedures default to public access.</span></span> <span data-ttu-id="a80a3-178">您可以調整它們的存取層級使用的存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="a80a3-178">You can adjust their access levels by using the access modifiers.</span></span>  
  
 <span data-ttu-id="a80a3-179">如果程序使用`Implements`關鍵字、 包含類別或結構必須`Implements`緊接在後面的陳述式其`Class`或`Structure`陳述式。</span><span class="sxs-lookup"><span data-stu-id="a80a3-179">If the procedure uses the `Implements` keyword, the containing class or structure must have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="a80a3-180">`Implements`陳述式必須包含在指定的每個介面`implementslist`。</span><span class="sxs-lookup"><span data-stu-id="a80a3-180">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="a80a3-181">不過，介面定義的名稱`Sub`(在`definedname`) 不一定要符合此程序的名稱 (在`name`)。</span><span class="sxs-lookup"><span data-stu-id="a80a3-181">However, the name by which an interface defines the `Sub` (in `definedname`) doesn't have to match the name of this procedure (in `name`).</span></span>  
  
## <a name="returning-from-a-sub-procedure"></a><span data-ttu-id="a80a3-182">從子程序傳回</span><span class="sxs-lookup"><span data-stu-id="a80a3-182">Returning from a Sub Procedure</span></span>  
 <span data-ttu-id="a80a3-183">當`Sub`程序會傳回呼叫程式碼，呼叫它的陳述式之後的陳述式繼續執行。</span><span class="sxs-lookup"><span data-stu-id="a80a3-183">When a `Sub` procedure returns to the calling code, execution continues with the statement after the statement that called it.</span></span>  
  
 <span data-ttu-id="a80a3-184">下列範例示範從傳回`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="a80a3-184">The following example shows a return from a `Sub` procedure.</span></span>  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 <span data-ttu-id="a80a3-185">`Exit Sub`和`Return`陳述式會造成立即結束`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="a80a3-185">The `Exit Sub` and `Return` statements cause an immediate exit from a `Sub` procedure.</span></span> <span data-ttu-id="a80a3-186">任何數目的`Exit Sub`和`Return`陳述式可以出現在任何地方程序，且您可以混合`Exit Sub`和`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="a80a3-186">Any number of `Exit Sub` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Sub` and `Return` statements.</span></span>  
  
## <a name="calling-a-sub-procedure"></a><span data-ttu-id="a80a3-187">呼叫子函數程序</span><span class="sxs-lookup"><span data-stu-id="a80a3-187">Calling a Sub Procedure</span></span>  
 <span data-ttu-id="a80a3-188">您呼叫`Sub`陳述式中使用的程序名稱，然後遵循和它的引數清單括號括住該名稱的程序。</span><span class="sxs-lookup"><span data-stu-id="a80a3-188">You call a `Sub` procedure by using the procedure name in a statement and then following that name with its argument list in parentheses.</span></span> <span data-ttu-id="a80a3-189">只有當您未提供任何引數，您可以省略括號。</span><span class="sxs-lookup"><span data-stu-id="a80a3-189">You can omit the parentheses only if you don't supply any arguments.</span></span> <span data-ttu-id="a80a3-190">不過，您的程式碼的可讀性您加上括號。</span><span class="sxs-lookup"><span data-stu-id="a80a3-190">However, your code is more readable if you always include the parentheses.</span></span>  
  
 <span data-ttu-id="a80a3-191">A`Sub`程序和`Function`程序可以有參數，並且執行一系列的陳述式。</span><span class="sxs-lookup"><span data-stu-id="a80a3-191">A `Sub` procedure and a `Function` procedure  can have parameters and perform a series of statements.</span></span> <span data-ttu-id="a80a3-192">不過，`Function`程序傳回的值，以及`Sub`程序不會。</span><span class="sxs-lookup"><span data-stu-id="a80a3-192">However, a `Function` procedure returns a value, and a `Sub` procedure doesn't.</span></span> <span data-ttu-id="a80a3-193">因此，您無法使用`Sub`在運算式中的程序。</span><span class="sxs-lookup"><span data-stu-id="a80a3-193">Therefore, you can't use a `Sub` procedure in an expression.</span></span>  
  
 <span data-ttu-id="a80a3-194">您可以使用`Call`關鍵字，當您呼叫`Sub`程序，但該關鍵字時，不建議用於大部分用途。</span><span class="sxs-lookup"><span data-stu-id="a80a3-194">You can use the `Call` keyword when you call a `Sub` procedure, but that keyword isn't recommended for most uses.</span></span> <span data-ttu-id="a80a3-195">如需詳細資訊，請參閱[Call 陳述式](call-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="a80a3-195">For more information, see [Call Statement](call-statement.md).</span></span>  
  
 <span data-ttu-id="a80a3-196">Visual Basic 有時會重新排列提高內部效率的算術運算式。</span><span class="sxs-lookup"><span data-stu-id="a80a3-196">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="a80a3-197">基於這個理由，如果引數清單中包含運算式呼叫其他程序，您不應該假設這些運算式，會以特定順序呼叫。</span><span class="sxs-lookup"><span data-stu-id="a80a3-197">For that reason, if your argument list includes expressions that call other procedures, you shouldn't assume that those expressions will be called in a particular order.</span></span>  
  
## <a name="async-sub-procedures"></a><span data-ttu-id="a80a3-198">非同步 Sub 程序</span><span class="sxs-lookup"><span data-stu-id="a80a3-198">Async Sub Procedures</span></span>  
 <span data-ttu-id="a80a3-199">使用 Async 功能，可以叫用非同步函數，而不使用明確的回呼或手動將您的程式碼分散到多個函式或 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="a80a3-199">By using the Async feature, you can invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>  
  
 <span data-ttu-id="a80a3-200">如果您將標示的程序[非同步](../modifiers/async.md)修飾詞，您可以使用[Await](../../../visual-basic/language-reference/operators/await-operator.md)程序中的運算子。</span><span class="sxs-lookup"><span data-stu-id="a80a3-200">If you mark a procedure with the [Async](../modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the procedure.</span></span> <span data-ttu-id="a80a3-201">當控制到達`Await`中的運算式`Async`程序中，控制權會回到呼叫端，並在程序的進度會暫停，直到等候的工作完成。</span><span class="sxs-lookup"><span data-stu-id="a80a3-201">When control reaches an `Await` expression in the `Async` procedure, control returns to the caller, and progress in the procedure is suspended until the awaited task completes.</span></span> <span data-ttu-id="a80a3-202">當工作完成時，可以在程序繼續執行。</span><span class="sxs-lookup"><span data-stu-id="a80a3-202">When the task is complete, execution can resume in the procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a80a3-203">`Async`程序傳回至呼叫端發生其中一個第一次的等候的物件尚未完成時或結尾`Async`達到程序時，何者先發生。</span><span class="sxs-lookup"><span data-stu-id="a80a3-203">An `Async` procedure returns to the caller when either the first awaited object that’s not yet complete is encountered or the end of the `Async` procedure is reached, whichever occurs first.</span></span>  
  
 <span data-ttu-id="a80a3-204">您也可以將標記[Function 陳述式](function-statement.md)與`Async`修飾詞。</span><span class="sxs-lookup"><span data-stu-id="a80a3-204">You can also mark a [Function Statement](function-statement.md) with the `Async` modifier.</span></span> <span data-ttu-id="a80a3-205">`Async`函數可以有傳回型別<xref:System.Threading.Tasks.Task%601>或<xref:System.Threading.Tasks.Task>。</xref:System.Threading.Tasks.Task> </xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="a80a3-205">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="a80a3-206">範例稍後在本主題將說明`Async` <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601>的傳回類型的函式</span><span class="sxs-lookup"><span data-stu-id="a80a3-206">An example later in this topic shows an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="a80a3-207">`Async``Sub`程序主要用於事件處理常式，無法傳回值的位置。</span><span class="sxs-lookup"><span data-stu-id="a80a3-207">`Async` `Sub` procedures are primarily used for event handlers, where a value can't be returned.</span></span> <span data-ttu-id="a80a3-208">`Async``Sub`無法等候程序，和呼叫端的`Async``Sub`程序無法攔截例外狀況，`Sub`程序則會擲回。</span><span class="sxs-lookup"><span data-stu-id="a80a3-208">An `Async``Sub` procedure can't be awaited, and the caller of an `Async``Sub` procedure can't catch exceptions that the `Sub` procedure throws.</span></span>  
  
 <span data-ttu-id="a80a3-209">`Async`程序不可以宣告任何[ByRef](../modifiers/byref.md)參數。</span><span class="sxs-lookup"><span data-stu-id="a80a3-209">An `Async` procedure can't declare any [ByRef](../modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="a80a3-210">如需詳細資訊`Async`程序，請參閱[使用 Async 和 Await 進行非同步程式設計](../../../visual-basic/programming-guide/concepts/async/index.md)，[非同步程式中的控制流程](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)，和[非同步傳回型別](../../../visual-basic/programming-guide/concepts/async/async-return-types.md)。</span><span class="sxs-lookup"><span data-stu-id="a80a3-210">For more information about `Async` procedures, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a80a3-211">範例</span><span class="sxs-lookup"><span data-stu-id="a80a3-211">Example</span></span>  
 <span data-ttu-id="a80a3-212">下列範例會使用`Sub`陳述式來定義名稱、 參數和程式碼，構成的主體`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="a80a3-212">The following example uses the `Sub` statement to define the name, parameters, and code that form the body of a `Sub` procedure.</span></span>  
  
 <span data-ttu-id="a80a3-213">[!code-vb[VbVbalrStatements #&58;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a80a3-213">[!code-vb[VbVbalrStatements#58](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="a80a3-214">範例</span><span class="sxs-lookup"><span data-stu-id="a80a3-214">Example</span></span>  
 <span data-ttu-id="a80a3-215">在下列範例中，`DelayAsync`是`Async``Function`具有<xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601>的傳回型別</span><span class="sxs-lookup"><span data-stu-id="a80a3-215">In the following example, `DelayAsync` is an an `Async``Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="a80a3-216">`DelayAsync` 具有傳回整數的 `Return` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="a80a3-216">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="a80a3-217">因此，函式宣告的`DelayAsync`的傳回型別必須`Task(Of Integer)`。</span><span class="sxs-lookup"><span data-stu-id="a80a3-217">Therefore, the function declaration of `DelayAsync` must have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="a80a3-218">因為傳回型別是`Task(Of Integer)`，評估`Await`中的運算式`DoSomethingAsync`產生一個整數，下列陳述式所示︰ `Dim result As Integer = Await delayTask`。</span><span class="sxs-lookup"><span data-stu-id="a80a3-218">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer, as the following statement shows: `Dim result As Integer = Await delayTask`.</span></span>  
  
 <span data-ttu-id="a80a3-219">`startButton_Click`程序是範例`Async Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="a80a3-219">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="a80a3-220">因為`DoSomethingAsync`是`Async`函式，呼叫工作`DoSomethingAsync`必須等候，下列陳述式所示︰ `Await DoSomethingAsync()`。</span><span class="sxs-lookup"><span data-stu-id="a80a3-220">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="a80a3-221">`startButton_Click``Sub`程序都必須定義`Async`修飾詞因為它有`Await`運算式。</span><span class="sxs-lookup"><span data-stu-id="a80a3-221">The `startButton_Click``Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>  
  
 <span data-ttu-id="a80a3-222">[!code-vb[csAsyncMethod&#1;](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="a80a3-222">[!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a80a3-223">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a80a3-223">See Also</span></span>  
 <span data-ttu-id="a80a3-224">[Implements 陳述式](implements-statement.md) </span><span class="sxs-lookup"><span data-stu-id="a80a3-224">[Implements Statement](implements-statement.md) </span></span>  
<span data-ttu-id="a80a3-225"> [Function 陳述式](function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="a80a3-225"> [Function Statement](function-statement.md) </span></span>  
<span data-ttu-id="a80a3-226"> [參數清單](parameter-list.md) </span><span class="sxs-lookup"><span data-stu-id="a80a3-226"> [Parameter List](parameter-list.md) </span></span>  
<span data-ttu-id="a80a3-227"> [Dim 陳述式](dim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="a80a3-227"> [Dim Statement](dim-statement.md) </span></span>  
<span data-ttu-id="a80a3-228"> [Call 陳述式](call-statement.md) </span><span class="sxs-lookup"><span data-stu-id="a80a3-228"> [Call Statement](call-statement.md) </span></span>  
<span data-ttu-id="a80a3-229"> [Of](of-clause.md) </span><span class="sxs-lookup"><span data-stu-id="a80a3-229"> [Of](of-clause.md) </span></span>  
<span data-ttu-id="a80a3-230"> [參數陣列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="a80a3-230"> [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md) </span></span>  
<span data-ttu-id="a80a3-231"> [如何︰ 使用泛型類別](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md) </span><span class="sxs-lookup"><span data-stu-id="a80a3-231"> [How to: Use a Generic Class](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md) </span></span>  
<span data-ttu-id="a80a3-232"> [疑難排解程序](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="a80a3-232"> [Troubleshooting Procedures](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="a80a3-233"> [部分方法](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)</span><span class="sxs-lookup"><span data-stu-id="a80a3-233"> [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)</span></span>

