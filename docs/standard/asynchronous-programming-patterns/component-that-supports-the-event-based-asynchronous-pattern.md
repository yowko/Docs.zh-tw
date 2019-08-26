---
title: 作法：實作支援事件架構非同步模式的元件
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 61f676b5-936f-40f6-83ce-f22805ec9c2f
ms.openlocfilehash: 2652c080951823e5289785b5906d2b0f48f5d658
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950783"
---
# <a name="how-to-implement-a-component-that-supports-the-event-based-asynchronous-pattern"></a>作法：實作支援事件架構非同步模式的元件
如果您正在撰寫的類別含有一些可能造成明顯延遲的作業，請考慮實作[事件架構非同步模式概觀](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)，來為它提供非同步功能。  
  
 本逐步解說說明如何建立實作「事件架構非同步模式」的元件。 其實作方式是使用 <xref:System.ComponentModel?displayProperty=nameWithType> 命名空間中的協助程式類別，確保此元件在任何應用程式模型下都能正常運作，包括 ASP.NET、主控台應用程式及 Windows Forms 應用程式。 您也可以使用 <xref:System.Windows.Forms.PropertyGrid> 控制項和您自己的自訂設計工具來設計此元件。  
  
 完成時，您將擁有一個以非同步方式計算質數的應用程式。 您的應用程式將會有一個主要使用者介面 (UI) 執行緒，以及一個用來計算每個質數的執行緒。 雖然測試一個大數是否為質數所需的時間很長，但主要 UI 執行緒並不會被此延遲打斷，在計算期間表單將能持續回應。 您將能夠想要執行多少次計算就同時執行多少次計算，並選擇性地取消擱置中的計算。  
  
 這個逐步解說中所述的工作包括：  
  
- 建立元件  
  
- 定義公用非同步事件和委派  
  
- 定義私用委派  
  
- 實作公用事件  
  
- 實作完成方法  
  
- 實作背景工作方法  
  
- 實作開始和取消方法  
  
 若要將此主題中的程式碼複製為單一清單，請參閱[如何：實作事件架構非同步模式的用戶端](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)。  
  
## <a name="creating-the-component"></a>建立元件  
 第一步是建立將會實作「事件架構非同步模式」的元件。  
  
### <a name="to-create-the-component"></a>建立元件  
  
- 建立一個名為 `PrimeNumberCalculator` 且會從 <xref:System.ComponentModel.Component> 繼承的類別。  
  
## <a name="defining-public-asynchronous-events-and-delegates"></a>定義公用非同步事件和委派  
 您的元件會使用事件與用戶端進行通訊。 _MethodName_**Completed** 事件會對用戶端發出已完成非同步工作的警示，而 _MethodName_**ProgressChanged** 事件則是會通知用戶端非同步工作的進度。  
  
### <a name="to-define-asynchronous-events-for-clients-of-your-component"></a>為元件的用戶端定義非同步事件：  
  
1. 在您檔案的頂端匯入 <xref:System.Threading?displayProperty=nameWithType> 和 <xref:System.Collections.Specialized?displayProperty=nameWithType> 命名空間。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#11)]  
  
2. 在 `PrimeNumberCalculator` 類別定義之前，宣告進度和完成事件的委派。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#7)]  
  
3. 在 `PrimeNumberCalculator` 類別定義中，宣告用來向用戶端回報進度和完成的事件。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#8)]  
  
4. 在 `PrimeNumberCalculator` 類別定義之後，衍生用來向 `CalculatePrimeCompleted`. 事件的用戶端事件處理常式回報每個計算結果的 `CalculatePrimeCompletedEventArgs` 類別。 除了 `AsyncCompletedEventArgs` 屬性之外，此類別還可讓用戶端判斷所測試的數字為何、是否為質數，以及如果該數字不是質數，第一個除數為何。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#6)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#6)]  
  
## <a name="checkpoint"></a>檢查點  
 現在，您可以建置元件。  
  
### <a name="to-test-your-component"></a>測試元件  
  
- 編譯元件。  
  
     您將會收到兩個編譯器警告：  
  
    ```  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.ProgressChanged' is never used  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.CalculatePrimeCompleted' is never used  
    ```  
  
     在下一節中將會清除這些警告。  
  
