---
title: TPL 和傳統 .NET 非同步程式設計
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, with other asynchronous models
ms.assetid: e7b31170-a156-433f-9f26-b1fc7cd1776f
ms.openlocfilehash: 498bde82d05259bdc561d08819d024090b0417f0
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92688016"
---
# <a name="tpl-and-traditional-net-asynchronous-programming"></a>TPL 和傳統 .NET 非同步程式設計

.NET 提供下列兩個標準模式來執行 i/o 系結和計算系結的非同步作業：  
  
- 非同步程式設計模型 (APM) ，其中非同步作業會以一對 begin/end 方法來表示。 例如：<xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> 和 <xref:System.IO.Stream.EndRead%2A?displayProperty=nameWithType>。  
  
- 以事件為基礎的非同步模式 (EAP) ，其中非同步作業是以名為和的方法/事件組來表示 `<OperationName>Async` `<OperationName>Completed` 。 例如：<xref:System.Net.WebClient.DownloadStringAsync%2A?displayProperty=nameWithType> 和 <xref:System.Net.WebClient.DownloadStringCompleted?displayProperty=nameWithType>。
  
工作平行程式庫 (TPL) 可以用各種方式搭配非同步模式的其中一種。 您可以將 APM 和 EAP 作業公開為連結 `Task` 庫取用者的物件，也可以公開 apm 模式，但使用 `Task` 物件在內部執行。 在這兩種情況下，藉由使用 `Task` 物件，您可以簡化程式碼，並利用下列有用的功能：  
  
- 在啟動工作的任何時間之後，註冊工作接續形式的回呼。  
  
- 使用和方法來協調執行的多個作業，以回應 `Begin_` 方法 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> ，或是 <xref:System.Threading.Tasks.Task.WaitAll%2A> 和 <xref:System.Threading.Tasks.Task.WaitAny%2A> 方法。  
  
- 封裝相同物件中的非同步 i/o 系結和計算系結作業 `Task` 。  
  
- 監視物件的狀態 `Task` 。  
  
- 使用將作業的狀態封送處理至 `Task` 物件 <xref:System.Threading.Tasks.TaskCompletionSource%601> 。  
  
