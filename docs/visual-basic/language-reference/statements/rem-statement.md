---
title: REM 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
helpviewer_keywords:
- REM statement [Visual Basic]
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
ms.openlocfilehash: 3bd526b08e1ba3be856e1e823cf8ef49ea9b6c97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604272"
---
# <a name="rem-statement-visual-basic"></a><span data-ttu-id="6d88a-102">REM 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d88a-102">REM Statement (Visual Basic)</span></span>
<span data-ttu-id="6d88a-103">用來在程式碼的原始程式碼中包含說明備註。</span><span class="sxs-lookup"><span data-stu-id="6d88a-103">Used to include explanatory remarks in the source code of a program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d88a-104">語法</span><span class="sxs-lookup"><span data-stu-id="6d88a-104">Syntax</span></span>  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a><span data-ttu-id="6d88a-105">組件</span><span class="sxs-lookup"><span data-stu-id="6d88a-105">Parts</span></span>  
 `comment`  
 <span data-ttu-id="6d88a-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="6d88a-106">Optional.</span></span> <span data-ttu-id="6d88a-107">您要包含的任何註解的文字。</span><span class="sxs-lookup"><span data-stu-id="6d88a-107">The text of any comment you want to include.</span></span> <span data-ttu-id="6d88a-108">不需要之間的空間`REM`關鍵字和`comment`。</span><span class="sxs-lookup"><span data-stu-id="6d88a-108">A space is required between the `REM` keyword and `comment`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d88a-109">備註</span><span class="sxs-lookup"><span data-stu-id="6d88a-109">Remarks</span></span>  
 <span data-ttu-id="6d88a-110">您可以放入`REM`陳述式單獨一行，或者您可以將它放在另一個陳述式的一行。</span><span class="sxs-lookup"><span data-stu-id="6d88a-110">You can put a `REM` statement alone on a line, or you can put it on a line following another statement.</span></span> <span data-ttu-id="6d88a-111">`REM`陳述式必須是該行的最後一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="6d88a-111">The `REM` statement must be the last statement on the line.</span></span> <span data-ttu-id="6d88a-112">如果另一個陳述式之後，`REM`必須從該陳述式，以空格分隔。</span><span class="sxs-lookup"><span data-stu-id="6d88a-112">If it follows another statement, the `REM` must be separated from that statement by a space.</span></span>  
  
 <span data-ttu-id="6d88a-113">您可以使用單引號 (`'`) 而不是`REM`。</span><span class="sxs-lookup"><span data-stu-id="6d88a-113">You can use a single quotation mark (`'`) instead of `REM`.</span></span> <span data-ttu-id="6d88a-114">您的註解是否另一個陳述式後面的同一行，或位於單獨的一行，也是如此。</span><span class="sxs-lookup"><span data-stu-id="6d88a-114">This is true whether your comment follows another statement on the same line or sits alone on a line.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d88a-115">您無法繼續`REM`陳述式使用行接續序列 (`_`)。</span><span class="sxs-lookup"><span data-stu-id="6d88a-115">You cannot continue a `REM` statement by using a line-continuation sequence (`_`).</span></span> <span data-ttu-id="6d88a-116">註解開始時，編譯器不會檢查特殊意義的字元。</span><span class="sxs-lookup"><span data-stu-id="6d88a-116">Once a comment begins, the compiler does not examine the characters for special meaning.</span></span> <span data-ttu-id="6d88a-117">對於多行註解，使用另一個`REM`陳述式或註解符號 (`'`) 在每一行。</span><span class="sxs-lookup"><span data-stu-id="6d88a-117">For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d88a-118">範例</span><span class="sxs-lookup"><span data-stu-id="6d88a-118">Example</span></span>  
 <span data-ttu-id="6d88a-119">下列範例說明`REM`陳述式，用來在程式中包含說明備註。</span><span class="sxs-lookup"><span data-stu-id="6d88a-119">The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program.</span></span> <span data-ttu-id="6d88a-120">它也會顯示另一種使用單一的引號字元 (`'`) 而不是`REM`。</span><span class="sxs-lookup"><span data-stu-id="6d88a-120">It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.</span></span>  
  
 [!code-vb[VbVbalrStatements#6](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/rem-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6d88a-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d88a-121">See Also</span></span>  
 [<span data-ttu-id="6d88a-122">程式碼中的註解</span><span class="sxs-lookup"><span data-stu-id="6d88a-122">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 [<span data-ttu-id="6d88a-123">操作說明：在程式碼內中斷和合併陳述式</span><span class="sxs-lookup"><span data-stu-id="6d88a-123">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
