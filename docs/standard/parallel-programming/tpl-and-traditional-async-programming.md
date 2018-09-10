---
title: TPL 和傳統 .NET Framework 非同步程式設計
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, with other asynchronous models
ms.assetid: e7b31170-a156-433f-9f26-b1fc7cd1776f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8024fe6673b39a611c55eb55742bcfd981300e7e
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44277141"
---
# <a name="tpl-and-traditional-net-framework-asynchronous-programming"></a>TPL 和傳統 .NET Framework 非同步程式設計
.NET Framework 提供下列兩個標準模式執行 I/O 繫結程序和計算繫結程序的非同步作業：  
  
-   非同步程式設計模型 (APM)，在這個模式中非同步作業會以一對 Begin/End 方法表示，例如 <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> 和 <xref:System.IO.Stream.EndRead%2A?displayProperty=nameWithType>。  
  
-   事件式非同步模式 (EAP)，在這個模式中非同步作業會以一對名為 *OperationName*Async 和 *OperationName*Completed 的方法/事件組表示，例如 <xref:System.Net.WebClient.DownloadStringAsync%2A?displayProperty=nameWithType> 和 <xref:System.Net.WebClient.DownloadStringCompleted?displayProperty=nameWithType>。 (EAP 是在 .NET Framework 2.0 版中引入的。)  
  
 工作平行程式庫 (TPL) 可以用各種方式搭配非同步模式的其中一種。 您可以將 APM 和 EAP 作業做為工作公開給程式庫的取用者，或公開 APM 模式，但使用工作物件在內部實作它們。 在這兩種案例，您可以使用工作物件簡化程式碼，並利用下列好用的功能：  
  
-   在啟動工作的任何時間之後，註冊工作接續形式的回呼。  
  
-   使用 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> 和 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> 方法，或 <xref:System.Threading.Tasks.Task.WaitAll%2A> 方法、<xref:System.Threading.Tasks.Task.WaitAny%2A> 方法協調多項為回應 `Begin_` 方法而執行的作業。  
  
-   在相同工作物件中封裝非同步 I/O 繫結和計算繫結的作業。  
  
-   監視工作物件的狀態。  
  
-   使用 <xref:System.Threading.Tasks.TaskCompletionSource%601> 封送處理作業狀態給工作物件。  
  
