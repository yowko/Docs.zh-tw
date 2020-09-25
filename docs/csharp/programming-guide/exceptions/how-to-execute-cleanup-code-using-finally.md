---
title: '如何使用 finally 執行清除程式碼-c # 程式設計指南'
description: 瞭解如何使用 ' finally ' 語句執行清除程式碼。 Finally 語句可確保物件的任何必要清除都會立即發生。
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: 283c36ab9b976a92e339000a982340148c2480a8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178641"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a><span data-ttu-id="38852-104">如何使用 finally 執行清除程式碼 (c # 程式設計手冊) </span><span class="sxs-lookup"><span data-stu-id="38852-104">How to execute cleanup code using finally (C# Programming Guide)</span></span>

<span data-ttu-id="38852-105">`finally` 陳述式的目的是為了確保在必要時會立即清除物件 (通常是含有外部資源的物件)，即使擲回例外狀況也一樣。</span><span class="sxs-lookup"><span data-stu-id="38852-105">The purpose of a `finally` statement is to ensure that the necessary cleanup of objects, usually objects that are holding external resources, occurs immediately, even if an exception is thrown.</span></span> <span data-ttu-id="38852-106">這類清除的一個例子，是在使用後立即呼叫 <xref:System.IO.FileStream> 的 <xref:System.IO.Stream.Close%2A>，而不等候 Common Language Runtime 回收物件的記憶體，如下所示：</span><span class="sxs-lookup"><span data-stu-id="38852-106">One example of such cleanup is calling <xref:System.IO.Stream.Close%2A> on a <xref:System.IO.FileStream> immediately after use instead of waiting for the object to be garbage collected by the common language runtime, as follows:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a><span data-ttu-id="38852-107">範例</span><span class="sxs-lookup"><span data-stu-id="38852-107">Example</span></span>  

 <span data-ttu-id="38852-108">為了將上述程式碼變成 `try-catch-finally` 陳述式，清除程式碼會與工作程式碼分開，如下所示。</span><span class="sxs-lookup"><span data-stu-id="38852-108">To turn the previous code into a `try-catch-finally` statement, the cleanup code is separated from the working code, as follows.</span></span>  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 <span data-ttu-id="38852-109">因為在 `OpenWrite()` 呼叫之前，`try` 區塊內隨時都可能會發生例外狀況，或是 `OpenWrite()` 呼叫本身可能會失敗，所以在嘗試關閉檔案時不保證檔案處於開啟狀態。</span><span class="sxs-lookup"><span data-stu-id="38852-109">Because an exception can occur at any time within the `try` block before the `OpenWrite()` call, or the `OpenWrite()` call itself could fail, we are not guaranteed that the file is open when we try to close it.</span></span> <span data-ttu-id="38852-110">`finally` 區塊新增檢查，先確定 <xref:System.IO.FileStream> 物件不是 `null`，再呼叫 <xref:System.IO.Stream.Close%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="38852-110">The `finally` block adds a check to make sure that the <xref:System.IO.FileStream> object is not `null` before you call the <xref:System.IO.Stream.Close%2A> method.</span></span> <span data-ttu-id="38852-111">如果沒有 `null` 檢查，`finally` 區塊可能會擲回本身的 <xref:System.NullReferenceException>，但應盡可能避免在 `finally` 區塊中擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="38852-111">Without the `null` check, the `finally` block could throw its own <xref:System.NullReferenceException>, but throwing exceptions in `finally` blocks should be avoided if it is possible.</span></span>  
  
 <span data-ttu-id="38852-112">在 `finally` 區塊中關閉資料庫連接是另一個不錯的選擇。</span><span class="sxs-lookup"><span data-stu-id="38852-112">A database connection is another good candidate for being closed in a `finally` block.</span></span> <span data-ttu-id="38852-113">因為允許連接至資料庫伺服器的連接數目有時候是有限的，所以您應該盡快關閉資料庫連接。</span><span class="sxs-lookup"><span data-stu-id="38852-113">Because the number of connections allowed to a database server is sometimes limited, you should close database connections as quickly as possible.</span></span> <span data-ttu-id="38852-114">如果在您可以關閉連接之前就擲回例外狀況，使用 `finally` 區塊會比等候記憶體回收更適合。</span><span class="sxs-lookup"><span data-stu-id="38852-114">If an exception is thrown before you can close your connection, this is another case where using the `finally` block is better than waiting for garbage collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38852-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38852-115">See also</span></span>

- [<span data-ttu-id="38852-116">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="38852-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="38852-117">例外狀況和例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="38852-117">Exceptions and Exception Handling</span></span>](./index.md)
- [<span data-ttu-id="38852-118">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="38852-118">Exception Handling</span></span>](./exception-handling.md)
- [<span data-ttu-id="38852-119">using 陳述式</span><span class="sxs-lookup"><span data-stu-id="38852-119">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
- [<span data-ttu-id="38852-120">try-catch</span><span class="sxs-lookup"><span data-stu-id="38852-120">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="38852-121">try-finally</span><span class="sxs-lookup"><span data-stu-id="38852-121">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="38852-122">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="38852-122">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
