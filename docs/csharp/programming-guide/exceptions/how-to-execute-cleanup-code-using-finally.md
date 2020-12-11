---
title: '如何使用 finally 執行清除程式碼-c # 程式設計指南'
description: 瞭解如何使用 ' finally ' 語句執行清除程式碼。 Finally 語句可確保物件的任何必要清除都會立即發生。
ms.date: 12/09/2020
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: e9b5d3086488d3f7e3c0709317d6fafd15c439e8
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110178"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a><span data-ttu-id="4a36f-104">如何使用 finally 執行清除程式碼 (c # 程式設計手冊) </span><span class="sxs-lookup"><span data-stu-id="4a36f-104">How to execute cleanup code using finally (C# Programming Guide)</span></span>

<span data-ttu-id="4a36f-105">`finally` 陳述式的目的是為了確保在必要時會立即清除物件 (通常是含有外部資源的物件)，即使擲回例外狀況也一樣。</span><span class="sxs-lookup"><span data-stu-id="4a36f-105">The purpose of a `finally` statement is to ensure that the necessary cleanup of objects, usually objects that are holding external resources, occurs immediately, even if an exception is thrown.</span></span> <span data-ttu-id="4a36f-106">這類清除的一個例子，是在使用後立即呼叫 <xref:System.IO.FileStream> 的 <xref:System.IO.Stream.Close%2A>，而不等候 Common Language Runtime 回收物件的記憶體，如下所示：</span><span class="sxs-lookup"><span data-stu-id="4a36f-106">One example of such cleanup is calling <xref:System.IO.Stream.Close%2A> on a <xref:System.IO.FileStream> immediately after use instead of waiting for the object to be garbage collected by the common language runtime, as follows:</span></span>

:::code language="csharp" source="snippets/exceptions/Program.cs" ID="NoCleanup":::

## <a name="example"></a><span data-ttu-id="4a36f-107">範例</span><span class="sxs-lookup"><span data-stu-id="4a36f-107">Example</span></span>

<span data-ttu-id="4a36f-108">為了將上述程式碼變成 `try-catch-finally` 陳述式，清除程式碼會與工作程式碼分開，如下所示。</span><span class="sxs-lookup"><span data-stu-id="4a36f-108">To turn the previous code into a `try-catch-finally` statement, the cleanup code is separated from the working code, as follows.</span></span>

:::code language="csharp" source="snippets/exceptions/Program.cs" ID="WithCleanup":::

<span data-ttu-id="4a36f-109">由於例外狀況可能會在呼叫之前的任何時間發生 `try` `OpenWrite()` ，或是 `OpenWrite()` 呼叫本身可能失敗，因此我們不保證在嘗試關閉檔案時，檔案是開啟的。</span><span class="sxs-lookup"><span data-stu-id="4a36f-109">Because an exception can occur at any time within the `try` block before the `OpenWrite()` call, or the `OpenWrite()` call itself could fail, we aren't guaranteed that the file is open when we try to close it.</span></span> <span data-ttu-id="4a36f-110">`finally`區塊會新增檢查，以確保 <xref:System.IO.FileStream> 物件不 `null` 會在呼叫方法之前 <xref:System.IO.Stream.Close%2A> 。</span><span class="sxs-lookup"><span data-stu-id="4a36f-110">The `finally` block adds a check to make sure that the <xref:System.IO.FileStream> object isn't `null` before you call the <xref:System.IO.Stream.Close%2A> method.</span></span> <span data-ttu-id="4a36f-111">如果沒有 `null` 檢查， `finally` 區塊可能會擲回它自己的 <xref:System.NullReferenceException> ，但 `finally` 如果可能的話，應避免在區塊中擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4a36f-111">Without the `null` check, the `finally` block could throw its own <xref:System.NullReferenceException>, but throwing exceptions in `finally` blocks should be avoided if it's possible.</span></span>

<span data-ttu-id="4a36f-112">在 `finally` 區塊中關閉資料庫連接是另一個不錯的選擇。</span><span class="sxs-lookup"><span data-stu-id="4a36f-112">A database connection is another good candidate for being closed in a `finally` block.</span></span> <span data-ttu-id="4a36f-113">因為允許連接至資料庫伺服器的連接數目有時候是有限的，所以您應該盡快關閉資料庫連接。</span><span class="sxs-lookup"><span data-stu-id="4a36f-113">Because the number of connections allowed to a database server is sometimes limited, you should close database connections as quickly as possible.</span></span> <span data-ttu-id="4a36f-114">如果在關閉連接之前擲回例外狀況，使用 `finally` 區塊比等候垃圾收集更好。</span><span class="sxs-lookup"><span data-stu-id="4a36f-114">If an exception is thrown before you can close your connection, using the `finally` block is better than waiting for garbage collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a36f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a36f-115">See also</span></span>

- [<span data-ttu-id="4a36f-116">using 陳述式</span><span class="sxs-lookup"><span data-stu-id="4a36f-116">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
- [<span data-ttu-id="4a36f-117">try-catch</span><span class="sxs-lookup"><span data-stu-id="4a36f-117">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="4a36f-118">try-finally</span><span class="sxs-lookup"><span data-stu-id="4a36f-118">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="4a36f-119">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="4a36f-119">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
