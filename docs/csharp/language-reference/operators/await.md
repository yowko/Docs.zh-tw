---
title: await 運算子 - C# 參考
ms.date: 11/08/2019
f1_keywords:
- await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
ms.openlocfilehash: 9f541ae9c26eb12acdcf9a8c59bab98c4772c3b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173441"
---
# <a name="await-operator-c-reference"></a>await 運算子 (C# 參考)

`await` 運算子會暫停封入[非同步](../keywords/async.md)方法的評估，直到其運算元所代表的非同步作業完成為止。 當非同步作業完成時，`await` 運算子會傳回作業的結果 (如果有的話)。 當 `await` 運算子套用至代表已完成作業的運算元時，它會立即傳回作業的結果，而不會暫停封入方法。 `await` 運算子不會封鎖評估非同步方法的執行緒。 當`await`運算子掛起封閉非同步方法時，控制項將返回到方法的調用方。

在下列範例中，<xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> 方法會傳回 `Task<byte[]>` 執行個體，代表在完成時產生位元組陣列的非同步作業。 `await` 運算子會暫停 `DownloadDocsMainPageAsync` 方法，直到作業完成為止。 當 `DownloadDocsMainPageAsync` 暫停時，控制權會返回 `Main` 方法，也就是 `DownloadDocsMainPageAsync` 的呼叫端。 `Main` 方法會執行直到需要 `DownloadDocsMainPageAsync` 方法所執行的非同步作業結果為止。 當 <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> 取得所有位元組時，會評估 `DownloadDocsMainPageAsync` 方法的其餘部分。 之後，會評估 `Main` 方法的其餘部分。

[!code-csharp[await example](snippets/AwaitOperator.cs)]

前面的示例使用[非同步`Main`方法](../../programming-guide/main-and-command-args/index.md)，該方法可能從 C# 7.1 開始。 如需詳細資訊，請參閱 [Main 方法中的 await 運算子](#await-operator-in-the-main-method)一節。

> [!NOTE]
> 如需非同步程式設計的簡介，請參閱[使用 async 和 await 進行非同步程式設計](../../programming-guide/concepts/async/index.md)。 使用 `async` 和 `await` 進行非同步程式設計時，會遵循[以工作為基礎的非同步模式](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)。

您只能在以 [async](../keywords/async.md) 關鍵字修改的方法、[Lambda 運算式](../../programming-guide/statements-expressions-operators/lambda-expressions.md)或[匿名方法](delegate-operator.md)中使用 `await` 運算子。 在非同步方法中，不能在同步函數的正文`await`、[鎖語句](../keywords/lock-statement.md)的塊內和[不安全的](../keywords/unsafe.md)上下文中使用運算子。

`await` 運算子的運算元通常是下列其中一個 .NET 類型：<xref:System.Threading.Tasks.Task>、<xref:System.Threading.Tasks.Task%601>、<xref:System.Threading.Tasks.ValueTask> 或 <xref:System.Threading.Tasks.ValueTask%601>。 不過，任何可等候運算式都可以是 `await` 運算子的運算元。 如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[可等候運算式](~/_csharplang/spec/expressions.md#awaitable-expressions)一節。

從 C# 8.0 開始，可以使用`await foreach`語句使用非同步資料流程。 有關詳細資訊，請參閱[C# 8.0 文章中的"新增功能"中的](../../whats-new/csharp-8.md)[`foreach`語句](../keywords/foreach-in.md)文章和[非同步流](../../whats-new/csharp-8.md#asynchronous-streams)部分。

如果運算式 `t` 的類型為 <xref:System.Threading.Tasks.Task%601> 或 <xref:System.Threading.Tasks.ValueTask%601>，則運算式 `await t` 的類型為 `TResult`。 如果 `t` 的類型為 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.ValueTask>，則 `await t` 的類型為 `void`。 在這兩種情況下，如果 `t` 擲回例外狀況，`await t` 會重新擲回該例外狀況。 如需例外狀況處理的詳細資訊，請參閱 [try-catch 陳述式](../keywords/try-catch.md)一文的[非同步方法中的例外狀況](../keywords/try-catch.md#exceptions-in-async-methods)一節。

和`async``await`關鍵字在 C# 5 及更高版本中可用。

## <a name="await-operator-in-the-main-method"></a>Main 方法中的 await 運算子

從 C# 7.1 開始，[`Main`作為](../../programming-guide/main-and-command-args/index.md)應用程式進入點的方法可以返回`Task`或`Task<int>`，使其具有非同步，以便您可以在其正文中使用`await`運算子。 在舊版 C# 中，若要確保 `Main` 方法會等候非同步作業完成，您可以擷取對應非同步方法所傳回 <xref:System.Threading.Tasks.Task%601> 執行個體的 <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> 屬性值。 針對不會產生值的非同步作業，您可以呼叫 <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> 方法。 有關如何選擇語言版本的資訊，請參閱[C# 語言版本控制](../configure-language-version.md)。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的 [Await 運算式](~/_csharplang/spec/expressions.md#await-expressions)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
- [async](../keywords/async.md)
- [非同步工作程式設計模型](../../programming-guide/concepts/async/task-asynchronous-programming-model.md)
- [非同步程式設計](../../async.md)
- [深入了解非同步](../../../standard/async-in-depth.md)
- [演練：使用非同步和等待訪問 Web](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [教程：使用 C# 8.0 和 .NET Core 3.0 生成和使用非同步流](../../tutorials/generate-consume-asynchronous-stream.md)
