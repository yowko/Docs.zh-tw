---
title: 如何：使用 try-catch 處理例外狀況 (C# 程式設計指南)
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
ms.openlocfilehash: 74503c510007b132a7bbb14da7eade4c379b2179
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43856571"
---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>如何：使用 try/catch 處理例外狀況 (C# 程式設計手冊)
[try-catch](../../../csharp/language-reference/keywords/try-catch.md) 區塊的目的是為了攔截和處理工作程式碼所產生的例外狀況。 某些例外狀況可在 `catch` 區塊中處理，並且可以解決問題而不會重新擲回例外狀況；不過，通常您只能用於確保會擲回適當的例外狀況。  
  
## <a name="example"></a>範例  
 在此範例中，<xref:System.IndexOutOfRangeException> 不是最適當的例外狀況︰<xref:System.ArgumentOutOfRangeException> 更適用於此方法，因為錯誤是由呼叫者傳入的 `index` 引數所導致。  
  
 [!code-csharp[csProgGuideExceptions#5](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-handle-an-exception-using-try-catch_1.cs)]  
  
## <a name="comments"></a>註解  
 造成例外狀況的程式碼位於 `try` 區塊中。 緊接在後面新增的 `catch` 陳述式可處理所發生的 `IndexOutOfRangeException`。 `catch` 區塊會處理 `IndexOutOfRangeException`，然後改為擲回更適當的 `ArgumentOutOfRangeException` 例外狀況。 為了盡可能為呼叫者提供更多資訊，請考慮將原始的例外狀況指定為新例外狀況的 <xref:System.Exception.InnerException%2A>。 因為 <xref:System.Exception.InnerException%2A> 屬性為 [readonly](../../../csharp/language-reference/keywords/readonly.md)，所以您必須在新例外狀況的建構函式中指派此屬性。  
  
## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [例外狀況和例外狀況處理](../../../csharp/programming-guide/exceptions/index.md)  
- [例外狀況處理](../../../csharp/programming-guide/exceptions/exception-handling.md)
