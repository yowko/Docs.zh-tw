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
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a>如何使用 finally 執行清除程式碼 (c # 程式設計手冊) 

`finally` 陳述式的目的是為了確保在必要時會立即清除物件 (通常是含有外部資源的物件)，即使擲回例外狀況也一樣。 這類清除的一個例子，是在使用後立即呼叫 <xref:System.IO.FileStream> 的 <xref:System.IO.Stream.Close%2A>，而不等候 Common Language Runtime 回收物件的記憶體，如下所示：

:::code language="csharp" source="snippets/exceptions/Program.cs" ID="NoCleanup":::

## <a name="example"></a>範例

為了將上述程式碼變成 `try-catch-finally` 陳述式，清除程式碼會與工作程式碼分開，如下所示。

:::code language="csharp" source="snippets/exceptions/Program.cs" ID="WithCleanup":::

由於例外狀況可能會在呼叫之前的任何時間發生 `try` `OpenWrite()` ，或是 `OpenWrite()` 呼叫本身可能失敗，因此我們不保證在嘗試關閉檔案時，檔案是開啟的。 `finally`區塊會新增檢查，以確保 <xref:System.IO.FileStream> 物件不 `null` 會在呼叫方法之前 <xref:System.IO.Stream.Close%2A> 。 如果沒有 `null` 檢查， `finally` 區塊可能會擲回它自己的 <xref:System.NullReferenceException> ，但 `finally` 如果可能的話，應避免在區塊中擲回例外狀況。

在 `finally` 區塊中關閉資料庫連接是另一個不錯的選擇。 因為允許連接至資料庫伺服器的連接數目有時候是有限的，所以您應該盡快關閉資料庫連接。 如果在關閉連接之前擲回例外狀況，使用 `finally` 區塊比等候垃圾收集更好。

## <a name="see-also"></a>另請參閱

- [using 陳述式](../../language-reference/keywords/using-statement.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
