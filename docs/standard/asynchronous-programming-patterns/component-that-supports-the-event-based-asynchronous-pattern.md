---
title: "逐步解說：實作支援事件架構非同步模式的元件"
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
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 150e4b27cc149774895574ddd196de5f9bc2acd8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-implementing-a-component-that-supports-the-event-based-asynchronous-pattern"></a>逐步解說：實作支援事件架構非同步模式的元件
如果您正在撰寫的類別可能會造成顯著的延遲某些作業，請考慮並賦予它所實作的非同步功能[事件架構非同步模式概觀](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)。  
  
 這個逐步解說將說明如何建立實作事件架構非同步模式的元件。 它使用中的 helper 類別來實作<xref:System.ComponentModel?displayProperty=nameWithType>命名空間，可確保元件如何在任何應用程式模式下正確運作，包括[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]，主控台應用程式和 Windows Forms 應用程式。 此元件也會與設計<xref:System.Windows.Forms.PropertyGrid>控制項和您自己自訂的設計工具。  
  
 當您完成時，您必須以非同步方式計算質數的應用程式。 您的應用程式必須在主要的使用者介面 (UI) 執行緒和執行緒的每一個質數計算。 雖然測試大型數字是否為質數需要相當長的時間、 主要 UI 執行緒不會中斷的這項延遲，而且進行計算時，表單會有回應。 您可以執行多個計算要選擇性地同時取消擱置的計算。  
  
 這個逐步解說中所述的工作包括：  
  
-   建立元件  
  
-   定義公用的非同步事件和委派  
  
-   定義私用委派  
  
-   實作公用事件  
  
-   實作完成方法  
  
-   實作工作者方法  
  
-   實作開始和取消方法  
  
 若要為單一列出本主題中複製的程式碼，請參閱[How to： 實作支援事件架構非同步模式的元件](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)。  
  
## <a name="creating-the-component"></a>建立元件  
 第一個步驟是建立會實作事件架構非同步模式的元件。  
  
#### <a name="to-create-the-component"></a>若要建立的元件  
  
-   建立類別，稱為`PrimeNumberCalculator`繼承自<xref:System.ComponentModel.Component>。  
  
## <a name="defining-public-asynchronous-events-and-delegates"></a>定義公用的非同步事件和委派  
 您的元件會使用事件的用戶端進行通訊。 *MethodName* `Completed`事件警示用戶端已完成的非同步工作，而*MethodName* `ProgressChanged`事件會通知用戶端的非同步工作的進度。  
  
#### <a name="to-define-asynchronous-events-for-clients-of-your-component"></a>若要為用戶端元件的定義非同步事件：  
  
1.  匯入<xref:System.Threading?displayProperty=nameWithType>和<xref:System.Collections.Specialized?displayProperty=nameWithType>在您的檔案最上方的命名空間。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#11)]  
  
2.  之前`PrimeNumberCalculator`類別定義，宣告的進度與完成狀態事件的委派。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#7)]  
  
3.  在`PrimeNumberCalculator`類別定義中，宣告事件以報告進度和完成用戶端。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#8)]  
  
4.  之後`PrimeNumberCalculator`類別定義中，衍生`CalculatePrimeCompletedEventArgs`類別報告的每個用戶端事件處理常式的計算結果的`CalculatePrimeCompleted`.event。 除了`AsyncCompletedEventArgs`屬性，這個類別可讓用戶端判斷何種號碼已測試、 是否為質數，以及第一個除數是如果它不是主要。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#6)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#6)]  
  
## <a name="checkpoint"></a>檢查點  
 此時，您可以建立元件。  
  
#### <a name="to-test-your-component"></a>若要測試您的元件  
  
-   編譯元件。  
  
     您會收到兩個編譯器警告：  
  
    ```  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.ProgressChanged' is never used  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.CalculatePrimeCompleted' is never used  
    ```  
  
     下一節中，將會清除這些警告。  
  
