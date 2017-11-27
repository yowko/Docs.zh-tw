---
title: "Continue 陳述式 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4a47819600a6c1d58f09c2f8ed3443632e9dab68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="4f595-102">Continue 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f595-102">Continue Statement (Visual Basic)</span></span>
<span data-ttu-id="4f595-103">將控制權立即迴圈的下一個反覆項目。</span><span class="sxs-lookup"><span data-stu-id="4f595-103">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f595-104">語法</span><span class="sxs-lookup"><span data-stu-id="4f595-104">Syntax</span></span>  
  
```  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="4f595-105">備註</span><span class="sxs-lookup"><span data-stu-id="4f595-105">Remarks</span></span>  
 <span data-ttu-id="4f595-106">您可以從傳輸內`Do`， `For`，或`While`迴圈，該迴圈的下一個反覆項目。</span><span class="sxs-lookup"><span data-stu-id="4f595-106">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="4f595-107">控制會傳遞給迴圈的條件測試，這相當於將傳送至立即`For`或`While`陳述式，或`Do`或`Loop`包含陳述式`Until`或`While`子句。</span><span class="sxs-lookup"><span data-stu-id="4f595-107">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="4f595-108">您可以使用`Continue`允許傳輸的迴圈中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="4f595-108">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="4f595-109">允許將控制項的規則是與使用相同[GoTo 陳述式](../../../visual-basic/language-reference/statements/goto-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="4f595-109">The rules allowing transfer of control are the same as with the [GoTo Statement](../../../visual-basic/language-reference/statements/goto-statement.md).</span></span>  
  
 <span data-ttu-id="4f595-110">比方說，如果迴圈是完全包含在`Try`區塊，`Catch`區塊，或`Finally`區塊中，您可以使用`Continue`迴圈之外傳輸。</span><span class="sxs-lookup"><span data-stu-id="4f595-110">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="4f595-111">另一方面，如果`Try`...`End Try`結構是否包含在迴圈中，您無法使用`Continue`傳輸超出控制項`Finally`區塊，以及您可以使用它來傳送出`Try`或`Catch`完全轉移出時才會封鎖`Try`...`End Try`結構。</span><span class="sxs-lookup"><span data-stu-id="4f595-111">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="4f595-112">如果您有巢狀的迴圈屬於相同的類型，例如`Do`另迴圈內`Do`迴圈，`Continue Do`陳述式會略過的最內層的下一個反覆運算`Do`包含它的迴圈。</span><span class="sxs-lookup"><span data-stu-id="4f595-112">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="4f595-113">您無法使用`Continue`跳至包含相同類型的迴圈的下一個反覆項目。</span><span class="sxs-lookup"><span data-stu-id="4f595-113">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="4f595-114">如果您有巢狀的迴圈的不同型別，例如`Do`迴圈內`For`迴圈中，您可以使用跳至其中一個迴圈的下一個反覆運算`Continue Do`或`Continue For`。</span><span class="sxs-lookup"><span data-stu-id="4f595-114">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f595-115">範例</span><span class="sxs-lookup"><span data-stu-id="4f595-115">Example</span></span>  
 <span data-ttu-id="4f595-116">下列程式碼範例使用`Continue While`陳述式跳至下一個資料行的陣列，如果除數為零。</span><span class="sxs-lookup"><span data-stu-id="4f595-116">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="4f595-117">`Continue While`位於`For`迴圈。</span><span class="sxs-lookup"><span data-stu-id="4f595-117">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="4f595-118">它會傳送到`While col < lastcol`陳述式，這是最內層的下一個反覆運算`While`迴圈，其中包含`For`迴圈。</span><span class="sxs-lookup"><span data-stu-id="4f595-118">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/continue-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4f595-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f595-119">See Also</span></span>  
 [<span data-ttu-id="4f595-120">Do...Loop 陳述式</span><span class="sxs-lookup"><span data-stu-id="4f595-120">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [<span data-ttu-id="4f595-121">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="4f595-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="4f595-122">While...End While 陳述式</span><span class="sxs-lookup"><span data-stu-id="4f595-122">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [<span data-ttu-id="4f595-123">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="4f595-123">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
