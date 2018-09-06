---
title: 存取 OperationContext
ms.date: 03/30/2017
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
ms.openlocfilehash: 3c7ce1c9c37ee93b58a07376e0aeae045f0ca408
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43735484"
---
# <a name="accessing-operationcontext"></a>存取 OperationContext
這個範例會示範如何傳訊活動 (<xref:System.ServiceModel.Activities.Receive>並<xref:System.ServiceModel.Activities.Send>) 可以與自訂範圍活動用來存取<xref:System.ServiceModel.OperationContext.Current%2A>以及附加或擷取傳出或傳入訊息中的自訂訊息標頭。  
  
## <a name="demonstrates"></a>示範  
 訊息活動、<xref:System.ServiceModel.Activities.ISendMessageCallback>、<xref:System.ServiceModel.Activities.IReceiveMessageCallback>。  
  
## <a name="discussion"></a>討論  
 這個範例示範如何在訊息活動中使用擴充點 (<xref:System.ServiceModel.Activities.ISendMessageCallback> 和 <xref:System.ServiceModel.Activities.IReceiveMessageCallback>)，以存取 <xref:System.ServiceModel.OperationContext.Current%2A>。 回呼是在工作流程執行階段中註冊成為 <xref:System.Activities.IExecutionProperty> 實作，而由訊息活動在完成時取用。 與該 <xref:System.Activities.IExecutionProperty> 實作位於相同範圍中的任何訊息活動都會受到影響。 尤其這個範例使用自訂範圍活動，強制執行回呼行為。 用戶端工作流程中會使用 <xref:System.ServiceModel.Activities.ISendMessageCallback>，包含工作流程的 <xref:System.Activities.WorkflowApplication.Id%2A> 做為傳出 <xref:System.ServiceModel.Channels.MessageHeader>。 接著服務會使用 <xref:System.ServiceModel.Activities.IReceiveMessageCallback> 取用此標頭，將標頭值印出至主控台。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  這個範例使用 HTTP 端點公開工作流程服務。 若要執行這個範例，適當的 URL Acl 必須加入 (請參閱[設定 HTTP 和 HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353)如需詳細資訊)，是由系統管理員身分執行 Visual Studio 或執行下列命令，提高權限的提示來加入適當 Acl。 請確定您的網域和使用者名稱已用來取代。  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2.  一旦加入 URL ACL，請使用下列步驟。  
  
    1.  建置方案。  
  
    2.  設定多個啟始專案，以滑鼠右鍵按一下方案，然後選取**設定啟始專案**。  
  
    3.  新增**服務**並**用戶端**（依此順序） 做為多個啟始專案。  
  
    4.  執行應用程式。 用戶端主控台會顯示執行兩次的工作流程，而 [服務] 視窗會顯示這些工作流程的執行個體識別碼。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
