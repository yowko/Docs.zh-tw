---
title: "實作以工作為基礎的非同步模式"
ms.date: 06/14/2017
ms.prod: .net
ms.technology:
- dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: fab6bd41-91bd-44ad-86f9-d8319988aa78
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 238f164fec78fe5e6dae9e7880fabc0a386bf399
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-the-task-based-asynchronous-pattern"></a>實作以工作為基礎的非同步模式
您可以採用三種方式實作工作式非同步模式 (TAP)：使用 Visual Studio 中的 C# 和 Visual Basic 編譯器、手動，或是透過編譯器和手動方法的組合。 下列章節詳細討論每一種方法。 您可以使用 TAP 方法實作計算繫結和 I/O 繫結的非同步作業。 [工作負載](#workloads)一節討論每種作業類型。

## <a name="generating-tap-methods"></a>產生 TAP 方法

### <a name="using-the-compilers"></a>使用編譯器
從 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 開始，屬性具有 `async` 關鍵字 (在 Visual Basic 中為 `Async`) 的任何方法都會視為非同步方法，而 C# 和 Visual Basic 編譯器會使用 TAP 執行必要的轉換，藉此透過非同步的方式實作這個方法。 非同步方法應該傳回 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 或 <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> 物件。 若是後者，函式主體應該會傳回 `TResult`，而編譯器會確保這個結果是透過產生的工作物件提供。 同樣地，方法主體內未處理的任何例外狀況會封送處理至輸出工作，並導致產生的工作在 <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> 狀態結束。 例外狀況就是當 <xref:System.OperationCanceledException> (或衍生類型) 未處理時，此時產生的工作會在 <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> 狀態結束。

### <a name="generating-tap-methods-manually"></a>以手動方式產生 TAP 方法
您可以手動實作 TAP 模式，以便更有效控制實作。 編譯器會依賴從 <xref:System.Threading.Tasks?displayProperty=nameWithType> 命名空間公開的公用表面區域，和 <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> 命名空間中的支援類型。 若要自行實作 TAP，請建立 <xref:System.Threading.Tasks.TaskCompletionSource%601> 物件、執行非同步作業，並完成之後呼叫 <xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A>、<xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A> 或 <xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A> 方法，或其中一個方法的 `Try` 版本。 當您以手動方式實作 TAP 方法時，您必須在代表的非同步作業完成時，完成產生的工作。 例如: 

