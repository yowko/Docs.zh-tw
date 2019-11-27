---
title: Resume 陳述式
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
ms.openlocfilehash: 95137a9f6a4a4a18655b51b95300bfaf93cca193
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333021"
---
# <a name="resume-statement"></a><span data-ttu-id="75c8b-102">Resume 陳述式</span><span class="sxs-lookup"><span data-stu-id="75c8b-102">Resume Statement</span></span>
<span data-ttu-id="75c8b-103">在錯誤處理常式完成後繼續執行。</span><span class="sxs-lookup"><span data-stu-id="75c8b-103">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="75c8b-104">我們建議您盡可能在程式碼中使用結構化例外狀況處理，而不是使用非結構化例外處理和 `On Error` 和 `Resume` 語句。</span><span class="sxs-lookup"><span data-stu-id="75c8b-104">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="75c8b-105">如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="75c8b-105">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75c8b-106">語法</span><span class="sxs-lookup"><span data-stu-id="75c8b-106">Syntax</span></span>  
  
```vb  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="75c8b-107">組件</span><span class="sxs-lookup"><span data-stu-id="75c8b-107">Parts</span></span>  
 `Resume`  
 <span data-ttu-id="75c8b-108">必要。</span><span class="sxs-lookup"><span data-stu-id="75c8b-108">Required.</span></span> <span data-ttu-id="75c8b-109">如果錯誤發生在與錯誤處理常式相同的程式中，則會繼續執行與造成錯誤的語句。</span><span class="sxs-lookup"><span data-stu-id="75c8b-109">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="75c8b-110">如果錯誤發生在被呼叫的程式中，則會在最後一次從包含錯誤處理常式的程式中呼叫的語句繼續執行。</span><span class="sxs-lookup"><span data-stu-id="75c8b-110">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="75c8b-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="75c8b-111">Optional.</span></span> <span data-ttu-id="75c8b-112">如果錯誤發生在與錯誤處理常式相同的程式中，則會以緊接在造成錯誤的語句之後的語句繼續執行。</span><span class="sxs-lookup"><span data-stu-id="75c8b-112">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="75c8b-113">如果錯誤發生在被呼叫的程式中，則會繼續執行，並緊接在最後一次從包含錯誤處理常式（或 `On Error Resume Next` 語句）的程式所呼叫的語句之後。</span><span class="sxs-lookup"><span data-stu-id="75c8b-113">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="75c8b-114">選擇性。</span><span class="sxs-lookup"><span data-stu-id="75c8b-114">Optional.</span></span> <span data-ttu-id="75c8b-115">執行會在所需的 `line` 引數中指定的那一行繼續進行。</span><span class="sxs-lookup"><span data-stu-id="75c8b-115">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="75c8b-116">`line` 引數是行標籤或行號，而且必須與錯誤處理常式位於相同的程式中。</span><span class="sxs-lookup"><span data-stu-id="75c8b-116">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75c8b-117">備註</span><span class="sxs-lookup"><span data-stu-id="75c8b-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="75c8b-118">我們建議您盡可能在程式碼中使用結構化例外狀況處理，而不要使用非結構化例外處理和 `On Error` 和 `Resume` 語句。</span><span class="sxs-lookup"><span data-stu-id="75c8b-118">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="75c8b-119">如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="75c8b-119">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="75c8b-120">如果您在錯誤處理常式以外的任何地方使用 `Resume` 語句，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="75c8b-120">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="75c8b-121">`Resume` 語句不能用在包含 `Try...Catch...Finally` 語句的任何程式中。</span><span class="sxs-lookup"><span data-stu-id="75c8b-121">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75c8b-122">範例</span><span class="sxs-lookup"><span data-stu-id="75c8b-122">Example</span></span>  
 <span data-ttu-id="75c8b-123">這個範例會使用 `Resume` 語句來結束程式中的錯誤處理，然後使用導致錯誤的語句繼續執行。</span><span class="sxs-lookup"><span data-stu-id="75c8b-123">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="75c8b-124">產生錯誤號碼55，以說明如何使用 `Resume` 語句。</span><span class="sxs-lookup"><span data-stu-id="75c8b-124">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a><span data-ttu-id="75c8b-125">需求</span><span class="sxs-lookup"><span data-stu-id="75c8b-125">Requirements</span></span>  
 <span data-ttu-id="75c8b-126">**命名空間：** [Microsoft.](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="75c8b-126">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="75c8b-127">**元件：** Visual Basic 執行時間程式庫（在 Microsoft 中）</span><span class="sxs-lookup"><span data-stu-id="75c8b-127">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75c8b-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="75c8b-128">See also</span></span>

- [<span data-ttu-id="75c8b-129">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="75c8b-129">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="75c8b-130">Error 陳述式</span><span class="sxs-lookup"><span data-stu-id="75c8b-130">Error Statement</span></span>](../../../visual-basic/language-reference/statements/error-statement.md)
- [<span data-ttu-id="75c8b-131">On Error 陳述式</span><span class="sxs-lookup"><span data-stu-id="75c8b-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
