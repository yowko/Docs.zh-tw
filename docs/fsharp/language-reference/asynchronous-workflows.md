---
title: 非同步工作流程
description: 深入瞭解以非同步方式F#執行計算的程式設計語言支援, 這會執行, 而不會封鎖其他工作的執行。
ms.date: 05/16/2016
ms.openlocfilehash: 2d967f6bfe46b4f3916648b3063210d1ba1c210f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630009"
---
# <a name="asynchronous-workflows"></a>非同步工作流程

> [!NOTE]
> API 參考連結將帶您前往 MSDN。  docs.microsoft.com API 參考不完整。

本主題描述如何以F#非同步方式執行計算 (也就是不會封鎖執行其他工作) 的支援。 例如, 當應用程式執行其他工作時, 可以使用非同步計算來撰寫應用程式, 使其具有可回應使用者的 Ui。

## <a name="syntax"></a>語法

```fsharp
async { expression }
```

## <a name="remarks"></a>備註

在先前的語法中, 所代表`expression`的計算會設定為以非同步方式執行, 也就是在執行非同步睡眠作業、i/o 和其他非同步作業時, 不會封鎖目前的計算執行緒。 非同步計算通常會在背景執行緒上啟動, 同時繼續在目前的執行緒上執行。 運算式的類型是`Async<'T>`, 其中`'T`是使用`return`關鍵字時, 運算式所傳回的類型。 這類運算式中的程式碼稱為*非同步區塊*或*非同步區塊*。

有各種不同的非同步程式設計方式, 而類別則[`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)提供支援數種案例的方法。 一般的方法是建立`Async`物件, 以代表您想要以非同步方式執行的計算或計算, 然後使用其中一個觸發函數來啟動這些計算。 各種觸發函式提供不同的方式來執行非同步計算, 而您使用哪一個方法取決於您要使用目前的執行緒、背景執行緒或 .NET Framework 工作物件, 以及是否有接續計算完成時應執行的函式。 例如, 若要在目前的執行緒上啟動非同步計算, 您可以使用[`Async.StartImmediate`](https://msdn.microsoft.com/library/2f71d1cc-187f-48cf-ac66-e7fda41c46e3)。 當您從 UI 執行緒啟動非同步計算時, 不會封鎖處理使用者動作 (例如按鍵和滑鼠活動) 的主要事件迴圈, 讓您的應用程式保持回應。

## <a name="asynchronous-binding-by-using-let"></a>使用 let 的非同步綁定

在非同步工作流程中, 某些運算式和作業是同步的, 有些則是設計來以非同步方式傳回結果的較長計算。 當您以非同步方式呼叫方法, 而不是`let`一般的系結`let!`時, 您會使用。 的作用`let!`是在執行計算時, 讓其他計算或執行緒繼續執行。 在系結的右側`let!`傳回之後, 非同步工作流程的其餘部分會繼續執行。

下列程式碼顯示和`let` `let!`之間的差異。 使用`let`的程式程式碼只會建立異步計算, 做為您稍後可以使用`Async.StartImmediate`來執行的物件, 例如或[`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b)。 使用`let!`的程式程式碼會啟動計算, 然後執行緒會暫停直到結果可供使用為止, 此時就會繼續執行。

```fsharp
// let just stores the result as an asynchronous operation.
let (result1 : Async<byte[]>) = stream.AsyncRead(bufferSize)
// let! completes the asynchronous operation and returns the data.
let! (result2 : byte[])  = stream.AsyncRead(bufferSize)
```

除了之外`let!`, 您還可以使用`use!`來執行非同步系結。 和`let!` `let` `use`之間的差異與和之間的差異相同。 `use!` 若是`use!`, 物件會在目前範圍結束時處置。 請注意, 在目前的F#語言版本中, `use!`不允許將值初始化為 null, 即使這樣也一樣。 `use`

## <a name="asynchronous-primitives"></a>非同步基本專案

執行單一非同步工作並傳回結果的方法稱為「*非同步基本*」, 而且這些都是特別設計來搭配使用`let!`。 F#核心程式庫中定義了數個非同步基本類型。 這兩種 Web 應用程式的方法都是在[`Microsoft.FSharp.Control.WebExtensions`](https://msdn.microsoft.com/library/95ef17bc-ee3f-44ba-8a11-c90fcf4cf003)模組[`WebRequest.AsyncGetResponse`](https://msdn.microsoft.com/library/09a60c31-e6e2-4b5c-ad23-92a86e50060c)中[`WebClient.AsyncDownloadString`](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a)定義: 和。 這兩個原始物件會在指定 URL 的情況下, 從網頁下載資料。 `AsyncGetResponse`產生物件, 並`AsyncDownloadString`產生代表網頁 HTML 的字串。 `System.Net.WebResponse`

[`Microsoft.FSharp.Control.CommonExtensions`](https://msdn.microsoft.com/library/2edb67cb-6814-4a30-849f-b6dbdd042396)模組中包含數個非同步 i/o 作業的基本專案。 這些`System.IO.Stream`類別的擴充方法為[`Stream.AsyncRead`](https://msdn.microsoft.com/library/85698aaa-bdda-47e6-abed-3730f59fda5e)和[`Stream.AsyncWrite`](https://msdn.microsoft.com/library/1b0a2751-e42a-47e1-bd27-020224adc618)。

您也可以藉由定義函式, 其完整主體會包含在非同步區塊中, 來撰寫您自己的非同步基本專案。

若要在 .NET Framework 中使用非同步方法, 而這些方法是針對使用F#非同步程式設計模型的其他非同步模型所設計, 您F# `Async`可以建立可傳回物件的函式。 此F#程式庫具有可讓您輕鬆執行此動作的功能。

這裡包含一個使用非同步工作流程的範例:在檔中,[非同步類別](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)的方法有許多其他功能。

這個範例示範如何使用非同步工作流程, 以平行方式執行計算。

在下列程式碼範例中, `fetchAsync`函式會取得 Web 要求所傳回的 HTML 文字。 `fetchAsync`函式包含非同步程式碼區塊。 當對非同步基本物件的結果進行系結時, 在此情況下[`AsyncDownloadString`](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a), 請讓! 會使用, 而不是 let。

您可以使用[`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b)函式來執行非同步作業, 並等候其結果。 例如, 您可以搭配函式一起[`Async.Parallel`](https://msdn.microsoft.com/library/aa9b0355-2d55-4858-b943-cbe428de9dc4) `Async.RunSynchronously`使用函式, 以平行方式執行多個非同步作業。 函式會取得`Async`物件的清單、設定每個`Async`工作物件的程式碼`Async`以平行方式執行, 並傳回代表平行計算的物件。 `Async.Parallel` 就像單一作業一樣, 您可以呼叫`Async.RunSynchronously`來開始執行。

`runAll`函式會平行啟動三個非同步工作流程, 並等待它們全部完成。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet8003.fs)]

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [計算運算式](computation-expressions.md)
- [控制項 Async 類別](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.async-class-%5bfsharp%5d)
