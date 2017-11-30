---
title: "Resume 陳述式"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3cb4334f302c07c81b6b8a7d0626be08cc69b1ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="resume-statement"></a><span data-ttu-id="d76d2-102">Resume 陳述式</span><span class="sxs-lookup"><span data-stu-id="d76d2-102">Resume Statement</span></span>
<span data-ttu-id="d76d2-103">在完成錯誤處理常式之後，請繼續執行。</span><span class="sxs-lookup"><span data-stu-id="d76d2-103">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="d76d2-104">我們建議您使用結構化例外狀況處理，可能的話，程式碼中的，而不是使用非結構化例外狀況處理和`On Error`和`Resume`陳述式。</span><span class="sxs-lookup"><span data-stu-id="d76d2-104">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="d76d2-105">如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="d76d2-105">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d76d2-106">語法</span><span class="sxs-lookup"><span data-stu-id="d76d2-106">Syntax</span></span>  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="d76d2-107">組件</span><span class="sxs-lookup"><span data-stu-id="d76d2-107">Parts</span></span>  
 `Resume`  
 <span data-ttu-id="d76d2-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="d76d2-108">Required.</span></span> <span data-ttu-id="d76d2-109">如果在相同的程序中的錯誤處理常式發生錯誤，造成錯誤的陳述式將會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="d76d2-109">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="d76d2-110">如果呼叫的程序中發生錯誤，在最後一次從程序包含錯誤處理常式呼叫的陳述式會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="d76d2-110">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="d76d2-111">選擇項。</span><span class="sxs-lookup"><span data-stu-id="d76d2-111">Optional.</span></span> <span data-ttu-id="d76d2-112">如果錯誤發生的錯誤處理常式的相同程序中，緊接造成錯誤的陳述式的陳述式將會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="d76d2-112">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="d76d2-113">如果呼叫的程序中發生錯誤，緊跟在最後一次從程序包含錯誤處理常式呼叫的陳述式的陳述式繼續執行 (或`On Error Resume Next`陳述式)。</span><span class="sxs-lookup"><span data-stu-id="d76d2-113">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="d76d2-114">選擇項。</span><span class="sxs-lookup"><span data-stu-id="d76d2-114">Optional.</span></span> <span data-ttu-id="d76d2-115">指定在所需的那一行就會繼續執行`line`引數。</span><span class="sxs-lookup"><span data-stu-id="d76d2-115">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="d76d2-116">`line`引數是行標籤或行號，且必須位於相同的程序的錯誤處理常式。</span><span class="sxs-lookup"><span data-stu-id="d76d2-116">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d76d2-117">備註</span><span class="sxs-lookup"><span data-stu-id="d76d2-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d76d2-118">我們建議您使用結構化例外狀況處理，可能的話，程式碼中的，而不是使用非結構化例外狀況處理和`On Error`和`Resume`陳述式。</span><span class="sxs-lookup"><span data-stu-id="d76d2-118">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="d76d2-119">如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="d76d2-119">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="d76d2-120">如果您使用`Resume`陳述式中任何位置以外的錯誤處理常式中，會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="d76d2-120">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="d76d2-121">`Resume`陳述式不能包含任何程序在`Try...Catch...Finally`陳述式。</span><span class="sxs-lookup"><span data-stu-id="d76d2-121">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d76d2-122">範例</span><span class="sxs-lookup"><span data-stu-id="d76d2-122">Example</span></span>  
 <span data-ttu-id="d76d2-123">這個範例會使用`Resume`結束處理程序中的錯誤，然後再繼續執行造成此錯誤的陳述式的陳述式。</span><span class="sxs-lookup"><span data-stu-id="d76d2-123">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="d76d2-124">錯誤號碼 55 產生來說明使用`Resume`陳述式。</span><span class="sxs-lookup"><span data-stu-id="d76d2-124">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#16](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/resume-statement_1.vb)]  
  
## <a name="requirements"></a><span data-ttu-id="d76d2-125">需求</span><span class="sxs-lookup"><span data-stu-id="d76d2-125">Requirements</span></span>  
 <span data-ttu-id="d76d2-126">**命名空間：** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="d76d2-126">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="d76d2-127">**組件：** Visual Basic Runtime Library （位於 Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="d76d2-127">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d76d2-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d76d2-128">See Also</span></span>  
 [<span data-ttu-id="d76d2-129">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="d76d2-129">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="d76d2-130">Error 陳述式</span><span class="sxs-lookup"><span data-stu-id="d76d2-130">Error Statement</span></span>](../../../visual-basic/language-reference/statements/error-statement.md)  
 [<span data-ttu-id="d76d2-131">On Error 陳述式</span><span class="sxs-lookup"><span data-stu-id="d76d2-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