## <a name="defining-private-delegates"></a>定義私用委派  
 非同步層面`PrimeNumberCalculator`元件會在內部實作特殊的委派，又稱為<xref:System.Threading.SendOrPostCallback>。 A<xref:System.Threading.SendOrPostCallback>代表執行的回呼方法<xref:System.Threading.ThreadPool>執行緒。 回呼方法必須接受類型的單一參數的簽章<xref:System.Object>，這表示您必須將包裝函式類別中的委派之間的狀態傳遞。 如需詳細資訊，請參閱<xref:System.Threading.SendOrPostCallback>。  
  
#### <a name="to-implement-your-components-internal-asynchronous-behavior"></a>若要實作您的元件內部非同步行為：  
  
1.  宣告和建立<xref:System.Threading.SendOrPostCallback>委派中`PrimeNumberCalculator`類別。 建立<xref:System.Threading.SendOrPostCallback>公用程式方法的物件稱為`InitializeDelegates`。  
  
     您將需要兩個委派： 一個用戶端報告進度，一個用於報告用戶端來完成。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#20)]  
  
2.  呼叫`InitializeDelegates`元件的建構函式中的方法。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#21)]  
  
3.  宣告的委派`PrimeNumberCalculator`處理要以非同步方式進行的實際工作的類別。 這個委派會包裝測試數字是否為質數的工作者方法。 委派會採用<xref:System.ComponentModel.AsyncOperation>參數，將用來追蹤非同步作業的存留期。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#22)]  
  
4.  建立管理暫止的非同步作業的存留期的集合。 用戶端需要追蹤作業，以及執行和完成時，此追蹤由要求用戶端時要傳遞的唯一的語彙基元或工作 ID、 用戶端提出的非同步方法呼叫的方法。 `PrimeNumberCalculator`元件必須追蹤的每個呼叫對應的引動過程與關聯工作識別碼。 如果用戶端會傳遞不是唯一的工作識別碼`PrimeNumberCalculator`元件必須引發例外狀況。  
  
     `PrimeNumberCalculator`元件會持續追蹤的工作識別碼使用一種特殊的集合類別，稱為<xref:System.Collections.Specialized.HybridDictionary>。 在類別定義中，建立<xref:System.Collections.Specialized.HybridDictionary>呼叫`userTokenToLifetime`。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#23)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#23)]  
  
## <a name="implementing-public-events"></a>實作公用事件  
 用戶端使用的事件實作事件架構非同步模式的元件進行通訊。 這些事件會搭配適當的執行緒上叫用<xref:System.ComponentModel.AsyncOperation>類別。  
  
#### <a name="to-raise-events-to-your-components-clients"></a>若要引發事件給元件的用戶端：  
  
1.  實作回報到用戶端的公用事件。 您必須為報告進度，另一個用於報告完成事件。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#24)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#24)]  
  
## <a name="implementing-the-completion-method"></a>實作完成方法  
 完成委派為基礎、 無限制執行緒的非同步行為將會叫用時成功完成、 錯誤或取消非同步作業會結束方法。 這個引動過程發生在任意的執行緒。  
  
 這個方法是從內部集合的唯一用戶端語彙基元移除用戶端的工作識別碼的所在。 這個方法也會在特定的非同步作業的存留期結束藉由呼叫<xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>方法在相對應<xref:System.ComponentModel.AsyncOperation>。 此呼叫引發完成事件適用於應用程式模型的執行緒上。 之後<xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>呼叫方法時，這個執行個體<xref:System.ComponentModel.AsyncOperation>不再可用，並使用它的任何後續嘗試將會擲回例外狀況。  
  
 `CompletionMethod`簽章必須保留所有的狀態需要描述非同步作業的結果。 數字是否為質數，以及其第一個除數的值如果不是質數，它會保留數目所測試之這個特定非同步作業的狀態。 它也包含說明發生任何例外狀況的狀態和<xref:System.ComponentModel.AsyncOperation>對應於這個特定工作。  
  
