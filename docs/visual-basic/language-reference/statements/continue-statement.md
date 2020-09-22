---
title: Continue 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: cf73ea1b3d402609c9966980dcab9ddd9bc096c2
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874970"
---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="c78e9-102">Continue 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c78e9-102">Continue Statement (Visual Basic)</span></span>

<span data-ttu-id="c78e9-103">立即將控制權轉移到迴圈的下一個反復專案。</span><span class="sxs-lookup"><span data-stu-id="c78e9-103">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c78e9-104">語法</span><span class="sxs-lookup"><span data-stu-id="c78e9-104">Syntax</span></span>  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="c78e9-105">備註</span><span class="sxs-lookup"><span data-stu-id="c78e9-105">Remarks</span></span>  

 <span data-ttu-id="c78e9-106">您可以從 `Do` 、 `For` 或迴圈內傳送 `While` 至該迴圈的下一個反復專案。</span><span class="sxs-lookup"><span data-stu-id="c78e9-106">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="c78e9-107">控制權會立即傳遞給迴圈條件測試，這相當於傳送至 `For` 或 `While` 語句，或是 `Do` `Loop` 包含或子句的或語句 `Until` `While` 。</span><span class="sxs-lookup"><span data-stu-id="c78e9-107">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="c78e9-108">您可以在 `Continue` 迴圈中允許傳送的任何位置使用。</span><span class="sxs-lookup"><span data-stu-id="c78e9-108">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="c78e9-109">允許傳送控制權的規則和 [GoTo 語句](goto-statement.md)相同。</span><span class="sxs-lookup"><span data-stu-id="c78e9-109">The rules allowing transfer of control are the same as with the [GoTo Statement](goto-statement.md).</span></span>  
  
 <span data-ttu-id="c78e9-110">例如，如果迴圈完全包含在 `Try` 區塊、 `Catch` 區塊或區塊內， `Finally` 您可以使用 `Continue` 來傳出迴圈。</span><span class="sxs-lookup"><span data-stu-id="c78e9-110">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="c78e9-111">另一方面，如果 `Try` ... `End Try` 結構包含在迴圈內，您就無法使用 `Continue` 將控制權傳送到 `Finally` 區塊中，而且 `Try` `Catch` 只有在您從 `Try` ... 結構完全傳輸時，才能使用它來傳出或封鎖 `End Try` 。</span><span class="sxs-lookup"><span data-stu-id="c78e9-111">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="c78e9-112">如果您有相同類型的嵌套迴圈，例如 `Do` 另一個迴圈中的迴圈 `Do` ，語句會 `Continue Do` 跳到包含它的最內層迴圈的下一個反復專案 `Do` 。</span><span class="sxs-lookup"><span data-stu-id="c78e9-112">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="c78e9-113">您不可以使用 `Continue` 跳到相同類型之包含迴圈的下一個反復專案。</span><span class="sxs-lookup"><span data-stu-id="c78e9-113">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="c78e9-114">如果您有不同類型的嵌套迴圈，例如 `Do` 迴圈內的迴圈 `For` ，您可以使用或，跳到任一個迴圈的下一個反覆運算 `Continue Do` `Continue For` 。</span><span class="sxs-lookup"><span data-stu-id="c78e9-114">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c78e9-115">範例</span><span class="sxs-lookup"><span data-stu-id="c78e9-115">Example</span></span>  

 <span data-ttu-id="c78e9-116">下列程式碼範例會使用 `Continue While` 語句來跳至陣列中的下一個資料行（如果除數為零）。</span><span class="sxs-lookup"><span data-stu-id="c78e9-116">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="c78e9-117">在 `Continue While` `For` 迴圈內。</span><span class="sxs-lookup"><span data-stu-id="c78e9-117">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="c78e9-118">它會傳送至 `While col < lastcol` 語句，這是包含迴圈之最內層迴圈的下一個反復專案 `While` `For` 。</span><span class="sxs-lookup"><span data-stu-id="c78e9-118">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="c78e9-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c78e9-119">See also</span></span>

- [<span data-ttu-id="c78e9-120">Do...Loop 陳述式</span><span class="sxs-lookup"><span data-stu-id="c78e9-120">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="c78e9-121">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="c78e9-121">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="c78e9-122">While...End While 陳述式</span><span class="sxs-lookup"><span data-stu-id="c78e9-122">While...End While Statement</span></span>](while-end-while-statement.md)
- [<span data-ttu-id="c78e9-123">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="c78e9-123">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
