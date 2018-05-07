---
title: 持續工作流程應用程式
ms.date: 03/30/2017
ms.assetid: abcff14c-f047-4195-ba26-d27f4a82c24e
ms.openlocfilehash: e5c0cf23dd238c0c5a81519b5e6c415f4ef75f1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="persisting-a-workflow-application"></a>持續工作流程應用程式
這個範例示範如何執行 <xref:System.Activities.WorkflowApplication>，當它變成閒置時加以卸載，然後重新載入以繼續執行。  
  
## <a name="sample-details"></a>範例詳細資料  
 <xref:System.Activities.WorkflowApplication> 是單一工作流程執行個體的主機，提供簡單介面以及啟用數個較為通用的裝載案例。 這類案例之一是透過持續性、長時間執行的工作流程。 持續性的主控制是透過在 <xref:System.Activities.WorkflowApplication> 呼叫持續性作業，或透過處理 <xref:System.Activities.WorkflowApplication> 事件並指示 <xref:System.Activities.WorkflowApplication> 應該保存來執行。  
  
 範例工作流程是提示使用者輸入名稱的 <xref:System.Activities.Statements.WriteLine> 活動、透過繼續使用 `ReadLine` 接收名稱做為輸入的 <xref:System.Activities.Bookmark> 活動，以及對使用者回應祝賀詞的另一個 <xref:System.Activities.Statements.WriteLine>。 當工作流程等候輸入時，這會提供自然的保存點。 這通常稱為 <xref:System.Workflow.Runtime.Tracking.TrackingWorkflowEvent.Idle> 點。 每當工作流程程式可保存、正在等候書籤繼續，而且沒有其他工作正在執行時，<xref:System.Activities.WorkflowApplication> 就會引發 <xref:System.Workflow.Runtime.Tracking.TrackingWorkflowEvent.Idle> 事件。 在這個範例的工作流程中，在 `ReadLine` 活動開始執行之後，隨即出現該點。  
  
 A<xref:System.Activities.WorkflowApplication>並將設定為執行與持續性<!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore`。 這個範例會使用 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>。 <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore`必須指派給<xref:System.Activities.WorkflowApplication.InstanceStore%2A>屬性之後再<xref:System.Activities.WorkflowApplication>執行。  
  
 範例將處理常式加入至 <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> 事件。 此事件處理常式傳回 <xref:System.Activities.WorkflowApplication>，藉以指示 <xref:System.Activities.PersistableIdleAction> 應該執行的工作。 如果傳回 <xref:System.Activities.PersistableIdleAction.Unload>，則會卸載 <xref:System.Activities.WorkflowApplication>。  
  
 範例接著接受使用者輸入並將保存的工作流程載入至新的 <xref:System.Activities.WorkflowApplication>。 它是藉由建立新<xref:System.Activities.WorkflowApplication>、 重新建立<!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore`，並將執行個體，已完成和卸載事件產生關聯，然後再呼叫<xref:System.Activities.WorkflowApplication.Load%2A>目標工作流程執行個體的識別碼。 一旦取得執行個體，則會繼續使用 `ReadLine` 活動的書籤。 工作流程會從 `ReadLine` 活動中繼續執行，直到完成為止。 當工作流程完成並卸載<!--zz <xref:System.Runtime.Persistence.InstanceStore> -->`System.Runtime.Persistence.InstanceStore`最後一次呼叫以刪除工作流程。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  開啟 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元。  
  
     這個範例需要預設隨 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 一起安裝的 SQL Server Express。  
  
2.  巡覽至範例目錄 (\WF\Basic\Persistence\InstancePersistence\CS)，並執行 CreateInstanceStore.cmd。  
  
    > [!CAUTION]
    >  CreateInstanceStore.cmd 指令碼會嘗試在 SQL Server 2008 Express 預設執行個體上建立資料庫。 如果您想要在不同的執行個體上安裝資料庫，請修改指令碼。  
  
3.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 來開啟 Persistence.sln 方案檔，然後按 CTRL+SHIFT+B 來建置方案。  
  
    > [!CAUTION]
    >  如果在非預設的 SQL Server 執行個體上安裝資料庫，請在建置方案之前，先更新程式碼中的連接字串。  
  
4.  瀏覽至專案的 bin 目錄 (\WF\Basic\Persistence\InstancePersistence\bin\Debug) 中執行範例，以系統管理員權限[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)]、 以滑鼠右鍵按一下 Workflow.exe 並選取**系統管理員身分執行**.  
  
#### <a name="to-remove-the-instance-store-database"></a>若要移除執行個體存放區資料庫  
  
1.  開啟 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元。  
  
2.  巡覽至範例目錄，並執行 RemoveInstanceStore.cmd。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\InstancePersistence`  
  
## <a name="see-also"></a>另請參閱  
 [AppFabric 主控與持續性範例](http://go.microsoft.com/fwlink/?LinkId=193961)
