---
title: "以非同步的方式呼叫同步方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- asynchronous programming, delegates
- asynchronous delegates
- AsyncWaitHandle property
- callback methods
- calling synchronous methods in asynchronous manner
- WaitHandle class, code examples
- asynchronous programming, status polling
- polling asynchronous operation status
- delegates [.NET Framework], asynchronous
- synchronous calling in asynchronous manner
- waiting for asynchronous calls
- status information [.NET Framework], asynchronous operations
ms.assetid: 41972034-92ed-450a-9664-ab93fcc6f1fb
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e7e6f402d9423a8ae1ee464499f1b794785c2b06
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="calling-synchronous-methods-asynchronously"></a>以非同步的方式呼叫同步方法
.NET Framework 可讓您以非同步方式呼叫任何方法。 若要這樣做，您使用相同簽章定義委派，做為您要呼叫的方法；Common Language Runtime 則會自動以適當簽章定義此委派的 `BeginInvoke` 和 `EndInvoke` 方法。  
  
> [!NOTE]
>  在 .NET Compact Framework 中不會支援非同步委派呼叫，尤其是 `BeginInvoke` 和 `EndInvoke` 方法  
  
 `BeginInvoke` 方法會起始非同步呼叫。 它有相同參數做為您要非同步執行的方法，再加上兩個額外的選擇性參數。 第一個參數是 <xref:System.AsyncCallback> 委派，參考非同步呼叫完成時所呼叫的方法。 第二個參數使用者定義的物件，可將資訊傳遞至回呼方法。 `BeginInvoke` 會立即傳回且不等候非同步呼叫完成。 `BeginInvoke` 傳回 <xref:System.IAsyncResult>，可用來監視非同步呼叫的進度。  
  
 `EndInvoke` 方法會擷取非同步呼叫的結果。 在 `BeginInvoke`之後隨時可以呼叫它。 如果非同步呼叫尚未完成，在完成前 `EndInvoke` 會封鎖呼叫執行緒。 `EndInvoke` 的參數包括您要非同步執行之方法的 `out` 和 `ref` 參數 (Visual Basic 為 `<Out>` `ByRef` 和 `ByRef`)，再加上 `BeginInvoke` 所傳回的 <xref:System.IAsyncResult>。  
  
> [!NOTE]
>  [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] 中的 IntelliSense 功能會顯示 `BeginInvoke` 和 `EndInvoke`的參數。 假如您並非使用 Visual Studio 或類似工具，或您使用 C# 搭配 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]，請參閱 [非同步程式設計模型 (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md)，以取得針對這些方法所定義的參數說明。  
  
 本主題中的程式碼範例將示範四個使用 `BeginInvoke` 和 `EndInvoke` 進行非同步呼叫的常用方法。 呼叫 `BeginInvoke` 之後您可執行以下動作：  
  
-   執行一些工作，然後呼叫 `EndInvoke` 進行封鎖，直到呼叫完成。  
  
-   取得使用 <xref:System.IAsyncResult.AsyncWaitHandle%2A?displayProperty=nameWithType> 屬性的 <xref:System.Threading.WaitHandle>，利用其 <xref:System.Threading.WaitHandle.WaitOne%2A> 方法封鎖執行，直到 <xref:System.Threading.WaitHandle> 收到信號，接著呼叫 `EndInvoke`。  
  
-   輪詢 <xref:System.IAsyncResult> 所傳回的 `BeginInvoke` ，判斷非同步呼叫完成的時間，然後再呼叫 `EndInvoke`。  
  
-   將回呼方法的委派傳遞至 `BeginInvoke`。 非同步呼叫完成之時，會在 <xref:System.Threading.ThreadPool> 執行緒上執行此方法。 回呼方法會呼叫 `EndInvoke`。  
  
> [!IMPORTANT]
>  不論您使用哪一種技術，請務必呼叫 `EndInvoke` 完成非同步呼叫。  
  