## <a name="defining-private-delegates"></a>定義私用委派  
 實作 `PrimeNumberCalculator` 元件的非同步層面時，會在內部使用稱為 <xref:System.Threading.SendOrPostCallback> 的特殊委派來實作。 <xref:System.Threading.SendOrPostCallback> 代表在 <xref:System.Threading.ThreadPool> 執行緒上執行的回呼方法。 此回呼方法必須具有會採用 <xref:System.Object> 類型之單一參數的簽章，這意謂著您將必須在包裝函式類別中傳遞委派之間的狀態。 如需詳細資訊，請參閱 <xref:System.Threading.SendOrPostCallback>。  
  
### <a name="to-implement-your-components-internal-asynchronous-behavior"></a>實作元件的內部非同步行為：  
  
1. 在 `PrimeNumberCalculator` 類別中宣告及建立 <xref:System.Threading.SendOrPostCallback> 委派。 在名為 `InitializeDelegates` 的公用程式方法中建立 <xref:System.Threading.SendOrPostCallback> 物件。  
  
     您將需要兩個委派：一個用來向用戶端回報進度，另一個用來向用戶端回報完成。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#20)]  
  
2. 在您元件的建構函式中呼叫 `InitializeDelegates` 方法。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#21)]  
  
3. 在處理要非同步執行之實際工作的 `PrimeNumberCalculator` 類別中宣告委派。 這個委派會包裝測試數字是否為質數的背景工作方法。 此委派會採用 <xref:System.ComponentModel.AsyncOperation> 參數，此參數將用來追蹤非同步作業的存留期。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#22)]  
  
4. 建立一個用來管理擱置中非同步作業的集合。 用戶端需要一個可追蹤作業執行和完成狀態的方式，而此追蹤的執行方式是在用戶端對非同步方法發出呼叫時，要求用戶端傳遞唯一的權杖或工作識別碼。 `PrimeNumberCalculator` 元件必須將工作識別碼與其對應的引動過程建立關聯，來追蹤每個呼叫。 如果用戶端傳遞的工作識別碼不是唯一的，`PrimeNumberCalculator` 元件必須引發例外狀況。  
  
     `PrimeNumberCalculator` 元件會使用一個名為 <xref:System.Collections.Specialized.HybridDictionary> 的特殊集合類別來追蹤工作識別碼。 在類別定義中，建立名為 `userTokenToLifetime` 的 <xref:System.Collections.Specialized.HybridDictionary>。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#23)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#23)]  
  
## <a name="implementing-public-events"></a>實作公用事件  
 實作「事件架構非同步模式」的元件會使用事件與用戶端進行通訊。 叫用這些事件時，會在 <xref:System.ComponentModel.AsyncOperation> 類別的協助下，在適當的執行緒上叫用。  
  
### <a name="to-raise-events-to-your-components-clients"></a>向元件的用戶端引發事件：  
  
1. 實作可向用戶端進行回報的公用事件。 您將需要一個事件來回報進度，另一個事件來回報完成。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#24)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#24)]  
  
## <a name="implementing-the-completion-method"></a>實作完成方法  
 完成委派是當非同步作業以成功完成、發生錯誤或取消作為結束時，基礎無限制執行緒非同步行為將叫用的方法。 此引動過程會在任意的執行緒上發生。  
  
 從唯一用戶端權杖的內部集合移除用戶端工作識別碼時，就是在此方法中進行。 此方法也會藉由呼叫對應之 <xref:System.ComponentModel.AsyncOperation> 上的 <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> 方法，來結束特定非同步作業的存留期。 此呼叫會在適用於應用程式模型的執行緒上引發完成事件。 在呼叫 <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> 方法之後，即無法再使用這個 <xref:System.ComponentModel.AsyncOperation> 執行個體，後續所有嘗試使用它的行為都會擲回例外狀況。  
  
 `CompletionMethod` 簽章必須保存描述非同步作業結果所需的所有狀態。 它會保存此特定非同步作業所測試的數字、該數字是否為質數，以及該數字第一個除數的值 (如果該數字不是質數的話)。 它也會保存描述所發生之任何例外狀況的狀態，以及與此特定工作對應的 <xref:System.ComponentModel.AsyncOperation>。  
  
