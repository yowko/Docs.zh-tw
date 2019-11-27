---
title: 迴圈結構
ms.date: 07/20/2015
helpviewer_keywords:
- control flow [Visual Basic], loops
- For keyword [Visual Basic], loop structures
- loops
- loop structures [Visual Basic]
- statements [Visual Basic], loop
- Do statement [Visual Basic], Do loops
- conditional statements [Visual Basic], loop structures
ms.assetid: ecacb09b-a4c9-42be-98b2-a15d368b5db8
ms.openlocfilehash: 0a75205a7d52c332094d624d082e5db3e89447f5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353920"
---
# <a name="loop-structures-visual-basic"></a><span data-ttu-id="ade4f-102">迴圈結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ade4f-102">Loop Structures (Visual Basic)</span></span>
<span data-ttu-id="ade4f-103">Visual Basic 迴圈結構可讓您重複執行一或多行程式碼。</span><span class="sxs-lookup"><span data-stu-id="ade4f-103">Visual Basic loop structures allow you to run one or more lines of code repetitively.</span></span> <span data-ttu-id="ade4f-104">您可以重複迴圈結構中的語句，直到 `True`條件，直到 `False`條件、指定的次數，或集合中的每個元素一次為止。</span><span class="sxs-lookup"><span data-stu-id="ade4f-104">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span></span>  
  
 <span data-ttu-id="ade4f-105">下圖顯示執行一組語句直到條件變成 true 為止的迴圈結構：</span><span class="sxs-lookup"><span data-stu-id="ade4f-105">The following illustration shows a loop structure that runs a set of statements until a condition becomes true:</span></span>  
  
 ![顯示 [...] 的流程圖Until 迴圈。](./media/loop-structures/do-until-loop-true-condition.gif)  
  
## <a name="while-loops"></a><span data-ttu-id="ade4f-107">While 迴圈</span><span class="sxs-lookup"><span data-stu-id="ade4f-107">While Loops</span></span>  
 <span data-ttu-id="ade4f-108">只要 `True``While` 語句中指定的條件，`While`...`End While` 結構就會執行一組語句。</span><span class="sxs-lookup"><span data-stu-id="ade4f-108">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span></span> <span data-ttu-id="ade4f-109">如需詳細資訊，請參閱[While .。。End While 語句](../../../../visual-basic/language-reference/statements/while-end-while-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ade4f-109">For more information, see [While...End While Statement](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span></span>  
  
## <a name="do-loops"></a><span data-ttu-id="ade4f-110">Do 迴圈</span><span class="sxs-lookup"><span data-stu-id="ade4f-110">Do Loops</span></span>  
 <span data-ttu-id="ade4f-111">`Do`...`Loop` 結構可讓您測試迴圈結構開頭或結尾的條件。</span><span class="sxs-lookup"><span data-stu-id="ade4f-111">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span></span> <span data-ttu-id="ade4f-112">您也可以指定是否要在條件保持 `True` 時重複迴圈，或直到它變成 `True`為止。</span><span class="sxs-lookup"><span data-stu-id="ade4f-112">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span></span> <span data-ttu-id="ade4f-113">如需詳細資訊，請參閱[Do .。。Loop 語句](../../../../visual-basic/language-reference/statements/do-loop-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ade4f-113">For more information, see [Do...Loop Statement](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="for-loops"></a><span data-ttu-id="ade4f-114">For 迴圈</span><span class="sxs-lookup"><span data-stu-id="ade4f-114">For Loops</span></span>  
 <span data-ttu-id="ade4f-115">`For`...`Next` 結構會執行迴圈一組設定的次數。</span><span class="sxs-lookup"><span data-stu-id="ade4f-115">The `For`...`Next` construction performs the loop a set number of times.</span></span> <span data-ttu-id="ade4f-116">它會使用迴圈控制變數（也稱為*計數器*）來追蹤重複項。</span><span class="sxs-lookup"><span data-stu-id="ade4f-116">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span></span> <span data-ttu-id="ade4f-117">您可指定此計數器的開始和結束值，也可以選擇性地指定從一個重複到下一個的增加量。</span><span class="sxs-lookup"><span data-stu-id="ade4f-117">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span></span> <span data-ttu-id="ade4f-118">如需詳細資訊，請參閱[For .。。下一個語句](../../../../visual-basic/language-reference/statements/for-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ade4f-118">For more information, see [For...Next Statement](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
## <a name="for-each-loops"></a><span data-ttu-id="ade4f-119">針對每個迴圈</span><span class="sxs-lookup"><span data-stu-id="ade4f-119">For Each Loops</span></span>  
 <span data-ttu-id="ade4f-120">`For Each`...`Next` 結構會針對集合中的每個元素執行一組語句。</span><span class="sxs-lookup"><span data-stu-id="ade4f-120">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span></span> <span data-ttu-id="ade4f-121">您可以指定迴圈控制變數，但是您不需要決定它的開始或結束值。</span><span class="sxs-lookup"><span data-stu-id="ade4f-121">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span></span> <span data-ttu-id="ade4f-122">如需詳細資訊，請參閱[For Each .。。下一個語句](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ade4f-122">For more information, see [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ade4f-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="ade4f-123">See also</span></span>

- [<span data-ttu-id="ade4f-124">控制流程</span><span class="sxs-lookup"><span data-stu-id="ade4f-124">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="ade4f-125">決策結構</span><span class="sxs-lookup"><span data-stu-id="ade4f-125">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="ade4f-126">其他控制結構</span><span class="sxs-lookup"><span data-stu-id="ade4f-126">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="ade4f-127">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="ade4f-127">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
