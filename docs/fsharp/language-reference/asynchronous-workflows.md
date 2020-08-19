---
title: 非同步工作流程
description: '瞭解 F # 程式設計語言中的支援以非同步方式執行計算，而不會封鎖執行其他工作。'
ms.date: 08/15/2020
ms.openlocfilehash: ac727fc630f13db01da964131ab39dc242a12cd1
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557707"
---
# <a name="asynchronous-workflows"></a>非同步工作流程

本文描述 F # 中的支援以非同步方式執行計算，也就是不會封鎖其他工作的執行。 例如，您可以使用非同步計算來撰寫應用程式，這些應用程式的 Ui 會在應用程式執行其他工作時，仍能回應使用者。

## <a name="syntax"></a>語法

```fsharp
async { expression }
```

## <a name="remarks"></a>備註

在先前的語法中，的計算 `expression` 是設定為以非同步方式執行，也就是在執行非同步睡眠作業、i/o 和其他非同步作業時，不會封鎖目前的計算執行緒。 非同步計算通常會在背景執行緒上啟動，而在目前的執行緒上繼續執行。 運算式的型別是 `Async<'T>` ，其中 `'T` 是使用關鍵字時，運算式所傳回的型別 `return` 。 這類運算式中的程式碼稱為 *非同步區塊*或 *非同步區塊*。

非同步程式設計的方式有許多種，而類別則 [`Async`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html) 提供支援數個案例的方法。 一般的方法是建立 `Async` 物件，以代表您想要以非同步方式執行的計算或計算，然後使用其中一個觸發函數來啟動這些計算。 不同的觸發函式提供不同的方式來執行非同步計算，而您要使用哪一個方法取決於您要使用目前的執行緒、背景執行緒或 .NET Framework 工作物件，以及在計算完成時是否應該執行接續函數。 例如，若要在目前的執行緒上啟動非同步計算，您可以使用 [`Async.StartImmediate`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#StartImmediate) 。 當您從 UI 執行緒啟動非同步計算時，不會封鎖處理使用者動作（例如按鍵和滑鼠活動）的主要事件迴圈，讓應用程式保持回應。

## <a name="asynchronous-binding-by-using-let"></a>使用 let！的非同步綁定

在非同步工作流程中，某些運算式和作業是同步的，有些則是較長的計算，其設計目的是要以非同步方式傳回結果。 當您以非同步方式呼叫方法，而不是使用一般系結時 `let` ，就會使用 `let!` 。 的作用 `let!` 是在執行計算時，讓執行在其他計算或執行緒上繼續執行。 在系結的右側傳回之後 `let!` ，其餘的非同步工作流程會繼續執行。

下列程式碼顯示與之間的 `let` 差異 `let!` 。 使用的程式程式碼 `let` 只會建立異步計算做為物件，您稍後可以使用來執行，例如 `Async.StartImmediate` 或 [`Async.RunSynchronously`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#RunSynchronously) 。 使用的程式程式碼 `let!` 會開始計算，然後執行緒會暫停，直到結果可用為止，此時會繼續執行。

```fsharp
// let just stores the result as an asynchronous operation.
let (result1 : Async<byte[]>) = stream.AsyncRead(bufferSize)
// let! completes the asynchronous operation and returns the data.
let! (result2 : byte[])  = stream.AsyncRead(bufferSize)
```

除了之外 `let!` ，您還可以使用 `use!` 來執行非同步系結。 和之間的差異與 `let!` `use!` 和之間的差異相同 `let` `use` 。 若為 `use!` ，則會在目前的範圍結束時處置物件。 請注意，在目前的 F # 語言版本中，不 `use!` 允許將值初始化為 null，即使這樣做也一樣 `use` 。

## <a name="asynchronous-primitives"></a>非同步基本類型

執行單一非同步工作並傳回結果的方法，稱為 *非同步基本*類型，而這些是專門設計來搭配使用 `let!` 。 F # 核心程式庫中定義了數個非同步基本類型。 這兩種 Web 應用程式的方法都是在模組中定義 [`FSharp.Control.WebExtensions`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-webextensions.html) ： [`WebRequest.AsyncGetResponse`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-webextensions.html#AsyncGetResponse) 和 [`WebClient.AsyncDownloadString`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-webextensions.html#AsyncDownloadString) 。 這兩個基本專案都會從網頁下載資料（假設有一個 URL）。 `AsyncGetResponse` 產生 `System.Net.WebResponse` 物件，並 `AsyncDownloadString` 產生表示網頁 HTML 的字串。

課程模組中包含數個非同步 i/o 作業的基本專案 [`FSharp.Control.CommonExtensions`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-commonextensions.html) 。 類別的這些擴充方法 `System.IO.Stream` 為 [`Stream.AsyncRead`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-commonextensions.html#AsyncRead) 和 [`Stream.AsyncWrite`](hhttps://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-commonextensions.html#AsyncWrite) 。

您也可以藉由定義一個函式，其完整主體會以非同步區塊括住，以撰寫您自己的非同步基本專案。

若要在使用 F # 非同步程式設計模型的其他非同步模型所設計的 .NET Framework 中使用非同步方法，您可以建立會傳回 F # 物件的函式 `Async` 。 F # 程式庫具有可讓您輕鬆執行此作業的函式。

這裡包含使用非同步工作流程的其中一個範例;檔中有許多其他的方法，適用于 [非同步類別](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html)的方法。

此範例示範如何使用非同步工作流程，以平行方式執行計算。

在下列程式碼範例中，函式會 `fetchAsync` 取得 Web 要求所傳回的 HTML 文字。 `fetchAsync`函數包含非同步程式碼區塊。 當您對非同步基本的結果進行系結時，在此情況下 [`AsyncDownloadString`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-webextensions.html#AsyncDownloadString) ， `let!` 會使用，而不是 `let` 。

您可以使用函數 [`Async.RunSynchronously`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#RunSynchronously) 來執行非同步作業，並等候其結果。 例如，您可以使用函式搭配函數來平行執行多個非同步作業 [`Async.Parallel`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#Parallel) `Async.RunSynchronously` 。 此函式 `Async.Parallel` 會取得物件的清單 `Async` 、將每個工作物件的程式碼設定 `Async` 為平行執行，並傳回 `Async` 代表平行計算的物件。 就像單一作業一樣，您可以呼叫 `Async.RunSynchronously` 來開始執行。

函式 `runAll` 會以平行方式啟動三個非同步工作流程，並等候直到全部完成為止。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet8003.fs)]

## <a name="see-also"></a>另請參閱

- [F # 語言參考](index.md)
- [計算運算式](computation-expressions.md)
- [Control. Async 類別](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.async-class-%5bfsharp%5d)
