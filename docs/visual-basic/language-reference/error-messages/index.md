---
title: Visual Basic 錯誤訊息
titleSuffix: ''
ms.date: 10/13/2020
helpviewer_keywords:
- errors [Visual Basic]
- error messages
ms.assetid: f2dda05b-baef-41f5-8bb1-598bd7cf239f
ms.openlocfilehash: 70973b6d34ed1a84a38af3694e144dfcefa61c20
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163372"
---
# <a name="error-messages-in-visual-basic"></a><span data-ttu-id="3112a-102">Visual Basic 中的錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="3112a-102">Error messages in Visual Basic</span></span>

<span data-ttu-id="3112a-103">當您編譯或執行 Visual Basic 應用程式時，可能會發生下列類型的錯誤：</span><span class="sxs-lookup"><span data-stu-id="3112a-103">When you compile or run a Visual Basic application, the following types of errors can occur:</span></span>

- <span data-ttu-id="3112a-104">編譯時期錯誤，當您編譯應用程式時就會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="3112a-104">Compile-time errors, which occur when you compile an application.</span></span>

- <span data-ttu-id="3112a-105">執行階段錯誤，當應用程式執行時，就會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="3112a-105">Run-time errors, which occur when an application is running.</span></span>

<span data-ttu-id="3112a-106">如需有關如何針對特定錯誤進行疑難排解的詳細資訊，請參閱[Visual Basic 程式設計人員的其他資源](../../getting-started/additional-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="3112a-106">For information about how to troubleshoot a specific error, see [Additional Resources for Visual Basic Programmers](../../getting-started/additional-resources.md).</span></span>

## <a name="run-time-errors"></a><span data-ttu-id="3112a-107">執行階段錯誤</span><span class="sxs-lookup"><span data-stu-id="3112a-107">Run-time errors</span></span>

<span data-ttu-id="3112a-108">如果 Visual Basic 應用程式嘗試執行系統無法執行的動作，就會發生執行階段錯誤，而 Visual Basic 會擲回 <xref:System.Exception> 物件。</span><span class="sxs-lookup"><span data-stu-id="3112a-108">If a Visual Basic application tries to perform an action that the system can't execute, a run-time error occurs, and Visual Basic throws an <xref:System.Exception> object.</span></span> <span data-ttu-id="3112a-109">Visual Basic 可以使用語句來產生任何資料類型（包括物件）的自訂錯誤 `Exception` `Throw` 。</span><span class="sxs-lookup"><span data-stu-id="3112a-109">Visual Basic can generate custom errors of any data type, including `Exception` objects, by using the `Throw` statement.</span></span> <span data-ttu-id="3112a-110">應用程式可以透過顯示已攔截例外狀況的錯誤碼和訊息來識別錯誤。</span><span class="sxs-lookup"><span data-stu-id="3112a-110">An application can identify the error by displaying the error number and message of a caught exception.</span></span> <span data-ttu-id="3112a-111">如果未攔截到錯誤，應用程式便會結束。</span><span class="sxs-lookup"><span data-stu-id="3112a-111">If an error isn't caught, the application ends.</span></span>

<span data-ttu-id="3112a-112">程式碼可以攔截並檢查執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="3112a-112">The code can trap and examine run-time errors.</span></span> <span data-ttu-id="3112a-113">如果您將產生錯誤的程式碼包含在 `Try` 區塊中，您可以攔截相對應 `Catch` 區塊內的所有擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="3112a-113">If you enclose the code that produces the error in a `Try` block, you can catch any thrown error within a matching `Catch` block.</span></span> <span data-ttu-id="3112a-114">如需有關如何在程式碼中於執行階段攔截錯誤並加以回應的詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="3112a-114">For information about how to trap errors at run time and respond to them in your code, see [Try...Catch...Finally Statement](../statements/try-catch-finally-statement.md).</span></span>

## <a name="compile-time-errors"></a><span data-ttu-id="3112a-115">編譯時期錯誤</span><span class="sxs-lookup"><span data-stu-id="3112a-115">Compile-time errors</span></span>

<span data-ttu-id="3112a-116">如果 Visual Basic 編譯器遇到程式碼中的問題時，就會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="3112a-116">If the Visual Basic compiler encounters a problem in the code, a compile-time error occurs.</span></span> <span data-ttu-id="3112a-117">在 [Visual Studio 程式碼編輯器] 中，您可以輕鬆地找出造成錯誤的程式程式碼，因為這一行程式碼下出現波浪線。</span><span class="sxs-lookup"><span data-stu-id="3112a-117">In the Visual Studio code editor, you can easily identify which line of code caused the error because a wavy line appears under that line of code.</span></span> <span data-ttu-id="3112a-118">如果您指向該波浪底線或是開啟 [錯誤清單]\*\*\*\*，將會顯示錯誤訊息 (這也會顯示其他訊息)。</span><span class="sxs-lookup"><span data-stu-id="3112a-118">The error message appears if you either point to the wavy underline or open the **Error List**, which also shows other messages.</span></span>

<span data-ttu-id="3112a-119">如果識別碼具有波浪底線，且最右邊的字元底下出現短底線，您可以為類別、函式、方法、屬性、欄位或列舉產生存根。</span><span class="sxs-lookup"><span data-stu-id="3112a-119">If an identifier has a wavy underline and a short underline appears under the rightmost character, you can generate a stub for the class, constructor, method, property, field, or enum.</span></span> <span data-ttu-id="3112a-120">如需詳細資訊，請參閱 [從使用方式產生 (Visual Studio) ](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage)。</span><span class="sxs-lookup"><span data-stu-id="3112a-120">For more information, see [Generate From Usage (Visual Studio)](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage).</span></span>

<span data-ttu-id="3112a-121">透過解決 Visual Basic 編譯器的警告，您可能可以撰寫出執行速度較快且具有較少錯誤 (bug) 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3112a-121">By resolving warnings from the Visual Basic compiler, you might be able to write code that runs faster and has fewer bugs.</span></span> <span data-ttu-id="3112a-122">這些警告會識別在應用程式執行時可能造成錯誤的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3112a-122">These warnings identify code that may cause errors when the application is run.</span></span> <span data-ttu-id="3112a-123">例如，如果您嘗試叫用未指派物件變數的成員、在沒有設定傳回值的情況下從函式傳回，或是執行具有邏輯錯誤的 `Try` 區塊以攔截例外狀況，編譯器都會警告您。</span><span class="sxs-lookup"><span data-stu-id="3112a-123">For example, the compiler warns you if you try to invoke a member of an unassigned object variable, return from a function without setting the return value, or execute a `Try` block with errors in the logic to catch exceptions.</span></span> <span data-ttu-id="3112a-124">如需有關警告的詳細資訊 (包括如何開啟與關閉警告)，請參閱[在 Visual Basic 中設定警告](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="3112a-124">For more information about warnings, including how to turn them on and off, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>
