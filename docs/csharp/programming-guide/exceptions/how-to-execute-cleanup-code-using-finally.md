---
title: "如何：使用 finally 執行清除程式碼 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b9c22ca8ee9c83e6f1808520530c6d1912d8f4f1
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a><span data-ttu-id="531a3-102">如何：使用 finally 執行清除程式碼 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="531a3-102">How to: Execute Cleanup Code Using finally (C# Programming Guide)</span></span>
<span data-ttu-id="531a3-103">`finally` 陳述式的目的是為了確保在必要時會立即清除物件 (通常是含有外部資源的物件)，即使擲回例外狀況也一樣。</span><span class="sxs-lookup"><span data-stu-id="531a3-103">The purpose of a `finally` statement is to ensure that the necessary cleanup of objects, usually objects that are holding external resources, occurs immediately, even if an exception is thrown.</span></span> <span data-ttu-id="531a3-104">這類清除的一個例子，是在使用後立即對 <xref:System.IO.FileStream> 呼叫 <xref:System.IO.Stream.Close%2A>，而不等候 Common Language Runtime 回收物件的記憶體，如下所示：</span><span class="sxs-lookup"><span data-stu-id="531a3-104">One example of such cleanup is calling <xref:System.IO.Stream.Close%2A> on a <xref:System.IO.FileStream> immediately after use instead of waiting for the object to be garbage collected by the common language runtime, as follows:</span></span>  
  
 <span data-ttu-id="531a3-105">[!code-cs[csProgGuideExceptions#16](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="531a3-105">[!code-cs[csProgGuideExceptions#16](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="531a3-106">範例</span><span class="sxs-lookup"><span data-stu-id="531a3-106">Example</span></span>  
 <span data-ttu-id="531a3-107">為了將上述程式碼變成 `try-catch-finally` 陳述式，清除程式碼會與工作程式碼分開，如下所示。</span><span class="sxs-lookup"><span data-stu-id="531a3-107">To turn the previous code into a `try-catch-finally` statement, the cleanup code is separated from the working code, as follows.</span></span>  
  
 <span data-ttu-id="531a3-108">[!code-cs[csProgGuideExceptions#17](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="531a3-108">[!code-cs[csProgGuideExceptions#17](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_2.cs)]</span></span>  
  
 <span data-ttu-id="531a3-109">因為在 `OpenWrite()` 呼叫之前，`try` 區塊內隨時都可能會發生例外狀況，或是 `OpenWrite()` 呼叫本身可能會失敗，所以在嘗試關閉檔案時不保證檔案處於開啟狀態。</span><span class="sxs-lookup"><span data-stu-id="531a3-109">Because an exception can occur at any time within the `try` block before the `OpenWrite()` call, or the `OpenWrite()` call itself could fail, we are not guaranteed that the file is open when we try to close it.</span></span> <span data-ttu-id="531a3-110">`finally` 區塊會新增檢查，以確保在呼叫 <xref:System.IO.Stream.Close%2A> 方法之前，<xref:System.IO.FileStream> 物件不是 `null`。</span><span class="sxs-lookup"><span data-stu-id="531a3-110">The `finally` block adds a check to make sure that the <xref:System.IO.FileStream> object is not `null` before you call the <xref:System.IO.Stream.Close%2A> method.</span></span> <span data-ttu-id="531a3-111">如果沒有 `null` 檢查，`finally` 區塊可能會擲回本身的 <xref:System.NullReferenceException>，但應盡可能避免在 `finally` 中擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="531a3-111">Without the `null` check, the `finally` block could throw its own <xref:System.NullReferenceException>, but throwing exceptions in `finally` blocks should be avoided if it is possible.</span></span>  
  
 <span data-ttu-id="531a3-112">在 `finally` 區塊中關閉資料庫連接是另一個不錯的選擇。</span><span class="sxs-lookup"><span data-stu-id="531a3-112">A database connection is another good candidate for being closed in a `finally` block.</span></span> <span data-ttu-id="531a3-113">因為允許連接至資料庫伺服器的連接數目有時候是有限的，所以您應該盡快關閉資料庫連接。</span><span class="sxs-lookup"><span data-stu-id="531a3-113">Because the number of connections allowed to a database server is sometimes limited, you should close database connections as quickly as possible.</span></span> <span data-ttu-id="531a3-114">如果在您可以關閉連接之前就擲回例外狀況，使用 `finally` 區塊會比等候記憶體回收更適合。</span><span class="sxs-lookup"><span data-stu-id="531a3-114">If an exception is thrown before you can close your connection, this is another case where using the `finally` block is better than waiting for garbage collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="531a3-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="531a3-115">See Also</span></span>  
 <span data-ttu-id="531a3-116">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="531a3-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="531a3-117"> [例外狀況和例外狀況處理](../../../csharp/programming-guide/exceptions/index.md) </span><span class="sxs-lookup"><span data-stu-id="531a3-117"> [Exceptions and Exception Handling](../../../csharp/programming-guide/exceptions/index.md) </span></span>  
<span data-ttu-id="531a3-118"> [例外狀況處理](../../../csharp/programming-guide/exceptions/exception-handling.md) </span><span class="sxs-lookup"><span data-stu-id="531a3-118"> [Exception Handling](../../../csharp/programming-guide/exceptions/exception-handling.md) </span></span>  
<span data-ttu-id="531a3-119"> [using 陳述式](../../../csharp/language-reference/keywords/using-statement.md) </span><span class="sxs-lookup"><span data-stu-id="531a3-119"> [using Statement](../../../csharp/language-reference/keywords/using-statement.md) </span></span>  
<span data-ttu-id="531a3-120"> [try-catch](../../../csharp/language-reference/keywords/try-catch.md) </span><span class="sxs-lookup"><span data-stu-id="531a3-120"> [try-catch](../../../csharp/language-reference/keywords/try-catch.md) </span></span>  
<span data-ttu-id="531a3-121"> [try-finally](../../../csharp/language-reference/keywords/try-finally.md) </span><span class="sxs-lookup"><span data-stu-id="531a3-121"> [try-finally](../../../csharp/language-reference/keywords/try-finally.md) </span></span>  
<span data-ttu-id="531a3-122"> [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)</span><span class="sxs-lookup"><span data-stu-id="531a3-122"> [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)</span></span>
