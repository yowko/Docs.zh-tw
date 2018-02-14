---
title: "如何：明確擲回例外狀況"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 02576db4b9920a367ac3111f2c2c49989ea45149
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-explicitly-throw-exceptions"></a><span data-ttu-id="9e303-102">如何明確擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="9e303-102">How to explicitly throw exceptions</span></span>

<span data-ttu-id="9e303-103">您可以使用 `throw` 陳述式，明確擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9e303-103">You can explicitly throw an exception using the `throw` statement.</span></span> <span data-ttu-id="9e303-104">您也可以使用 `throw` 陳述式，再次擲回所攔截的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9e303-104">You can also throw a caught exception again using the `throw` statement.</span></span> <span data-ttu-id="9e303-105">建議您撰寫程式碼，將資訊加入要重新擲回的例外狀況，以在偵錯時提供更多資訊。</span><span class="sxs-lookup"><span data-stu-id="9e303-105">It is good coding practice to add information to an exception that is re-thrown to provide more information when debugging.</span></span>

<span data-ttu-id="9e303-106">下列程式碼範例使用 `try`/`catch` 區塊來攔截可能的 <xref:System.IO.FileNotFoundException>。</span><span class="sxs-lookup"><span data-stu-id="9e303-106">The following code example uses a `try`/`catch` block to catch a possible <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="9e303-107">`try` 區塊後面會接著 `catch` 區塊，該區塊可在找不到資料檔案時攔截 <xref:System.IO.FileNotFoundException>，並將訊息寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="9e303-107">Following the `try` block is a `catch` block that catches the <xref:System.IO.FileNotFoundException> and writes a message to the console if the data file is not found.</span></span> <span data-ttu-id="9e303-108">下一個陳述式是 `throw` 陳述式，會擲回新的 <xref:System.IO.FileNotFoundException> ，並將文字資訊新增到例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9e303-108">The next statement is the `throw` statement that throws a new <xref:System.IO.FileNotFoundException> and adds text information to the exception.</span></span>

[!code-csharp[Exception.Throwing#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a><span data-ttu-id="9e303-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="9e303-109">See Also</span></span>  
[<span data-ttu-id="9e303-110">例外狀況</span><span class="sxs-lookup"><span data-stu-id="9e303-110">Exceptions</span></span>](index.md)
