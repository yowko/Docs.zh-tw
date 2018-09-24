---
title: 操作說明：使用 Try/Catch 區塊攔截例外狀況
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try blocks
- try/catch blocks
- catch blocks
ms.assetid: a3ce6dfd-1f64-471b-8ad8-8cfaf406275d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 852df5cb3eeea2ee5fa44ddce2f97e9c4f8d8b5a
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2018
ms.locfileid: "46699309"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>如何使用 try/catch 區塊攔截例外狀況

將可能擲回例外狀況的程式碼區段放在 `try` 區塊中，並將處理例外狀況的程式碼放在 `catch` 區塊中。 `catch` 區塊為一系列的陳述式，以關鍵字 `catch` 開頭，後面接著例外狀況類型和要採取的動作。

下列程式碼範例使用 `try`/`catch` 區塊攔截可能的例外狀況。 `Main` 方法包含內存 <xref:System.IO.StreamReader> 陳述式的 `try` 區塊，該陳述式可開啟名為 `data.txt` 的資料檔案，並寫入檔案中的字串。 `try` 區塊後面接著 `catch` 區塊，該區塊會攔截 `try` 區塊所產生的任何例外狀況。

 [!code-cpp[CatchException#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception2.cpp#3)]
 [!code-csharp[CatchException#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
 [!code-vb[CatchException#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]  

Common Language Runtime 會攔截 catch 區塊未攔截的例外狀況。 根據執行階段的設定方式，可能會發生下列其中一種情況：顯示偵錯對話方塊、程式停止執行並顯示內含例外狀況資訊的對話方塊，或錯誤印出至 STDERR。

> [!NOTE] 
> 幾乎任何一行程式碼都可能造成例外狀況，尤其是 Common Language Runtime 本身擲回的例外狀況，例如 <xref:System.OutOfMemoryException>。 大多數應用程式都不需要處理這些例外狀況，但您應該在撰寫供他人使用的程式庫時留意這點可能性。 如需何時在 Try 區塊中設定程式碼的建議，請參閱[例外狀況的最佳做法](best-practices-for-exceptions.md)。

## <a name="see-also"></a>另請參閱

- [例外狀況](index.md)
