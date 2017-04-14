---
title: "Windows Workflow Foundation 功能內容 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e84d12da-a055-45f6-b4d1-878d127b46b6
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Windows Workflow Foundation 功能內容
[!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] 在 Windows Workflow Foundation 中加入一些功能。本文件將描述一些新功能，並且詳細說明適合使用這些功能的案例。  
  
## 傳訊活動  
 傳訊活動 \(<xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.SendReply>、<xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.ReceiveReply>\) 是用來從工作流程傳送和接收 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 訊息。<xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 活動是用來構成經由 WSDL 所公開的 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 服務作業，就像標準 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Web 服務一樣。<xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 是用來取用 Web 服務，與 WCF <xref:System.ServiceModel.ChannelFactory> 很相似。產生預先設定之活動的 Workflow Foundation 也具備 \[**加入服務參考**\] 使用經驗。  
  
### 傳訊活動使用者入門  
  
-   在 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 中，建立 WCF 工作流程服務應用程式專案。一組 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 將置於畫布上。  
  
-   以滑鼠右鍵按一下專案，然後選取 \[**加入服務參考**\]。指向現有的 Web 服務 WSDL，然後按一下 \[**確定**\]。接著，建置您的專案，以便在工具箱中顯示產生的活動 \(使用 <xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 實作\)。  
  
