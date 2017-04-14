---
title: "Walkthrough: Implementing a Component That Supports the Event-based Asynchronous Pattern | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Event-based Asynchronous Pattern"
  - "ProgressChangedEventArgs class"
  - "BackgroundWorker component"
  - "events [.NET Framework], asynchronous"
  - "Asynchronous Pattern"
  - "AsyncOperationManager class"
  - "threading [.NET Framework], asynchronous features"
  - "components [.NET Framework], asynchronous"
  - "AsyncOperation class"
  - "threading [Windows Forms], asynchronous features"
  - "AsyncCompletedEventArgs class"
ms.assetid: 61f676b5-936f-40f6-83ce-f22805ec9c2f
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# Walkthrough: Implementing a Component That Supports the Event-based Asynchronous Pattern
如果您在撰寫的類別具有一些可能造成顯著延遲的作業，請考慮實作[Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)以給予該類別非同步的功能。  
  
 本逐步解說會說明如何建立實作事件架構非同步模式的元件。  此元件的實作，是使用 <xref:System.ComponentModel?displayProperty=fullName> 命名空間中的 Helper 類別來進行的。如此可確定元件會在任何應用程式模型 \(包括 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]、主控台應用程式和 Windows Form 應用程式\) 底下，正確地進行運作。  運用 <xref:System.Windows.Forms.PropertyGrid> 控制項和您自己的自訂控制項，也都能夠設計這個元件。  
  
 在完成時，您就會擁有能以非同步方式計算質數值的一個應用程式。  您的應用程式將會具有一個主使用者介面 \(UI\) 執行緒，以及用於每次質數計算的另一個執行緒。  儘管測試大型數字是否為質數需要一些時間，主 UI 執行緒依然不會被這項延遲中斷，而且在進行計算時，表單也會有回應的能力。  您將能夠盡量執行並行計算，並能選擇性地取消擱置的計算。  
  
 逐步解說將說明的工作包括：  
  
-   建立元件  
  
-   定義公用非同步事件和委派  
  
-   定義私用委派  
  
-   實作公用事件  
  
-   實作 Completion 方法  
  
-   實作 Worker 方法  
  
-   實作 Start 和 Cancel 方法  
  
 若要將此主題中的程式碼複製為一份清單，請參閱 [How to: Implement a Component That Supports the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)。  
  
## 建立元件  
 第一個步驟就是建立將會實作事件架構非同步模式的元件。  
  
#### 若要建立元件  
  
-   建立繼承自 <xref:System.ComponentModel.Component>、稱為 `PrimeNumberCalculator` 的類別。  
  
## 定義公用非同步事件和委派  
 元件會使用事件來與用戶端通訊。  *MethodName*`Completed` 事件會向用戶端警示非同步工作的完成，而 *MethodName*`ProgressChanged`事件則會向用戶端通知非同步工作的進度。  
  
#### 若要為元件的用戶端定義非同步事件：  
  
1.  在檔案的頂端，匯入 <xref:System.Threading?displayProperty=fullName> 和 <xref:System.Collections.Specialized?displayProperty=fullName> 命名空間。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#11)]  
  
2.  在  `PrimeNumberCalculator`  類別定義之前，宣告進度和完成事件的委派。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#7)]  
  
3.  在  `PrimeNumberCalculator`  類別定義中，宣告事件以對用戶端報告進度和完成。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#8)]  
  
4.  在  `PrimeNumberCalculator`  類別定義之後，衍生  `CalculatePrimeCompletedEventArgs`  類別，以便將每次計算的結果，都報告到 `CalculatePrimeCompleted` 事件的用戶端事件處理常式。  除了 `AsyncCompletedEventArgs` 屬性，這個類別還讓用戶端能夠決定要測試何種數值、該數值是否為質數，以及該數值不為質數時所具有的第一個除數。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#6)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#6)]  
  
## 檢查點  
 完成這個步驟之後，您就可以建置元件了。  
  
#### 若要測試您的元件  
  
