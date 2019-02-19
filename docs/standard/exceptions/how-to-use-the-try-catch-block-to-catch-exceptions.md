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
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>如何使用 try/catch 區塊攔截例外狀況

將任何可能引發或擲回例外狀況的程式碼陳述式放置於 `try` 區塊，並將用來處理例外狀況的陳述式放置於 `try` 區塊之下的一或多個 `catch` 區塊中。 每個 `catch` 區塊都會包含例外狀況類型，而且可以包含處理該例外狀況類型所需的其他陳述式。

在下列範例中，<xref:System.IO.StreamReader> 開啟名為 *data.txt* 的檔案，並從該檔案擷取了一行。 因為程式碼可能會擲回三個例外狀況的任何一個，所以將其放置於 `try` 區塊。 三個 `catch` 區塊可以藉由將結果顯示給主控台，來攔截例外狀況並加以處理。

[!code-csharp[CatchException#3](~/samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
[!code-vb[CatchException#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]  

通用語言執行平台 (CLR) 會攔截 `catch` 區塊未處理的例外狀況。 如果 CLR 攔截了例外狀況，可能會發生下列其中一種結果，視您的 CLR 組態而有所不同：

- [偵錯] 對話方塊隨即出現。
- 程式停止執行，內容為例外狀況資訊的對話方塊隨即出現。
- 錯誤會輸出至[標準錯誤輸出資料流](xref:System.Console.Error)。

> [!NOTE]
> 多數程式碼可以擲回例外狀況，而且某些例外狀況 (例如 <xref:System.OutOfMemoryException>) 可能在任何時間由 CLR 本身擲回。 雖然應用程式不必處理這些例外狀況，但是請在撰寫供他人使用的程式庫時注意其發生的可能性。 如需何時在 `try` 區塊中設定程式碼的建議，請參閱[例外狀況的最佳做法](best-practices-for-exceptions.md)。

## <a name="see-also"></a>另請參閱

[例外狀況](index.md)  
[在 .NET 中處理 I/O 錯誤](../io/handling-io-errors.md)