### <a name="to-complete-an-asynchronous-operation"></a>完成非同步作業：  
  
- 實作完成方法。 此方法採用六個參數，用來填入會透過用戶端的 `CalculatePrimeCompletedEventHandler`.傳回到用戶端的 `CalculatePrimeCompletedEventArgs`。 它會從內部集合移除用戶端的工作識別碼權杖，然後藉由對 <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> 的呼叫來結束非同步作業的存留期。 <xref:System.ComponentModel.AsyncOperation> 會將呼叫封送處理至適用於應用程式模型的執行緒或內容。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#26)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#26)]  
  
## <a name="checkpoint"></a>檢查點  
 現在，您可以建置元件。  
  
### <a name="to-test-your-component"></a>測試元件  
  
- 編譯元件。  
  
     您將會收到一個編譯器警告：  
  
    ```  
    warning CS0169: The private field 'AsynchronousPatternExample.PrimeNumberCalculator.workerDelegate' is never used  
    ```  
  
     在下一節中將會解決此警告。  
  
## <a name="implementing-the-worker-methods"></a>實作背景工作方法  
 到目前為止，您已經為 `PrimeNumberCalculator` 元件實作提供支援的非同步程式碼。 現在，您可以實作執行實際工作的程式碼。 您將實作三個方法：`CalculateWorker``BuildPrimeNumberList` 及 `IsPrime`。 `BuildPrimeNumberList` 與 `IsPrime` 一起會構成稱為「埃拉托斯特尼篩法」(Sieve of Eratosthenes) 的著名演算法，此演算法可藉由尋找所有質數，最大可到測試數字的平方根為止，來判斷數字是否為質數。 如果到該點為止未發現任何除數，即表示該測試數字為質數。  
  
 如果此元件的撰寫目的是要發揮最高效率，它就會記住不同測試數字的各種引動過程所探索到的所有質數。 此外，它也會檢查是否有平凡除數，例如 2、3 及 5。 此範例的目的是要示範如何以非同步方式執行耗時的作業，不過，也因此這些最佳化會留給您作為練習。  
  
 `CalculateWorker` 方法會包裝在委派中，且叫用此方法時，會藉由對 `BeginInvoke` 的呼叫以非同步方式叫用。  
  
> [!NOTE]
> 實作進度回報時，是在 `BuildPrimeNumberList` 方法中實作。 在執行速度快的電腦上，可以快速地連續引發 `ProgressChanged` 事件。 作為這些事件之引發位置的用戶端執行緒必須能夠處理此情況。 使用者介面程式碼可能會湧入大量訊息而來不及處理，導致停止回應。 如需可處理此情形的使用者介面範例，請參閱[如何：實作事件架構非同步模式的用戶端](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)。  
  
### <a name="to-execute-the-prime-number-calculation-asynchronously"></a>以非同步方式執行質數計算：  
  
1. 實作 `TaskCanceled` 公用程式方法。 這會檢查指定之工作識別碼的工作存留期集合，如果找不到該工作識別碼，就會傳回 `true`。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#32)]  
  
2. 實作 `CalculateWorker` 方法。 此方法採用兩個參數：要測試的數字和 <xref:System.ComponentModel.AsyncOperation>。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#27)]  
  
3. 實作 `BuildPrimeNumberList`。 此方法採用兩個參數：要測試的數字和 <xref:System.ComponentModel.AsyncOperation>。 它會使用 <xref:System.ComponentModel.AsyncOperation> 來回報進度和累加結果。 這可確保在應用程式模型的適當執行緒或內容上呼叫用戶端的事件處理常式。 當 `BuildPrimeNumberList` 找到質數時，它會以累加結果的方式，向 `ProgressChanged` 事件的用戶端事件處理常式回報此質數。 這需要一個衍生自 <xref:System.ComponentModel.ProgressChangedEventArgs> 的類別 (稱為 `CalculatePrimeProgressChangedEventArgs`)，此類別具有一個稱為 `LatestPrimeNumber` 的附加屬性。  
  
     `BuildPrimeNumberList` 方法也會定期呼叫 `TaskCanceled` 方法，如果此方法傳回 `true`，就會結束。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#5)]  
  
