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
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a>作法：使用 finally 執行清除程式碼 (C# 程式設計手冊)
`finally` 陳述式的目的是為了確保在必要時會立即清除物件 (通常是含有外部資源的物件)，即使擲回例外狀況也一樣。 這類清除的一個例子，是在使用後立即呼叫 <xref:System.IO.FileStream> 的 <xref:System.IO.Stream.Close%2A>，而不等候 Common Language Runtime 回收物件的記憶體，如下所示：  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a>範例  
 為了將上述程式碼變成 `try-catch-finally` 陳述式，清除程式碼會與工作程式碼分開，如下所示。  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 因為在 `OpenWrite()` 呼叫之前，`try` 區塊內隨時都可能會發生例外狀況，或是 `OpenWrite()` 呼叫本身可能會失敗，所以在嘗試關閉檔案時不保證檔案處於開啟狀態。 `finally` 區塊新增檢查，先確定 <xref:System.IO.FileStream> 物件不是 `null`，再呼叫 <xref:System.IO.Stream.Close%2A> 方法。 如果沒有 `null` 檢查，`finally` 區塊可能會擲回本身的 <xref:System.NullReferenceException>，但應盡可能避免在 `finally` 區塊中擲回例外狀況。  
  
 在 `finally` 區塊中關閉資料庫連接是另一個不錯的選擇。 因為允許連接至資料庫伺服器的連接數目有時候是有限的，所以您應該盡快關閉資料庫連接。 如果在您可以關閉連接之前就擲回例外狀況，使用 `finally` 區塊會比等候記憶體回收更適合。  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [例外狀況和例外狀況處理](../../../csharp/programming-guide/exceptions/index.md)
- [例外狀況處理](../../../csharp/programming-guide/exceptions/exception-handling.md)
- [using 陳述式](../../../csharp/language-reference/keywords/using-statement.md)
- [try-catch](../../../csharp/language-reference/keywords/try-catch.md)
- [try-finally](../../../csharp/language-reference/keywords/try-finally.md)
- [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)
