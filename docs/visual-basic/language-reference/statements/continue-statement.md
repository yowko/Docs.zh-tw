---
title: Continue 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 20140cafb68c7e5518bf3d5fa80e56ca1c1de2c6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354115"
---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="fc36e-102">Continue 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc36e-102">Continue Statement (Visual Basic)</span></span>
<span data-ttu-id="fc36e-103">立即將控制權轉移到迴圈的下一個反復專案。</span><span class="sxs-lookup"><span data-stu-id="fc36e-103">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc36e-104">語法</span><span class="sxs-lookup"><span data-stu-id="fc36e-104">Syntax</span></span>  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="fc36e-105">備註</span><span class="sxs-lookup"><span data-stu-id="fc36e-105">Remarks</span></span>  
 <span data-ttu-id="fc36e-106">您可以從 `Do`、`For`或 `While` 迴圈內部轉移到該迴圈的下一個反復專案。</span><span class="sxs-lookup"><span data-stu-id="fc36e-106">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="fc36e-107">控制權會立即傳遞至迴圈條件測試，這相當於傳送至 `For` 或 `While` 語句，或包含 `Until` 或 `While` 子句的 `Do` 或 `Loop` 語句。</span><span class="sxs-lookup"><span data-stu-id="fc36e-107">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="fc36e-108">您可以使用迴圈中允許傳輸的任何位置上的 `Continue`。</span><span class="sxs-lookup"><span data-stu-id="fc36e-108">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="fc36e-109">允許傳送控制項的規則與[GoTo 語句](../../../visual-basic/language-reference/statements/goto-statement.md)相同。</span><span class="sxs-lookup"><span data-stu-id="fc36e-109">The rules allowing transfer of control are the same as with the [GoTo Statement](../../../visual-basic/language-reference/statements/goto-statement.md).</span></span>  
  
 <span data-ttu-id="fc36e-110">例如，如果迴圈完全包含在 `Try` 區塊、`Catch` 區塊或 `Finally` 區塊中，您可以使用 `Continue` 來傳出迴圈。</span><span class="sxs-lookup"><span data-stu-id="fc36e-110">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="fc36e-111">另一方面，如果 `Try`...`End Try` 結構包含在迴圈內，您就無法使用 `Continue` 從 `Finally` 區塊中轉移控制權，而且只有在您完全從 `Try` 結構傳輸出來時，才可以使用它來傳出 `Catch` 或 `Try`區塊。`End Try`</span><span class="sxs-lookup"><span data-stu-id="fc36e-111">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="fc36e-112">如果您有相同類型的嵌套迴圈（例如，另一個 `Do` 迴圈內的 `Do` 迴圈），`Continue Do` 語句會跳到包含它的最內層 `Do` 迴圈的下一個反復專案。</span><span class="sxs-lookup"><span data-stu-id="fc36e-112">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="fc36e-113">您無法使用 `Continue` 跳到相同類型之包含迴圈的下一個反復專案。</span><span class="sxs-lookup"><span data-stu-id="fc36e-113">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="fc36e-114">如果您有不同類型的嵌套迴圈（例如 `For` 迴圈內的 `Do` 迴圈），您可以使用 `Continue Do` 或 `Continue For`跳到任一迴圈的下一個反復專案。</span><span class="sxs-lookup"><span data-stu-id="fc36e-114">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc36e-115">範例</span><span class="sxs-lookup"><span data-stu-id="fc36e-115">Example</span></span>  
 <span data-ttu-id="fc36e-116">如果除數為零，下列程式碼範例會使用 `Continue While` 語句來跳到陣列的下一個資料行。</span><span class="sxs-lookup"><span data-stu-id="fc36e-116">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="fc36e-117">`Continue While` 是在 `For` 迴圈內。</span><span class="sxs-lookup"><span data-stu-id="fc36e-117">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="fc36e-118">它會傳送至 `While col < lastcol` 語句，這是包含 `For` 迴圈的最內層 `While` 迴圈的下一個反復專案。</span><span class="sxs-lookup"><span data-stu-id="fc36e-118">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="fc36e-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="fc36e-119">See also</span></span>

- [<span data-ttu-id="fc36e-120">Do...Loop 陳述式</span><span class="sxs-lookup"><span data-stu-id="fc36e-120">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="fc36e-121">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="fc36e-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="fc36e-122">While...End While 陳述式</span><span class="sxs-lookup"><span data-stu-id="fc36e-122">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="fc36e-123">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="fc36e-123">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
