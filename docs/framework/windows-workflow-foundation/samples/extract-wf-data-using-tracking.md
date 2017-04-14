---
title: "使用追蹤擷取 WF 資料 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e30c68f5-8c6a-495a-bd20-667a4364c68e
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# 使用追蹤擷取 WF 資料
此範例會示範如何使用工作流程追蹤，從活動中擷取工作流程變數和引數。也會示範如何加入追蹤記錄的註釋，以及在自訂追蹤記錄內擷取資料裝載。此範例會使用 Windows 事件追蹤 \(ETW\) 追蹤參與者，從工作流程中擷取資料。  
  
## 範例詳細資料  
 [!INCLUDE[wf](../../../../includes/wf-md.md)] 會提供可取得執行工作流程執行個體可見性的追蹤。追蹤執行階段會在工作流程執行期間發出工作流程追蹤記錄。連同工作流程追蹤記錄，工作流程執行個體內的資料也可以從工作流程中擷取。下列清單詳述可以從追蹤記錄中擷取的資料型別：  
  
1.  活動內的工作流程變數以及活動執行期間的追蹤記錄。  
  
     為了擷取工作流程變數，要擷取的變數會指定在設定檔中。要擷取的變數只能使用 `ActivityStateQueries` 來指定。下列程式碼範例會示範用來從活動中擷取工作流程變數的追蹤設定檔。  
  
    ```xml  
    <activityStateQuery activityName="StockPriceService">  
         <states>  
              <state name="Closed"/>  
         </states>  
         <variables>  
              <variable name="symbol"/>  
         </variables>  
    </activityStateQuery>  
    ```  
  
2.  活動引數和活動狀態追蹤記錄。  
  
     引數會定義資料流入或流出活動的方式。要擷取的引數會使用 <xref:System.Activities.Tracking.ActivityStateQuery> 來指定。下列程式碼範例是擷取 `Value` 引數的追蹤設定檔。  
  
    ```xml  
    <activityStateQuery activityName="GetStockPrice">  
         <states>  
              <state name="Closed"/>  
         </states>  
         <arguments>  
              <argument name="Value"/>  
         </arguments>  
    </activityStateQuery>  
    ```  
  
3.  註釋是可以加入至發出之任何追蹤記錄的索引鍵\/值組。  
  
     註釋會當做追蹤記錄的標記機制。註釋會透過追蹤設定檔加入至追蹤記錄。註釋可以加入至任何類型的工作流程追蹤查詢。下列程式碼範例是一個追蹤設定檔，它會示範註釋如何加入至追蹤記錄。  
  
    ```xml  
    <workflowInstanceQuery>  
         <states>  
              <state name="Started"/>  
         </states>  
         <annotations>  
              <annotation name="StockPriceWorkflow" value="Begin"/>  
         </annotations>  
    </workflowInstanceQuery>  
    ```  
  
4.  自訂追蹤記錄是從使用者定義的活動所發出。  
  
     自訂追蹤記錄可以夾帶這個活動內定義的裝載資料。訂閱追蹤設定檔內的自訂追蹤記錄可允許擷取追蹤記錄內的裝載。自訂追蹤記錄可以使用自訂 <xref:System.Activities.Tracking.TrackingQuery> 來擷取。下列程式碼範例是一個追蹤設定檔，它會擷取自訂追蹤記錄以及其裝載。  
  
    ```  
    <customTrackingQuery name="QuoteLookupEvent" activityName="GetStockPrice"/>  
    ```  
  
 此範例示範如何擷取變數、引數和自訂記錄，以及使用 Web.config 中指定的設定檔來加入註釋。範例工作流程服務上會啟用追蹤，其方式是加入 `<etwTracking>` 行為項目。下列程式碼範例會啟用 `ExtractWorkflowVariables` 追蹤設定檔的追蹤。  
  
```  
<serviceBehaviors>  
     <behavior>  
               <etwTracking profileName="ExtractWorkflowVariables"/>  
     </behavior>  
</serviceBehaviors>  
```  
  
#### 若要使用這個範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 WFStockPriceApplication.sln 方案檔案。  
  
2.  若要建置此方案，請按下 CTRL\+SHIFT\+B。  
  
3.  若要執行此方案，請按 F5。  
  
     瀏覽器視窗隨即開啟並顯示應用程式的目錄清單。  
  
4.  在瀏覽器中，按一下 StockPriceService.xamlx。  
  