#### <a name="to-complete-an-asynchronous-operation"></a>若要完成的非同步作業：  
  
-   實作完成的方法。 它會採用六個參數，用來填入`CalculatePrimeCompletedEventArgs`為傳回給用戶端透過用戶端`CalculatePrimeCompletedEventHandler`。 移除內部的集合，用戶端的工作 ID 語彙基元和結束非同步作業的存留期呼叫<xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>。 <xref:System.ComponentModel.AsyncOperation>封送處理呼叫的執行緒或適用於應用程式模型的內容。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#26)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#26)]  
  
## <a name="checkpoint"></a>檢查點  
 此時，您可以建立元件。  
  
#### <a name="to-test-your-component"></a>若要測試您的元件  
  
-   編譯元件。  
  
     您會收到一個編譯器警告：  
  
    ```  
    warning CS0169: The private field 'AsynchronousPatternExample.PrimeNumberCalculator.workerDelegate' is never used  
    ```  
  
     將在下一節中解決這個警告。  
  
## <a name="implementing-the-worker-methods"></a>實作工作者方法  
 目前為止，您已實作的支援非同步程式碼`PrimeNumberCalculator`元件。 現在，您可以實作到實際執行工作的程式碼。 您會實作三種方法： `CalculateWorker`， `BuildPrimeNumberList`，和`IsPrime`。 在一起，`BuildPrimeNumberList`和`IsPrime`組成已知的演算法，稱為 Sieve Eratosthenes，可判斷數字是否為質數藉由尋找所有質數最大數字為測試數字的平方根。 如果找不到該點的任何除數，測試數字是質數。  
  
 如果此元件所撰寫的最大效率，它會記住不同測試的數字的各種引動過程所探索到的所有質數。 它也會檢查普通除數像是 2、 3 和 5。 此範例的目的是為了示範如何耗時的作業可以是以非同步方式執行，不過，讓這些最佳化會為您保留做為練習。  
  
 `CalculateWorker`方法會包裝在委派中，並會以非同步方式叫用呼叫`BeginInvoke`。  
  
> [!NOTE]
>  進度報表在實作`BuildPrimeNumberList`方法。 在快速的電腦上`ProgressChanged`可以快速而連續引發事件。 用戶端執行緒，在其會引發這些事件，必須能夠處理這種情況。 使用者介面程式碼可能會大量湧入訊息且無法跟上，因此產生懸置行為。 範例使用者介面會處理此情況，請參閱[How to： 實作事件架構非同步模式的用戶端](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)。  
  
#### <a name="to-execute-the-prime-number-calculation-asynchronously"></a>若要以非同步方式執行質數計算：  
  
1.  實作`TaskCanceled`公用程式方法。 這會檢查指定的工作識別碼的工作存留期集合並傳回`true`如果找不到工作識別碼。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#32)]  
  
2.  實作 `CalculateWorker` 方法。 它會採用兩個參數： 一個數字，若要測試，和<xref:System.ComponentModel.AsyncOperation>。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#27)]  
  
3.  實作 `BuildPrimeNumberList`。 它會採用兩個參數： 要測試的數字和<xref:System.ComponentModel.AsyncOperation>。 它會使用<xref:System.ComponentModel.AsyncOperation>報告進度和累加結果。 如此可確保用戶端事件處理常式會呼叫適當的執行緒或應用程式模型的內容。 當`BuildPrimeNumberList`質數的數字，會發現，它將此報告累加結果用戶端事件處理常式`ProgressChanged`事件。 這需要一個衍生自類別<xref:System.ComponentModel.ProgressChangedEventArgs>，稱為`CalculatePrimeProgressChangedEventArgs`，其中已加入一個稱為屬性`LatestPrimeNumber`。  
  
     `BuildPrimeNumberList`方法也會定期呼叫`TaskCanceled`方法，如果此方法傳回的結束`true`。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#5)]  
  