-   編譯元件。  
  
     您將會收到兩項編譯器警告：  
  
    ```  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.ProgressChanged' is never used  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.CalculatePrimeCompleted' is never used  
    ```  
  
     這些警告將會在下一區段中清除。  
  
## 定義私用委派  
 `PrimeNumberCalculator`  元件的非同步概念，是由稱為 <xref:System.Threading.SendOrPostCallback> 的特殊委派，在內部進行實作的。  <xref:System.Threading.SendOrPostCallback> 表示在 <xref:System.Threading.ThreadPool> 執行緒上所執行的回呼 \(Callback\) 方法。  此回呼方法必須具有使用 <xref:System.Object> 型別之單一參數的簽章 \(Signature\)，這表示您將需要在包裝函式類別 \(Wrapper Class\) 中的委派之中傳遞狀態。  如需詳細資訊，請參閱<xref:System.Threading.SendOrPostCallback>。  
  
#### 若要實作元件的內部非同步行為：  
  
1.  在  `PrimeNumberCalculator`  類別中，宣告和建立 <xref:System.Threading.SendOrPostCallback> 委派。  在稱為  `InitializeDelegates` 的公用程式方法中，建立 <xref:System.Threading.SendOrPostCallback> 物件。  
  
     您將需要兩個委派：一個用於向用戶端回報進度，另一個則用於向用戶端回報已完成作業。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#20)]  
  
2.  在您的元件建構函式 \(Constructor\) 內呼叫 `InitializeDelegates` 方法。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#21)]  
  
3.  在處理需要非同步地完成之實際工作的 `PrimeNumberCalculator` 類別中，宣告一個委派。  這個委派會包裝測試數值是否為質數的 Worker 方法。  這個委派會使用 <xref:System.ComponentModel.AsyncOperation> 參數來追蹤非同步作業的存留期 \(Lifetime\)。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#22)]  
  
4.  為擱置中非同步運算建立管理存留期的集合。  在作業執行和完成時，用戶端需要具有追蹤這些作業的方法。若要進行這種追蹤，需要用戶端在對非同步方法進行呼叫時，傳遞唯一語彙基元 \(Token，又稱為工作 ID\)。  `PrimeNumberCalculator` 元件必須使工作 ID 與其對應的引動過程關聯，以持續追蹤每次呼叫。  如果用戶端傳遞的工作 ID 並非唯一，`PrimeNumberCalculator` 元件就必須引發例外狀況。  
  
     `PrimeNumberCalculator` 元件會使用稱為 <xref:System.Collections.Specialized.HybridDictionary> 的特殊集合類別，持續追蹤工作 ID。  在類別定義中，建立一個稱為  `userTokenToLifetime` 的 <xref:System.Collections.Specialized.HybridDictionary>。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#23)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#23)]  
  
## 實作公用事件  
 實作事件架構非同步模式的元件，都會使用事件來與用戶端通訊。  藉由 <xref:System.ComponentModel.AsyncOperation> 類別的協助，這些事件會在適當的執行緒上被叫用 \(Invoke\)。  
  
#### 若要對元件的用戶端引發事件：  
  
1.  實作公用事件以向用戶端報告。  您將需要一個用來報告進度的事件，以及一個用來報告完成的事件。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#24)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#24)]  
  
## 實作 Completion 方法  
 完成委派就是在非同步作業由於成功完成、錯誤或取消而結束時，便會由基礎、無限制執行緒的非同步行為所叫用的方法。  這個引動過程會在任意執行緒上發生。  
  
 這個方法，也就是從唯一用戶端語彙基元的內部集合中，移除用戶端工作 ID 的地方。  這個方法也會呼叫對應 <xref:System.ComponentModel.AsyncOperation> 上的 <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> 方法，以結束特定非同步作業的存留期。  這個呼叫會在適合於應用程式模型的執行緒上，引發完成事件。  在呼叫 <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> 方法之後，就會無法再使用這個 <xref:System.ComponentModel.AsyncOperation> 執行個體，而且使用該執行個體的任何嘗試，都會擲回例外狀況。  
  
 `CompletionMethod` 簽章必須持有說明非同步作業結果的所有狀態。  此類別持有這個特定非同步作業所測試之數值的狀態：數值是否為質數，以及不為質數時所具有的第一個除數。  此類別也持有用來描述發生之任何例外狀況及對應於此特定工作之 <xref:System.ComponentModel.AsyncOperation> 的狀態。  
  
