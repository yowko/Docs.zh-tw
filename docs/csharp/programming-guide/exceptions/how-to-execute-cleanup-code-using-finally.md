---
title: 作法：使用 finally 執行清除程式碼 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: 0ec661e5fb0e13eaf8c3c8e4a7b274ab58853f58
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978081"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a><span data-ttu-id="9549b-102">作法：使用 finally 執行清除程式碼 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="9549b-102">How to: Execute Cleanup Code Using finally (C# Programming Guide)</span></span>
<span data-ttu-id="9549b-103">`finally` 陳述式的目的是為了確保在必要時會立即清除物件 (通常是含有外部資源的物件)，即使擲回例外狀況也一樣。</span><span class="sxs-lookup"><span data-stu-id="9549b-103">The purpose of a `finally` statement is to ensure that the necessary cleanup of objects, usually objects that are holding external resources, occurs immediately, even if an exception is thrown.</span></span> <span data-ttu-id="9549b-104">這類清除的一個例子，是在使用後立即呼叫 <xref:System.IO.FileStream> 的 <xref:System.IO.Stream.Close%2A>，而不等候 Common Language Runtime 回收物件的記憶體，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9549b-104">One example of such cleanup is calling <xref:System.IO.Stream.Close%2A> on a <xref:System.IO.FileStream> immediately after use instead of waiting for the object to be garbage collected by the common language runtime, as follows:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a><span data-ttu-id="9549b-105">範例</span><span class="sxs-lookup"><span data-stu-id="9549b-105">Example</span></span>  
 <span data-ttu-id="9549b-106">為了將上述程式碼變成 `try-catch-finally` 陳述式，清除程式碼會與工作程式碼分開，如下所示。</span><span class="sxs-lookup"><span data-stu-id="9549b-106">To turn the previous code into a `try-catch-finally` statement, the cleanup code is separated from the working code, as follows.</span></span>  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 <span data-ttu-id="9549b-107">因為在 `OpenWrite()` 呼叫之前，`try` 區塊內隨時都可能會發生例外狀況，或是 `OpenWrite()` 呼叫本身可能會失敗，所以在嘗試關閉檔案時不保證檔案處於開啟狀態。</span><span class="sxs-lookup"><span data-stu-id="9549b-107">Because an exception can occur at any time within the `try` block before the `OpenWrite()` call, or the `OpenWrite()` call itself could fail, we are not guaranteed that the file is open when we try to close it.</span></span> <span data-ttu-id="9549b-108">`finally` 區塊新增檢查，先確定 <xref:System.IO.FileStream> 物件不是 `null`，再呼叫 <xref:System.IO.Stream.Close%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="9549b-108">The `finally` block adds a check to make sure that the <xref:System.IO.FileStream> object is not `null` before you call the <xref:System.IO.Stream.Close%2A> method.</span></span> <span data-ttu-id="9549b-109">如果沒有 `null` 檢查，`finally` 區塊可能會擲回本身的 <xref:System.NullReferenceException>，但應盡可能避免在 `finally` 區塊中擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9549b-109">Without the `null` check, the `finally` block could throw its own <xref:System.NullReferenceException>, but throwing exceptions in `finally` blocks should be avoided if it is possible.</span></span>  
  
 <span data-ttu-id="9549b-110">在 `finally` 區塊中關閉資料庫連接是另一個不錯的選擇。</span><span class="sxs-lookup"><span data-stu-id="9549b-110">A database connection is another good candidate for being closed in a `finally` block.</span></span> <span data-ttu-id="9549b-111">因為允許連接至資料庫伺服器的連接數目有時候是有限的，所以您應該盡快關閉資料庫連接。</span><span class="sxs-lookup"><span data-stu-id="9549b-111">Because the number of connections allowed to a database server is sometimes limited, you should close database connections as quickly as possible.</span></span> <span data-ttu-id="9549b-112">如果在您可以關閉連接之前就擲回例外狀況，使用 `finally` 區塊會比等候記憶體回收更適合。</span><span class="sxs-lookup"><span data-stu-id="9549b-112">If an exception is thrown before you can close your connection, this is another case where using the `finally` block is better than waiting for garbage collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9549b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9549b-113">See also</span></span>

- [<span data-ttu-id="9549b-114">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="9549b-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="9549b-115">例外狀況和例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="9549b-115">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)
- [<span data-ttu-id="9549b-116">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="9549b-116">Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/exception-handling.md)
- [<span data-ttu-id="9549b-117">using 陳述式</span><span class="sxs-lookup"><span data-stu-id="9549b-117">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)
- [<span data-ttu-id="9549b-118">try-catch</span><span class="sxs-lookup"><span data-stu-id="9549b-118">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)
- [<span data-ttu-id="9549b-119">try-finally</span><span class="sxs-lookup"><span data-stu-id="9549b-119">try-finally</span></span>](../../../csharp/language-reference/keywords/try-finally.md)
- [<span data-ttu-id="9549b-120">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="9549b-120">try-catch-finally</span></span>](../../../csharp/language-reference/keywords/try-catch-finally.md)
