---
title: 錯誤訊息 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- errors [Visual Basic]
- error messages
- trappable errors
- errors [Visual Basic], trappable
ms.assetid: f2dda05b-baef-41f5-8bb1-598bd7cf239f
ms.openlocfilehash: c326b781222429d68ec4385d95507a6ba99eafcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590130"
---
# <a name="error-messages-visual-basic"></a><span data-ttu-id="3755d-102">錯誤訊息 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3755d-102">Error Messages (Visual Basic)</span></span>
<span data-ttu-id="3755d-103">當您撰寫、編譯或執行 Visual Basic 應用程式時，可能發生下列類型的錯誤：</span><span class="sxs-lookup"><span data-stu-id="3755d-103">When you write, compile, or run a Visual Basic application, the following types of errors can occur:</span></span>  
  
1.  <span data-ttu-id="3755d-104">設計階段錯誤，當您在 Visual Studio 中撰寫應用程式時可能發生。</span><span class="sxs-lookup"><span data-stu-id="3755d-104">Design-time errors, which occur when you write an application in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="3755d-105">編譯時期錯誤，當您在 Visual Studio 或於命令提示字元中編譯應用程式時可能發生。</span><span class="sxs-lookup"><span data-stu-id="3755d-105">Compile-time errors, which occur when you compile an application in Visual Studio or at a command prompt.</span></span>  
  
3.  <span data-ttu-id="3755d-106">執行階段錯誤，當您在 Visual Studio 中執行應用程式，或是以獨立的可執行檔執行應用程式時可能發生。</span><span class="sxs-lookup"><span data-stu-id="3755d-106">Run-time errors, which occur when you run an application in Visual Studio or as a stand-alone executable file.</span></span>  
  
 <span data-ttu-id="3755d-107">如需有關如何針對特定錯誤進行疑難排解的詳細資訊，請參閱[Visual Basic 程式設計人員的其他資源](../../../visual-basic/getting-started/additional-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="3755d-107">For information about how to troubleshoot a specific error, see [Additional Resources for Visual Basic Programmers](../../../visual-basic/getting-started/additional-resources.md).</span></span>  
  
## <a name="run-time-errors"></a><span data-ttu-id="3755d-108">執行階段錯誤</span><span class="sxs-lookup"><span data-stu-id="3755d-108">Run Time Errors</span></span>  
 <span data-ttu-id="3755d-109">如果 Visual Basic 應用程式嘗試執行系統無法執行的動作，就會發生執行階段錯誤，和 Visual Basic 會擲回`Exception`物件。</span><span class="sxs-lookup"><span data-stu-id="3755d-109">If a Visual Basic application tries to perform an action that the system can't execute, a run-time error occurs, and Visual Basic throws an `Exception` object.</span></span> <span data-ttu-id="3755d-110">Visual Basic 可以產生自訂錯誤的任何資料類型，包括`Exception`物件，使用`Throw`陳述式。</span><span class="sxs-lookup"><span data-stu-id="3755d-110">Visual Basic can generate custom errors of any data type, including `Exception` objects, by using the `Throw` statement.</span></span> <span data-ttu-id="3755d-111">應用程式可以透過顯示已攔截例外狀況的錯誤碼和訊息來識別錯誤。</span><span class="sxs-lookup"><span data-stu-id="3755d-111">An application can identify the error by displaying the error number and message of a caught exception.</span></span> <span data-ttu-id="3755d-112">如果未攔截到錯誤，應用程式便會結束。</span><span class="sxs-lookup"><span data-stu-id="3755d-112">If an error isn't caught, the application ends.</span></span>  
  
 <span data-ttu-id="3755d-113">程式碼可以攔截並檢查執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="3755d-113">The code can trap and examine run-time errors.</span></span> <span data-ttu-id="3755d-114">如果您將產生錯誤的程式碼包含在 `Try` 區塊中，您可以攔截相對應 `Catch` 區塊內的所有擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="3755d-114">If you enclose the code that produces the error in a `Try` block, you can catch any thrown error within a matching `Catch` block.</span></span> <span data-ttu-id="3755d-115">如需有關如何在程式碼中於執行階段攔截錯誤並加以回應的詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="3755d-115">For information about how to trap errors at run time and respond to them in your code, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="compile-time-errors"></a><span data-ttu-id="3755d-116">編譯時期錯誤</span><span class="sxs-lookup"><span data-stu-id="3755d-116">Compile Time Errors</span></span>  
 <span data-ttu-id="3755d-117">如果 Visual Basic 編譯器遇到程式碼中的問題時，就會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="3755d-117">If the Visual Basic compiler encounters a problem in the code, a compile-time error occurs.</span></span> <span data-ttu-id="3755d-118">在程式碼編輯器中，您可以輕鬆識別造成錯誤的程式碼行，因為該行程式碼下方會顯示波浪線。</span><span class="sxs-lookup"><span data-stu-id="3755d-118">In the Code Editor, you can easily identify which line of code caused the error because a wavy line appears under that line of code.</span></span> <span data-ttu-id="3755d-119">如果您指向該波浪底線或是開啟 [錯誤清單]，將會顯示錯誤訊息 (這也會顯示其他訊息)。</span><span class="sxs-lookup"><span data-stu-id="3755d-119">The error message appears if you either point to the wavy underline or open the **Error List**, which also shows other messages.</span></span>  
  
 <span data-ttu-id="3755d-120">如果識別碼具有波浪底線，且在最右邊的字元底下顯示短底線，您可以針對類別、建構函式、方法、屬性、欄位或列舉產生虛設常式。</span><span class="sxs-lookup"><span data-stu-id="3755d-120">If an identifier has a wavy underline and a short underline appears under the rightmost character, you can generate a stub for the class, constructor, method, property, field or enum.</span></span> <span data-ttu-id="3755d-121">如需詳細資訊，請參閱[使用時產生](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage)。</span><span class="sxs-lookup"><span data-stu-id="3755d-121">For more information, see [Generate From Usage](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage).</span></span>
  
 <span data-ttu-id="3755d-122">透過解決 Visual Basic 編譯器的警告，您可能可以撰寫出執行速度較快且具有較少錯誤 (bug) 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3755d-122">By resolving warnings from the Visual Basic compiler, you might be able to write code that runs faster and has fewer bugs.</span></span> <span data-ttu-id="3755d-123">這些警告會識別在應用程式執行時可能造成錯誤的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3755d-123">These warnings identify code that may cause errors when the application is run.</span></span> <span data-ttu-id="3755d-124">例如，如果您嘗試叫用未指派物件變數的成員、在沒有設定傳回值的情況下從函式傳回，或是執行具有邏輯錯誤的 `Try` 區塊以攔截例外狀況，編譯器都會警告您。</span><span class="sxs-lookup"><span data-stu-id="3755d-124">For example, the compiler warns you if you try to invoke a member of an unassigned object variable, return from a function without setting the return value, or execute a `Try` block with errors in the logic to catch exceptions.</span></span> <span data-ttu-id="3755d-125">如需有關警告的詳細資訊 (包括如何開啟與關閉警告)，請參閱[在 Visual Basic 中設定警告](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="3755d-125">For more information about warnings, including how to turn them on and off, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>
