---
title: Resume 語句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Resume
- vb.ResumeNext
helpviewer_keywords:
- Next statement [Visual Basic], Resume
- Resume Next statement [Visual Basic]
- execution [Visual Basic], resuming
- run-time errors [Visual Basic], resuming after
- Resume statement [Visual Basic], syntax
- errors [Visual Basic], resuming after
- Error statement [Visual Basic], and Resume statement
- execution
- Resume statement [Visual Basic]
ms.assetid: e24d058b-1a5c-4274-acb9-7d295d3ea537
ms.openlocfilehash: 884bdaa0c19508b5a6bf6377568a53acc6880518
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957683"
---
# <a name="resume-statement"></a><span data-ttu-id="b79db-102">Resume 陳述式</span><span class="sxs-lookup"><span data-stu-id="b79db-102">Resume Statement</span></span>
<span data-ttu-id="b79db-103">在錯誤處理常式完成後繼續執行。</span><span class="sxs-lookup"><span data-stu-id="b79db-103">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="b79db-104">我們建議您盡可能在程式碼中使用結構化例外狀況處理, 而不是使用非結構化`On Error`例外`Resume`狀況處理和和語句。</span><span class="sxs-lookup"><span data-stu-id="b79db-104">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="b79db-105">如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b79db-105">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b79db-106">語法</span><span class="sxs-lookup"><span data-stu-id="b79db-106">Syntax</span></span>  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="b79db-107">組件</span><span class="sxs-lookup"><span data-stu-id="b79db-107">Parts</span></span>  
 `Resume`  
 <span data-ttu-id="b79db-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="b79db-108">Required.</span></span> <span data-ttu-id="b79db-109">如果錯誤發生在與錯誤處理常式相同的程式中, 則會繼續執行與造成錯誤的語句。</span><span class="sxs-lookup"><span data-stu-id="b79db-109">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="b79db-110">如果錯誤發生在被呼叫的程式中, 則會在最後一次從包含錯誤處理常式的程式中呼叫的語句繼續執行。</span><span class="sxs-lookup"><span data-stu-id="b79db-110">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="b79db-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="b79db-111">Optional.</span></span> <span data-ttu-id="b79db-112">如果錯誤發生在與錯誤處理常式相同的程式中, 則會以緊接在造成錯誤的語句之後的語句繼續執行。</span><span class="sxs-lookup"><span data-stu-id="b79db-112">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="b79db-113">如果錯誤發生在被呼叫的程式中, 則會繼續執行, 語句緊接在最後一次從包含錯誤處理常式 (或`On Error Resume Next`語句) 的程式所呼叫的語句之後。</span><span class="sxs-lookup"><span data-stu-id="b79db-113">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="b79db-114">選擇性。</span><span class="sxs-lookup"><span data-stu-id="b79db-114">Optional.</span></span> <span data-ttu-id="b79db-115">執行會在必要`line`引數中指定的那一行繼續進行。</span><span class="sxs-lookup"><span data-stu-id="b79db-115">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="b79db-116">`line`引數是行標籤或行號, 而且必須與錯誤處理常式位於相同的程式中。</span><span class="sxs-lookup"><span data-stu-id="b79db-116">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b79db-117">備註</span><span class="sxs-lookup"><span data-stu-id="b79db-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b79db-118">我們建議您盡可能在程式碼中使用結構化例外狀況處理, 而不是使用非結構化`On Error`例外`Resume`狀況處理和和語句。</span><span class="sxs-lookup"><span data-stu-id="b79db-118">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="b79db-119">如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b79db-119">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="b79db-120">如果您在錯誤`Resume`處理常式以外的任何地方使用語句, 就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="b79db-120">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="b79db-121">語句不能用在`Try...Catch...Finally`包含語句的任何程式中。 `Resume`</span><span class="sxs-lookup"><span data-stu-id="b79db-121">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b79db-122">範例</span><span class="sxs-lookup"><span data-stu-id="b79db-122">Example</span></span>  
 <span data-ttu-id="b79db-123">這個範例會使用`Resume`語句來結束程式中的錯誤處理, 然後使用導致錯誤的語句繼續執行。</span><span class="sxs-lookup"><span data-stu-id="b79db-123">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="b79db-124">產生錯誤號碼55以說明`Resume`語句的使用。</span><span class="sxs-lookup"><span data-stu-id="b79db-124">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a><span data-ttu-id="b79db-125">需求</span><span class="sxs-lookup"><span data-stu-id="b79db-125">Requirements</span></span>  
 <span data-ttu-id="b79db-126">**命名空間：** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="b79db-126">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="b79db-127">**Assembly**Visual Basic Runtime Library (位於 Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="b79db-127">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b79db-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b79db-128">See also</span></span>

- [<span data-ttu-id="b79db-129">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="b79db-129">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="b79db-130">Error 陳述式</span><span class="sxs-lookup"><span data-stu-id="b79db-130">Error Statement</span></span>](../../../visual-basic/language-reference/statements/error-statement.md)
- [<span data-ttu-id="b79db-131">On Error 陳述式</span><span class="sxs-lookup"><span data-stu-id="b79db-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
