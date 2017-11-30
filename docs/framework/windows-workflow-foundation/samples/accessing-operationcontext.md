---
title: "存取 OperationContext"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 861329c3945a53bf6c8ceeb7487aa0ef9902c93a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="accessing-operationcontext"></a>存取 OperationContext
這個範例會示範如何傳訊活動 (<xref:System.ServiceModel.Activities.Receive>和<xref:System.ServiceModel.Activities.Send>) 可以與自訂範圍活動用來存取<xref:System.ServiceModel.OperationContext.Current%2A>以及附加或擷取傳出或傳入訊息中的自訂訊息標頭。  
  
## <a name="demonstrates"></a>示範  
 訊息活動、<xref:System.ServiceModel.Activities.ISendMessageCallback>、<xref:System.ServiceModel.Activities.IReceiveMessageCallback>。  
  
## <a name="discussion"></a>討論  
 這個範例示範如何在訊息活動中使用擴充點 (<xref:System.ServiceModel.Activities.ISendMessageCallback> 和 <xref:System.ServiceModel.Activities.IReceiveMessageCallback>)，以存取 <xref:System.ServiceModel.OperationContext.Current%2A>。 回呼是在工作流程執行階段中註冊成為 <xref:System.Activities.IExecutionProperty> 實作，而由訊息活動在完成時取用。 與該 <xref:System.Activities.IExecutionProperty> 實作位於相同範圍中的任何訊息活動都會受到影響。 尤其這個範例使用自訂範圍活動，強制執行回呼行為。 用戶端工作流程中會使用 <xref:System.ServiceModel.Activities.ISendMessageCallback>，包含工作流程的 <xref:System.Activities.WorkflowApplication.Id%2A> 做為傳出 <xref:System.ServiceModel.Channels.MessageHeader>。 接著服務會使用 <xref:System.ServiceModel.Activities.IReceiveMessageCallback> 取用此標頭，將標頭值印出至主控台。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  這個範例使用 HTTP 端點公開工作流程服務。 必須新增至執行此範例中，適當的 URL Acl (請參閱[設定 HTTP 和 HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353)如需詳細資訊)，以系統管理員身分執行 Visual Studio，或執行下列命令在提升權限的提示字元，加入適當的 Acl。 請確定您的網域和使用者名稱已用來取代。  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2.  一旦加入 URL ACL，請使用下列步驟。  
  
    1.  建置方案。  
  
    2.  設定多個啟始專案，以滑鼠右鍵按一下方案，然後選取**設定啟始專案**。  
  
    3.  新增**服務**和**用戶端**（依該順序） 做為多個啟始專案。  
  
    4.  執行應用程式。 用戶端主控台會顯示執行兩次的工作流程，而 [服務] 視窗會顯示這些工作流程的執行個體識別碼。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
