---
title: "持續工作流程應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: abcff14c-f047-4195-ba26-d27f4a82c24e
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# 持續工作流程應用程式
這個範例示範如何執行 <xref:System.Activities.WorkflowApplication>，當它變成閒置時加以卸載，然後重新載入以繼續執行。  
  
## 範例詳細資料  
 <xref:System.Activities.WorkflowApplication> 是單一工作流程執行個體的主機，提供簡單介面以及啟用數個較為通用的裝載案例。這類案例之一是透過持續性、長時間執行的工作流程。持續性的主控制是透過在 <xref:System.Activities.WorkflowApplication> 呼叫持續性作業，或透過處理 <xref:System.Activities.WorkflowApplication> 事件並指示 <xref:System.Activities.WorkflowApplication> 應該保存來執行。  
  
 範例工作流程是提示使用者輸入名稱的 <xref:System.Activities.Statements.WriteLine> 活動、透過繼續使用 <xref:System.Activities.Bookmark> 接收名稱做為輸入的 `ReadLine` 活動，以及對使用者回應祝賀詞的另一個 <xref:System.Activities.Statements.WriteLine>。當工作流程等候輸入時，這會提供自然的保存點。這通常稱為<xref:System.Workflow.Runtime.Tracking.TrackingWorkflowEvent>點。當工作流程程式可保存、等候書籤繼續中，而且沒有其他工作正在執行時，<xref:System.Activities.WorkflowApplication> 就會引發 <xref:System.Workflow.Runtime.Tracking.TrackingWorkflowEvent> 事件。在這個範例的工作流程中，在 `ReadLine` 活動開始執行之後，隨即出現該點。  
  
 <xref:System.Activities.WorkflowApplication> 設為使用 <xref:System.Runtime.Persistence.InstanceStore> 來執行持續性。這個範例會使用 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>。<xref:System.Runtime.Persistence.InstanceStore> 必須先指派給 <xref:System.Activities.WorkflowApplication.InstanceStore%2A> 屬性，才能執行 <xref:System.Activities.WorkflowApplication>。  
  
 範例將處理常式加入至 <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> 事件。此事件處理常式傳回 <xref:System.Activities.PersistableIdleAction>，藉以指示 <xref:System.Activities.WorkflowApplication> 應該執行的工作。如果傳回 <xref:System.Activities.PersistableIdleAction>，則會卸載 <xref:System.Activities.WorkflowApplication>。  
  
 範例接著接受使用者輸入並將保存的工作流程載入至新的 <xref:System.Activities.WorkflowApplication>。執行的方式是建立新的 <xref:System.Activities.WorkflowApplication>、重新建立 <xref:System.Runtime.Persistence.InstanceStore>、將已完成和卸載的事件與執行個體產生關聯，接著呼叫具有目標工作流程執行個體識別碼的 <xref:System.Activities.WorkflowApplication.Load%2A>。一旦取得執行個體，則會繼續使用 `ReadLine` 活動的書籤。工作流程會從 `ReadLine` 活動中繼續執行，直到完成為止。當工作流程完成並卸載時，最後一次呼叫 <xref:System.Runtime.Persistence.InstanceStore> 以刪除工作流程。  
  
#### 若要使用這個範例  
  
1.  開啟 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元。  
  
     這個範例需要預設隨 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 一起安裝的 SQL Server Express。  
  
2.  巡覽至範例目錄 \(\\WF\\Basic\\Persistence\\InstancePersistence\\CS\)，並執行 CreateInstanceStore.cmd。  
  
    > [!CAUTION]
    >  CreateInstanceStore.cmd 指令碼會嘗試在 SQL Server 2008 Express 預設執行個體上建立資料庫。如果您想要在不同的執行個體上安裝資料庫，請修改指令碼。  
  
3.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 Persistence.sln 方案檔案，然後按 CTRL\+SHIFT\+B 建置方案。  
  
    > [!CAUTION]
    >  如果在非預設的 SQL Server 執行個體上安裝資料庫，請在建置方案之前，先更新程式碼中的連接字串。  
  
4.  在 [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] 中巡覽至專案的 bin 目錄 \(\\WF\\Basic\\Persistence\\InstancePersistence\\bin\\Debug\)，然後以滑鼠右鍵按一下 Workflow.exe 並選取 \[**以系統管理員身分執行**\]，以系統管理員權限執行此範例。  
  
#### 若要移除執行個體存放區資料庫  
  
1.  開啟 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元。  
  
2.  巡覽至範例目錄，並執行 RemoveInstanceStore.cmd。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\InstancePersistence`  
  
## 請參閱  
 [AppFabric 主控與持續性範例](http://go.microsoft.com/fwlink/?LinkId=193961)