-   您可以在下列章節中找到這些活動的範例：  
  
    -   基本：[服務](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   案例：[服務](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
-   [概念文件](http://go.microsoft.com/fwlink/?LinkId=204801)  
  
-   [傳訊活動設計工具文件](http://go.microsoft.com/fwlink/?LinkId=204802)  
  
### 傳訊活動範例案例  
 `BestPriceFinder` 服務會呼叫多個航空公司服務，以便尋找特定航線的最佳票價。實作此案例時，您必須使用訊息活動來接收價格要求、從後端服務擷取價格，並且以最佳價格回覆價格要求。此外，您也必須使用其他全新活動來建立計算最佳價格的商務邏輯。  
  
## WorkflowServiceHost  
 <xref:System.ServiceModel.WorkflowServiceHost> 是全新的工作流程主機，它支援多個執行個體、組態和 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 傳訊 \(不過，這些工作流程不需要使用傳訊，就能裝載\)。此外，它也會透過一組服務行為，與持續性、追蹤和執行個體控制項整合。就像 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 的 <xref:System.ServiceModel.ServiceHost> 一樣，<xref:System.ServiceModel.WorkflowServiceHost> 可以在主控台\/WinForms\/WPF 應用程式或 Windows 服務中自我裝載，也可以在 IIS 或 WAS 中 Web 裝載 \(成為 .xamlx 檔案\)。  
  
### 工作流程服務主機使用者入門  
  
-   在 Visual Studio 2010 中，建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 工作流程服務應用程式專案：這個專案將設定為使用 Web 主機環境中的 <xref:System.ServiceModel.WorkflowServiceHost>。  
  
-   若要裝載非傳訊工作流程，請加入會根據訊息建立執行個體的自訂 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>。  
  
-   工作流程執行個體可以控制 \(例如暫停或終止\)，方法是將 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> 加入至 <xref:System.ServiceModel.WorkflowServiceHost>，然後使用 <xref:System.ServiceModel.Activities.WorkflowControlClient>。  
  
-   您可以在下列章節中找到 <xref:System.ServiceModel.WorkflowServiceHost> 的範例：  
  
    -   [執行](../../../docs/framework/windows-workflow-foundation/samples/execution.md)  
  
    -   基本：[服務](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   案例：[服務](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   應用程式：[暫停的執行個體管理](../../../docs/framework/windows-workflow-foundation/samples/suspended-instance-management.md)  
  
-   [WorkflowServiceHost 概念文件](http://go.microsoft.com/fwlink/?LinkId=204807)  
  
### WorkflowServiceHost 案例  
 BestPriceFinder 服務會呼叫多個航空公司服務，以便尋找特定航線的最佳票價。實作此案例時，您必須在 <xref:System.ServiceModel.WorkflowServiceHost> 中裝載工作流程。此外，它也會使用訊息活動來接收價格要求、從後端服務擷取價格，並且以最佳價格回覆價格要求。  
  
## 相互關聯  
 相互關聯是指下列其中一種情況：  
  
-   群組訊息的方式。亦即，要求訊息與其回覆之間的關聯性。  
  
-   將資料片段對應至服務執行個體的方式。  
  
### 使用者入門  
  
-   若要開始使用相互關聯，請在 Visual Studio 中建立新的專案。建立型別為 <xref:System.ServiceModel.Activities.CorrelationHandle> 的變數。  
  
-   用來將訊息群組在一起之相互關聯的範例就是，將訊息群組在一起的要求\-回覆相互關聯。  
  
    -   在 <xref:System.ServiceModel.Activities.Receive> 活動上，按一下 <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> 屬性，然後使用您在上述第一個步驟中建立的 CorrelationHandle 來加入 <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>。  
  
    -   以滑鼠右鍵按一下 <xref:System.ServiceModel.Activities.Receive>，然後按一下 \[建立 SendReply\]，藉以建立 <xref:System.ServiceModel.Activities.SendReply> 活動。接著，將它貼入工作流程中 <xref:System.ServiceModel.Activities.Receive> 活動的後面。  
  
-   將資料片段對應至服務執行個體的範例就是內容架構的相互關聯，它會將資料片段 \(例如訂單 ID\) 對應至特定工作流程執行個體。  
  
    -   在任何傳訊活動上，按一下 `CorrelationInitializers` 屬性，然後使用您在上述步驟中建立的 <xref:System.ServiceModel.Activities.CorrelationHandle> 變數來加入 <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>。按兩下所需的訊息屬性 \(例如 OrderID\)，從下拉式功能表。接著，將 `CorrelatesWith` 屬性設定為上述使用的 <xref:System.ServiceModel.Activities.CorrelationHandle> 變數。  
  
-   範例：  
  
    -   基本：[服務](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   案例：[服務](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   [相互關聯概念文件](http://go.microsoft.com/fwlink/?LinkId=204939)  
  
### 相互關聯案例  
 訂單處理工作流程是用來處理新訂單建立工作以及更新進行中的現有訂單。實作此案例時，您必須在 <xref:System.ServiceModel.WorkflowServiceHost> 中裝載工作流程，並且使用傳訊活動。此外，它也需要使用以 `orderId` 為基礎的相互關聯，確保系統對正確的工作流程進行更新。  
  
## 簡化的組態  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 組態結構描述很複雜，而且為使用者提供了許多難以找到的功能。在 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 中，我們已經著重於協助 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 使用者使用下列功能來設定其服務：  
  
-   移除每項服務明確組態的需求。如果您沒有為服務設定任何 \<service\> 項目，而且您的服務並未以程式設計方式定義任何端點，則系統會自動將一組端點加入至服務，而且每個服務基底位址和服務實作的每個合約都會有一個端點。  
  
-   讓使用者定義 WCF 繫結和行為的預設值，以便套用至沒有明確組態的服務。  
  
-   標準端點會定義可重複使用的預先設定端點，其中一個或多個端點屬性 \(位址、繫結和合約\) 具有固定的值，而且允許定義自訂屬性。  
  
-   最後，<xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> 可讓您集中管理 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端組態，這在應用程式定義域載入時間之後選取或變更組態的案例中很有用。  
  
### 使用者入門  
  
-   [WCF 4.0 開發人員指南](http://go.microsoft.com/fwlink/?LinkId=204940)  
  
-   [組態通道處理站](http://go.microsoft.com/fwlink/?LinkId=204941)  
  
-   [標準端點項目](http://go.microsoft.com/fwlink/?LinkId=204942)  
  
-   [.Net Framework 4 中的服務組態改良](http://go.microsoft.com/fwlink/?LinkId=204943)  
  
-   [.NET 4 的常見使用者錯誤：WF\/WCF 服務組態名稱拼錯](http://go.microsoft.com/fwlink/?LinkId=204944)  
  
### 簡化的組態案例  
  
-   有經驗的 ASMX 開發人員想要開始使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]。不過，[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 看起來太複雜！我需要在組態檔中寫入哪些資訊？在 .NET 4 中，您甚至可以決定完全不使用組態檔。  
  
-   現有的 WCF 服務集非常難以設定和維護。組態檔具有數千行 XML 程式碼，任意修改可能會非常危險。因此需要相關協助，以便將程式碼數量減少至較容易管理的數量。  
  
## 資料合約解析程式  
 在 .NET 3.5 中，已知型別的設計具有一些限制：  
  
-   您無法在序列化或還原序列化期間，以動態方式加入已知型別。  
  
-   序列化程式無法處理不明的 xsi:type 資訊。  
  
-   使用者無法指定想要顯示在 Wire 上的 xsi:type，以便降低 Wire 上序列化執行個體的大小。  
  
 .NET 4.5 中的 [DataContractResolver](../../../docs/framework/wcf/samples/datacontractresolver.md) 可解決上述問題。  
  
### 使用者入門  
  
-   [資料合約解析程式應用程式開發介面文件](http://go.microsoft.com/fwlink/?LinkId=204946)  
  
-   [資料合約解析程式簡介](http://go.microsoft.com/fwlink/?LinkId=204947)  
  
-   範例：  
  
    -   [DataContractResolver](../../../docs/framework/wcf/samples/datacontractresolver.md)  
  
    -   [KnownAssemblyAttribute](../../../docs/framework/wcf/samples/knownassemblyattribute.md)  
  
### 資料合約解析程式案例  
  
-   避免在服務中宣告數十個 <xref:System.Runtime.Serialization.KnownTypeAttribute> 物件。  
  
-   減少 XML BLOB 的大小。  
  
## 流程圖  
 流程圖是已知的開發架構，可以視覺化方式表示網域問題。它是我們在 .NET 4 中導入的新控制流程樣式。流程圖的核心特性在於，一次只能執行一項活動。流程圖可以表達迴圈和替代的結果，但本身無法表示同時執行的多個節點。  
  
### 使用者入門  
  
-   在 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 中，建立工作流程主控台應用程式。在工作流程設計工具中加入流程圖。  
  
-   流程圖功能會使用下列類別：  
  
    -   <xref:System.Activities.Statements.Flowchart>  
  
    -   <xref:System.Activities.Statements.FlowNode>  
  
    -   <xref:System.Activities.Statements.FlowDecision>  
  
    -   <xref:System.Activities.Statements.FlowStep>  
  
    -   <xref:System.Activities.Statements.FlowSwitch%601>  
  
-   範例：  
  
    -   [使用 TryCatch 錯誤處理流程圖活動](../../../docs/framework/windows-workflow-foundation/samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)  
  
    -   [使用 FlowChart 及 Pick 組合的 StateMachine 案例](../../../docs/framework/windows-workflow-foundation/samples/statemachine-scenario-using-a-combination-of-flowchart-and-pick.md)  
  
    -   [招聘程序](../../../docs/framework/windows-workflow-foundation/samples/hiring-process.md)  
  
-   設計工具文件：  
  
    -   [流程圖活動設計工具](../Topic/Flowchart%20Activity%20Designers.md)  
  
### 流程圖案例  
 流程圖活動可用來實作猜測遊戲。猜測遊戲非常簡單：電腦會選取一個隨機數字，而玩家必須猜測該數字。當玩家送出每項猜測時，電腦就會顯示一個提示 \(例如「試試看較小的數字」\)。如果玩家在 7 次內猜到數字，電腦會對使用者顯示特別的恭賀畫面。您可以透過組合下列程序性活動來實作此遊戲：  
  
-   <xref:System.Activities.Statements.Sequence>  
  
-   <xref:System.Activities.Statements.While>  
  
-   <xref:System.Activities.Statements.Switch%601>  
  
-   <xref:System.Activities.Statements.TryCatch>  
  
-   <xref:System.Activities.Statements.Assign%601>  
  
-   <xref:System.Activities.Statements.If>  
  
## 程序性活動 \(Sequence、If、ForEach、Switch、Assign、DoWhile 和 While\)  
 程序性活動會使用程式設計人員所熟悉的概念來提供模型循序控制流程的機制。這些活動會啟用傳統結構的程式語言建構，並且在適當的情況下，提供一般程序性語言 \(例如 C\#\/VB\) 的語言同位項目。  
  
### 使用者入門  
  
-   在 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 中，建立工作流程主控台應用程式。在工作流程設計工具中加入程序性活動。  
  
-   範例：  
  
    -   [招聘程序](../../../docs/framework/windows-workflow-foundation/samples/hiring-process.md)  
  
    -   [公司購買程序](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md)  
  
-   設計工具文件：  
  
    -   [Parallel 活動設計工具](../Topic/Parallel%20Activity%20Designer.md)  
  
    -   [ParallelForEach\<T\> 活動設計工具](../Topic/ParallelForEach%3CT%3E%20Activity%20Designer.md)  
  
### 程序性活動案例  
  
-   <xref:System.Activities.Statements.Parallel>：內部網路文件管理系統具有文件核准工作流程。文件必須先由數個部門的人員核准，然後才能發行至內部網路。並沒有建立核准順序，只要文件處於「待核准」階段，即可隨時進行核准。當使用者送出文件以供檢閱時，其直屬經理、內部網路管理員和內部通訊經理就必須核准該份文件。  
  
-   <xref:System.Activities.Statements.ParallelForEach%601>：WF 應用程式可管理大型公司內部的企業採購。企業規則表示，規劃任何採購作業之前，需要三家不同廠商的估價。採購部門的員工會從公司的廠商清單中選取三家廠商。選取並通知這些廠商之後，公司將等候其經濟提案。這些提案可以按照任何順序提出。為了在 WF 中實作此案例，我們使用了 <xref:System.Activities.Statements.ParallelForEach%601>，以便逐一查看廠商的集合並且要求其經濟提案。蒐集所有提案之後，系統會選取並顯示最佳提案。  
  
## InvokeMethod  
 <xref:System.Activities.Statements.InvokeMethod> 活動允許叫用範圍內物件或型別的公用方法。它支援叫用包含或不包含參數 \(包括參數陣列\) 的執行個體和靜態方法，以及泛型方法。此外，它也允許以同步和非同步方式執行方法。  
  
### 使用者入門  
  
-   在 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 中，建立工作流程主控台應用程式。在工作流程設計工具中加入 <xref:System.Activities.Statements.InvokeMethod> 活動，並且針對此活動設定靜態和執行個體方法。  
  
-   範例：  
  
    -   [InvokeMethod](../../../docs/framework/windows-workflow-foundation/samples/invokemethod.md)  
  
-   設計工具文件：[InvokeMethod 活動設計工具](../Topic/InvokeMethod%20Activity%20Designer.md)  
  
### InvokeMethod 案例  
  
-   需要叫用範圍內物件的方法。例如，需要將某個值加入至字典。此時，系統會叫用字典執行個體的 Add 方法，並且提供索引鍵和值。  
  
-   需要針對舊版 CLR 物件叫用方法。您可以使用 <xref:System.Activities.Statements.InvokeMethod>，而非建立自訂活動來包裝該舊版類別的呼叫 \(如果它在工作流程執行期間位於範圍內的話\)。  
  
## 錯誤處理活動  
 <xref:System.Activities.Statements.TryCatch> 活動會提供一項機制來攔截一組包含的活動執行時發生的例外狀況 \(與 C\#\/VB 中的 Try\/Catch 建構很相似\)。<xref:System.Activities.Statements.TryCatch> 提供工作流程層級的例外狀況處理。當系統擲回未處理的例外狀況時，就會中止工作流程，而且不會執行 Finally 區塊。這種行為與 C\# 一致。  
  
### 使用者入門  
  
-   在 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 中，建立工作流程主控台應用程式。在工作流程設計工具中加入 <xref:System.Activities.Statements.TryCatch> 活動。  
  
-   範例：  
  
    1.  [使用 TryCatch 錯誤處理流程圖活動](../../../docs/framework/windows-workflow-foundation/samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)  
  
    2.  [使用程序性活動](../../../docs/framework/windows-workflow-foundation/samples/using-procedural-activities.md)  
  
-   設計工具文件：[錯誤處理活動設計工具](../Topic/Error%20Handling%20Activity%20Designers.md)  
  
### 錯誤處理案例  
 需要執行一組活動，而且需要在發生錯誤時執行特定邏輯。如果在錯誤處理邏輯期間發現錯誤無法復原，就會重新擲回例外狀況，而且父活動 \(或主機\) 將會處理此問題。  
  
## Pick 活動  
 <xref:System.Activities.Statements.Pick> 活動會提供 WF 中以事件為主的控制流程模型。<xref:System.Activities.Statements.Pick> 包含許多分支，每個分支會先等待特定事件發生後，再開始執行。在此設定中，<xref:System.Activities.Statements.Pick> 的行為與 <xref:System.Activities.Statements.Switch%601> 很相似，因為此活動只會執行它所接聽的其中一個事件集。每個分支都是由事件驅動，而發生的事件會先執行對應的分支。所有其他的分支都會取消並停止接聽事件。  
  
### 使用者入門  
  
-   在 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 中，建立工作流程主控台應用程式。在工作流程設計工具中加入 <xref:System.Activities.Statements.Pick> 活動。  
  
-   範例：[使用 Pick 活動](../../../docs/framework/windows-workflow-foundation/samples/using-the-pick-activity.md)  
  
-   設計工具文件：[Pick 活動設計工具](../Topic/Pick%20Activity%20Designer.md)  
  
### Pick 案例  
 系統需要提示使用者輸入。在一般情況下，開發人員會使用 <xref:System.Console.ReadLine%2A> 之類的方法呼叫來提示使用者輸入。這種設定的問題在於，直到使用者輸入某些內容為止，程式都會處於等候狀態。在此案例中，您需要使用逾時將封鎖的活動解除封鎖。常見的案例就是要求在指定的一段時間內完成工作。讓封鎖的活動逾時則為 Pick 發揮功能的案例。  
  
## WCF 路由服務  
 路由服務是設計成泛型軟體路由器，可讓您控制 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 訊息如何在用戶端與服務之間流動。路由服務可讓您降低用戶端與服務之間的耦合，以便在可支援的組態方面提供更多自由，並且在考慮如何裝載服務時提供更多彈性。在 .NET 3.5 中，用戶端與服務會緊密耦合。用戶端必須知道與它進行通訊的所有服務，以及這些服務的所在位置。此外，.Net Framework 3.5 中的 WCF 具有下列限制：  
  
-   錯誤處理很複雜，因為此邏輯必須透過硬式編碼寫入用戶端。  
  
-   用戶端與服務一定要使用相同的繫結。  
  
-   很少妥善分解服務：讓用戶端與實作所有功能的單一服務通訊會比在多個服務之間選擇更簡單。  
  
 .Net 4 中路由服務的設計目的是要讓上述問題更容易解決。新的路由服務具有下列功能：  
  
1.  以內容為基礎的路由 \(<xref:System.ServiceModel.Dispatcher.MessageFilter> 物件會檢查訊息來判斷應該傳送的目的地\)。  
  
2.  通訊協定橋接 \(傳輸與訊息\)。  
  
3.  錯誤處理 \(路由器會攔截通訊例外狀況並容錯移轉至備份端點\)。  
  
4.  <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> 和路由組態的動態 \(記憶體中\) 更新。  
  
### 使用者入門  
  
1.  文件：[路由](../../../docs/framework/wcf/feature-details/routing.md)  
  
2.  範例：[路由服務 &#91;WCF 範例&#93;](../../../docs/framework/wcf/samples/routing-services.md)  
  
3.  部落格：[路由規則！](http://go.microsoft.com/fwlink/?LinkId=204956)  
  
### 路由案例  
 在下列案例中，路由服務很有用：  
  
-   用戶端可以與多個服務通訊，而不需要直接處理所有服務。  
  
-   用戶端可以針對用戶端要求執行其他邏輯，以便判斷要路由傳送的目的地。  
  
-   將用戶端所執行的作業分解成多個服務實作，而不需要重構用戶端。  
  
-   用戶端與服務可以宣告具有不同安全性設定的不同繫結。  
  
-   用戶端可以具備更健全的功能，以防範失敗或無法使用服務的情況。  
  
## WCF 探索  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 探索是一項架構技術，可讓您將探索機制併入應用程式基礎結構中。您可以使用這項技術，讓服務成為可探索的服務，並且設定用戶端來搜尋服務。用戶端不再需要對端點進行硬式編碼，讓應用程式更健全並提高容錯能力。探索是在應用程式中建置自動組態功能的完美平台。  
  
 此產品是以 WS\-Discovery 標準為建置基礎。其設計目的是要成為可互通、可擴充且泛型的產品。此產品支援兩種作業模式：  
  
1.  受管理：網路上有一個了解現有服務的實體，因此用戶端會直接查詢此實體以取得資訊。這種模式類似於 Active Directory。  
  
2.  臨機操作：用戶端會使用多點傳送訊息來找出服務。  
  
 此外，探索訊息無從驗證網路通訊協定。您可以在支援模式需求的任何通訊協定上使用這些訊息。例如，探索多點傳送訊息可以透過 UDP 通道傳送，也可以透過支援多點傳送訊息的任何其他網路傳送。這些設計重點 \(與功能彈性結合\) 可讓您針對方案明確地調整探索。  
  
### 使用者入門  
  
-   文件：[WCF 探索](../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
  
-   範例：[探索 \(範例\)](../../../docs/framework/wcf/samples/discovery-samples.md)  
  
### 探索案例  
 開發人員不想要對端點進行硬式編碼，因為它在服務可用時處於未知狀態。不過，開發人員想要在執行階段選擇服務。因此，應用程式的元件之間需要降低耦合、提高健全度，以及自動組態功能。  
  
## 追蹤  
 工作流程追蹤可讓您深入了解工作流程執行個體的執行方式。這些追蹤事件是在工作流程內部的活動執行時，從工作流程執行個體層級的工作流程發出的。您必須將工作流程追蹤參與者加入至工作流程主機，才能訂閱追蹤記錄。系統會使用追蹤設定檔來篩選追蹤記錄。.Net Framework 提供了 ETW \(Windows 事件追蹤\) 追蹤參與者，而且基本設定檔安裝在 machine.config 檔案中。  
  
### 使用者入門  
  
1.  在 [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] 中，建立 WCF 工作流程服務應用程式專案。一組 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 將置於畫布上，以便開始。  
  
2.  開啟 web.config 並加入不含設定檔的 ETW 追蹤行為。  
  
    1.  系統會使用預設設定檔。  
  
    2.  開啟事件檢視器並啟用下列節點中的分析通道：\[**事件檢視器**\]、\[**應用程式及服務記錄檔**\]、\[**Microsoft**\]、\[**Windows**\]、\[**應用程式伺服器\-應用程式**\]。以滑鼠右鍵按一下 \[**分析**\]，並選取 \[**啟用記錄**\]。  
  
    3.  執行工作流程服務。  
  
    4.  在事件檢視器中查看工作流程追蹤事件。  
  
3.  範例：[追蹤](../../../docs/framework/windows-workflow-foundation/samples/tracking.md)  
  
4.  概念文件：[工作流程追蹤與追查](../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)  
  
## SQL 工作流程執行個體存放區  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 是以 SQL Server 為基礎的執行個體存放區實作。執行個體存放區會儲存執行中執行個體的狀態以及載入和繼續該執行個體所需的所有資料。如果工作流程會保存，服務主機就會指示執行個體存放區儲存執行個體狀態，而且當該執行個體的訊息送達或延遲活動過期時，它就會指示執行個體存放區載入執行個體狀態。  
  
### 使用者入門  
  
1.  在 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 中，建立包含隱含或明確 <xref:System.Activities.Statements.Persist> 活動的工作流程。將 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 行為加入至工作流程服務主機。您可以在程式碼或應用程式組態檔中進行這項作業。  
  
2.  範例：[持續性](../../../docs/framework/windows-workflow-foundation/samples/persistence.md)  
  
3.  概念文件：[SQL 工作流程執行個體存放區](../../../docs/framework/windows-workflow-foundation//sql-workflow-instance-store.md)