4.  實作 `IsPrime`。 它會採用三個參數： 一份已知的質數、 要測試的數字的第一個找到的除數的輸出參數。 它會假設質數清單時，判斷測試數目是否為質數。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#28)]  
  
5.  衍生`CalculatePrimeProgressChangedEventArgs`從<xref:System.ComponentModel.ProgressChangedEventArgs>。 這個類別是所需的用戶端事件處理常式報告累加結果`ProgressChanged`事件。 它有一個加入的屬性稱為`LatestPrimeNumber`。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#29)]  
  
## <a name="checkpoint"></a>檢查點  
 此時，您可以建立元件。  
  
#### <a name="to-test-your-component"></a>若要測試您的元件  
  
-   編譯元件。  
  
     會維持為寫入所有的啟動和取消非同步作業，方法`CalculatePrimeAsync`和`CancelAsync`。  
  
## <a name="implementing-the-start-and-cancel-methods"></a>實作的開始和取消方法  
 您在自己的執行緒上啟動工作者方法藉由呼叫`BeginInvoke`包裝它的委派上。 若要管理特定的非同步作業的存留期，請呼叫<xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A>方法<xref:System.ComponentModel.AsyncOperationManager>協助程式類別。 這會傳回<xref:System.ComponentModel.AsyncOperation>，其封送處理至適當的執行緒或內容在用戶端事件處理常式上呼叫。  
  
 您藉由呼叫取消暫止作業的特定<xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>上其對應<xref:System.ComponentModel.AsyncOperation>。 這樣會結束該作業和任何後續呼叫其<xref:System.ComponentModel.AsyncOperation>將會擲回例外狀況。  
  
#### <a name="to-implement-start-and-cancel-functionality"></a>若要實作啟動和取消功能：  
  
1.  實作 `CalculatePrimeAsync` 方法。 請確定用戶端提供的語彙基元 (工作 ID) 都是唯一代表目前暫止工作的所有語彙基元。 如果用戶端會在非唯一的權杖中，`CalculatePrimeAsync`引發例外狀況。 否則，語彙基元加入工作識別碼集合。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#3)]  
  
2.  實作 `CancelAsync` 方法。 如果`taskId`語彙基元的集合中的參數存在，就會移除。 這可防止已取消的工作尚未開始執行的。 如果工作執行時，`BuildPrimeNumberList`方法結束時偵測到工作識別碼已從存留期集合中移除。  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#4)]  
  
## <a name="checkpoint"></a>檢查點  
 此時，您可以建立元件。  
  
#### <a name="to-test-your-component"></a>若要測試您的元件  
  
-   編譯元件。  
  
 `PrimeNumberCalculator`元件現在已完成且可供使用。  
  
 範例用戶端使用`PrimeNumberCalculator`元件，請參閱[How to： 實作事件架構非同步模式的用戶端](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)。  
  
## <a name="next-steps"></a>後續步驟  
 您可以藉由撰寫填寫此範例`CalculatePrime`，相當於同步`CalculatePrimeAsync`方法。 這會讓`PrimeNumberCalculator`完全遵循事件架構非同步模式的元件。  
  
 您可以藉由保留不同的測試數字的各種引動過程所探索到的所有質數清單改善此範例。 使用這個方法，每項工作將受益於先前的工作所完成的工作。 謹慎保護這份清單與`lock`區域，所以由不同的執行緒清單的存取序列化的。  
  
 您也可以改善這個範例藉由測試普通除數，例如 2、 3 和 5。  
  
## <a name="see-also"></a>另請參閱  
 [操作說明：在背景執行作業](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [事件架構非同步模式概觀](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [不在組建中： Visual Basic 中的多執行緒](http://msdn.microsoft.com/en-us/c731a50c-09c1-4468-9646-54c86b75d269)  
 [操作說明：實作支援事件架構非同步模式的元件](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [使用事件架構非同步模式設計多執行緒程式](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)
