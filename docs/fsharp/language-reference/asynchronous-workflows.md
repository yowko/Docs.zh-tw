---
title: 非同步工作流程 (F#)
description: '了解支援的 F # 程式語言，以非同步方式執行計算的詳細執行而不封鎖其他工作的執行。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 1521ea3719f906a45b11d19a27256e87c5643e28
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="asynchronous-workflows"></a>非同步工作流程

> [!NOTE]
API 參考連結將帶您前往 MSDN。  docs.microsoft.com API 參考不完整。

本主題描述支援 F # 中的執行的計算以非同步的方式，亦即，而不會封鎖執行其他工作。 例如，非同步計算可用來撰寫為應用程式會執行其他工作能繼續回應使用者的 Ui 的應用程式。

## <a name="syntax"></a>語法

```fsharp
async { expression }
```

## <a name="remarks"></a>備註

在上一個語法中，計算由`expression`並將設定為以非同步方式執行，也就是說，而不會封鎖目前的計算執行緒睡眠非同步作業、 I/O 和其他非同步作業執行的時間。 同時執行會繼續目前的執行緒上非同步計算通常會啟動背景執行緒上。 運算式的類型是`Async<'T>`，其中`'T`是運算式所傳回的型別時`return`關鍵字使用。 這類運算式中的程式碼指*非同步區塊*，或*非同步區塊*。

有各種不同的非同步程式設計的方式和[ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)類別會提供方法，可支援幾個案例。 一般方法是建立`Async`物件，代表計算或您想要以非同步方式執行的計算，並使用其中一個觸發的函式，以啟動這些計算。 各種觸發函式提供不同的方式執行非同步計算，以及您使用這個資料行依存於您是否想要使用目前的執行緒，背景執行緒或.NET Framework 工作物件，以及是否有接續在計算完成時應該執行的函式。 例如，若要在目前的執行緒上開始非同步的計算，您可以使用[ `Async.StartImmediate` ](https://msdn.microsoft.com/library/2f71d1cc-187f-48cf-ac66-e7fda41c46e3)。 當您從 UI 執行緒開始非同步的計算時，您不會封鎖主要事件迴圈處理使用者動作，例如按鍵及滑鼠活動，因此您的應用程式仍然能夠保持回應。

## <a name="asynchronous-binding-by-using-let"></a>使用可讓非同步繫結 ！

非同步工作流程中，在某些運算式和作業是同步的而有些則用來以非同步方式傳回結果的時間計算。 當您呼叫的方法以非同步的方式，而不是一般`let`繫結，請使用`let!`。 效果`let!`是要讓正在執行，以計算為其他運算或在執行緒上繼續執行。 在右邊的 list 之後`let!`繫結傳回時，非同步工作流程的其餘部分會繼續執行。

下列程式碼顯示之間的差異`let`和`let!`。 使用的程式碼行`let`則只會建立為物件，您可以稍後再執行所使用，例如，非同步計算`Async.StartImmediate`或[ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b)。 使用的程式碼行`let!`開始計算，並再暫止執行緒的結果，直到可用在哪個點執行會持續。

```fsharp
// let just stores the result as an asynchronous operation.
let (result1 : Async<byte[]>) = stream.AsyncRead(bufferSize)
// let! completes the asynchronous operation and returns the data.
let! (result2 : byte[])  = stream.AsyncRead(bufferSize)
```

除了`let!`，您可以使用`use!`執行非同步的繫結。 之間的差異`let!`和`use!`之間的差異相同`let`和`use`。 如`use!`，物件已處置的在目前範圍的結束。 請注意，在目前版本的 F # 語言，`use!`不允許的值，初始化為 null，即使`use`沒有。

## <a name="asynchronous-primitives"></a>非同步基本項目

執行單一的非同步工作，並傳回結果的方法會呼叫*非同步基本型別*，以及這些專為搭配`let!`。 數個非同步基本型别都定義在 F # 核心程式庫中。 Web 應用程式的兩個這類方法會在模組中定義[ `Microsoft.FSharp.Control.WebExtensions` ](https://msdn.microsoft.com/library/95ef17bc-ee3f-44ba-8a11-c90fcf4cf003): [ `WebRequest.AsyncGetResponse` ](https://msdn.microsoft.com/library/09a60c31-e6e2-4b5c-ad23-92a86e50060c)和[ `WebClient.AsyncDownloadString` ](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a)。 這兩個基本項目從網頁上，假設有一個 URL 下載資料。 `AsyncGetResponse` 會產生`System.Net.WebResponse`物件，和`AsyncDownloadString`會產生表示網頁的 HTML 字串。

非同步 I/O 作業數個基本類型中包含[ `Microsoft.FSharp.Control.CommonExtensions` ](https://msdn.microsoft.com/library/2edb67cb-6814-4a30-849f-b6dbdd042396)模組。 這些擴充方法`System.IO.Stream`類別[ `Stream.AsyncRead` ](https://msdn.microsoft.com/library/85698aaa-bdda-47e6-abed-3730f59fda5e)和[ `Stream.AsyncWrite` ](https://msdn.microsoft.com/library/1b0a2751-e42a-47e1-bd27-020224adc618)。

中的其他非同步的基本項目可用[F # PowerTools](https://fsprojects.github.io/VisualFSharpPowerTools/)。 您也可以藉由定義其完整的內文被括在非同步區塊中的函式來撰寫您自己的非同步基本項目。

若要使用其他非同步模型的 F # 非同步程式設計模型與.NET Framework 中設計的非同步方法，您可以建立傳回 F # 的函式`Async`物件。 F # 程式庫有方便執行的函式。

使用非同步工作流程的其中一個範例是包含以下;還有許多其他的方法的文件中[Async 類別](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)。

這個範例示範如何使用非同步工作流程以平行方式執行計算。

在下列程式碼範例中，函式`fetchAsync`取得來自 Web 要求傳回 HTML 文字。 `fetchAsync`函式包含的非同步程式碼區塊。 繫結進行時結果的非同步的基本型別，在此情況下[ `AsyncDownloadString` ](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a)，讓 ！ 會用來讓取代。

您可以使用函數[ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b)來執行非同步作業，並等候其結果。 例如，您可以執行多個非同步作業以平行方式使用[ `Async.Parallel` ](https://msdn.microsoft.com/library/aa9b0355-2d55-4858-b943-cbe428de9dc4)函數搭配`Async.RunSynchronously`函式。 `Async.Parallel`函式的清單`Async`物件資訊，請針對每個程式碼會設定`Async`task 物件以平行方式，並傳回在執行`Async`物件，表示平行計算。 在您呼叫一樣可以在單一作業`Async.RunSynchronously`即可開始執行。

`runAll`函式會啟動三個平行的非同步工作流程，並等待，直到所有必須完成它們。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet8003.fs)]

## <a name="see-also"></a>另請參閱

[F# 語言參考](index.md)

[計算運算式](computation-expressions.md)

[Control.Async 類別](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.async-class-%5bfsharp%5d)