5.  瀏覽器隨即顯示 StockPriceService 頁面，其中包含本機服務 WSDL 位址。複製此位址。  
  
     下列範例會顯示本機服務 WSDL 位址。`http://localhost:53797/StockPriceService.xamlx?wsdl`  
  
6.  叫用服務之前，啟動 \[事件檢視器\] 並確認事件記錄正在接聽從工作流程服務發出的追蹤事件。  
  
7.  從 \[**開始**\] 功能表中，依序選取 \[**系統管理工具**\] 和 \[**事件檢視器**\]。  
  
8.  在 \[事件檢視器\] 的樹狀檢視中，巡覽至 \[**事件檢視器**\]、\[**應用程式及服務記錄檔**\] 和 \[**Microsoft**\]。以滑鼠右鍵按一下 \[**Microsoft**\]，並選取 \[**檢視**\] 和 \[**顯示分析與偵錯記錄檔**\]。  
  
     確認已核取 \[**顯示分析與偵錯記錄檔**\] 選項。  
  
9. 在 \[事件檢視器\] 的樹狀檢視中，巡覽至 \[**事件檢視器**\]、\[**應用程式及服務記錄檔**\]、\[**Microsoft**\]、\[**Windows**\]、\[**應用程式伺服器\-應用程式**\]。以滑鼠右鍵按一下 \[**分析**\]，並選取 \[**啟用記錄**\]。  
  
10. 使用 [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] 開啟 WCF 測試用戶端。  
  
     WCF 測試用戶端 \(WcfTestClient.exe\) 位於 \<[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 安裝資料夾\>\\Common7\\IDE\\ 資料夾中。  
  
     預設 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 安裝資料夾為 C:\\Program Files\\Microsoft Visual Studio 10.0。  
  
11. 在 WCF 測試用戶端中，選取 \[**檔案**\] 功能表上的 \[**新增服務**\]。  
  
     新增您之前在輸入方塊中複製的本機服務 WSDL 位址。  
  
12. 在 WCF 測試用戶端中，按兩下 `GetStockPrice`。  
  
     這樣會開啟 `GetStockPrice` 方法。要求會接受一個參數。請使用 \[**Contoso**\] 值。  
  
13. 按一下 \[**叫用**\]。  
  
14. 切換回 \[事件檢視器\]，並巡覽至 \[**事件檢視器**\]、\[**應用程式及服務記錄檔**\]、\[**Microsoft**\]、\[**Windows**\]、\[**應用程式伺服器\-應用程式**\]。以滑鼠右鍵按一下 \[**分析**\]，並選取 \[**重新整理**\]。工作流程事件位於事件識別碼範圍 100\-199。  
  
     事件包括可以在事件檢視器中檢視的註釋、變數、引數和自訂追蹤記錄。  
  
## 在事件檢視器中清除  
 您可以執行以下動作，在事件檢視器中清除事件記錄檔中的分析通道。  
  
#### 若要清除 \(選擇性\)  
  
1.  開啟 \[事件檢視器\]。  
  
2.  巡覽至 \[**事件檢視器**\]、\[**應用程式及服務記錄檔**\]、\[**Microsoft**\]、\[**Windows**\]、\[**應用程式伺服器\-應用程式**\]。以滑鼠右鍵按一下 \[**分析**\]，並選取 \[**停用記錄**\]。  
  
3.  巡覽至 \[**事件檢視器**\]、\[**應用程式及服務記錄檔**\]、\[**Microsoft**\]、\[**Windows**\]、\[**應用程式伺服器\-應用程式**\]。以滑鼠右鍵按一下 \[**分析**\]，並選取 \[**清除記錄**\]。  
  
     選擇 \[**清除**\] 選項可清除事件。  
  
## 已知問題  
  
> [!NOTE]
>  在 \[事件檢視器\] 中有一個可能無法為 ETW 事件解碼的已知問題。您可能會看到類似下面的錯誤訊息。  
>   
>  `找不到來自來源 Microsoft-Windows-應用程式伺服器-應用程式之事件識別碼 <id> 的描述。本機電腦可能並未安裝引發此事件的元件，或安裝已損毀。您可以在本機電腦上安裝或修復該元件。`  
>   
>  如果您遇到這個錯誤，請按一下執行窗格中的 \[**重新整理**\]。現在，此事件應該就會正確解碼。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\ExtractWfData`  
  
## 請參閱  
 [AppFabric 監控範例](http://go.microsoft.com/fwlink/?LinkId=193959)