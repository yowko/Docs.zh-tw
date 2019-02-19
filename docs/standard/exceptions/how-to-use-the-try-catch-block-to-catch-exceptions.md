---
title: 作法：使用 Try-Catch 區塊攔截例外狀況
ms.date: 02/06/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- exceptions, try/catch blocks
- try blocks
- try/catch blocks
- catch blocks
ms.assetid: a3ce6dfd-1f64-471b-8ad8-8cfaf406275d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5183a854ee2b7462ecc27786a5fc0697565194c0
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092744"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a><span data-ttu-id="b589e-102">如何使用 try/catch 區塊攔截例外狀況</span><span class="sxs-lookup"><span data-stu-id="b589e-102">How to use the try/catch block to catch exceptions</span></span>

<span data-ttu-id="b589e-103">將任何可能引發或擲回例外狀況的程式碼陳述式放置於 `try` 區塊，並將用來處理例外狀況的陳述式放置於 `try` 區塊之下的一或多個 `catch` 區塊中。</span><span class="sxs-lookup"><span data-stu-id="b589e-103">Place any code statements that might raise or throw an exception in a `try` block, and place statements used to handle the exception or exceptions in one or more `catch` blocks below the `try` block.</span></span> <span data-ttu-id="b589e-104">每個 `catch` 區塊都會包含例外狀況類型，而且可以包含處理該例外狀況類型所需的其他陳述式。</span><span class="sxs-lookup"><span data-stu-id="b589e-104">Each `catch` block includes the exception type and can contain additional statements needed to handle that exception type.</span></span>

<span data-ttu-id="b589e-105">在下列範例中，<xref:System.IO.StreamReader> 開啟名為 *data.txt* 的檔案，並從該檔案擷取了一行。</span><span class="sxs-lookup"><span data-stu-id="b589e-105">In the following example, a <xref:System.IO.StreamReader> opens a file called *data.txt* and retrieves a line from the file.</span></span> <span data-ttu-id="b589e-106">因為程式碼可能會擲回三個例外狀況的任何一個，所以將其放置於 `try` 區塊。</span><span class="sxs-lookup"><span data-stu-id="b589e-106">Since the code might throw any of three exceptions, it's placed in a `try` block.</span></span> <span data-ttu-id="b589e-107">三個 `catch` 區塊可以藉由將結果顯示給主控台，來攔截例外狀況並加以處理。</span><span class="sxs-lookup"><span data-stu-id="b589e-107">Three `catch` blocks catch the exceptions and handle them by displaying the results to the console.</span></span>

[!code-csharp[CatchException#3](~/samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
[!code-vb[CatchException#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]  

<span data-ttu-id="b589e-108">通用語言執行平台 (CLR) 會攔截 `catch` 區塊未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b589e-108">The Common Language Runtime (CLR) catches exceptions not handled by `catch` blocks.</span></span> <span data-ttu-id="b589e-109">如果 CLR 攔截了例外狀況，可能會發生下列其中一種結果，視您的 CLR 組態而有所不同：</span><span class="sxs-lookup"><span data-stu-id="b589e-109">If an exception is caught by the CLR, one of the following results may occur depending on your CLR configuration:</span></span>

- <span data-ttu-id="b589e-110">[偵錯] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="b589e-110">A **Debug** dialog box appears.</span></span>
- <span data-ttu-id="b589e-111">程式停止執行，內容為例外狀況資訊的對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="b589e-111">The program stops execution and a dialog box with exception information appears.</span></span>
- <span data-ttu-id="b589e-112">錯誤會輸出至[標準錯誤輸出資料流](xref:System.Console.Error)。</span><span class="sxs-lookup"><span data-stu-id="b589e-112">An error prints out to the [standard error output stream](xref:System.Console.Error).</span></span>

> [!NOTE]
> <span data-ttu-id="b589e-113">多數程式碼可以擲回例外狀況，而且某些例外狀況 (例如 <xref:System.OutOfMemoryException>) 可能在任何時間由 CLR 本身擲回。</span><span class="sxs-lookup"><span data-stu-id="b589e-113">Most code can throw an exception, and some exceptions, like <xref:System.OutOfMemoryException>, can be thrown by the CLR itself at any time.</span></span> <span data-ttu-id="b589e-114">雖然應用程式不必處理這些例外狀況，但是請在撰寫供他人使用的程式庫時注意其發生的可能性。</span><span class="sxs-lookup"><span data-stu-id="b589e-114">While applications aren't required to deal with these exceptions, be aware of the possibility when writing libraries to be used by others.</span></span> <span data-ttu-id="b589e-115">如需何時在 `try` 區塊中設定程式碼的建議，請參閱[例外狀況的最佳做法](best-practices-for-exceptions.md)。</span><span class="sxs-lookup"><span data-stu-id="b589e-115">For suggestions on when to set code in a `try` block, see [Best Practices for Exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b589e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b589e-116">See also</span></span>

[<span data-ttu-id="b589e-117">例外狀況</span><span class="sxs-lookup"><span data-stu-id="b589e-117">Exceptions</span></span>](index.md)  
[<span data-ttu-id="b589e-118">在 .NET 中處理 I/O 錯誤</span><span class="sxs-lookup"><span data-stu-id="b589e-118">Handling I/O errors in .NET</span></span>](../io/handling-io-errors.md)
