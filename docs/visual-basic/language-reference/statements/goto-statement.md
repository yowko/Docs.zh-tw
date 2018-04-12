---
title: GoTo 陳述式
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.GoTo
helpviewer_keywords:
- GoTo statement [Visual Basic]
- control flow [Visual Basic], branching
- unconditional branching [Visual Basic]
- branching [Visual Basic]
- branching [Visual Basic], unconditional
- branching [Visual Basic], conditional
- conditional statements [Visual Basic], GoTo statement
- GoTo statement [Visual Basic], syntax
ms.assetid: 313274c2-8ab3-4b9c-9ba3-0fd6798e4f6d
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 22a6315e69cd6c797d462d0835e85bb1dde67dcc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="goto-statement"></a><span data-ttu-id="fcb59-102">GoTo 陳述式</span><span class="sxs-lookup"><span data-stu-id="fcb59-102">GoTo Statement</span></span>
<span data-ttu-id="fcb59-103">無條件分支的程序中指定的行。</span><span class="sxs-lookup"><span data-stu-id="fcb59-103">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcb59-104">語法</span><span class="sxs-lookup"><span data-stu-id="fcb59-104">Syntax</span></span>  
  
```  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="fcb59-105">組件</span><span class="sxs-lookup"><span data-stu-id="fcb59-105">Part</span></span>  
 `line`  
 <span data-ttu-id="fcb59-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="fcb59-106">Required.</span></span> <span data-ttu-id="fcb59-107">任何行標籤。</span><span class="sxs-lookup"><span data-stu-id="fcb59-107">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fcb59-108">備註</span><span class="sxs-lookup"><span data-stu-id="fcb59-108">Remarks</span></span>  
 <span data-ttu-id="fcb59-109">`GoTo`陳述式只能將程式分支中的程序中的行。</span><span class="sxs-lookup"><span data-stu-id="fcb59-109">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="fcb59-110">行必須擁有行加上標籤的`GoTo`可以參考。</span><span class="sxs-lookup"><span data-stu-id="fcb59-110">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="fcb59-111">如需詳細資訊，請參閱[How to： 標籤陳述式](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)。</span><span class="sxs-lookup"><span data-stu-id="fcb59-111">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fcb59-112">`GoTo`陳述式會讓程式碼難以讀取和維護。</span><span class="sxs-lookup"><span data-stu-id="fcb59-112">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="fcb59-113">您應該盡可能改用控制結構。</span><span class="sxs-lookup"><span data-stu-id="fcb59-113">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="fcb59-114">如需詳細資訊，請參閱[控制流程](../../../visual-basic/programming-guide/language-features/control-flow/index.md)。</span><span class="sxs-lookup"><span data-stu-id="fcb59-114">For more information, see [Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="fcb59-115">您無法使用`GoTo`陳述式來從外部的分支`For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`，或`Using`...`End Using`建構內的標籤。</span><span class="sxs-lookup"><span data-stu-id="fcb59-115">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="fcb59-116">分支，然後再次嘗試語法結構</span><span class="sxs-lookup"><span data-stu-id="fcb59-116">Branching and Try Constructions</span></span>  
 <span data-ttu-id="fcb59-117">內`Try`...`Catch`...`Finally`建構，下列規則適用於與分支`GoTo`陳述式。</span><span class="sxs-lookup"><span data-stu-id="fcb59-117">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="fcb59-118">區塊或地區</span><span class="sxs-lookup"><span data-stu-id="fcb59-118">Block or region</span></span>|<span data-ttu-id="fcb59-119">分支中從外部</span><span class="sxs-lookup"><span data-stu-id="fcb59-119">Branching in from outside</span></span>|<span data-ttu-id="fcb59-120">從內部往外分支</span><span class="sxs-lookup"><span data-stu-id="fcb59-120">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="fcb59-121">`Try`區塊</span><span class="sxs-lookup"><span data-stu-id="fcb59-121">`Try` block</span></span>|<span data-ttu-id="fcb59-122">只能從`Catch`相同建構區塊<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="fcb59-122">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="fcb59-123">只在整個建構之外</span><span class="sxs-lookup"><span data-stu-id="fcb59-123">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="fcb59-124">`Catch`區塊</span><span class="sxs-lookup"><span data-stu-id="fcb59-124">`Catch` block</span></span>|<span data-ttu-id="fcb59-125">不允許</span><span class="sxs-lookup"><span data-stu-id="fcb59-125">Never allowed</span></span>|<span data-ttu-id="fcb59-126">僅外部整個建構，或為`Try`相同建構區塊<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="fcb59-126">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="fcb59-127">`Finally`區塊</span><span class="sxs-lookup"><span data-stu-id="fcb59-127">`Finally` block</span></span>|<span data-ttu-id="fcb59-128">不允許</span><span class="sxs-lookup"><span data-stu-id="fcb59-128">Never allowed</span></span>|<span data-ttu-id="fcb59-129">不允許</span><span class="sxs-lookup"><span data-stu-id="fcb59-129">Never allowed</span></span>|  
  
 <span data-ttu-id="fcb59-130"><sup>1</sup>如果一個`Try`...`Catch`...`Finally`建構，巢狀`Catch`區塊可以分支到`Try`區塊在它自己的巢狀層級，而不用到任何其他`Try`區塊。</span><span class="sxs-lookup"><span data-stu-id="fcb59-130"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="fcb59-131">巢狀`Try`...`Catch`...`Finally`建構必須完全在包含`Try`或`Catch`建構巢狀所在的區塊。</span><span class="sxs-lookup"><span data-stu-id="fcb59-131">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="fcb59-132">下圖顯示一個`Try`建構巢狀方式置於另一個。</span><span class="sxs-lookup"><span data-stu-id="fcb59-132">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="fcb59-133">兩個建構區塊之間的不同分支就會表示成有效或無效。</span><span class="sxs-lookup"><span data-stu-id="fcb59-133">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 <span data-ttu-id="fcb59-134">![Try 語法結構的分支示意圖](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")</span><span class="sxs-lookup"><span data-stu-id="fcb59-134">![Graphic diagram of branching in Try constructions](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")</span></span>  
<span data-ttu-id="fcb59-135">Try 語法結構的有效和無效的分支</span><span class="sxs-lookup"><span data-stu-id="fcb59-135">Valid and invalid branches in Try constructions</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcb59-136">範例</span><span class="sxs-lookup"><span data-stu-id="fcb59-136">Example</span></span>  
 <span data-ttu-id="fcb59-137">下列範例會使用`GoTo`分支到程序中的線條標籤的陳述式。</span><span class="sxs-lookup"><span data-stu-id="fcb59-137">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/goto-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fcb59-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcb59-138">See Also</span></span>  
 [<span data-ttu-id="fcb59-139">Do...Loop 陳述式</span><span class="sxs-lookup"><span data-stu-id="fcb59-139">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [<span data-ttu-id="fcb59-140">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="fcb59-140">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="fcb59-141">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="fcb59-141">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="fcb59-142">If...Then...Else 陳述式</span><span class="sxs-lookup"><span data-stu-id="fcb59-142">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="fcb59-143">Select...Case 陳述式</span><span class="sxs-lookup"><span data-stu-id="fcb59-143">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [<span data-ttu-id="fcb59-144">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="fcb59-144">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="fcb59-145">While...End While 陳述式</span><span class="sxs-lookup"><span data-stu-id="fcb59-145">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [<span data-ttu-id="fcb59-146">With...End With 陳述式</span><span class="sxs-lookup"><span data-stu-id="fcb59-146">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
