---
title: Interop 與其他非同步模式和類型
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: f120a5d9-933b-4d1d-acb6-f034a57c3749
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c92725a43e43877488ff9ba93007530c794dd290
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a>Interop 與其他非同步模式和類型
.NET Framework 1.0 導入了 <xref:System.IAsyncResult> 模式，亦稱為 [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md)或 `Begin/End` 模式。  .NET Framework 2.0 加入了 [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)。  從 .NET Framework 4 開始， [Task-based Asynchronous Pattern (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) 取代了 APM 和 EAP，但是可讓您從較早的模式輕鬆建置移轉常式。  
  
 本主題內容：  
  
-   [工作與 APM](#APM) ([從 APM 到 TAP](#ApmToTap) 或 [從 TAP 到 APM](#TapToApm))  
  
-   [工作與 EAP](#EAP)  
  
-   [工作與等候控制代碼](#WaitHandles) ([從等候控制代碼到 TAP](#WHToTap) 或 [從 TAP 到等候控制代碼](#TapToWH))  
  
<a name="APM"></a>   
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a>工作與非同步程式設計模型 (APM)  
  
<a name="ApmToTap"></a>   
### <a name="from-apm-to-tap"></a>從 APM 到 TAP  
 由於 [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) 模式結構嚴謹，因此很容易就能建置包裝函式將 APM 實作公開為 TAP 實作。 事實上，以 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]為開頭的 .NET Framework，以 <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> 方法多載的形式來包含 Helper 常式，以提供這項轉譯。  
  
 請考慮 <xref:System.IO.Stream> 類別以及其 <xref:System.IO.Stream.BeginRead%2A> 與 <xref:System.IO.Stream.EndRead%2A> 方法，此類方法代表同步 <xref:System.IO.Stream.Read%2A> 方法的 APM 對應項目：  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 您可以使用 <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> 方法來實作這項作業的 TAP 包裝函式，如下所示：  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 這個實作相似下面這個：  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
<a name="TapToApm"></a>   
### <a name="from-tap-to-apm"></a>從 TAP 到 APM  
 如果您現有的基礎結構預期 APM 模式，則您也需進行 TAP 實作，並在預期 APM 實作的位置加以使用。  由於可以組成工作，並且 <xref:System.Threading.Tasks.Task> 類別會實作 <xref:System.IAsyncResult>，因此您可以使用簡單的 Helper 函式來完成這項作業。 下列程式碼會使用 <xref:System.Threading.Tasks.Task%601> 類別的擴充功能，但是您可以針對非泛型工作使用幾乎完全相同的函式。  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 現在，考量一下有下列 TAP 實作的案例：  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 而且您想要提供此 APM 實作：  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 下列範例將示範如何移轉至 APM：  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
<a name="EAP"></a>   
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a>工作與事件架構非同步模式 (EAP)  
 包裝 [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) 實作會比包裝 APM 模式更為複雜，原因是 EAP 模式擁有較多的變化，結構也不如 APM 模式嚴謹。  供示範所用，下列程式碼包裝了 `DownloadStringAsync` 方法。  `DownloadStringAsync` 會接受 URI、在下載時引發 `DownloadProgressChanged` 事件，以報告多個進行中的統計資料，然後在完成時引發 `DownloadStringCompleted` 。  最終結果是字串，其中包含指定之 URI 頁面的內容。  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
<a name="WaitHandles"></a>   
## <a name="tasks-and-wait-handles"></a>工作與等候控制代碼  
  
<a name="WHToTap"></a>   
### <a name="from-wait-handles-to-tap"></a>從等候控制代碼到 TAP  
 雖然等候控制代碼不會實作非同步模式，但進階開發人員可能會在等候控制代碼設定完成後，使用 <xref:System.Threading.WaitHandle> 類別與 <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> 方法，用於非同步通知。  您可以包裝 <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> 方法，以啟用等候控制代碼上任何同步等候的工作式替代方案：  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 有了此方法，您可以使用非同步方法中現有的 <xref:System.Threading.WaitHandle> 實作。  例如，如果您想要節流處理任何特定時間執行的非同步作業數目，可以利用旗號 (<xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> 物件)。  您可以節流處理至 *N* ，即同時執行的作業數，方法是透過將旗號的計數初始化至 *N*，在任何想執行作業時等待旗號，並在完成作業時釋放旗號：  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 您也可以建置非同步的旗號，而該旗號不會依賴等候控制代碼，並會完全與工作一同合作。 若要這樣做，您可以使用像是 [Consuming the Task-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) 中所討論的技術，用以在 <xref:System.Threading.Tasks.Task>。  
  
<a name="TapToWH"></a>   
### <a name="from-tap-to-wait-handles"></a>從 TAP 到等候控制代碼  
 如先前所述， <xref:System.Threading.Tasks.Task> 類別會實作 <xref:System.IAsyncResult>，且該實作會公開 <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> 屬性，而該屬性會傳回 <xref:System.Threading.Tasks.Task> 完成時將進行設定的等候控制代碼。  您可以取得 <xref:System.Threading.WaitHandle> 的 <xref:System.Threading.Tasks.Task> ，如下所示：  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a>請參閱  
 [工作式非同步模式 (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 [實作以工作為基礎的非同步模式](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)  
 [使用以工作為基礎的非同步模式](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
