---
title: 如何：明確擲回例外狀況
description: '瞭解如何使用 c # throw 語句或 Visual Basic Throw 語句，在 .NET 中明確地擲回例外狀況。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- exceptions, try/catch blocks
- FileNotFoundException class
- try/catch blocks
- exceptions, throwing
- implicitly throwing exceptions
ms.assetid: 72bdd157-caa9-4478-9ee3-cb4500b84528
ms.openlocfilehash: 37ba5f952d621ff2e209a3bac375b62894c944a7
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828045"
---
# <a name="how-to-explicitly-throw-exceptions"></a><span data-ttu-id="bb8d0-103">如何明確擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="bb8d0-103">How to explicitly throw exceptions</span></span>

<span data-ttu-id="bb8d0-104">您可以使用 c # 或 Visual Basic 語句明確擲回例外狀況 [`throw`](../../csharp/language-reference/keywords/throw.md) [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) 。</span><span class="sxs-lookup"><span data-stu-id="bb8d0-104">You can explicitly throw an exception using the C# [`throw`](../../csharp/language-reference/keywords/throw.md) or the Visual Basic [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) statement.</span></span> <span data-ttu-id="bb8d0-105">您也可以使用 `throw` 陳述式，再次擲回所攔截的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bb8d0-105">You can also throw a caught exception again using the `throw` statement.</span></span> <span data-ttu-id="bb8d0-106">建議您撰寫程式碼，將資訊加入要重新擲回的例外狀況，以在偵錯時提供更多資訊。</span><span class="sxs-lookup"><span data-stu-id="bb8d0-106">It is good coding practice to add information to an exception that is re-thrown to provide more information when debugging.</span></span>

<span data-ttu-id="bb8d0-107">下列程式碼範例使用 `try`/`catch` 區塊來攔截可能的 <xref:System.IO.FileNotFoundException>。</span><span class="sxs-lookup"><span data-stu-id="bb8d0-107">The following code example uses a `try`/`catch` block to catch a possible <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="bb8d0-108">`try` 區塊後面會接著 `catch` 區塊，該區塊可在找不到資料檔案時攔截 <xref:System.IO.FileNotFoundException>，並將訊息寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="bb8d0-108">Following the `try` block is a `catch` block that catches the <xref:System.IO.FileNotFoundException> and writes a message to the console if the data file is not found.</span></span> <span data-ttu-id="bb8d0-109">下一個陳述式是 `throw` 陳述式，會擲回新的 <xref:System.IO.FileNotFoundException> ，並將文字資訊新增到例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bb8d0-109">The next statement is the `throw` statement that throws a new <xref:System.IO.FileNotFoundException> and adds text information to the exception.</span></span>

[!code-csharp[Exception.Throwing#1](~/samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a><span data-ttu-id="bb8d0-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="bb8d0-110">See also</span></span>

- [<span data-ttu-id="bb8d0-111">例外狀況</span><span class="sxs-lookup"><span data-stu-id="bb8d0-111">Exceptions</span></span>](index.md)
