---
title: Continue 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 9ee5fb19db6eafeb7e4bed12935d0b950d6368d6
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005112"
---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="1d113-102">Continue 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d113-102">Continue Statement (Visual Basic)</span></span>
<span data-ttu-id="1d113-103">立即將控制權轉移到迴圈的下一個反復專案。</span><span class="sxs-lookup"><span data-stu-id="1d113-103">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d113-104">語法</span><span class="sxs-lookup"><span data-stu-id="1d113-104">Syntax</span></span>  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="1d113-105">備註</span><span class="sxs-lookup"><span data-stu-id="1d113-105">Remarks</span></span>  
 <span data-ttu-id="1d113-106">您可以從 `Do`、`For` 或 @no__t 2 迴圈內部傳輸到該迴圈的下一個反復專案。</span><span class="sxs-lookup"><span data-stu-id="1d113-106">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="1d113-107">控制權會立即傳遞至迴圈條件測試，這相當於傳送至 `For` 或 `While` 語句，或包含 `Until` 或 `While` 子句的 `Do` 或 `Loop` 語句。</span><span class="sxs-lookup"><span data-stu-id="1d113-107">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="1d113-108">您可以在允許傳輸的迴圈中的任何位置使用 `Continue`。</span><span class="sxs-lookup"><span data-stu-id="1d113-108">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="1d113-109">允許傳送控制項的規則與[GoTo 語句](../../../visual-basic/language-reference/statements/goto-statement.md)相同。</span><span class="sxs-lookup"><span data-stu-id="1d113-109">The rules allowing transfer of control are the same as with the [GoTo Statement](../../../visual-basic/language-reference/statements/goto-statement.md).</span></span>  
  
 <span data-ttu-id="1d113-110">例如，如果迴圈完全包含在 `Try` 區塊、@no__t 1 區塊或 @no__t 2 區塊中，您可以使用 `Continue` 來傳出迴圈。</span><span class="sxs-lookup"><span data-stu-id="1d113-110">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="1d113-111">另一方面，如果 `Try` ... `End Try` 結構包含在迴圈內，您就不能使用 `Continue` 將控制權轉移出 @no__t 3 區塊，而且只有在您完全轉移完 @no__t 時，才能使用它來傳出 `Try` 或 @no_-5 區塊。_t-6 ... `End Try` 結構。</span><span class="sxs-lookup"><span data-stu-id="1d113-111">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="1d113-112">如果您有相同類型的嵌套迴圈（例如，在另一個 `Do` 迴圈內的 `Do` 迴圈），@no__t 2 語句會跳到包含它的最內層 `Do` 迴圈的下一個反復專案。</span><span class="sxs-lookup"><span data-stu-id="1d113-112">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="1d113-113">您無法使用 `Continue` 來跳至相同類型之包含迴圈的下一個反復專案。</span><span class="sxs-lookup"><span data-stu-id="1d113-113">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="1d113-114">如果您有不同類型的嵌套迴圈（例如，在 @no__t 1 迴圈內的 `Do` 迴圈），您可以使用 `Continue Do` 或 `Continue For`，跳到任一迴圈的下一個反復專案。</span><span class="sxs-lookup"><span data-stu-id="1d113-114">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d113-115">範例</span><span class="sxs-lookup"><span data-stu-id="1d113-115">Example</span></span>  
 <span data-ttu-id="1d113-116">如果除數為零，下列程式碼範例會使用 `Continue While` 語句來跳到陣列的下一個資料行。</span><span class="sxs-lookup"><span data-stu-id="1d113-116">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="1d113-117">@No__t-0 位於 @no__t 1 迴圈內。</span><span class="sxs-lookup"><span data-stu-id="1d113-117">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="1d113-118">它會傳送至 `While col < lastcol` 語句，這是包含 @no__t 2 迴圈的最內層 `While` 迴圈的下一個反復專案。</span><span class="sxs-lookup"><span data-stu-id="1d113-118">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="1d113-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d113-119">See also</span></span>

- [<span data-ttu-id="1d113-120">Do...Loop 陳述式</span><span class="sxs-lookup"><span data-stu-id="1d113-120">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="1d113-121">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="1d113-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="1d113-122">While...End While 陳述式</span><span class="sxs-lookup"><span data-stu-id="1d113-122">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="1d113-123">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="1d113-123">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