[!code-csharp[Conceptual.TAP_Patterns#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#1)]
[!code-vb[Conceptual.TAP_Patterns#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#1)]

### <a name="hybrid-approach"></a>混合式方法
 您可能會發現以手動方式實作 TAP 模式，但將實作的核心邏輯委派給編譯器很實用。 例如，當您想要確認編譯器產生的非同步方法之外的引數時，您可能會想要使用混合方法，以便例外狀況可以逸出方法的直接呼叫端，而非透過 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 物件公開：

 [!code-csharp[Conceptual.TAP_Patterns#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#2)]
 [!code-vb[Conceptual.TAP_Patterns#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#2)]

 這類委派的另一種實用情況是在您實作快速路徑最佳化，而且想要傳回快取工作之時。

## <a name="workloads"></a>工作負載
您可以將計算繫結和 I/O 繫結的非同步作業都實作為 TAP 方法。 不過，當 TAP 方法從程式庫公開時，它們只應該提供給牽涉到 I/O 繫結操作 (它們可能也牽涉到計算，但不應該完全只有計算) 的工作負載。 如果是單純的計算繫結方法，則只可將它當做同步實作公開。 使用該方法的程式碼就可以選擇是否在工作中包裝該同步方法的引動過程，以便將工作卸載至另一個執行緒或實現平行處理。 而且，如果是 IO 繫結方法，則只可將它當做非同步實作公開。

### <a name="compute-bound-tasks"></a>計算繫結工作
<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 類別非常適合代表耗用大量運算資源的作業。 根據預設，它會利用 <xref:System.Threading.ThreadPool> 類別內的特殊支援提供有效率的執行，而且它也提供對要於何時、何處、及如何執行非同步計算的重大控制。

您可以以下列方式產生計算繫結工作：

- 在 .NET Framework 4 中，使用 <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> 方法，它接受以非同步方式執行委派 (通常是 <xref:System.Action%601> 或 <xref:System.Func%601>)。 如果您提供 <xref:System.Action%601> 委派，方法會傳回 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 物件，代表該委派的非同步執行。 如果您提供 <xref:System.Func%601> 委派，則該方法會傳回 <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> 物件。 <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> 方法的多載接受取消語彙基元 (<xref:System.Threading.CancellationToken>)、工作建立選項 (<xref:System.Threading.Tasks.TaskCreationOptions>) 和工作排程器 (<xref:System.Threading.Tasks.TaskScheduler>)，這些全都對工作的排程和執行提供精細的控制。 以目前工作排程器為目標的 Factory 執行個體可以當做 <xref:System.Threading.Tasks.Task.Factory%2A> 類別的靜態屬性(<xref:System.Threading.Tasks.Task>)，例如：`Task.Factory.StartNew(…)`。

- 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 與更新版本 (包括 .NET Core 與 .NET Standard) 中，使用靜態 <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> 方法作為 <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> 的捷徑。 您可以使用 <xref:System.Threading.Tasks.Task.Run%2A>，輕鬆啟動以執行緒集區為目標的計算繫結工作。 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 與更新版本中，這是啟動計算繫結工作的慣用機制。 只有在您想要對工作擁有更細部的掌控時，才直接使用 `StartNew`。

- 如果您想要個別產生並排定工作，請使用 `Task` 類型的建構函式或 `Start` 方法。 公用方法只能傳回已啟動的工作。

- 使用 <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> 方法的多載。 這個方法會建立新的工作，此工作排定在另一個工作完成時。 部分 <xref:System.Threading.Tasks.Task.ContinueWith%2A> 多載接受取消語彙基元、接續選項，以及工作排程器，以便更有效控制接續工作的排程和執行。

- 使用 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType> 方法。 這些方法會建立新的工作，此工作排定在所有或任何提供的一組工作完成時。 這些方法也會提供多載以控制這些工作的排程和執行。

在計算繫結工作中，如果系統在開始執行工作前收到取消要求，系統可以避免執行排定的工作。 因此，如果您提供取消語彙基元 (<xref:System.Threading.CancellationToken> 物件)，您可以將該語彙基元傳遞至監視語彙基元的非同步程式碼。 您也可以將語彙基元提供給先前所述方法之一，例如 `StartNew` 或 `Run`，讓 `Task` 執行階段也能監視語彙基元。

例如，請考慮呈現影像的非同步方法。 工作主體可以輪詢取消語彙基元，如果在呈現期間收到取消要求，程式碼可以提早結束。 此外，如果取消要求在轉譯開始之前到達，您會想要避免轉譯作業：

[!code-csharp[Conceptual.TAP_Patterns#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#3)]
[!code-vb[Conceptual.TAP_Patterns#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#3)]

如果下列條件至少其一為真，則計算繫結工作會在 <xref:System.Threading.Tasks.TaskStatus.Canceled> 狀態結束：

- 在工作轉換成 <xref:System.Threading.CancellationToken> 狀態之前，取消要求透過 `StartNew` 物件到達，此物件提供作為建立方法的引數 (例如，`Run` 或 <xref:System.Threading.Tasks.TaskStatus.Running>)。

- 這類工作主體內未處理 <xref:System.OperationCanceledException> 例外狀況，該例外狀況包含傳遞給工作的相同 <xref:System.Threading.CancellationToken>，且該語彙基元顯示已要求取消。

如果在工作主體中未處理另一個例外狀況，則工作會在 <xref:System.Threading.Tasks.TaskStatus.Faulted> 狀態結束，且任何等待該工作或存取其結果的嘗試都會造成擲回例外狀況。

### <a name="io-bound-tasks"></a>I/O 繫結工作
若要建立不該在整個執行緒執行期間直接支援的工作，請使用 <xref:System.Threading.Tasks.TaskCompletionSource%601> 類型。 這個類型會公開 <xref:System.Threading.Tasks.TaskCompletionSource%601.Task%2A> 屬性，此屬性傳回相關的 <xref:System.Threading.Tasks.Task%601> 執行個體。 此工作的生命週期是由 <xref:System.Threading.Tasks.TaskCompletionSource%601> 方法所控制，例如 <xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A>、<xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A>、<xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A> 及其 `TrySet` 變體。

我們假設您想要建立在指定的一段時間後才會完成的工作。 例如，您可能想要延遲使用者介面中的活動。 <xref:System.Threading.Timer?displayProperty=nameWithType> 類別已提供在一段指定的時間之後以非同步方式叫用委派的功能，您可以使用 <xref:System.Threading.Tasks.TaskCompletionSource%601> 將 <xref:System.Threading.Tasks.Task%601> 置於計時器之前，例如：

[!code-csharp[Conceptual.TAP_Patterns#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#4)]
[!code-vb[Conceptual.TAP_Patterns#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#4)]

從 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 開始，提供了 <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> 方法以達到此目的，且您可以在另一個非同步方法內使用它，例如，實作非同步輪詢迴圈：

[!code-csharp[Conceptual.TAP_Patterns#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#5)]
[!code-vb[Conceptual.TAP_Patterns#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#5)]

<xref:System.Threading.Tasks.TaskCompletionSource%601> 類別沒有非泛型對應項目。 不過，<xref:System.Threading.Tasks.Task%601> 衍生自 <xref:System.Threading.Tasks.Task>，所以您可以針對只傳回一項工作的 I/O 繫結方法使用泛型 <xref:System.Threading.Tasks.TaskCompletionSource%601> 物件。 若要執行這項操作，您可以使用具有假 `TResult` 的來源 (<xref:System.Boolean> 是很好的預設選擇，但如果您擔心 <xref:System.Threading.Tasks.Task> 的使用者將它向下轉換成 <xref:System.Threading.Tasks.Task%601>，您可以改用私用 `TResult` 類型)。 例如，在先前範例中的 `Delay` 方法會傳回目前的時間，以及所產生的位移 (`Task<DateTimeOffset>`)。 如果這樣的結果值是不必要的，方法可以改為編碼如下 (請注意變更傳回之類型和引數為 <xref:System.Threading.Tasks.TaskCompletionSource%601.TrySetResult%2A>)：

[!code-csharp[Conceptual.TAP_Patterns#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#6)]
[!code-vb[Conceptual.TAP_Patterns#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#6)]

### <a name="mixed-compute-bound-and-io-bound-tasks"></a>混合計算繫結和 I/O 繫結工作
非同步方法並不限於只有計算繫結或 I/O 繫結作業，而是可能出現兩者的混合。 事實上，經常會將多個非同步作業結合成較大的混合作業。 例如，在上述範例中的 `RenderAsync` 方法會執行密集運算的作業，以某些輸入的 `imageData` 為基礎呈現影像。 這個 `imageData` 可能來自您以非同步的方式存取的 Web 服務：

[!code-csharp[Conceptual.TAP_Patterns#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#7)]
[!code-vb[Conceptual.TAP_Patterns#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#7)]

這個範例也示範單一取消語彙基元如何透過多個非同步作業進行執行緒處理。 如需詳細資訊，請參閱[使用以工作為基礎的非同步模式](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)的取消使用方式一節。

## <a name="see-also"></a>另請參閱
 [工作式非同步模式 (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 [使用以工作為基礎的非同步模式](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)  
 [與其他非同步模式和型別互通](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)  
