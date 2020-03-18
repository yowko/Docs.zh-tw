---
title: 如何使用最後執行清理代碼 - C# 程式設計指南
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: d1ba761e64053d656ad4cd004133fc455a57c6f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705271"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a>如何使用最終執行清理代碼（C# 程式設計指南）
`finally` 陳述式的目的是為了確保在必要時會立即清除物件 (通常是含有外部資源的物件)，即使擲回例外狀況也一樣。 這類清除的一個例子，是在使用後立即呼叫 <xref:System.IO.FileStream> 的 <xref:System.IO.Stream.Close%2A>，而不等候 Common Language Runtime 回收物件的記憶體，如下所示：  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a>範例  
 為了將上述程式碼變成 `try-catch-finally` 陳述式，清除程式碼會與工作程式碼分開，如下所示。  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 因為在 `OpenWrite()` 呼叫之前，`try` 區塊內隨時都可能會發生例外狀況，或是 `OpenWrite()` 呼叫本身可能會失敗，所以在嘗試關閉檔案時不保證檔案處於開啟狀態。 `finally` 區塊新增檢查，先確定 <xref:System.IO.FileStream> 物件不是 `null`，再呼叫 <xref:System.IO.Stream.Close%2A> 方法。 如果沒有 `null` 檢查，`finally` 區塊可能會擲回本身的 <xref:System.NullReferenceException>，但應盡可能避免在 `finally` 區塊中擲回例外狀況。  
  
 在 `finally` 區塊中關閉資料庫連接是另一個不錯的選擇。 因為允許連接至資料庫伺服器的連接數目有時候是有限的，所以您應該盡快關閉資料庫連接。 如果在您可以關閉連接之前就擲回例外狀況，使用 `finally` 區塊會比等候記憶體回收更適合。  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [例外狀況和例外狀況處理](./index.md)
- [例外狀況處理](./exception-handling.md)
- [使用語句](../../language-reference/keywords/using-statement.md)
- [試捕](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
