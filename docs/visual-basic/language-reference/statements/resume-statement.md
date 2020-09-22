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
ms.openlocfilehash: db9d47798d087d60f4318b06fe3291fb895e6618
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871871"
---
# <a name="resume-statement"></a><span data-ttu-id="eba2c-102">Resume 陳述式</span><span class="sxs-lookup"><span data-stu-id="eba2c-102">Resume Statement</span></span>

<span data-ttu-id="eba2c-103">在錯誤處理常式完成之後繼續執行。</span><span class="sxs-lookup"><span data-stu-id="eba2c-103">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="eba2c-104">建議您盡可能在程式碼中使用結構化例外狀況處理，而不是使用非結構化例外 `On Error` 狀況處理和和 `Resume` 語句。</span><span class="sxs-lookup"><span data-stu-id="eba2c-104">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="eba2c-105">如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="eba2c-105">For more information, see [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eba2c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="eba2c-106">Syntax</span></span>  
  
```vb  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="eba2c-107">組件</span><span class="sxs-lookup"><span data-stu-id="eba2c-107">Parts</span></span>  

 `Resume`  
 <span data-ttu-id="eba2c-108">必要。</span><span class="sxs-lookup"><span data-stu-id="eba2c-108">Required.</span></span> <span data-ttu-id="eba2c-109">如果錯誤發生在與錯誤處理常式相同的程式中，則會繼續執行並產生錯誤的語句。</span><span class="sxs-lookup"><span data-stu-id="eba2c-109">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="eba2c-110">如果在呼叫的程式中發生錯誤，則會在最後從包含錯誤處理常式的程式中呼叫的語句繼續執行。</span><span class="sxs-lookup"><span data-stu-id="eba2c-110">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="eba2c-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="eba2c-111">Optional.</span></span> <span data-ttu-id="eba2c-112">如果錯誤發生在與錯誤處理常式相同的程式中，則會以緊接在引發錯誤的語句後面的語句繼續執行。</span><span class="sxs-lookup"><span data-stu-id="eba2c-112">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="eba2c-113">如果在被呼叫的程式中發生錯誤，則會繼續執行最後一次從包含錯誤處理常式的程式所呼叫的語句，而不是) 的 (或 `On Error Resume Next` 語句。</span><span class="sxs-lookup"><span data-stu-id="eba2c-113">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="eba2c-114">選擇性。</span><span class="sxs-lookup"><span data-stu-id="eba2c-114">Optional.</span></span> <span data-ttu-id="eba2c-115">執行會在所需的引數中指定的行繼續 `line` 。</span><span class="sxs-lookup"><span data-stu-id="eba2c-115">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="eba2c-116">`line`引數是行標籤或行號，而且必須與錯誤處理常式在相同的程式中。</span><span class="sxs-lookup"><span data-stu-id="eba2c-116">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eba2c-117">備註</span><span class="sxs-lookup"><span data-stu-id="eba2c-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eba2c-118">建議您盡可能在程式碼中使用結構化例外狀況處理，而不是使用非結構化例外 `On Error` 狀況處理和和 `Resume` 語句。</span><span class="sxs-lookup"><span data-stu-id="eba2c-118">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="eba2c-119">如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="eba2c-119">For more information, see [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="eba2c-120">如果您 `Resume` 在錯誤處理常式以外的任何地方使用語句，則會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="eba2c-120">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="eba2c-121">`Resume`語句不能用在包含語句的任何程式中 `Try...Catch...Finally` 。</span><span class="sxs-lookup"><span data-stu-id="eba2c-121">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eba2c-122">範例</span><span class="sxs-lookup"><span data-stu-id="eba2c-122">Example</span></span>  

 <span data-ttu-id="eba2c-123">這則範例會使用 `Resume` 語句來結束程式中的錯誤處理，然後再繼續執行造成錯誤的語句。</span><span class="sxs-lookup"><span data-stu-id="eba2c-123">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="eba2c-124">產生錯誤號碼55，以說明如何使用 `Resume` 語句。</span><span class="sxs-lookup"><span data-stu-id="eba2c-124">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a><span data-ttu-id="eba2c-125">規格需求</span><span class="sxs-lookup"><span data-stu-id="eba2c-125">Requirements</span></span>  

 <span data-ttu-id="eba2c-126">**命名空間：** [Microsoft.](../runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="eba2c-126">**Namespace:** [Microsoft.VisualBasic](../runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="eba2c-127">**元件：** Microsoft.VisualBasic.dll) 中的 Visual Basic 執行時間程式庫 (</span><span class="sxs-lookup"><span data-stu-id="eba2c-127">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eba2c-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eba2c-128">See also</span></span>

- [<span data-ttu-id="eba2c-129">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="eba2c-129">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- [<span data-ttu-id="eba2c-130">Error 陳述式</span><span class="sxs-lookup"><span data-stu-id="eba2c-130">Error Statement</span></span>](error-statement.md)
- [<span data-ttu-id="eba2c-131">On Error 陳述式</span><span class="sxs-lookup"><span data-stu-id="eba2c-131">On Error Statement</span></span>](on-error-statement.md)
