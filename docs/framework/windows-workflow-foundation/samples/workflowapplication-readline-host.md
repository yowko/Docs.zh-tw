---
title: "WorkflowApplication ReadLine 主機"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7b362be-cb42-40d7-b9ef-cfc4aed2455b
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1ba33dff4be8ae3e75ee4d1873feeb4d5e5944b7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="workflowapplication-readline-host"></a>WorkflowApplication ReadLine 主機
這個範例為泛型 ReadLine 主機。 您可以使用包含的 `ReadLine` 活動來載入及執行任何工作流程 (或是與它類似的其他活動，從使用字串繼續的書籤中取得資料)。 來自 `WriteLine` 活動的輸出或是寫入 <xref:System.Activities.Statements.WriteLine.TextWriter%2A> 延伸模組的任何內容都會導向主機視窗。 當執行個體閒置時，該執行個體可用的書籤會出現在下拉式方塊中。 選取書籤、輸入某些文字並按下繼續書籤按鈕，將會繼續執行工作流程。 您也可以取消、中止或終止選取的工作流程。 預設會啟用持續性，您可以關閉主機並將它開啟，執行個體清單就會填入資料庫內所存放的執行個體。 追蹤是用來將 <xref:System.Activities.WorkflowApplication> 層級的事件輸出到主機，而且包含了加入活動層級之詳細追蹤的選項。  
  
## <a name="sample-details"></a>範例詳細資料  
 這個主機有兩層：檢視及執行個體管理員。 檢視是由 `HostView` 和 `WorkflowApplicationInfo` 類別所組成。 這個主機的一般模式是讓 `HostView` 類別根據 `WorkflowApplicationInfo` 物件顯示可用的選項給使用者，這些物件會合理地保持與其代表的執行個體同步的狀態。 執行個體管理員層是由 `WorkflowApplicationManager` 類別 (它是所有主機通訊的核心) 與 `WorkflowDefinitionExtension` 類別 (它會保存執行個體以及此執行個體一開始具備的程式定義之間的關聯性) 以及其他幾個類別所組成。 `HostView` 呼叫會控制 `WorkflowApplicationManager` 上的作業。 這些呼叫通常會以非同步方式來維護具有回應性的使用者介面。 當非同步呼叫完成時，`WorkflowApplicationManager` 會透過定義完善的介面 (`IHostView`) 回呼檢視層。 `HostView` 類別最常從 `WorkflowApplicationManager` 類別將這些呼叫發送給使用者介面執行緒。 文字寫入是針對 <xref:System.Activities.Statements.WriteLine.TextWriter%2A> 類別提供的安全執行緒 `HostView` 物件所執行。 使用者介面並不是產生事件的唯一項目。 例如，當 <xref:System.Activities.WorkflowApplication> 物件進入 `WorkflowApplicationManager`、`Idle` 或 `Complete` 狀態時，也會指示 `Aborted`。 `WorkflowApplicationManager` 類別會離開事件執行緒，其方式是將清除或更新工作發送給主機。  
  
 用來啟動 <xref:System.Activities.WorkflowApplication> 之檔案的記錄可由 `WorkflowDefinitionExtension` 類別來加速。 它會實作 <xref:System.Activities.Persistence.PersistenceIOParticipant> 介面來參與持續性，並保存工作流程定義的路徑。  
  
 `WorkflowApplicationManager.Load` 方法會使用預存路徑來具現化用來載入未完成的 <xref:System.Activities.WorkflowApplication> 物件所需的工作流程程式。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  這個範例需要安裝 SQL Express。 SQL Express 隨附於 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中。  
  
2.  開啟 Visual Studio 2010 命令提示字元。  
  
3.  巡覽至範例目錄 (\WF\Basic\Execution\ControllingWorkflowApplications) 並執行 CreateInstanceStore.cmd。  
  
4.  CreateInstanceStore.cmd 指令碼會嘗試在 SQL Server 2008 Express 預設執行個體上建立資料庫。 如果您想要在不同的執行個體上安裝資料庫，請修改指令碼。  
  
5.  編譯 WorkflowApplicationReadLineHost 專案，並從命令列執行它。  
  
6.  一旦執行專案之後，您可以選擇開啟或關閉持續性。 您可以進一步選擇開啟或關閉詳細活動追蹤。  
  
7.  按下省略符號按鈕旁的 **執行**按鈕瀏覽 XAML 檔案中定義的工作流程  
  
     您可以在 SampleWorkflows 資料夾底下找到兩個範例。 parallel1.xaml 範例會進入閒置狀態。  
  
8.  一旦選取範例之後，按**執行** 按鈕。  
  
9. 如果連接或在工作流程閒置時**書籤**下拉式方塊會填入可用的書籤。  
  
10. 此時的選項包括繼續書籤、取消、中止或終止工作流程。 您也可以關閉主機，然後重新啟動。 如果將持續性保留在開啟狀態，關閉主機時會卸載執行個體，並在啟動時重新載入。  
  
     若要繼續書籤，選取所需的書籤、 輸入的值，在文字方塊旁邊的下拉式方塊，然後按**繼續書籤**。  
  
#### <a name="to-remove-the-instance-store-database"></a>若要移除執行個體存放區資料庫  
  
1.  開啟 Visual Studio 2010 命令提示字元。  
  
2.  巡覽至範例目錄 (\WF\Basic\Execution\ControllingWorkflowApplications) 並執行 RemoveInstanceStore.cmd。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ControllingWorkflowApplications`