#### 若要完成非同步作業：  
  
-   實作完成方法。  這個方法會使用六個參數，以填入將會透過用戶端的  `CalculatePrimeCompletedEventHandler` 傳回給用戶端的  `CalculatePrimeCompletedEventArgs`。  此方法還會從內部集合中移除用戶端的工作 ID 語彙基元，並以對於 <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> 的呼叫來結束非同步作業的存留期。  <xref:System.ComponentModel.AsyncOperation> 則會將此呼叫封送處理 \(Marshal\) 至執行緒，或是適合於應用程式模型的內容。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#26)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#26)]  
  
## 檢查點  
 完成這個步驟之後，您就可以建置元件了。  
  
#### 若要測試您的元件  
  
-   編譯元件。  
  
     您將會收到一項編譯器警告：  
  
    ```  
    warning CS0169: The private field 'AsynchronousPatternExample.PrimeNumberCalculator.workerDelegate' is never used  
    ```  
  
     這些警告將會在下一區段中解決。  
  
## 實作 Worker 方法  
 直到目前為止，您已經實作了 `PrimeNumberCalculator` 元件的支援非同步程式碼。  現在您就可以實作進行實際工作的程式碼。  您將會實作三種方法 `CalculateWorker`、 `BuildPrimeNumberList` 和 `IsPrime`。  在一起使用時，`BuildPrimeNumberList` 和 `IsPrime` 組成了稱為 Sieve of Eratosthenes 的著名演算式，此演算式會找出直到測試數值平方根的所有質數，以判斷該數值是否為質數。  如果到時候都沒有找到任何除數，則表示測試數值就是質數。  
  
 如果這個元件的撰寫是為了提供最高效率，就會記得針對不同測試數值的各種引動過程所探索到的所有質數。  此元件也會檢查 2、3、5 之類的普通除數。  然而，這個範例的目的是要示範非同步作業的執行會如何耗費時間，因此這些最佳化的事項都將留給您做為練習。  
  
 `CalculateWorker` 方法包裝在委派中，而且會以 `BeginInvoke` 的呼叫來非同步叫用。  
  
> [!NOTE]
>  進度回報會在 `BuildPrimeNumberList` 方法中實作。  在速度快的電腦中，可以在快速執行時引發 `ProgressChanged` 事件。  用戶端執行緒 \(即引發這些事件的執行緒\) 必須能夠處理這個情況。  使用者介面的程式碼可能充滿了訊息且無法保留，導致懸置行為的產生。  如需處理這個情況的使用者介面範例，請參閱 [How to: Implement a Client of the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)。  
  
#### 若要非同步地執行質數計算：  
  
1.  實作 `TaskCanceled` 公用程式方法。  這個方法會檢查工作存留期集合，以找出指定的工作 ID，而如果找不到此工作 ID，就會傳回 `true`。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#32)]  
  
2.  實作 `CalculateWorker` 方法。  這項實作需要兩個參數：要測試的數值，以及 <xref:System.ComponentModel.AsyncOperation>。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#27)]  
  
3.  實作 `BuildPrimeNumberList`。  這項實作需要使用兩個參數：要測試的數值，以及 <xref:System.ComponentModel.AsyncOperation>。  此實作會使用 <xref:System.ComponentModel.AsyncOperation> 來報告進度和累加結果。  如此就能確定用戶端的事件處理常式，會在適當的執行緒或應用程式模型的內容中被呼叫。  在 `BuildPrimeNumberList` 找到質數時，就會將此報告為 `ProgressChanged` 事件之用戶端事件處理常式的累加結果。  此時需要使用衍生自 <xref:System.ComponentModel.ProgressChangedEventArgs> 的類別 \(稱為 `CalculatePrimeProgressChangedEventArgs`\)，此類別包含一個添加的屬性，稱為 `LatestPrimeNumber`。  
  
     `BuildPrimeNumberList` 方法也會定期呼叫 `TaskCanceled` 方法，並在此方法傳回 `true` 時結束。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#5)]  
  
