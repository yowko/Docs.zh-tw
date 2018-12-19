---
title: 使用例外狀況 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], about exceptions
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
ms.openlocfilehash: 64e62d9c6cfcffb9ea5c0b0e05a546753278e186
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240186"
---
# <a name="using-exceptions-c-programming-guide"></a><span data-ttu-id="73b27-102">使用例外狀況 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="73b27-102">Using Exceptions (C# Programming Guide)</span></span>
<span data-ttu-id="73b27-103">在 C# 中，若程式在執行階段發生錯誤，會利用一種稱為例外狀況的機制，讓整個程式都得知此狀況。</span><span class="sxs-lookup"><span data-stu-id="73b27-103">In C#, errors in the program at run time are propagated through the program by using a mechanism called exceptions.</span></span> <span data-ttu-id="73b27-104">例外狀況是由遇到錯誤的程式碼所擲回，並由可以更正此錯誤的程式碼所攔截。</span><span class="sxs-lookup"><span data-stu-id="73b27-104">Exceptions are thrown by code that encounters an error and caught by code that can correct the error.</span></span> <span data-ttu-id="73b27-105">例外狀況可由 .NET Framework Common Language Runtime (CLR) 或程式中的程式碼所擲回。</span><span class="sxs-lookup"><span data-stu-id="73b27-105">Exceptions can be thrown by the .NET Framework common language runtime (CLR) or by code in a program.</span></span> <span data-ttu-id="73b27-106">一旦擲回了例外狀況，便會在呼叫堆疊中將此訊息往上傳，直至找到例外狀況的 `catch` 陳述式為止。</span><span class="sxs-lookup"><span data-stu-id="73b27-106">Once an exception is thrown, it propagates up the call stack until a `catch` statement for the exception is found.</span></span> <span data-ttu-id="73b27-107">未被攔截的例外狀況會由系統提供的泛型例外處理常式負責處理，這時會顯示對話方塊。</span><span class="sxs-lookup"><span data-stu-id="73b27-107">Uncaught exceptions are handled by a generic exception handler provided by the system that displays a dialog box.</span></span>  
  
 <span data-ttu-id="73b27-108">例外狀況會以衍生自 <xref:System.Exception> 的類別表示。</span><span class="sxs-lookup"><span data-stu-id="73b27-108">Exceptions are represented by classes derived from <xref:System.Exception>.</span></span> <span data-ttu-id="73b27-109">此類別會識別例外狀況的類型，並包含具有例外狀況詳細資料的屬性。</span><span class="sxs-lookup"><span data-stu-id="73b27-109">This class identifies the type of exception and contains properties that have details about the exception.</span></span> <span data-ttu-id="73b27-110">擲回例外狀況的作業包括建立例外狀況衍生類別的執行個體、選擇性地設定例外狀況的屬性，然後使用 `throw` 關鍵字擲回物件。</span><span class="sxs-lookup"><span data-stu-id="73b27-110">Throwing an exception involves creating an instance of an exception-derived class, optionally configuring properties of the exception, and then throwing the object by using the `throw` keyword.</span></span> <span data-ttu-id="73b27-111">例如：</span><span class="sxs-lookup"><span data-stu-id="73b27-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#1](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_1.cs)]  
  
 <span data-ttu-id="73b27-112">擲回例外狀況之後，執行階段會檢查目前的陳述式是否在 `try` 區塊內。</span><span class="sxs-lookup"><span data-stu-id="73b27-112">After an exception is thrown, the runtime checks the current statement to see whether it is within a `try` block.</span></span> <span data-ttu-id="73b27-113">如果是的話，便會檢查與 `try` 區塊關聯的任何 `catch` 區塊，以查看其是否能攔截該例外狀況。</span><span class="sxs-lookup"><span data-stu-id="73b27-113">If it is, any `catch` blocks associated with the `try` block are checked to see whether they can catch the exception.</span></span> <span data-ttu-id="73b27-114">`Catch` 區塊通常會指定例外狀況類型；如果 `catch` 區塊的類型與例外狀況或其基底類別的類型相同，`catch` 區塊便可處理此方法。</span><span class="sxs-lookup"><span data-stu-id="73b27-114">`Catch` blocks typically specify exception types; if the type of the `catch` block is the same type as the exception, or a base class of the exception, the `catch` block can handle the method.</span></span> <span data-ttu-id="73b27-115">例如：</span><span class="sxs-lookup"><span data-stu-id="73b27-115">For example:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#2](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_2.cs)]  
  
 <span data-ttu-id="73b27-116">如果擲回例外狀況的陳述式不在 `try` 區塊內，或是例外狀況所在的 `try` 區塊內沒有相符的 `catch` 區塊，執行階段便會檢查 `try` 陳述式和 `catch` 區塊的呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="73b27-116">If the statement that throws an exception is not within a `try` block or if the `try` block that encloses it has no matching `catch` block, the runtime checks the calling method for a `try` statement and `catch` blocks.</span></span> <span data-ttu-id="73b27-117">執行階段會繼續在呼叫堆疊中往上搜尋，直到找到相容的 `catch` 區塊。</span><span class="sxs-lookup"><span data-stu-id="73b27-117">The runtime continues up the calling stack, searching for a compatible `catch` block.</span></span> <span data-ttu-id="73b27-118">找到並執行 `catch` 區塊之後，控制項就會傳遞至該 `catch` 區塊後面的下一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="73b27-118">After the `catch` block is found and executed, control is passed to the next statement after that `catch` block.</span></span>  
  
 <span data-ttu-id="73b27-119">`try` 陳述式可以包含多個 `catch` 區塊。</span><span class="sxs-lookup"><span data-stu-id="73b27-119">A `try` statement can contain more than one `catch` block.</span></span> <span data-ttu-id="73b27-120">第一個可以處理例外狀況的 `catch` 陳述式會先執行，接在後面的任何 `catch` 陳述式不論相容與否，都會予以略過。</span><span class="sxs-lookup"><span data-stu-id="73b27-120">The first `catch` statement that can handle the exception is executed; any following `catch` statements, even if they are compatible, are ignored.</span></span> <span data-ttu-id="73b27-121">因此，catch 區塊一律會從最特殊 (最具衍生性) 的區塊，排列到最不特殊的區塊。</span><span class="sxs-lookup"><span data-stu-id="73b27-121">Therefore, catch blocks should always be ordered from most specific (or most-derived) to least specific.</span></span> <span data-ttu-id="73b27-122">例如：</span><span class="sxs-lookup"><span data-stu-id="73b27-122">For example:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#3](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_3.cs)]  
  
 <span data-ttu-id="73b27-123">執行 `catch` 之前，執行階段會檢查 `finally` 區塊。</span><span class="sxs-lookup"><span data-stu-id="73b27-123">Before the `catch` block is executed, the runtime checks for `finally` blocks.</span></span> <span data-ttu-id="73b27-124">`Finally` 區塊可讓程式設計人員清除任何中止之 `try` 區塊中所殘留的任何模稜兩可狀態，或是不用等候執行階段內的記憶體回收行程完成物件，便可釋放任何外部資源 (例如圖形控制代碼、資料庫連接或檔案資料流)。</span><span class="sxs-lookup"><span data-stu-id="73b27-124">`Finally` blocks enable the programmer to clean up any ambiguous state that could be left over from an aborted `try` block, or to release any external resources (such as graphics handles, database connections or file streams) without waiting for the garbage collector in the runtime to finalize the objects.</span></span> <span data-ttu-id="73b27-125">例如：</span><span class="sxs-lookup"><span data-stu-id="73b27-125">For example:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#4](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_4.cs)]  
  
 <span data-ttu-id="73b27-126">當 `WriteByte()` 擲回例外狀況時，如果未呼叫 `file.Close()`，則嘗試重新開啟檔案之第二個 `try` 區塊中的程式碼會失敗，而且該檔案會保持鎖定狀態。</span><span class="sxs-lookup"><span data-stu-id="73b27-126">If `WriteByte()` threw an exception, the code in the second `try` block that tries to reopen the file would fail if `file.Close()` is not called, and the file would remain locked.</span></span> <span data-ttu-id="73b27-127">由於即使擲回例外狀況也會執行 `finally` 區塊，因此上述範例中的 `finally` 區塊可讓檔案正常關閉，並協助避免發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="73b27-127">Because `finally` blocks are executed even if an exception is thrown, the `finally` block in the previous example allows for the file to be closed correctly and helps avoid an error.</span></span>  
  
 <span data-ttu-id="73b27-128">擲回例外狀況之後，如果在呼叫堆疊中找不到相容的 `catch` 區塊，則會發生下列三種情況的其中一種：</span><span class="sxs-lookup"><span data-stu-id="73b27-128">If no compatible `catch` block is found on the call stack after an exception is thrown, one of three things occurs:</span></span>  
  
-   <span data-ttu-id="73b27-129">如果例外狀況在完成項內，就會中止完成項並呼叫基底完成項 (如果有)。</span><span class="sxs-lookup"><span data-stu-id="73b27-129">If the exception is within a finalizer, the finalizer is aborted and the base finalizer, if any, is called.</span></span>  
  
-   <span data-ttu-id="73b27-130">如果呼叫堆疊包含靜態建構函式或靜態欄位初始設定式，則會擲回 <xref:System.TypeInitializationException>，同時將原始例外狀況指派給新例外狀況的 <xref:System.Exception.InnerException%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="73b27-130">If the call stack contains a static constructor, or a static field initializer, a <xref:System.TypeInitializationException> is thrown, with the original exception assigned to the <xref:System.Exception.InnerException%2A> property of the new exception.</span></span>  
  
-   <span data-ttu-id="73b27-131">如果到達執行緒的開頭，則會終止執行緒。</span><span class="sxs-lookup"><span data-stu-id="73b27-131">If the start of the thread is reached, the thread is terminated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73b27-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="73b27-132">See Also</span></span>

- [<span data-ttu-id="73b27-133">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="73b27-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="73b27-134">例外狀況和例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="73b27-134">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)
