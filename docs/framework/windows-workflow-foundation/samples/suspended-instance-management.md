---
title: 暫停的執行個體管理
ms.date: 03/30/2017
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
ms.openlocfilehash: ace4d2baef8f6b030790deaa5b1c20bb4b0cd30d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59319556"
---
# <a name="suspended-instance-management"></a>暫停的執行個體管理
這個範例會示範如何管理已暫止的工作流程執行個體。  <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> 的預設動作為 `AbandonAndSuspend`。 這表示根據預設，從裝載於 <xref:System.ServiceModel.WorkflowServiceHost> 中之工作流程執行個體所擲回的未處理例外狀況將會造成此執行個體從記憶體中處置 (放棄)，而且此執行個體的永久性/持續版本將會標示為已暫停。 暫停的工作流程執行個體要等到取消暫停之後才能夠執行。

 此範例會示範如何實作命令列公用程式來查詢暫停的執行個體，以及如何提供使用者繼續或終止執行個體的選擇。 在這個範例中，工作流程服務會故意擲回例外狀況，使得它遭到暫停。 然後可以使用此命令列公用程式來查詢執行個體，之後再繼續或終止執行個體。

## <a name="demonstrates"></a>示範
 <xref:System.ServiceModel.WorkflowServiceHost> 具有<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>和<xref:System.ServiceModel.Activities.WorkflowControlEndpoint>Windows Workflow Foundation (WF) 中。

## <a name="discussion"></a>討論
 這個範例中所實作的命令列公用程式是 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 隨附之 SQL 執行個體存放區實作所特有。 如果您擁有執行個體存放區的自訂實作，您可以改寫此公用程式，其方式是使用您的執行個體存放區所特有的實作來取代範例中的 `WorkflowInstanceCommand` 實作。

 提供的實作會直接針對 SQL 執行個體存放區來執行 SQL 命令，以列出暫停的執行個體，而且此實作會依賴加入至 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> 的 <xref:System.ServiceModel.WorkflowServiceHost> 來結束或終止執行個體。

#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例

1. 本範例需要啟用下列 Windows 元件：

    1.  Microsoft Message Queues (MSMQ) 伺服器

    2.  SQL Server Express

2. 設定 SQL Server 資料庫。

    1.  從 Visual Studio 2010 命令提示字元，執行"setup.cmd"從 SuspendedInstanceManagement 範例目錄，會執行下列作業：

        1.  使用 SQL Server Express 建立持續性資料庫。 如果持續性資料庫已經存在，請將它卸除然後重新建立。

        2.  設定資料庫擁有持續性。

        3.  將 IIS APPPOOL\DefaultAppPool 和 NT AUTHORITY\Network Service 加入至 InstanceStoreUsers 角色，這是設定資料庫擁有持續性時所定義的角色。

3. 設定服務佇列。

    1.  在 Visual Studio 2010 中，以滑鼠右鍵按一下**SampleWorkflowApp**專案，然後按一下**設定為啟始專案**。

    2.  編譯及執行 SampleWorkflowApp 按下**F5**。 這樣會建立所需的佇列。

    3.  按下**Enter**停止 SampleWorkflowApp。

    4.  從命令提示字元執行 Compmgmt.msc，開啟 [電腦管理] 主控台。

    5.  依序展開**服務和應用程式**， **Message Queuing**，**私用佇列**。

    6.  以滑鼠右鍵按一下**ReceiveTx**排入佇列，並選取**屬性**。

    7.  選取 **安全性**索引標籤，並允許**Everyone**擁有權限**接收訊息**，**查看訊息**，和**將訊息傳送**。

4. 現在，請執行範例。

    1.  在 Visual Studio 2010 中，執行 SampleWorkflowApp 專案一次但不偵錯，藉由按下**Ctrl + F5**。 兩個端點位址將會列印到主控台視窗：一個適用於應用程式端點，另一個來自 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>。 然後會建立工作流程執行個體，該執行個體的追蹤記錄將會出現在主控台視窗。 工作流程執行個體將會擲回例外狀況，造成執行個體被暫停及中止。

    2.  然後可以使用此命令列公用程式來針對任何執行個體採取進一步的動作。 命令列引數的語法如下：

         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`

         支援的命令為：`Query`、`Resume` 和 `Terminate`。  只有 `Resume` 和 `Terminate` 作業需要 InstanceId 參數。

#### <a name="to-cleanup-optional"></a>若要清除 (選擇性)

1. 從 `vs2010` 命令提示字元執行 Compmgmt.msc，開啟 [電腦管理] 主控台。

2. 依序展開**服務和應用程式**， **Message Queuing**，**私用佇列**。

3. 刪除**ReceiveTx**佇列。

4. 若要移除持續性資料庫，請執行 cleanup.cmd。

> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`