4.  實作 `IsPrime`。  這項實作需要使用三個參數：一份已知質數的清單、要測試的數值，以及找到的第一個除數的輸出參數。  利用質數的清單，此實作即可判斷測試數值是否為質數。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#28)]  
  
5.  從 <xref:System.ComponentModel.ProgressChangedEventArgs> 衍生 `CalculatePrimeProgressChangedEventArgs`。  要向 `ProgressChanged` 事件的用戶端事件處理常式報告累加結果，這個類別是必要的。  此類別有一個稱為 `LatestPrimeNumber` 的添加屬性。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#29)]  
  
## 檢查點  
 完成這個步驟之後，您就可以建置元件了。  
  
#### 若要測試您的元件  
  
-   編譯元件。  
  
     還需要撰寫的部分，只剩下啟動和取消非同步作業的方法，也就是 `CalculatePrimeAsync` 和 `CancelAsync`。  
  
## 實作 Start 和 Cancel 方法  
 在包裝 Worker 方法的委派上呼叫 `BeginInvoke`，即可讓 Worker 方法在自己的執行緒上啟動。  若要管理特定非同步作業的存留期，您可以呼叫 <xref:System.ComponentModel.AsyncOperationManager> Helper 類別上的 <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> 方法。  這樣就會傳回 <xref:System.ComponentModel.AsyncOperation>，它會將用戶端事件處理常式的呼叫封送處理至適當的執行緒或內容。  
  
 藉由在其對應的 <xref:System.ComponentModel.AsyncOperation> 上呼叫 <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>，即可取消特定的擱置中的作業。  這樣就會結束作業，而且對於 <xref:System.ComponentModel.AsyncOperation> 的任何後續呼叫，也都會擲回例外狀況。  
  
#### 若要實作啟動和取消功能：  
  
1.  實作 `CalculatePrimeAsync` 方法。  確定用戶端支援的語彙基元 \(工作 ID\)，在表示目前擱置工作的所有語彙基元中是唯一的。  如果用戶端傳入的語彙基元並非唯一，`CalculatePrimeAsync` 就會引發例外狀況。  否則，語彙基元就會加入到工作 ID 集合中。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#3)]  
  
2.  實作 `CancelAsync` 方法。  如果 `taskId` 參數存在於語彙基元 \(Token\) 集合內，則會被移除。  如此一來，可避免執行尚未啟動的取消工作。  如果該工作正在執行中，則當 `BuildPrimeNumberList` 方法偵測到此工作 ID 已從存留期集合中移除時，就會結束。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#4)]  
  
## 檢查點  
 完成這個步驟之後，您就可以建置元件了。  
  
#### 若要測試您的元件  
  
-   編譯元件。  
  
 `PrimeNumberCalculator`  元件現在已經完成，並且已經可以使用。  
  
 如需使用 `PrimeNumberCalculator` 元件的範例用戶端，請參閱 [How to: Implement a Client of the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)。  
  
## 後續步驟  
 您可以藉由撰寫 `CalculatePrime`，也就是 `CalculatePrimeAsync` 方法的同步對等方法，來填寫這個範例。  這樣就會讓 `PrimeNumberCalculator` 元件完全遵循事件架構非同步模式。  
  
 保留針對不同測試數值的各種引動過程所探索到所有質數清單，即可改進這個範例。  只要使用這種處理方法，每項工作都會受益於先前完成的工作。  請以 `lock` 區域小心保護這份清單，如此即可序列化不同執行緒對此清單的存取。  
  
 您也可以測試普通除數 \(像是 2、3 和 5\)，以改進這個範例。  
  
## 請參閱  
 [如何：在背景執行作業](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)   
 [Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)   
 [NOT IN BUILD: Multithreading in Visual Basic](http://msdn.microsoft.com/zh-tw/c731a50c-09c1-4468-9646-54c86b75d269)   
 [How to: Implement a Component That Supports the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)   
 [Multithreaded Programming with the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)