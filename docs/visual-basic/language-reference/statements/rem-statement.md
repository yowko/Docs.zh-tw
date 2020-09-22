---
title: REM 陳述式
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
ms.openlocfilehash: 6161a9f7e589988882b5f76477bc069afd2b9b41
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871955"
---
# <a name="rem-statement-visual-basic"></a><span data-ttu-id="74091-102">REM 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74091-102">REM Statement (Visual Basic)</span></span>

<span data-ttu-id="74091-103">用來在程式的原始程式碼中包含解釋備註。</span><span class="sxs-lookup"><span data-stu-id="74091-103">Used to include explanatory remarks in the source code of a program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74091-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="74091-104">Syntax</span></span>  
  
```vb  
REM comment  
' comment  
```  
  
## <a name="parts"></a><span data-ttu-id="74091-105">組件</span><span class="sxs-lookup"><span data-stu-id="74091-105">Parts</span></span>  

 `comment`  
 <span data-ttu-id="74091-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="74091-106">Optional.</span></span> <span data-ttu-id="74091-107">您想要包含的任何註解文字。</span><span class="sxs-lookup"><span data-stu-id="74091-107">The text of any comment you want to include.</span></span> <span data-ttu-id="74091-108">關鍵字和之間必須有一個空格 `REM` `comment` 。</span><span class="sxs-lookup"><span data-stu-id="74091-108">A space is required between the `REM` keyword and `comment`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74091-109">備註</span><span class="sxs-lookup"><span data-stu-id="74091-109">Remarks</span></span>  

 <span data-ttu-id="74091-110">您可以單獨將 `REM` 語句放在一行上，也可以將它放在另一個語句後面的一行。</span><span class="sxs-lookup"><span data-stu-id="74091-110">You can put a `REM` statement alone on a line, or you can put it on a line following another statement.</span></span> <span data-ttu-id="74091-111">`REM`語句必須是該行的最後一個語句。</span><span class="sxs-lookup"><span data-stu-id="74091-111">The `REM` statement must be the last statement on the line.</span></span> <span data-ttu-id="74091-112">如果它遵循另一個語句，則 `REM` 必須以空格分隔該語句。</span><span class="sxs-lookup"><span data-stu-id="74091-112">If it follows another statement, the `REM` must be separated from that statement by a space.</span></span>  
  
 <span data-ttu-id="74091-113">您可以使用單引號 (`'`) 而不是 `REM` 。</span><span class="sxs-lookup"><span data-stu-id="74091-113">You can use a single quotation mark (`'`) instead of `REM`.</span></span> <span data-ttu-id="74091-114">無論您的批註是在同一行上的另一個語句之後，還是單獨在一行上，都是如此。</span><span class="sxs-lookup"><span data-stu-id="74091-114">This is true whether your comment follows another statement on the same line or sits alone on a line.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74091-115">您無法 `REM` 使用行接續順序 () 來繼續執行語句 `_` 。</span><span class="sxs-lookup"><span data-stu-id="74091-115">You cannot continue a `REM` statement by using a line-continuation sequence (`_`).</span></span> <span data-ttu-id="74091-116">當批註開始時，編譯器不會檢查字元的特殊意義。</span><span class="sxs-lookup"><span data-stu-id="74091-116">Once a comment begins, the compiler does not examine the characters for special meaning.</span></span> <span data-ttu-id="74091-117">若為多行批註，請 `REM` 在每一行上使用另一個語句或批註符號 (`'`) 。</span><span class="sxs-lookup"><span data-stu-id="74091-117">For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74091-118">範例</span><span class="sxs-lookup"><span data-stu-id="74091-118">Example</span></span>  

 <span data-ttu-id="74091-119">下列範例說明 `REM` 用來在程式中包含說明備註的語句。</span><span class="sxs-lookup"><span data-stu-id="74091-119">The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program.</span></span> <span data-ttu-id="74091-120">它也會顯示使用單引號字元 (`'`) ，而不是的替代方法 `REM` 。</span><span class="sxs-lookup"><span data-stu-id="74091-120">It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.</span></span>  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="74091-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74091-121">See also</span></span>

- [<span data-ttu-id="74091-122">程式碼中的註解</span><span class="sxs-lookup"><span data-stu-id="74091-122">Comments in Code</span></span>](../../programming-guide/program-structure/comments-in-code.md)
- [<span data-ttu-id="74091-123">作法：程式碼中的 Break 及 Combine 陳述式</span><span class="sxs-lookup"><span data-stu-id="74091-123">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
