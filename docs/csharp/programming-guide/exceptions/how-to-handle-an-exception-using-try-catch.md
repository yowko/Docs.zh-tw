---
title: '如何使用 try-catch 處理例外狀況-c # 程式設計指南'
description: 瞭解如何使用 try-catch 區塊來處理例外狀況。 請參閱程式碼範例，並查看其他可用的資源。
ms.date: 12/09/2020
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
ms.openlocfilehash: b6368660dbe037123f5bb6ce52502d4a94fcfc3a
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110516"
---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>如何使用 try/catch 處理例外狀況 (c # 程式設計手冊) 

[try-catch](../../language-reference/keywords/try-catch.md) 區塊的目的是為了攔截和處理工作程式碼所產生的例外狀況。 某些例外狀況可以在區塊中處理 `catch` ，而解決問題，而不會重新擲回例外狀況; 不過，您可以執行的唯一動作是確定擲回適當的例外狀況。

## <a name="example"></a>範例

在此範例中， <xref:System.IndexOutOfRangeException> 不是最適當的例外狀況：對 <xref:System.ArgumentOutOfRangeException> 方法來說更有意義，因為錯誤是由 `index` 呼叫者傳入的引數所造成。

:::code language="csharp" source="snippets/exceptions/ExampleTryCatch.cs" id="ExampleTryCatch":::

## <a name="comments"></a>註解

造成例外狀況的程式碼位於 `try` 區塊中。 緊接在後面新增的 `catch` 陳述式可處理所發生的 `IndexOutOfRangeException`。 `catch` 區塊會處理 `IndexOutOfRangeException`，然後改為擲回更適當的 `ArgumentOutOfRangeException` 例外狀況。 為了盡可能為呼叫者提供更多資訊，請考慮將原始的例外狀況指定為新例外狀況的 <xref:System.Exception.InnerException%2A>。 因為 <xref:System.Exception.InnerException%2A> 屬性是唯讀的，所以您必須在新例外狀況的函 [式](../../properties.md#read-only)中指派它。
