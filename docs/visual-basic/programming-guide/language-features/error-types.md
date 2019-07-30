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
ms.openlocfilehash: 030986111a50ab59c605a1d683fedc118d10b260
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626608"
---
# <a name="error-types-visual-basic"></a><span data-ttu-id="9bde6-102">錯誤類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9bde6-102">Error Types (Visual Basic)</span></span>
<span data-ttu-id="9bde6-103">在 Visual Basic 中, 錯誤會屬於下列三個類別之一: 語法錯誤、執行階段錯誤和邏輯錯誤。</span><span class="sxs-lookup"><span data-stu-id="9bde6-103">In Visual Basic, errors fall into one of three categories: syntax errors, run-time errors, and logic errors.</span></span>

## <a name="syntax-errors"></a><span data-ttu-id="9bde6-104">語法錯誤</span><span class="sxs-lookup"><span data-stu-id="9bde6-104">Syntax Errors</span></span>
 <span data-ttu-id="9bde6-105">*語法錯誤*是您撰寫程式碼時所顯示的錯誤。</span><span class="sxs-lookup"><span data-stu-id="9bde6-105">*Syntax errors* are those that appear while you write code.</span></span> <span data-ttu-id="9bde6-106">如果您使用 Visual Studio, 當您在 [程式**代碼編輯器**] 視窗中輸入程式碼時, Visual Basic 會檢查它, 並在犯錯誤時向您發出警告, 例如拼錯單字或使用 language 元素不正確。</span><span class="sxs-lookup"><span data-stu-id="9bde6-106">If you're using Visual Studio, Visual Basic checks your code as you type it in the **Code Editor** window and alerts you if you make a mistake, such as misspelling a word or using a language element improperly.</span></span> <span data-ttu-id="9bde6-107">如果您從命令列進行編譯, Visual Basic 會顯示編譯器錯誤, 其中包含語法錯誤的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9bde6-107">If you compile from the command line, Visual Basic displays a compiler error with information about the syntax error.</span></span> <span data-ttu-id="9bde6-108">語法錯誤是最常見的錯誤類型。</span><span class="sxs-lookup"><span data-stu-id="9bde6-108">Syntax errors are the most common type of errors.</span></span> <span data-ttu-id="9bde6-109">您可以輕鬆地在程式碼撰寫環境中進行修正。</span><span class="sxs-lookup"><span data-stu-id="9bde6-109">You can fix them easily in the coding environment as soon as they occur.</span></span>

> [!NOTE]
>  <span data-ttu-id="9bde6-110">`Option Explicit`語句是避免語法錯誤的一種方法。</span><span class="sxs-lookup"><span data-stu-id="9bde6-110">The `Option Explicit` statement is one means of avoiding syntax errors.</span></span> <span data-ttu-id="9bde6-111">它會強制您事先宣告要在應用程式中使用的所有變數。</span><span class="sxs-lookup"><span data-stu-id="9bde6-111">It forces you to declare, in advance, all the variables to be used in the application.</span></span> <span data-ttu-id="9bde6-112">因此, 在程式碼中使用這些變數時, 任何印刷樣式錯誤都會立即捕捉, 而且可以修正。</span><span class="sxs-lookup"><span data-stu-id="9bde6-112">Therefore, when those variables are used in the code, any typographic errors are caught immediately and can be fixed.</span></span>

## <a name="run-time-errors"></a><span data-ttu-id="9bde6-113">執行階段錯誤</span><span class="sxs-lookup"><span data-stu-id="9bde6-113">Run-Time Errors</span></span>
 <span data-ttu-id="9bde6-114">*執行階段錯誤*是指只有在您編譯和執行程式碼之後才會出現的錯誤。</span><span class="sxs-lookup"><span data-stu-id="9bde6-114">*Run-time errors* are those that appear only after you compile and run your code.</span></span> <span data-ttu-id="9bde6-115">這些程式碼包含可能正確的程式碼, 因為它沒有任何語法錯誤, 但不會執行。</span><span class="sxs-lookup"><span data-stu-id="9bde6-115">These involve code that may appear to be correct in that it has no syntax errors, but that will not execute.</span></span> <span data-ttu-id="9bde6-116">例如, 您可以正確地撰寫一行程式碼來開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="9bde6-116">For example, you might correctly write a line of code to open a file.</span></span> <span data-ttu-id="9bde6-117">但是, 如果檔案不存在, 應用程式就無法開啟檔案, 而且會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9bde6-117">But if the file does not exist, the application cannot open the file, and it throws an exception.</span></span> <span data-ttu-id="9bde6-118">您可以藉由重寫錯誤的程式碼或使用[例外狀況處理](../../language-reference/statements/try-catch-finally-statement.md)來修正大部分的執行階段錯誤, 然後重新編譯並重新執行它。</span><span class="sxs-lookup"><span data-stu-id="9bde6-118">You can fix most run-time errors by rewriting the faulty code or by using [exception handling](../../language-reference/statements/try-catch-finally-statement.md), and then recompiling and rerunning it.</span></span>
  
## <a name="logic-errors"></a><span data-ttu-id="9bde6-119">邏輯錯誤</span><span class="sxs-lookup"><span data-stu-id="9bde6-119">Logic Errors</span></span>
 <span data-ttu-id="9bde6-120">*邏輯錯誤*是應用程式在使用中時出現的錯誤。</span><span class="sxs-lookup"><span data-stu-id="9bde6-120">*Logic errors* are those that appear once the application is in use.</span></span> <span data-ttu-id="9bde6-121">這通常是開發人員所做的錯誤假設, 或回應使用者動作的不必要或非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="9bde6-121">They are most often faulty assumptions made by the developer, or unwanted or unexpected results in response to user actions.</span></span> <span data-ttu-id="9bde6-122">例如, 輸入錯誤的索引鍵可能會提供不正確的資訊給方法, 或者您可能會假設有效的值一律會提供給方法 (如果不是這種情況)。</span><span class="sxs-lookup"><span data-stu-id="9bde6-122">For example, a mistyped key might provide incorrect information to a method, or you may assume that a valid value is always supplied to a method when that is not the case.</span></span> <span data-ttu-id="9bde6-123">雖然邏輯錯誤可以使用[例外狀況處理](../../language-reference/statements/try-catch-finally-statement.md)來處理 (例如, 藉由測試引數是否為`Nothing`和<xref:System.ArgumentNullException>擲回), 但最常見的解決方法是在邏輯中更正錯誤並重新編譯應用程式.</span><span class="sxs-lookup"><span data-stu-id="9bde6-123">Although logic errors can be handled by using [exception handling](../../language-reference/statements/try-catch-finally-statement.md) (for example, by testing whether an argument is `Nothing` and throwing an <xref:System.ArgumentNullException>), most commonly they should be addressed by correcting the error in logic and recompiling the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="9bde6-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bde6-124">See also</span></span>

- [<span data-ttu-id="9bde6-125">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="9bde6-125">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="9bde6-126">偵錯工具基礎</span><span class="sxs-lookup"><span data-stu-id="9bde6-126">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)
