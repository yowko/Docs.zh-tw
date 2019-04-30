---
title: 錯誤類型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors [Visual Basic], Visual Basic
- run-time errors [Visual Basic], types of errors
- syntax errors [Visual Basic], Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
ms.openlocfilehash: 07db963ac3cf9d1c0d17c420480189d362cdaf2c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973169"
---
# <a name="error-types-visual-basic"></a><span data-ttu-id="650b5-102">錯誤類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="650b5-102">Error Types (Visual Basic)</span></span>
<span data-ttu-id="650b5-103">在 Visual Basic 中的錯誤 (也稱為*例外狀況*) 分為三類： 語法錯誤、 執行階段錯誤，以及邏輯錯誤。</span><span class="sxs-lookup"><span data-stu-id="650b5-103">In Visual Basic, errors (also called *exceptions*) fall into one of three categories: syntax errors, run-time errors, and logic errors.</span></span>  
  
## <a name="syntax-errors"></a><span data-ttu-id="650b5-104">語法錯誤</span><span class="sxs-lookup"><span data-stu-id="650b5-104">Syntax Errors</span></span>  
 <span data-ttu-id="650b5-105">*語法錯誤*是指您撰寫程式碼時出現。</span><span class="sxs-lookup"><span data-stu-id="650b5-105">*Syntax errors* are those that appear while you write code.</span></span> <span data-ttu-id="650b5-106">Visual Basic 會檢查您的程式碼，在您輸入時所**程式碼編輯器**視窗，提醒您，如果您犯了錯誤，例如拼錯字，或不當使用語言項目。</span><span class="sxs-lookup"><span data-stu-id="650b5-106">Visual Basic checks your code as you type it in the **Code Editor** window and alerts you if you make a mistake, such as misspelling a word or using a language element improperly.</span></span> <span data-ttu-id="650b5-107">語法錯誤是最常見的錯誤類型。</span><span class="sxs-lookup"><span data-stu-id="650b5-107">Syntax errors are the most common type of errors.</span></span> <span data-ttu-id="650b5-108">修正方式輕鬆地在程式碼撰寫環境中，它們就會發生。</span><span class="sxs-lookup"><span data-stu-id="650b5-108">You can fix them easily in the coding environment as soon as they occur.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="650b5-109">`Option Explicit`陳述式是一種避免發生語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="650b5-109">The `Option Explicit` statement is one means of avoiding syntax errors.</span></span> <span data-ttu-id="650b5-110">它會強制您預先宣告的應用程式中使用的所有變數。</span><span class="sxs-lookup"><span data-stu-id="650b5-110">It forces you to declare, in advance, all the variables to be used in the application.</span></span> <span data-ttu-id="650b5-111">因此，當程式碼中使用這些變數，印刷樣式的任何錯誤立即發現，而且可以修正。</span><span class="sxs-lookup"><span data-stu-id="650b5-111">Therefore, when those variables are used in the code, any typographic errors are caught immediately and can be fixed.</span></span>  
  
## <a name="run-time-errors"></a><span data-ttu-id="650b5-112">執行階段錯誤</span><span class="sxs-lookup"><span data-stu-id="650b5-112">Run-Time Errors</span></span>  
 <span data-ttu-id="650b5-113">*執行階段錯誤*是指您編譯並執行您的程式碼時，才會出現。</span><span class="sxs-lookup"><span data-stu-id="650b5-113">*Run-time errors* are those that appear only after you compile and run your code.</span></span> <span data-ttu-id="650b5-114">這些轉換可能會顯示為正確，因為它沒有任何語法錯誤，但卻無法執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="650b5-114">These involve code that may appear to be correct in that it has no syntax errors, but that will not execute.</span></span> <span data-ttu-id="650b5-115">例如，您可以正確撰寫一行程式碼，以開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="650b5-115">For example, you might correctly write a line of code to open a file.</span></span> <span data-ttu-id="650b5-116">如果檔案已損毀，無法執行應用程式，但`Open`函式，而且它會停止執行。</span><span class="sxs-lookup"><span data-stu-id="650b5-116">But if the file is corrupted, the application cannot carry out the `Open` function, and it stops running.</span></span> <span data-ttu-id="650b5-117">您可以重寫程式碼，然後重新編譯並重新執行它，就可修正大部分的執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="650b5-117">You can fix most run-time errors by rewriting the faulty code, and then recompiling and rerunning it.</span></span>  
  
## <a name="logic-errors"></a><span data-ttu-id="650b5-118">邏輯錯誤</span><span class="sxs-lookup"><span data-stu-id="650b5-118">Logic Errors</span></span>  
 <span data-ttu-id="650b5-119">*邏輯錯誤*是指應用程式在使用時出現。</span><span class="sxs-lookup"><span data-stu-id="650b5-119">*Logic errors* are those that appear once the application is in use.</span></span> <span data-ttu-id="650b5-120">也就是回應使用者動作的大部分通常不必要或非預期結果。</span><span class="sxs-lookup"><span data-stu-id="650b5-120">They are most often unwanted or unexpected results in response to user actions.</span></span> <span data-ttu-id="650b5-121">例如，輸入錯誤的索引鍵或其他外部的影響可能會導致您的應用程式停止運作中預期的參數，或完全。</span><span class="sxs-lookup"><span data-stu-id="650b5-121">For example, a mistyped key or other outside influence might cause your application to stop working within expected parameters, or altogether.</span></span> <span data-ttu-id="650b5-122">邏輯錯誤通常是最困難的型別，若要修正，因為它不一定清楚其來源。</span><span class="sxs-lookup"><span data-stu-id="650b5-122">Logic errors are generally the hardest type to fix, since it is not always clear where they originate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="650b5-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="650b5-123">See also</span></span>

- [<span data-ttu-id="650b5-124">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="650b5-124">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="650b5-125">偵錯工具基礎</span><span class="sxs-lookup"><span data-stu-id="650b5-125">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)
