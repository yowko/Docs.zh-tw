---
title: '如何使用 try-catch 處理例外狀況-c # 程式設計指南'
description: 瞭解如何使用 try-catch 區塊來處理例外狀況。 請參閱程式碼範例，並查看其他可用的資源。
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
ms.openlocfilehash: 556f4459f5d1f8b7a7419122b640c661e182a51c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178654"
---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>如何使用 try/catch 處理例外狀況 (c # 程式設計手冊) 

[try-catch](../../language-reference/keywords/try-catch.md) 區塊的目的是為了攔截和處理工作程式碼所產生的例外狀況。 某些例外狀況可在 `catch` 區塊中處理，並且可以解決問題而不會重新擲回例外狀況；不過，通常您只能用於確保會擲回適當的例外狀況。  
  
## <a name="example"></a>範例  

 在此範例中，<xref:System.IndexOutOfRangeException> 不是最適當的例外狀況︰<xref:System.ArgumentOutOfRangeException> 更適用於此方法，因為錯誤是由呼叫者傳入的 `index` 引數所導致。  
  
 [!code-csharp[csProgGuideExceptions#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#5)]  
  
## <a name="comments"></a>註解  

 造成例外狀況的程式碼位於 `try` 區塊中。 緊接在後面新增的 `catch` 陳述式可處理所發生的 `IndexOutOfRangeException`。 `catch` 區塊會處理 `IndexOutOfRangeException`，然後改為擲回更適當的 `ArgumentOutOfRangeException` 例外狀況。 為了盡可能為呼叫者提供更多資訊，請考慮將原始的例外狀況指定為新例外狀況的 <xref:System.Exception.InnerException%2A>。 因為 <xref:System.Exception.InnerException%2A> 屬性是唯讀的，所以您必須在新例外狀況的函 [式](../../properties.md#read-only)中指派它。  
  
## <a name="see-also"></a>另請參閱

- [C # 程式設計指南](../index.md)
- [例外狀況和例外狀況處理](./index.md)
- [例外狀況處理](./exception-handling.md)
