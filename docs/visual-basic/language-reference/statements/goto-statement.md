---
title: GoTo 陳述式
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
ms.openlocfilehash: 000f6754575bcce6b2d79d85541e755219aca956
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866623"
---
# <a name="goto-statement"></a><span data-ttu-id="bce64-102">GoTo 陳述式</span><span class="sxs-lookup"><span data-stu-id="bce64-102">GoTo Statement</span></span>

<span data-ttu-id="bce64-103">無條件地分支至程式中的指定行。</span><span class="sxs-lookup"><span data-stu-id="bce64-103">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bce64-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="bce64-104">Syntax</span></span>  
  
```vb  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="bce64-105">組件</span><span class="sxs-lookup"><span data-stu-id="bce64-105">Part</span></span>  

 `line`  
 <span data-ttu-id="bce64-106">必要。</span><span class="sxs-lookup"><span data-stu-id="bce64-106">Required.</span></span> <span data-ttu-id="bce64-107">任何行標籤。</span><span class="sxs-lookup"><span data-stu-id="bce64-107">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bce64-108">備註</span><span class="sxs-lookup"><span data-stu-id="bce64-108">Remarks</span></span>  

 <span data-ttu-id="bce64-109">`GoTo`語句只能分支至其出現程式中的行。</span><span class="sxs-lookup"><span data-stu-id="bce64-109">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="bce64-110">這一行必須有可以參考的行標籤 `GoTo` 。</span><span class="sxs-lookup"><span data-stu-id="bce64-110">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="bce64-111">如需詳細資訊，請參閱 [如何：標記語句](../../programming-guide/program-structure/how-to-label-statements.md)。</span><span class="sxs-lookup"><span data-stu-id="bce64-111">For more information, see [How to: Label Statements](../../programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bce64-112">`GoTo` 語句可能使程式碼難以讀取和維護。</span><span class="sxs-lookup"><span data-stu-id="bce64-112">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="bce64-113">可能的話，請改用控制項結構。</span><span class="sxs-lookup"><span data-stu-id="bce64-113">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="bce64-114">如需詳細資訊，請參閱 [控制流程](../../programming-guide/language-features/control-flow/index.md)。</span><span class="sxs-lookup"><span data-stu-id="bce64-114">For more information, see [Control Flow](../../programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="bce64-115">您無法使用 `GoTo` 語句從外部 `For` `Next` `For Each` `Next` `SyncLock` `End SyncLock` `Try` 進行分支 ...、...、...、...。 `Catch`...、... `Finally` `With` `End With` 或 `Using` ... `End Using` 結構的內部標籤。</span><span class="sxs-lookup"><span data-stu-id="bce64-115">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="bce64-116">分支和 Try 結構</span><span class="sxs-lookup"><span data-stu-id="bce64-116">Branching and Try Constructions</span></span>  

 <span data-ttu-id="bce64-117">在 `Try` ... `Catch`...`Finally` 結構，下列規則適用于與語句的分支 `GoTo` 。</span><span class="sxs-lookup"><span data-stu-id="bce64-117">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="bce64-118">封鎖或區域</span><span class="sxs-lookup"><span data-stu-id="bce64-118">Block or region</span></span>|<span data-ttu-id="bce64-119">從外部分支</span><span class="sxs-lookup"><span data-stu-id="bce64-119">Branching in from outside</span></span>|<span data-ttu-id="bce64-120">從內部分支</span><span class="sxs-lookup"><span data-stu-id="bce64-120">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="bce64-121">`Try` 區塊</span><span class="sxs-lookup"><span data-stu-id="bce64-121">`Try` block</span></span>|<span data-ttu-id="bce64-122">僅從 `Catch` 相同結構<sup>1</sup>的區塊</span><span class="sxs-lookup"><span data-stu-id="bce64-122">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="bce64-123">僅在整個結構之外</span><span class="sxs-lookup"><span data-stu-id="bce64-123">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="bce64-124">`Catch` 區塊</span><span class="sxs-lookup"><span data-stu-id="bce64-124">`Catch` block</span></span>|<span data-ttu-id="bce64-125">永不允許</span><span class="sxs-lookup"><span data-stu-id="bce64-125">Never allowed</span></span>|<span data-ttu-id="bce64-126">只有在整個結構之外，或 `Try` 相同結構<sup>1</sup>的區塊</span><span class="sxs-lookup"><span data-stu-id="bce64-126">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="bce64-127">`Finally` 區塊</span><span class="sxs-lookup"><span data-stu-id="bce64-127">`Finally` block</span></span>|<span data-ttu-id="bce64-128">永不允許</span><span class="sxs-lookup"><span data-stu-id="bce64-128">Never allowed</span></span>|<span data-ttu-id="bce64-129">永不允許</span><span class="sxs-lookup"><span data-stu-id="bce64-129">Never allowed</span></span>|  
  
 <span data-ttu-id="bce64-130"><sup>1</sup> （如果 `Try` 有的話 `Catch` ） .。。...`Finally` 結構會內嵌在另一個區塊中， `Catch` 區塊可以 `Try` 在它自己的嵌套層級分支至區塊，但不能分成任何其他 `Try` 區塊。</span><span class="sxs-lookup"><span data-stu-id="bce64-130"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="bce64-131">嵌套的 `Try` ... `Catch`...`Finally` 結構必須完整地包含在 `Try` `Catch` 它所用之結構的或區塊中。</span><span class="sxs-lookup"><span data-stu-id="bce64-131">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="bce64-132">下圖顯示 `Try` 在另一個結構中嵌套的結構。</span><span class="sxs-lookup"><span data-stu-id="bce64-132">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="bce64-133">兩個結構的區塊之間的各種分支都會表示為有效或無效。</span><span class="sxs-lookup"><span data-stu-id="bce64-133">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 ![Try 語法結構中的分支示意圖](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a><span data-ttu-id="bce64-135">範例</span><span class="sxs-lookup"><span data-stu-id="bce64-135">Example</span></span>  

 <span data-ttu-id="bce64-136">下列範例會使用 `GoTo` 語句來分支至程式中的行標籤。</span><span class="sxs-lookup"><span data-stu-id="bce64-136">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="bce64-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bce64-137">See also</span></span>

- [<span data-ttu-id="bce64-138">Do...Loop 陳述式</span><span class="sxs-lookup"><span data-stu-id="bce64-138">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="bce64-139">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="bce64-139">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="bce64-140">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="bce64-140">For Each...Next Statement</span></span>](for-each-next-statement.md)
- [<span data-ttu-id="bce64-141">If...Then...Else 陳述式</span><span class="sxs-lookup"><span data-stu-id="bce64-141">If...Then...Else Statement</span></span>](if-then-else-statement.md)
- [<span data-ttu-id="bce64-142">Select...Case 陳述式</span><span class="sxs-lookup"><span data-stu-id="bce64-142">Select...Case Statement</span></span>](select-case-statement.md)
- [<span data-ttu-id="bce64-143">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="bce64-143">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- [<span data-ttu-id="bce64-144">While...End While 陳述式</span><span class="sxs-lookup"><span data-stu-id="bce64-144">While...End While Statement</span></span>](while-end-while-statement.md)
- [<span data-ttu-id="bce64-145">With...End With 陳述式</span><span class="sxs-lookup"><span data-stu-id="bce64-145">With...End With Statement</span></span>](with-end-with-statement.md)
