---
title: 使用例外狀況 - C# 程式設計手冊
description: 瞭解如何使用例外狀況。 例外狀況是由遇到錯誤的程式碼所擲回，並由修正錯誤的程式碼所攔截。
ms.date: 12/09/2020
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], about exceptions
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
ms.openlocfilehash: 30a7c3eecb599493dfa74d664c4899836c1b9276
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110217"
---
# <a name="use-exceptions-c-programming-guide"></a>使用例外狀況 (c # 程式設計手冊) 

在 C# 中，若程式在執行階段發生錯誤，會利用一種稱為例外狀況的機制，讓整個程式都得知此狀況。 例外狀況是由遇到錯誤的程式碼所擲回，並由可以更正此錯誤的程式碼所攔截。 .NET 執行時間或程式中的程式碼可能會擲回例外狀況。 一旦擲回了例外狀況，便會在呼叫堆疊中將此訊息往上傳，直至找到例外狀況的 `catch` 陳述式為止。 未被攔截的例外狀況會由系統提供的泛型例外處理常式負責處理，這時會顯示對話方塊。

例外狀況會以衍生自 <xref:System.Exception> 的類別表示。 此類別會識別例外狀況的類型，並包含具有例外狀況詳細資料的屬性。 擲回例外狀況的作業包括建立例外狀況衍生類別的執行個體、選擇性地設定例外狀況的屬性，然後使用 `throw` 關鍵字擲回物件。 例如：

:::code language="csharp" source="snippets/exceptions/Program.cs" id="ThrowException":::

擲回例外狀況之後，執行階段會檢查目前的陳述式是否在 `try` 區塊內。 如果是的話，便會檢查與 `try` 區塊關聯的任何 `catch` 區塊，以查看其是否能攔截該例外狀況。 `Catch` 區塊通常會指定例外狀況類型；如果 `catch` 區塊的類型與例外狀況或其基底類別的類型相同，`catch` 區塊便可處理此方法。 例如：

:::code language="csharp" source="snippets/exceptions/Program.cs" id="CatchException":::

如果擲回例外狀況的語句不在 `try` 區塊內，或如果 `try` 封閉它的區塊沒有相符的 `catch` 區塊，則執行時間會檢查 `try` 語句和區塊的呼叫方法 `catch` 。 執行階段會繼續在呼叫堆疊中往上搜尋，直到找到相容的 `catch` 區塊。 找到並執行 `catch` 區塊之後，控制項就會傳遞至該 `catch` 區塊後面的下一個陳述式。

`try` 陳述式可以包含多個 `catch` 區塊。 系統會 `catch` 執行可處理例外狀況的第一個語句; 任何下列 `catch` 語句（即使它們相容）都會被忽略。 Catch 區塊應該一律從最特定的 (或最常衍生的) 排列到最不特定的。 例如：

:::code language="csharp" source="snippets/exceptions/CatchOrder.cs":::

執行 `catch` 之前，執行階段會檢查 `finally` 區塊。 `Finally` 區塊可讓程式設計師清除任何不明確的狀態，這些狀態可能會從中止的區塊中移除 `try` ，或釋放任何外部資源 (例如圖形控制碼、資料庫連接或檔案資料流程) ，而不需要等待執行時間的垃圾收集行程完成物件。 例如：

:::code language="csharp" source="snippets/exceptions/Program.cs" id="TestFinally":::

如果擲 `WriteByte()` 回例外狀況，則嘗試重新開啟檔案的第二個區塊中的 `try` 程式碼會在未呼叫時失敗 `file.Close()` ，而且檔案會保持鎖定。 由於即使擲回例外狀況也會執行 `finally` 區塊，因此上述範例中的 `finally` 區塊可讓檔案正常關閉，並協助避免發生錯誤。

擲回例外狀況之後，如果在呼叫堆疊中找不到相容的 `catch` 區塊，則會發生下列三種情況的其中一種：

- 如果例外狀況在完成項內，就會中止完成項並呼叫基底完成項 (如果有)。
- 如果呼叫堆疊包含靜態建構函式或靜態欄位初始設定式，則會擲回 <xref:System.TypeInitializationException>，同時將原始例外狀況指派給新例外狀況的 <xref:System.Exception.InnerException%2A> 屬性。
- 如果到達執行緒的開頭，則會終止執行緒。