4. 實作 `IsPrime`。 此方法採用三個參數：已知的質數清單、要測試的數字，以及所找到之第一個除數的輸出參數。 在有質數清單的情況下，它會判斷測試數字是否為質數。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#28)]  
  
5. 從 <xref:System.ComponentModel.ProgressChangedEventArgs>衍生 `CalculatePrimeProgressChangedEventArgs`。 此類別是向 `ProgressChanged` 事件的用戶端事件處理常式回報累加結果的必要類別。 它有一個稱為 `LatestPrimeNumber`的附加屬性。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#29)]  
  
## <a name="checkpoint"></a>檢查點  
 現在，您可以建置元件。  
  
### <a name="to-test-your-component"></a>測試元件  
  
- 編譯元件。  
  
     剩下要撰寫的只有用來開始和取消非同步作業的方法 `CalculatePrimeAsync` 和 `CancelAsync`。  
  
## <a name="implementing-the-start-and-cancel-methods"></a>實作開始和取消方法  
 開始背景工作方法的方式，是在背景工作方法自己的執行緒上，呼叫包裝它之委派上的 `BeginInvoke`。 若要管理特定非同步作業的存留期，您需呼叫 <xref:System.ComponentModel.AsyncOperationManager> 協助程式類別上的 <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> 方法。 這會傳回 <xref:System.ComponentModel.AsyncOperation> 以將用戶端事件處理常式上的呼叫封送處理至適當的執行緒或內容。  
  
 取消特定擱置中作業的方式，是呼叫其對應之 <xref:System.ComponentModel.AsyncOperation> 上的 <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>。 這會結束該作業，後續對其 <xref:System.ComponentModel.AsyncOperation> 發出的呼叫都會擲回例外狀況。  
  
### <a name="to-implement-start-and-cancel-functionality"></a>實作「開始」和「取消」功能：  
  
1. 實作 `CalculatePrimeAsync` 方法。 請確定就代表目前擱置中工作的所有權杖而言，用戶端所提供的權杖 (工作識別碼) 是唯一的。 如果用戶端傳入的權杖不是唯一的，`CalculatePrimeAsync` 就會引發例外狀況。 否則，該權杖會新增至工作識別碼集合中。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#3)]  
  
2. 實作 `CancelAsync` 方法。 如果 `taskId` 存在於權杖集合中，系統就會將它移除。 這可防止執行已取消但尚未開始的工作。 如果工作正在執行，當偵測到該工作識別碼已自存留期集合中移除時，`BuildPrimeNumberList` 方法就會結束。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#4)]  
  
## <a name="checkpoint"></a>檢查點  
 現在，您可以建置元件。  
  
### <a name="to-test-your-component"></a>測試元件  
  
- 編譯元件。  
  
 `PrimeNumberCalculator` 元件現在已完整而可供使用。  
  
 如需使用了 `PrimeNumberCalculator` 元件的用戶端範例，請參閱[如何：實作事件架構非同步模式的用戶端](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)。  
  
## <a name="next-steps"></a>後續步驟  
 您可以撰寫 `CalculatePrime` (`CalculatePrimeAsync` 方法的對等同步方法) 來填寫此範例。 這將可讓 `PrimeNumberCalculator` 元件完全符合「事件架構非同步模式」的規範。  
  
 您可以藉由保留不同測試數字的各種引動過程所探索到的所有質數清單，來改善此範例。 使用此做法時，每個工作都可從先前工作所完成的工作受益。 請使用 `lock` 區域來小心保護此清單，如此才能將不同執行緒對此清單的存取序列化。  
  
 您也可以針對平凡除數 (例如 2、3 及 5) 進行測試來改善此範例。  
  
## <a name="see-also"></a>另請參閱

- [如何：在背景執行作業](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [事件架構非同步模式概觀](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [事件架構非同步模式 (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
