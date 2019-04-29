---
title: GoTo 陳述式 (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: c4dd249620ba1bf445642ce4600498f6beb30461
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61637959"
---
# <a name="goto-statement"></a><span data-ttu-id="7549d-102">GoTo 陳述式</span><span class="sxs-lookup"><span data-stu-id="7549d-102">GoTo Statement</span></span>
<span data-ttu-id="7549d-103">無條件分支到程序中指定的行。</span><span class="sxs-lookup"><span data-stu-id="7549d-103">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7549d-104">語法</span><span class="sxs-lookup"><span data-stu-id="7549d-104">Syntax</span></span>  
  
```  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="7549d-105">組件</span><span class="sxs-lookup"><span data-stu-id="7549d-105">Part</span></span>  
 `line`  
 <span data-ttu-id="7549d-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="7549d-106">Required.</span></span> <span data-ttu-id="7549d-107">任何行標籤。</span><span class="sxs-lookup"><span data-stu-id="7549d-107">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7549d-108">備註</span><span class="sxs-lookup"><span data-stu-id="7549d-108">Remarks</span></span>  
 <span data-ttu-id="7549d-109">`GoTo`陳述式只可以分支在程序中出現的行。</span><span class="sxs-lookup"><span data-stu-id="7549d-109">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="7549d-110">列必須有標籤的列`GoTo`可以參考。</span><span class="sxs-lookup"><span data-stu-id="7549d-110">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="7549d-111">如需詳細資訊，請參閱[如何：標記陳述式](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)。</span><span class="sxs-lookup"><span data-stu-id="7549d-111">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7549d-112">`GoTo` 陳述式可以讓程式碼難以閱讀和維護。</span><span class="sxs-lookup"><span data-stu-id="7549d-112">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="7549d-113">可能的話，請改為使用控制結構。</span><span class="sxs-lookup"><span data-stu-id="7549d-113">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="7549d-114">如需詳細資訊，請參閱 <<c0> [ 控制流程](../../../visual-basic/programming-guide/language-features/control-flow/index.md)。</span><span class="sxs-lookup"><span data-stu-id="7549d-114">For more information, see [Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="7549d-115">您無法使用`GoTo`陳述式，以從外部的分支`For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`，或`Using`...`End Using`建構內的標籤。</span><span class="sxs-lookup"><span data-stu-id="7549d-115">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="7549d-116">分支，然後再試語法結構</span><span class="sxs-lookup"><span data-stu-id="7549d-116">Branching and Try Constructions</span></span>  
 <span data-ttu-id="7549d-117">內`Try`...`Catch`...`Finally`建構，下列規則適用於使用分支`GoTo`陳述式。</span><span class="sxs-lookup"><span data-stu-id="7549d-117">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="7549d-118">區塊或地區</span><span class="sxs-lookup"><span data-stu-id="7549d-118">Block or region</span></span>|<span data-ttu-id="7549d-119">分支中從外部</span><span class="sxs-lookup"><span data-stu-id="7549d-119">Branching in from outside</span></span>|<span data-ttu-id="7549d-120">從內往外分支</span><span class="sxs-lookup"><span data-stu-id="7549d-120">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="7549d-121">`Try` 區塊</span><span class="sxs-lookup"><span data-stu-id="7549d-121">`Try` block</span></span>|<span data-ttu-id="7549d-122">只能從`Catch`相同的建構區塊<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="7549d-122">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="7549d-123">只為整個建構之外</span><span class="sxs-lookup"><span data-stu-id="7549d-123">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="7549d-124">`Catch` 區塊</span><span class="sxs-lookup"><span data-stu-id="7549d-124">`Catch` block</span></span>|<span data-ttu-id="7549d-125">永遠不允許</span><span class="sxs-lookup"><span data-stu-id="7549d-125">Never allowed</span></span>|<span data-ttu-id="7549d-126">只之外的整個建構，或是`Try`相同的建構區塊<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="7549d-126">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="7549d-127">`Finally` 區塊</span><span class="sxs-lookup"><span data-stu-id="7549d-127">`Finally` block</span></span>|<span data-ttu-id="7549d-128">永遠不允許</span><span class="sxs-lookup"><span data-stu-id="7549d-128">Never allowed</span></span>|<span data-ttu-id="7549d-129">永遠不允許</span><span class="sxs-lookup"><span data-stu-id="7549d-129">Never allowed</span></span>|  
  
 <span data-ttu-id="7549d-130"><sup>1</sup>如果`Try`...`Catch`...`Finally`建構巢狀在另一個`Catch`區塊可以分支到`Try`區塊，在它自己的巢狀層級，但不是到任何其他`Try`區塊。</span><span class="sxs-lookup"><span data-stu-id="7549d-130"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="7549d-131">巢狀`Try`...`Catch`...`Finally`建構必須完全在包含`Try`或`Catch`建構巢狀所在的區塊。</span><span class="sxs-lookup"><span data-stu-id="7549d-131">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="7549d-132">下圖顯示一個`Try`建構巢狀在另一個。</span><span class="sxs-lookup"><span data-stu-id="7549d-132">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="7549d-133">在兩個建構的區塊之間的各種分支會表示成有效或無效。</span><span class="sxs-lookup"><span data-stu-id="7549d-133">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 ![Try 語法結構中的分支示意圖](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a><span data-ttu-id="7549d-135">範例</span><span class="sxs-lookup"><span data-stu-id="7549d-135">Example</span></span>  
 <span data-ttu-id="7549d-136">下列範例會使用`GoTo`分支到程序中的線條標籤的陳述式。</span><span class="sxs-lookup"><span data-stu-id="7549d-136">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="7549d-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7549d-137">See also</span></span>

- [<span data-ttu-id="7549d-138">Do...Loop 陳述式</span><span class="sxs-lookup"><span data-stu-id="7549d-138">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="7549d-139">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="7549d-139">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="7549d-140">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="7549d-140">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="7549d-141">If...Then...Else 陳述式</span><span class="sxs-lookup"><span data-stu-id="7549d-141">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="7549d-142">Select...Case 陳述式</span><span class="sxs-lookup"><span data-stu-id="7549d-142">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [<span data-ttu-id="7549d-143">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="7549d-143">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="7549d-144">While...End While 陳述式</span><span class="sxs-lookup"><span data-stu-id="7549d-144">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="7549d-145">With...End With 陳述式</span><span class="sxs-lookup"><span data-stu-id="7549d-145">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
