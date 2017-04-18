---
title: "內建組態 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 34e85c9b-088d-4347-816c-0f77cb73ef2f
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# 內建組態
這個範例示範使用和設定 SQL 工作流程執行個體存放區。SQL 工作流程執行個體存放區是以 SQL 為基礎的執行個體存放區實作。它允許執行個體在 SQL Server 或 SQL Server Express 資料庫中來回儲存及載入。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 \(下載頁面\) 以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\BuiltInConfiguration`  
  
## 範例詳細資料  
 這個範例是由實作計數服務的工作流程所組成。一旦叫用服務的 Start 方法，服務就會從 0 計數到 59。計數器每 2 秒遞增一次。每次計數後，工作流程會保存。  
  
 計數工作流程是由工作流程服務主機自我主控的。程式的 `Main` 方法會建立裝載計數工作流程之工作流程服務主機的執行個體。它會定義可用來連接至計數工作流程的端點。定義端點之後，它會定義 SQL 工作流程執行個體存放區行為，用來設定 SQL 工作流程執行個體存放區。接著程式會建立呼叫計數工作流程 Start 方法的用戶端。  
  
 一旦程式啟動，計數器會自動開始計數。請注意，載入執行個體以及設定 SQL 工作流程執行個體存放區可能要花幾秒才能完成。[!INCLUDE[crabout](../../../../includes/crabout-md.md)] 工作流程執行個體存放區，請參閱 [SQL 工作流程執行個體存放區](../../../../docs/framework/windows-workflow-foundation//sql-workflow-instance-store.md)。  
  
 此範例包含二個部分：  
  
1.  InstanceStore1 示範如何使用 C\# 程式碼設定 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> \(請參閱 Program.cs\)。  
  
2.  InstanceStore2 示範如何使用 XML 設定 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> \(請參閱 App.config\)。  
  
 以下為可用來設定 SQL 工作流程執行個體存放區行為的設定：  
  
-   設定 `HostLockRenewalPeriod`。這個時間會定義時間間隔，用於主機更新其執行之執行個體的擁有權鎖定。鎖定資訊儲存在執行個體存放區中。如果擁有權連續兩次未在 `HostLockRenewalPeriod` 中定義的時間間隔更新，則會將執行個體視為已放棄。如果另一個 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 正在執行相同的工作流程，並且連接至相同的執行個體存放區 \(在同一部或不同部電腦上\)，則它會復原該執行個體 \(執行個體復原不在本範例的範圍內\)。  
  
-   設定 `RunnableInstancesDetectionPeriod`。這段時間定義主機輪詢可執行之執行個體的時間間隔。執行個體在下列任何事件發生時會變成可執行：  
  
    -   永久性計時器 \(<xref:System.Activities.Statements.Delay>\) 過期。  
  
    -   另一部主機遺失其 `HostLockRenewal` 活動訊號 \(例如，因為電腦當機\) 且執行個體已復原。  
  
-   設定 `InstanceCompletionAction`。如果這個屬性設為 `DeleteNothing`，就會在執行個體存放區中保存完整的執行個體；如果設為 `DeleteAll`，則會在完成時從存放區中刪除執行個體。請注意  
  
    > [!NOTE]
    >  在計時完成之前按下 ENTER 終止主機，並不會完成工作流程執行個體。  
  
-   設定 `InstanceLockedExceptionAction`。這個設定會定義主機想要載入另一部主機鎖定的執行個體時，應該怎麼做。以下為可行的選項：  
  
    -   如果設為 `NoRetry`：不重試載入並將 `InstanceLockedException` 傳回至主機。  
  
    -   如果設為 `BasicRetry`：繼續重試載入執行個體。重試是根據簡單的線性演算法排程 \(例如，每 5 秒重試一次\)。  
  
    -   如果設為 `AggressiveRetry`：繼續重試載入執行個體。重試是根據主動指數後退演算法 \(Aggressive Exponential Back\-off Algorithm\) 排程。  
  
-   設定編碼選項。這個設定會定義執行個體狀態儲存在 SQL 工作流程執行個體存放區中的方式。以下為可行的選項：  
  
    -   執行個體狀態是使用 GZip 壓縮演算法進行壓縮。  
  
    -   執行個體狀態不會經過壓縮。  
  
#### 若要使用這個範例  
  
1.  以系統管理員身分開啟 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元 \(如果有權限可以使用的話\)。  
  
2.  巡覽至範例目錄 \(\\WF\\Basic\\Persistence\\BuiltInConfiguration\\CS\)，並執行 CreateInstanceStore.cmd。  
  
3.  如果未提供系統管理員權限，請建立 SQL Server 登入。移至 `Security`、\[**登入**\]。以滑鼠右鍵按一下 \[**登入**\]，並建立新登入。  
  
4.  將 ACL 使用者加入至 SQL 角色。開啟 \[**資料庫**\]、\[**InstanceStore**\]、\[**安全性**\]。以滑鼠右鍵按一下 \[**使用者**\]，並選取 \[**新增使用者**\]。將 \[**登入名稱**\] 設定為上一個步驟中建立的使用者。將使用者加入至資料庫角色成員資格 \[**System.Activities.DurableInstancing.InstanceStoreUsers**\] \(以及其他\)。請注意，使用者可能已存在 \(例如 dbo 使用者\)。  
  
5.  開啟 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中的 InstanceStore.sln 檔案，然後按 CTRL\+SHIFT\+B 建置方案。  
  
6.  在 [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] 中巡覽至範例的適當 bin\\debug 目錄 \(\\WF\\Basic\\Persistence\\BuiltInConfiguration\\cs\\InstanceStore\(1 或 2\)\\bin\\debug\)，然後以滑鼠右鍵按一下 \[InstanceStore.exe\] 並選取 \[**以系統管理員身分執行**\]。這個範例必須以系統管理權限執行，因為它會開啟通道接聽程式。  
  
7.  如果您在 SQL Server Express 的本機安裝以外的資料庫中建立了執行個體存放區，則必須更新範例中的資料庫連接字串 \(InstanceStore1 專案的 Program.cs 中為 `const string ConnectionString`，InstanceStore2 專案的 App.config 中為 `connectionString` 屬性\)，並且重新編譯範例。  
  
#### 若要驗證範例是否正常執行  
  
1.  在範例正在執行時，啟動 SQL Server Management Studio。  
  
2.  在 \[**物件總管**\] 中，依序選取 \[**資料庫**\]、\[**InstanceStore**\]、\[**資料表**\] 和 \[**System.Activities.DurableInstancing.InstanceTable**\]。  
  
3.  以滑鼠右鍵按一下 \[**InstanceTable**\]，然後選取 \[**選取前 1000 列**\]。  
  
4.  您會看見一個新項目，且 \[**鎖定期限**\] 每 5 秒會改變一次 \(按一下工作列的 \[**執行**\] 按鈕重新整理查詢\)。這是將 \[**Host Lock Renewal Period**\] 設為 5 的結果。  
  
5.  在計時完成之後，您會看見執行個體表中該項目已移除。這是將 \[**執行個體完成動作**\] 設為 \[**DeleteAll**\] 的結果。  
  
6.  按下 ENTER 終止工作流程主應用程式，就會看見 \[**LockOwnersTable**\] 已刪除。  
  
#### 若要解除安裝範例  
  
1.  執行範例目錄 \(\\WF\\Basic\\Persistence\\BuiltInConfiguration\) 中的 RemoveInstanceStore.cmd。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\BuiltInConfiguration`  
  
## 請參閱  
 [AppFabric 主控與持續性範例](http://go.microsoft.com/fwlink/?LinkId=193961)