## <a name="wrapping-apm-operations-in-a-task"></a>在工作中包裝 APM 作業  
 <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType> 類別都會提供數個 <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> 方法的多載，可讓您封裝 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 執行個體的其中一種 APM Begin/End 方法組。 這幾種多載會容納具有零到三個輸入參數的任何 Begin/End 方法組。  
  
 對於具有會傳回值的 `End` 方法組 (在 Visual Basic 中為 `Function`)，請使用會建立 <xref:System.Threading.Tasks.Task%601> 之 <xref:System.Threading.Tasks.TaskFactory%601> 中的方法。 對於會傳回 void 的 `End` 方法 (在 Visual Basic 中為 `Sub`)，請使用會建立 <xref:System.Threading.Tasks.Task> 之 <xref:System.Threading.Tasks.TaskFactory> 中的方法。  
  
 在 `Begin` 方法有三個以上的參數，或是包含 `ref` 或 `out` 參數的少數情況下，會提供其他僅封裝 `End` 方法的 `FromAsync` 多載。  
  
 下列範例示範 `FromAsync` 多載的簽章，該多載會比對 <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> 和 <xref:System.IO.FileStream.EndRead%2A?displayProperty=nameWithType> 方法。 這個多載會採用三個輸入參數，如下所示。  
  
 [!code-csharp[FromAsync#01](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#01)]
 [!code-vb[FromAsync#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#01)]  
  
 第一個參數是 <xref:System.Func%606> 委派，這與 <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> 方法的簽章相符。 第二個參數是 <xref:System.Func%602> 委派，會取得 <xref:System.IAsyncResult> 並傳回 `TResult`。 因為 <xref:System.IO.FileStream.EndRead%2A> 會傳回整數，所以編譯器會推斷 `TResult` 的類型為 <xref:System.Int32>，並且推斷工作的類型為 <xref:System.Threading.Tasks.Task>。 最後四個參數和在 <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> 方法中的相同：  
  
-   用來儲存檔案資料的緩衝區。  
  
-   開始寫入資料的緩衝區之位移。  
  
-   從檔案讀取的資料數量上限。  
  
-   選擇性的物件，其中儲存要傳遞至回呼的使用者定義狀態資料。  
  
### <a name="using-continuewith-for-the-callback-functionality"></a>對於回呼功能使用 ContinueWith  
 如果您需要在檔案中資料的存取權，而不只是需要位元組數，則 <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> 方法仍不足夠。 請改用 <xref:System.Threading.Tasks.Task>，其 `Result` 屬性包含檔案資料。 您可將接續加入原始工作來達到此目的。 接續會執行通常由 <xref:System.AsyncCallback> 委派所執行的工作。 當前項完成，而且資料緩衝區已滿時，則會叫用它。 (<xref:System.IO.FileStream> 物件應該在傳回之前關閉。)  
  
 下列範例示範如何傳回 <xref:System.Threading.Tasks.Task>，這會封裝 <xref:System.IO.FileStream> 類別的 BeginRead/EndRead 組。  
  
 [!code-csharp[FromAsync#03](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#03)]
 [!code-vb[FromAsync#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#03)]  
  
 然後可以呼叫此方法，如下所示。  
  
 [!code-csharp[FromAsync#04](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#04)]
 [!code-vb[FromAsync#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#04)]  
  
### <a name="providing-custom-state-data"></a>提供自訂狀態資料  
 在一般 <xref:System.IAsyncResult> 作業中，如果您的 <xref:System.AsyncCallback> 委派需要一些自訂狀態資料，則您必須透過 `Begin` 方法中的最後一個參數傳遞它，以便資料可以封裝到 <xref:System.IAsyncResult> 物件，而該物件最終會傳遞至回呼方法。 當使用 `FromAsync` 方法時，這通常不必要。 如果自訂資料對接續為已知，則可以直接在接續委派中擷取。 下列範例類似上述範例，但不檢查前項的 `Result` 屬性，接續會檢查自訂狀態資料，此為接續的使用者委派所直接存取。  
  
 [!code-csharp[FromAsync#05](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#05)]
 [!code-vb[FromAsync#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#05)]  
  
### <a name="synchronizing-multiple-fromasync-tasks"></a>同步處理多個 FromAsync 工作  
 當搭配 `FromAsync` 方法使用時，靜態 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> 和 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> 方法會提供額外的彈性。 下列範例示範如何初始化多個非同步 I/O 作業，然後等候它們全部完成，才執行接續。  
  
 [!code-csharp[FromAsync#06](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#06)]
 [!code-vb[FromAsync#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#06)]  
  
### <a name="fromasync-tasks-for-only-the-end-method"></a>僅適用 End 方法的 FromAsync 工作  
 在 `Begin` 方法需要三個以上輸入參數，或是具有 `ref` 或 `out` 參數的少數情況下，您可以使用 `FromAsync` 多載，例如 <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%600%7D%29?displayProperty=nameWithType>，這只會代表 `End` 方法。 這些方法也可用在當您傳遞 <xref:System.IAsyncResult> 且想要將它封裝在工作中的任何情況下。  
  
 [!code-csharp[FromAsync#07](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#07)]
 [!code-vb[FromAsync#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#07)]  
  
### <a name="starting-and-canceling-fromasync-tasks"></a>啟動及取消 FromAsync 工作  
 `FromAsync` 方法所傳回的工作具有 WaitingForActivation 狀態，並且會在工作建立之後由系統在某個時間點啟動。 如果您嘗試呼叫這類工作上的 Start，就會引發例外狀況。  
  
 您不能取消 `FromAsync` 工作，因為基礎 .NET Framework API 目前不支援檔案或網路 I/O 的進行中取消。 您可以加入取消功能到封裝 `FromAsync` 呼叫的方法，但是您只可以在 `FromAsync` 呼叫之前或完成之後回應取消 (例如在接續工作中)。  
  
 有些類別支援 EAP，例如 <xref:System.Net.WebClient> 支援取消，您可以使用取消語彙基元整合該原生的取消功能。  
  
## <a name="exposing-complex-eap-operations-as-tasks"></a>將複雜的 EAP 作業公開為工作  
 TPL 不提供任何專門用來封裝事件架構非同步作業的方法，和 `FromAsync` 系列方法包裝 <xref:System.IAsyncResult> 模式的方式相同。 但是，TPL 並不提供 <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> 類別，這可用來代表任意一組作業為 <xref:System.Threading.Tasks.Task%601>。 此作業可能為同步或非同步，而且可能為 I/O 繫結或計算繫結，或兩者兼具。  
  
 下列範例示範如何使用 <xref:System.Threading.Tasks.TaskCompletionSource%601>來公開一組非同步 <xref:System.Net.WebClient> 作業給用戶端程式碼做為基本的 <xref:System.Threading.Tasks.Task%601>。 此方法可讓您輸入 Web URL 和要搜尋的詞彙或名稱之陣列，然後傳回在每個網站出現搜尋詞彙的次數。  
  
 [!code-csharp[FromAsync#10](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/snippet10.cs#10)]
 [!code-vb[FromAsync#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/snippet10.vb#10)]  
  
 如需更完整的範例，其中包含其他例外狀況處理，並示範如何從用戶端程式碼呼叫方法，請參閱[如何：將 EAP 模式包裝在工作中](../../../docs/standard/parallel-programming/how-to-wrap-eap-patterns-in-a-task.md)。  
  
 請記住任何由 <xref:System.Threading.Tasks.TaskCompletionSource%601> 所建立的工作，都將由 TaskCompletionSource 啟動，因此使用者程式碼不應該在該工作上呼叫 Start 方法。  
  
## <a name="implementing-the-apm-pattern-by-using-tasks"></a>使用工作來實作 APM 模式  
 在某些案例，可能會希望使用 API 中的 Begin/End 方法組來直接公開 <xref:System.IAsyncResult> 模式。 例如，您可能想要維護現有 API 的一致性，或者您想要有需要此模式的自動化工具。 在這種情況下，您可以使用工作來簡化內部實作 APM 模式的方式。  
  
 對於長時間執行的計算繫結方法，下列範例示範如何使用工作來實作 APM Begin/End 方法組。  
  
 [!code-csharp[FromAsync#09](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#09)]
 [!code-vb[FromAsync#09](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#09)]  
  
## <a name="using-the-streamextensions-sample-code"></a>使用 StreamExtensions 範例程式碼  
 [使用 .NET Framework 4 進行平行程式設計的範例](https://code.msdn.microsoft.com/ParExtSamples)中的 Streamextensions.cs 檔案包含數個參考實作，這些參考實作會使用 Task 物件來執行非同步檔案和網路 I/O。  
  
## <a name="see-also"></a>另請參閱

- [工作平行程式庫 (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