## <a name="wrap-apm-operations-in-a-task"></a>將 APM 作業包裝在工作中  

 <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType>和 <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType> 類別提供數個多載的 <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> 方法，可讓您在一個或多個實例中封裝 APM begin/end 方法組 <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> 。 不同的多載會容納具有零至三個輸入參數的任何 begin/end 方法組。  
  
 對於具有傳回 `End` 值 (Visual Basic) 中之方法的配對 `Function` ，請使用中的方法 <xref:System.Threading.Tasks.TaskFactory%601> 來建立 <xref:System.Threading.Tasks.Task%601> 。 針對傳回 `End` void (`Sub` 中 Visual Basic) 的方法，請使用中的方法 <xref:System.Threading.Tasks.TaskFactory> 來建立 <xref:System.Threading.Tasks.Task> 。  
  
 在 `Begin` 方法有三個以上的參數，或是包含 `ref` 或 `out` 參數的少數情況下，會提供其他僅封裝 `End` 方法的 `FromAsync` 多載。  
  
 下列範例示範 `FromAsync` 多載的簽章，該多載會比對 <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> 和 <xref:System.IO.FileStream.EndRead%2A?displayProperty=nameWithType> 方法。
  
 [!code-csharp[FromAsync#01](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#01)]
 [!code-vb[FromAsync#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#01)]  
  
這個多載會採用三個輸入參數，如下所示。 第一個參數是 <xref:System.Func%606> 委派，這與 <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> 方法的簽章相符。 第二個參數是 <xref:System.Func%602> 委派，會取得 <xref:System.IAsyncResult> 並傳回 `TResult`。 因為 <xref:System.IO.FileStream.EndRead%2A> 會傳回整數，所以編譯器會推斷 `TResult` 的類型為 <xref:System.Int32>，並且推斷工作的類型為 <xref:System.Threading.Tasks.Task>。 最後四個參數和在 <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> 方法中的相同：  
  
- 用來儲存檔案資料的緩衝區。  
  
- 開始寫入資料的緩衝區之位移。  
  
- 從檔案讀取的資料數量上限。  
  
- 選擇性的物件，其中儲存要傳遞至回呼的使用者定義狀態資料。  
  
### <a name="use-continuewith-for-the-callback-functionality"></a>使用 System.threading.tasks.task.continuewith 作為回呼功能

 如果您需要在檔案中資料的存取權，而不只是需要位元組數，則 <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> 方法仍不足夠。 請改用 <xref:System.Threading.Tasks.Task>，其 `Result` 屬性包含檔案資料。 您可將接續加入原始工作來達到此目的。 接續會執行通常由 <xref:System.AsyncCallback> 委派所執行的工作。 當前項完成，而且資料緩衝區已滿時，則會叫用它。 (<xref:System.IO.FileStream> 物件應該在傳回之前關閉。)  
  
 下列範例顯示如何傳回 <xref:System.Threading.Tasks.Task> 封裝 `BeginRead` / `EndRead` 類別配對的 <xref:System.IO.FileStream> 。  
  
 [!code-csharp[FromAsync#03](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#03)]
 [!code-vb[FromAsync#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#03)]  
  
 然後可以呼叫此方法，如下所示。  
  
 [!code-csharp[FromAsync#04](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#04)]
 [!code-vb[FromAsync#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#04)]  
  
### <a name="provide-custom-state-data"></a>提供自訂狀態資料

 在一般 <xref:System.IAsyncResult> 作業中，如果您的 <xref:System.AsyncCallback> 委派需要一些自訂狀態資料，則您必須透過 `Begin` 方法中的最後一個參數傳遞它，以便資料可以封裝到 <xref:System.IAsyncResult> 物件，而該物件最終會傳遞至回呼方法。 當使用 `FromAsync` 方法時，這通常不必要。 如果自訂資料對接續為已知，則可以直接在接續委派中擷取。 下列範例類似上述範例，但不檢查前項的 `Result` 屬性，接續會檢查自訂狀態資料，此為接續的使用者委派所直接存取。  
  
 [!code-csharp[FromAsync#05](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#05)]
 [!code-vb[FromAsync#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#05)]  
  
### <a name="synchronize-multiple-fromasync-tasks"></a>同步處理多個 System.threading.tasks.taskfactory.fromasync 工作

 當搭配 `FromAsync` 方法使用時，靜態 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> 和 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> 方法會提供額外的彈性。 下列範例示範如何初始化多個非同步 I/O 作業，然後等候它們全部完成，才執行接續。  
  
 [!code-csharp[FromAsync#06](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#06)]
 [!code-vb[FromAsync#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#06)]  
  
### <a name="fromasync-tasks-for-only-the-end-method"></a>僅 System.threading.tasks.taskfactory.fromasync End 方法的工作

 在 `Begin` 方法需要三個以上的輸入參數或具有或參數的少數情況下， `ref` `out` 您可以使用多載 `FromAsync` ，例如， <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%600%7D%29?displayProperty=nameWithType> 只代表 `End` 方法。 這些方法也可以在您傳遞的任何案例中使用 <xref:System.IAsyncResult> ，而且想要將它封裝在工作中。  
  
 [!code-csharp[FromAsync#07](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#07)]
 [!code-vb[FromAsync#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#07)]  
  
### <a name="start-and-cancel-fromasync-tasks"></a>啟動和取消 System.threading.tasks.taskfactory.fromasync 工作

 方法所傳回的工作 `FromAsync` 具有的狀態 `WaitingForActivation` ，並且會在工作建立之後的某個時間點啟動系統。 如果您嘗試呼叫這類工作上的 Start，就會引發例外狀況。  
  
 `FromAsync`因為基礎 .Net api 目前不支援檔案或網路 i/o 的進行中取消，所以無法取消工作。 您可以加入取消功能到封裝 `FromAsync` 呼叫的方法，但是您只可以在 `FromAsync` 呼叫之前或完成之後回應取消 (例如在接續工作中)。  
  
 有些類別支援 EAP，例如 <xref:System.Net.WebClient> 支援取消，您可以使用取消語彙基元整合該原生的取消功能。  
  
## <a name="expose-complex-eap-operations-as-tasks"></a>將複雜的 EAP 作業公開為工作

 TPL 不提供任何專門用來封裝事件架構非同步作業的方法，和 `FromAsync` 系列方法包裝 <xref:System.IAsyncResult> 模式的方式相同。 但是，TPL 並不提供 <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> 類別，這可用來代表任意一組作業為 <xref:System.Threading.Tasks.Task%601>。 此作業可能為同步或非同步，而且可能為 I/O 繫結或計算繫結，或兩者兼具。  
  
 下列範例示範如何使用 <xref:System.Threading.Tasks.TaskCompletionSource%601>來公開一組非同步 <xref:System.Net.WebClient> 作業給用戶端程式碼做為基本的 <xref:System.Threading.Tasks.Task%601>。 此方法可讓您輸入 Web URL 和要搜尋的詞彙或名稱之陣列，然後傳回在每個網站出現搜尋詞彙的次數。  
  
 [!code-csharp[FromAsync#10](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/snippet10.cs#10)]
 [!code-vb[FromAsync#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/snippet10.vb#10)]  
  
 如需更完整的範例，其中包含其他例外狀況處理，並示範如何從用戶端程式碼呼叫方法，請參閱[如何：將 EAP 模式包裝在工作中](how-to-wrap-eap-patterns-in-a-task.md)。  
  
 請記住，由所建立的任何工作 <xref:System.Threading.Tasks.TaskCompletionSource%601> 都會由該啟動， `TaskCompletionSource` 因此，使用者程式碼不應該 `Start` 在該工作上呼叫方法。  
  
## <a name="implement-the-apm-pattern-by-using-tasks"></a>使用工作來執行 APM 模式

 在某些情況下，您可能會想要 <xref:System.IAsyncResult> 在 API 中使用 begin/end 方法組來直接公開模式。 例如，您可能想要維護現有 API 的一致性，或者您想要有需要此模式的自動化工具。 在這種情況下，您可以使用 `Task` 物件來簡化 APM 模式在內部的內部執行方式。  
  
 下列範例示範如何使用工作，針對長時間執行的計算系結方法，執行 APM begin/end 方法組。  
  
 [!code-csharp[FromAsync#09](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#09)]
 [!code-vb[FromAsync#09](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#09)]  
  
## <a name="use-the-streamextensions-sample-code"></a>使用 StreamExtensions 範例程式碼

 *StreamExtensions.cs* 檔案在 [.NET Standard 平行擴充功能額外](/samples/dotnet/samples/parallel-programming-extensions-extras-cs/)存放庫中，包含數個使用 `Task` 物件進行非同步檔案和網路 i/o 的參考。
  
## <a name="see-also"></a>請參閱

- [工作平行程式庫 (TPL)](task-parallel-library-tpl.md)