## <a name="defining-the-test-method-and-asynchronous-delegate"></a>定義測試方法和非同步委派  
 以下程式碼範例示範非同步呼叫同一個長時間執行之方法 `TestMethod`的各種方式。 `TestMethod` 方法會顯示主控台訊息，告訴您它已經開始處理、睡眠數秒鐘，然後結束。 `TestMethod` 具有 `out` 參數，以示範這類參數加入 `BeginInvoke` 和 `EndInvoke`簽章的方法。 您可以用類似方式處理 `ref` 參數。  
  
 下列程式碼範例顯示 `TestMethod` 的定義及名為 `AsyncMethodCaller` 且可用來非同步呼叫 `TestMethod` 的委派。 若要編譯程式碼範例，您必須包含 `TestMethod` 的定義和 `AsyncMethodCaller` 委派。  
  
 [!code-cpp[AsyncDelegateExamples#1](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/TestMethod.cpp#1)]
 [!code-csharp[AsyncDelegateExamples#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/TestMethod.cs#1)]
 [!code-vb[AsyncDelegateExamples#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/TestMethod.vb#1)]  
  
## <a name="waiting-for-an-asynchronous-call-with-endinvoke"></a>使用 EndInvoke 等候非同步呼叫  
 以非同步方式執行方法最簡單的方式，就是以呼叫委派的 `BeginInvoke` 方法來開始執行方法，在主執行緒上執行相同的工作，然後呼叫委派的 `EndInvoke` 方法。 `EndInvoke` 有可能會封鎖呼叫執行緒，因為它在非同赴呼叫完成之前都不會傳回。 這個技術非常適合運用於檔案或網路作業。  
  
> [!IMPORTANT]
>  由於 `EndInvoke` 可能會進行封鎖，因此請您千萬不要從服役於使用者介面的執行緒中呼叫它。  
  
 [!code-cpp[AsyncDelegateExamples#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/EndInvoke.cpp#2)]
 [!code-csharp[AsyncDelegateExamples#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/EndInvoke.cs#2)]
 [!code-vb[AsyncDelegateExamples#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/EndInvoke.vb#2)]  
  
## <a name="waiting-for-an-asynchronous-call-with-waithandle"></a>使用 WaitHandle 等候非同步呼叫  
 您可以使用取得 <xref:System.Threading.WaitHandle> 所傳回之 <xref:System.IAsyncResult.AsyncWaitHandle%2A> 的 <xref:System.IAsyncResult> 屬性，取得 `BeginInvoke` 非同步呼叫完成時， <xref:System.Threading.WaitHandle> 會收到信號，且您可以呼叫 <xref:System.Threading.WaitHandle.WaitOne%2A> 方法來等候它。  
  
 如果您使用 <xref:System.Threading.WaitHandle>，您可以在非同步呼叫完成之前或之後，且在呼叫 `EndInvoke` 擷取結果之前，執行其他的處理。  
  
> [!NOTE]
>  當您呼叫 `EndInvoke` 時，等候控制代碼不會自動關閉。 如果您釋放所有等候控制代碼的參考，當記憶體回收收回等候控制代碼時，系統資源就會釋放。 若要在您使用完等候控制代碼後立即釋放系統資源，請呼叫 <xref:System.Threading.WaitHandle.Close%2A?displayProperty=nameWithType> 方法來加以配置。 明確配置可處置的物件之後，記憶體回收會更有效率。  
  
 [!code-cpp[AsyncDelegateExamples#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/waithandle.cpp#3)]
 [!code-csharp[AsyncDelegateExamples#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/waithandle.cs#3)]
 [!code-vb[AsyncDelegateExamples#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/WaitHandle.vb#3)]  
  
## <a name="polling-for-asynchronous-call-completion"></a>輪詢是否完成非同步呼叫  
 您可以使用 <xref:System.IAsyncResult.IsCompleted%2A> 所傳回之 <xref:System.IAsyncResult> 的 `BeginInvoke` 屬性，找出非同步呼叫完成的時間。 從服役於使用者介面的執行緒進行非同步呼叫時，您有可能會執行這項操作。 輪詢完成這個動作，可在非同步呼叫於 <xref:System.Threading.ThreadPool> 執行緒上執行的同時，讓呼叫執行緒能夠繼續執行。  
  
 [!code-cpp[AsyncDelegateExamples#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/polling.cpp#4)]
 [!code-csharp[AsyncDelegateExamples#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/polling.cs#4)]
 [!code-vb[AsyncDelegateExamples#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/polling.vb#4)]  
  
## <a name="executing-a-callback-method-when-an-asynchronous-call-completes"></a>當非同步呼叫完成時執行回呼方法  
 如果起始非同步呼叫的執行緒不一定非是處理結果的執行緒時，您可以在呼叫完成時執行回呼方法。 回呼方法是在 <xref:System.Threading.ThreadPool> 執行緒上執行的。  
  
 若要使用回呼方法，您必須對 `BeginInvoke` 傳遞表示回呼方法的 <xref:System.AsyncCallback> 委派。 您也可以傳遞物件，包含回呼方法所使用的資訊。 在回呼方法中，您可以將 <xref:System.IAsyncResult>這個回呼方法唯一的參數，轉換成 <xref:System.Runtime.Remoting.Messaging.AsyncResult> 物件。 接著可以再使用 <xref:System.Runtime.Remoting.Messaging.AsyncResult.AsyncDelegate%2A?displayProperty=nameWithType> 屬性來取得委派，用來起使呼叫，以便您呼叫 `EndInvoke`。  
  
 此範例的注意事項如下：  
  
-   `TestMethod` 的 `threadId` 參數是 `out` 參數 (在 Visual Basic 中為 [`<Out>` `ByRef`)，因此 `TestMethod` 絕對不會使用它的輸入值。 虛設變數會傳遞給 `BeginInvoke` 呼叫。 如果 `threadId` 參數是 `ref` 參數 (Visual Basic 中的`ByRef` )，則變數必須是類別層級的欄位，才能同時傳遞至 `BeginInvoke` 和 `EndInvoke`。  
  
-   傳遞至 `BeginInvoke` 的狀態資訊是格式字串，回呼方法會用它來格式化輸出訊息。 由於狀態資訊傳遞時的型別是 <xref:System.Object>，因此必須先轉換成適當型別才能使用。  
  
-   回呼是在 <xref:System.Threading.ThreadPool> 執行緒上執行的。 <xref:System.Threading.ThreadPool> 執行緒為背景執行緒，也就是說主執行緒結束之時，並不會讓應用程式繼續執行，因此此範例的主執行緒必須進入睡眠直到回呼完成為止。  
  
 [!code-cpp[AsyncDelegateExamples#5](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/callback.cpp#5)]
 [!code-csharp[AsyncDelegateExamples#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/callback.cs#5)]
 [!code-vb[AsyncDelegateExamples#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/callback.vb#5)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Delegate>  
 [事件架構非同步模式 (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
